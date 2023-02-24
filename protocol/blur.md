# Blur-Protocol



## 合约结构

```sh
BlurToken.sol ⭐️⭐️⭐️
 -inherits op/Ownable.sol
 -inherits op/ERC20.sol
 -inherits op/ERC20Votes.sol
 -inherits op/draft-ERC20Permit.sol
 -interface ITokenLockup.sol
 
BlurPool.sol ⭐️
 -inherites IBlurPool.sol
 -inherites op/UUPSUpgradeable.sol
 -inherites op/OwnableUpgradeable.sol

BlurExchange.sol ⭐️⭐️⭐️
 -inherites IBlurExchange.sol 
 -inherits op/Initializable.sol
 -inherites op/UUPSUpgradeable.sol
 -inherites op/OwnableUpgradeable.sol
 -library ReentrancyGuarded.sol
 -library EIP712.sol
 -library MerkleVerifier.sol
 -library OrderStructs.sol
 -interface IBlurPool.sol
 -interface IExecutionDelegate.sol
 -interface IPolicyManager.sol
 -interface IMatchingPolicy.sol

StandardPolicyERC721.sol ⭐️⭐️
 -inherites IMatchingPolicy.sol
 -library OrderStructs.sol

StandardCollectionBidPolicyERC721.sol ⭐️⭐️
 -inherites IMatchingPolicy.sol
 -library OrderStructs.sol

BlurSwap.sol ⭐️⭐️⭐️
 -inherites op/Ownable.sol
 -library op/ReentrancyGuard.sol
 -library MarketRegistry.sol
 -library SpecialTransferHelper.sol
 -interface IERC20.sol
 -interface IERC721.sol
 -interface IERC721.sol

MarketRegistry.sol ⭐️⭐️⭐️ UnVerify
```

[BlurToken.sol](https://etherscan.io/address/0x5283d291dbcf85356a21ba090e6db59121208b44#code)

[BlurPool.sol](https://etherscan.io/address/0x17584a148d27ac5d06d87771464dacbaf625ce45#code)

[BlurExchange.sol](https://etherscan.io/address/0x983e96c26782a8db500a6fb8ab47a52e1b44862d#code)

[StandardPolicyERC721.sol](https://etherscan.io/address/0x0000000000daB4A563819e8fd93dbA3b25BC3495#code)

[StandardCollectionBidPolicyERC721](https://etherscan.io/address/0x0000000000b92D5d043FaF7CECf7E2EE6aaeD232#code)

[BlurSwap](https://etherscan.io/address/0x39da41747a83aee658334415666f3ef92dd0d541#code)

[MarketRegistry](https://etherscan.io/address/0x3a574baC669F3B1CB54b92cCBAefbAFd07054d96)



## 合约功能分析





