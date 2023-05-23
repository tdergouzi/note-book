# openzeppelin-contracts



## 合约目录



```shell
.
├── access
│   ├── AccessControl.sol
│   ├── AccessControlCrossChain.sol
│   ├── AccessControlDefaultAdminRules.sol
│   ├── AccessControlEnumerable.sol
│   ├── IAccessControl.sol
│   ├── IAccessControlDefaultAdminRules.sol
│   ├── IAccessControlEnumerable.sol
│   ├── Ownable.sol
│   ├── Ownable2Step.sol
│   └── README.adoc
├── crosschain
│   ├── CrossChainEnabled.sol
│   ├── README.adoc
│   ├── amb
│   │   ├── CrossChainEnabledAMB.sol
│   │   └── LibAMB.sol
│   ├── arbitrum
│   │   ├── CrossChainEnabledArbitrumL1.sol
│   │   ├── CrossChainEnabledArbitrumL2.sol
│   │   ├── LibArbitrumL1.sol
│   │   └── LibArbitrumL2.sol
│   ├── errors.sol
│   ├── optimism
│   │   ├── CrossChainEnabledOptimism.sol
│   │   └── LibOptimism.sol
│   └── polygon
│       └── CrossChainEnabledPolygonChild.sol
├── finance
│   ├── PaymentSplitter.sol
│   ├── README.adoc
│   └── VestingWallet.sol
├── governance
│   ├── Governor.sol
│   ├── IGovernor.sol
│   ├── README.adoc
│   ├── TimelockController.sol
│   ├── compatibility
│   │   ├── GovernorCompatibilityBravo.sol
│   │   └── IGovernorCompatibilityBravo.sol
│   ├── extensions
│   │   ├── GovernorCountingSimple.sol
│   │   ├── GovernorPreventLateQuorum.sol
│   │   ├── GovernorProposalThreshold.sol
│   │   ├── GovernorSettings.sol
│   │   ├── GovernorTimelockCompound.sol
│   │   ├── GovernorTimelockControl.sol
│   │   ├── GovernorVotes.sol
│   │   ├── GovernorVotesComp.sol
│   │   ├── GovernorVotesQuorumFraction.sol
│   │   └── IGovernorTimelock.sol
│   └── utils
│       ├── IVotes.sol
│       └── Votes.sol
├── interfaces
│   ├── IERC1155.sol
│   ├── IERC1155MetadataURI.sol
│   ├── IERC1155Receiver.sol
│   ├── IERC1271.sol
│   ├── IERC1363.sol
│   ├── IERC1363Receiver.sol
│   ├── IERC1363Spender.sol
│   ├── IERC165.sol
│   ├── IERC1820Implementer.sol
│   ├── IERC1820Registry.sol
│   ├── IERC1967.sol
│   ├── IERC20.sol
│   ├── IERC20Metadata.sol
│   ├── IERC2309.sol
│   ├── IERC2612.sol
│   ├── IERC2981.sol
│   ├── IERC3156.sol
│   ├── IERC3156FlashBorrower.sol
│   ├── IERC3156FlashLender.sol
│   ├── IERC4626.sol
│   ├── IERC4906.sol
│   ├── IERC5267.sol
│   ├── IERC5313.sol
│   ├── IERC5805.sol
│   ├── IERC6372.sol
│   ├── IERC721.sol
│   ├── IERC721Enumerable.sol
│   ├── IERC721Metadata.sol
│   ├── IERC721Receiver.sol
│   ├── IERC777.sol
│   ├── IERC777Recipient.sol
│   ├── IERC777Sender.sol
│   ├── README.adoc
│   ├── draft-IERC1822.sol
│   └── draft-IERC2612.sol
├── metatx
│   ├── ERC2771Context.sol
│   ├── MinimalForwarder.sol
│   └── README.adoc
├── mocks
│   ├── AccessControlCrossChainMock.sol
│   ├── ArraysMock.sol
│   ├── CallReceiverMock.sol
│   ├── ConditionalEscrowMock.sol
│   ├── ContextMock.sol
│   ├── DummyImplementation.sol
│   ├── EIP712Verifier.sol
│   ├── ERC1271WalletMock.sol
│   ├── ERC165
│   │   ├── ERC165MaliciousData.sol
│   │   ├── ERC165MissingData.sol
│   │   ├── ERC165NotSupported.sol
│   │   └── ERC165ReturnBomb.sol
│   ├── ERC20Mock.sol
│   ├── ERC20Reentrant.sol
│   ├── ERC2771ContextMock.sol
│   ├── ERC3156FlashBorrowerMock.sol
│   ├── ERC4626Mock.sol
│   ├── EtherReceiverMock.sol
│   ├── InitializableMock.sol
│   ├── MulticallTest.sol
│   ├── MultipleInheritanceInitializableMocks.sol
│   ├── PausableMock.sol
│   ├── PullPaymentMock.sol
│   ├── ReentrancyAttack.sol
│   ├── ReentrancyMock.sol
│   ├── RegressionImplementation.sol
│   ├── SafeMathMemoryCheck.sol
│   ├── SingleInheritanceInitializableMocks.sol
│   ├── StorageSlotMock.sol
│   ├── TimelockReentrant.sol
│   ├── TimersBlockNumberImpl.sol
│   ├── TimersTimestampImpl.sol
│   ├── VotesMock.sol
│   ├── compound
│   │   └── CompTimelock.sol
│   ├── crosschain
│   │   ├── bridges.sol
│   │   └── receivers.sol
│   ├── docs
│   │   └── ERC4626Fees.sol
│   ├── governance
│   │   ├── GovernorCompMock.sol
│   │   ├── GovernorCompatibilityBravoMock.sol
│   │   ├── GovernorMock.sol
│   │   ├── GovernorPreventLateQuorumMock.sol
│   │   ├── GovernorTimelockCompoundMock.sol
│   │   ├── GovernorTimelockControlMock.sol
│   │   ├── GovernorVoteMock.sol
│   │   └── GovernorWithParamsMock.sol
│   ├── proxy
│   │   ├── BadBeacon.sol
│   │   ├── ClashingImplementation.sol
│   │   ├── UUPSLegacy.sol
│   │   └── UUPSUpgradeableMock.sol
│   ├── token
│   │   ├── ERC1155ReceiverMock.sol
│   │   ├── ERC20DecimalsMock.sol
│   │   ├── ERC20ExcessDecimalsMock.sol
│   │   ├── ERC20FlashMintMock.sol
│   │   ├── ERC20ForceApproveMock.sol
│   │   ├── ERC20MulticallMock.sol
│   │   ├── ERC20NoReturnMock.sol
│   │   ├── ERC20PermitNoRevertMock.sol
│   │   ├── ERC20ReturnFalseMock.sol
│   │   ├── ERC20VotesLegacyMock.sol
│   │   ├── ERC4626OffsetMock.sol
│   │   ├── ERC4646FeesMock.sol
│   │   ├── ERC721ConsecutiveEnumerableMock.sol
│   │   ├── ERC721ConsecutiveMock.sol
│   │   ├── ERC721ReceiverMock.sol
│   │   ├── ERC721URIStorageMock.sol
│   │   ├── ERC777Mock.sol
│   │   ├── ERC777SenderRecipientMock.sol
│   │   └── VotesTimestamp.sol
│   └── wizard
│       ├── MyGovernor1.sol
│       ├── MyGovernor2.sol
│       └── MyGovernor3.sol
├── package.json
├── proxy
│   ├── Clones.sol
│   ├── ERC1967
│   │   ├── ERC1967Proxy.sol
│   │   └── ERC1967Upgrade.sol
│   ├── Proxy.sol
│   ├── README.adoc
│   ├── beacon
│   │   ├── BeaconProxy.sol
│   │   ├── IBeacon.sol
│   │   └── UpgradeableBeacon.sol
│   ├── transparent
│   │   ├── ProxyAdmin.sol
│   │   └── TransparentUpgradeableProxy.sol
│   └── utils
│       ├── Initializable.sol
│       └── UUPSUpgradeable.sol
├── security
│   ├── Pausable.sol
│   ├── PullPayment.sol
│   ├── README.adoc
│   └── ReentrancyGuard.sol
├── token
│   ├── ERC1155
│   │   ├── ERC1155.sol
│   │   ├── IERC1155.sol
│   │   ├── IERC1155Receiver.sol
│   │   ├── README.adoc
│   │   ├── extensions
│   │   ├── presets
│   │   └── utils
│   ├── ERC20
│   │   ├── ERC20.sol
│   │   ├── IERC20.sol
│   │   ├── README.adoc
│   │   ├── extensions
│   │   ├── presets
│   │   └── utils
│   ├── ERC721
│   │   ├── ERC721.sol
│   │   ├── IERC721.sol
│   │   ├── IERC721Receiver.sol
│   │   ├── README.adoc
│   │   ├── extensions
│   │   ├── presets
│   │   └── utils
│   ├── ERC777
│   │   ├── ERC777.sol
│   │   ├── IERC777.sol
│   │   ├── IERC777Recipient.sol
│   │   ├── IERC777Sender.sol
│   │   ├── README.adoc
│   │   └── presets
│   └── common
│       ├── ERC2981.sol
│       └── README.adoc
├── utils
│   ├── Address.sol
│   ├── Arrays.sol
│   ├── Base64.sol
│   ├── Checkpoints.sol
│   ├── Context.sol
│   ├── Counters.sol
│   ├── Create2.sol
│   ├── Multicall.sol
│   ├── README.adoc
│   ├── ShortStrings.sol
│   ├── StorageSlot.sol
│   ├── Strings.sol
│   ├── Timers.sol
│   ├── cryptography
│   │   ├── ECDSA.sol
│   │   ├── EIP712.sol
│   │   ├── MerkleProof.sol
│   │   ├── SignatureChecker.sol
│   │   └── draft-EIP712.sol
│   ├── escrow
│   │   ├── ConditionalEscrow.sol
│   │   ├── Escrow.sol
│   │   └── RefundEscrow.sol
│   ├── introspection
│   │   ├── ERC165.sol
│   │   ├── ERC165Checker.sol
│   │   ├── ERC165Storage.sol
│   │   ├── ERC1820Implementer.sol
│   │   ├── IERC165.sol
│   │   ├── IERC1820Implementer.sol
│   │   └── IERC1820Registry.sol
│   ├── math
│   │   ├── Math.sol
│   │   ├── SafeCast.sol
│   │   ├── SafeMath.sol
│   │   ├── SignedMath.sol
│   │   └── SignedSafeMath.sol
│   └── structs
│       ├── BitMaps.sol
│       ├── DoubleEndedQueue.sol
│       ├── EnumerableMap.sol
│       └── EnumerableSet.sol
└── vendor
    ├── amb
    │   └── IAMB.sol
    ├── arbitrum
    │   ├── IArbSys.sol
    │   ├── IBridge.sol
    │   ├── IDelayedMessageProvider.sol
    │   ├── IInbox.sol
    │   └── IOutbox.sol
    ├── compound
    │   ├── ICompoundTimelock.sol
    │   └── LICENSE
    ├── optimism
    │   ├── ICrossDomainMessenger.sol
    │   └── LICENSE
    └── polygon
        └── IFxMessageProcessor.sol
```



## 合约解析

### access/AccessControl.sol

角色权限控制合约。

数据结构

```solidity
// line 51 - 58
struct RoleData {
	mapping(address => bool) members; // 该角色的地址映射表
	bytes32 adminRole;
}

mapping(bytes32 => RoleData) private _roles;

bytes32 public constant DEFAULT_ADMIN_ROLE = 0x00;
```

方法

```solidity
modifier onlyRole(bytes32 role){}
```

