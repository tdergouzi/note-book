# Foundry

Foundry is a framework for developing solidity.



## Install

MacOS or Linus

```sh
curl -L https://foundry.paradigm.xyz | bash

foundryup
```



## Project structure

```sh
.
├── README.md
├── cache
├── foundry.toml
├── lib
├── out
├── remappings.txt
├── script
├── src
├── test
└── tmp.md
```



## Test

### Contract templates

src/ERC20Token.sol

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract ERC20Token is ERC20, Ownable {
    constructor(string memory name, string memory symbol, uint256 totalSupply) ERC20(name, symbol) {
        _mint(msg.sender, totalSupply);
    }

    function mint(address to, uint256 amount) external onlyOwner {
        _mint(to, amount);
    }

    function burn(uint256 amount) external {
        _burn(msg.sender, amount);
    }
}

```

test/ERC20Token.t.sol

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "forge-std/Test.sol";
import "../src/token/ERC20Token.sol";

contract ERC20TokenTest is Test {
    ERC20Token erc20Token;

    address owner = address(0x1);
    address userA = address(0x2);
    uint256 totalSupply = 10000;

    function setUp() public {
        vm.startPrank(owner);
        erc20Token = new ERC20Token("Test Token", "TTT", totalSupply);
    }

    function testConstructor() public {
        assertEq(erc20Token.owner(), owner);
        assertEq(erc20Token.balanceOf(owner), totalSupply);
    }

    function testFailMintIfNotOwner() public {
        vm.prank(userA);
        erc20Token.mint(userA, 10000);
    }

    function testMint() public {
        erc20Token.mint(userA, 100);
        assertEq(erc20Token.balanceOf(userA), 100);
    }
}
```



### Standard libraries

设置下一次交易 caller 地址，仅限下一次交易

```solidity
function vm.prank(address) external;
```



设置下一次交易块高，设置的块高更新为当前块高

```solidity
function vm.roll(uint256) external;
```

与 hardhat 不同，fondry 测试环境运行在 VM ，测试交易不能完全模仿真实交易（可能需要配置），导致交易不会增加块高，需手动调整块高

```solidity
function testCase() public {
    assertEq(block.number, 1);
    erc20Token.mint(userA, 100);
    assertEq(block.number, 1); // block number 还是1
    vm.roll(block.number + 1); // cheatcode 手动配置块高
    assertEq(block.number, 2); // block number 变为2
}
```



合约中（测试合约 + 源合约）输出打印日志，需要配合测试输出级别 `-v` 使用

```solidity
import "forge-std/console.sol";

function testCase() public {
		console.log("blocknumber: %s", block.number);
}
```



### Commands

运行全部测试用例，默认运行项目根目录下test文件夹中所有 `testXXX.t.sol`格式的合约测试文件

```sh
forge test
```

运行单个测试文件

```sh
forge test --match-path testXXX.t.sol
```

运行单个文件中某个测试用例

```sh
forge test --match-path testXXX.t.sol --match-test "testFuncName"
```

运行测试用例时，日志输出

```sh
forge test --match-path testXXX.t.sol -v

-vv # 输出打印日志
-vvv # 输出失败测试用例的打印日志和执行流
-vvvv # Print execution traces for all tests, and setup traces for failing tests
-vvvvv # Print execution and setup traces for all tests
```

