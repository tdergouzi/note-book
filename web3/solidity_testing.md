# Solidity Testing



*“Truth can only be found in one place: the code”* - Robert C. Martin



## Concepts



### F.I.R.S.T

- Fast - The speed of testing should be very fast.
- Independent - Each testing should be independent and can be run by any 顺序.
- Repeatable - Testing can be run in any enviroment.
- Self-validating - There should be a exact result which type is boolean when the test passed.
- Timely - Write your testing code before production.



### AAA (Arrange-Act-Assert)

AAA is the stardard mode in software testing. It suggests split testing into three parts: arrange, act and assert. Every part should be responsible to the meaning of the part's name.

- Arrange - Setup the testing code.
- Act - Call the testing functions.
- Assert - Check the result.

Every test must use only one assertion.



### Testing split

#### Unit test 

Testing the target function is suitable. This usually is a independent function, We need to test the function by diffierent parameters and make sure the result is right.

#### Intergration test

Testing the connection between the unit software developed independently. There will be many interactions in contracts.



### Percent of coverage

If you want the application will work successulf, Write the testing code is not enough. You will never know how much codes is testing, the percent of coverage is an useful tool for helping you figure it out.

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
