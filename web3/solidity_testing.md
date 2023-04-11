# Solidity Testing



*“Truth can only be found in one place: the code”* - Robert C. Martin



## Concepts



### F.I.R.S.T

- Fast - The testing speed should be fast enough to run them frequently.
- Independent - The tests should be independent of each other and able to run in any order.
- Repeatable - The tests should be repeatable in any enviroment.
- Self-validating - If the test passes, there should be clear (boolean) output.
- Timely - Write your testing code before the production.



### AAA (Arrange-Act-Assert)

AAA (Arrange-Act-Assert) pattern is one of the most common standards in sofrware testing. It suggests dividing tests into corresponding sections: arrange, act, and assert. Each of them is responsible for the part that they are named after.

- Arrange - Codes required for setting up the test.
- Act - Call the testing functions.
- Assert - Check if the expectations have been met.

Use only one asserttion per test.

### Testing separation

#### Unit testing

Determine if  the source code unit is suitable for use. This is typically done by testing a single function with different parameters to ensure it returns expected result.

#### Intergration testing

To determine whether an independently developed software unit works properly when connected, for smart contracts, this means verifying the interaction between different components within a single contract or among multiple contracts.

### Test coverage

Writing a good tests to ensure your application works as expected is not enough. Without measuring anything, it's hard to say how much of your code is  actually being tested. Test coverage is a useful tool for identifying sections of your codebase that are not being tested.

About the exact percent, it depends on you. But it should be high as possible. There will be many unexcept result happen when does not test the codes.



### Testing tool

Hardhat

Foundry

Waffle

Remix

Solidity-coverage



## Safety & Code analyse

Static analyse is an analyse methods without execute the code.

Smart contract development tools:

- Echidna
- Manticore
- Mythril
- Oyente
- Slither



## Continuous Intergration (CI)

Although continuous intergration is not a part of code-clean principle, it has been the base thing in developing code. The major adventage of CI is you can find the reason and source when some error happened.

CI followed a series of principles:

- Keep a storage repository that contains all source codes, anyone can get current version and history
- Automatic consutruc process that allows anyone call build the code from source code.
- Automatic testing, anyone can easy run your test cases any time.
- Make sure the result is tranparency, and any can get the executeable profile duration contructor process.



*"Continuous intergration doesn't get rid of bugs, but it does make them dramatically easier to find and remove." -- Martin Fowler*
