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
		// 角色数据
		struct RoleData {
        mapping(address => bool) members; // 角色地址-布尔映射表
        bytes32 adminRole; // 角色管理员角色，只有拥有该角色的账户地址拥有权限添加该角色的账户地址（有点绕口）
    }

		// 角色-角色数据映射表
    mapping(bytes32 => RoleData) private _roles;

		// 默认管理员角色 key
    bytes32 public constant DEFAULT_ADMIN_ROLE = 0x00;

    modifier onlyRole(bytes32 role) {
        _checkRole(role);
        _;
    }
```

方法

```solidity
// IERC165-supportsInterface 用于校验合约是否实现继承的 interfaces
function supportsInterface(bytes4 interfaceId) public view returns (bool);

// 获取账户地址是否拥有指定的角色
function hasRole(bytes32 role, address account) public view returns (bool);

// 获取目标角色管理角色
function getRoleAdmin(bytes32 role) public view returns (bytes32);

// 授予目标地址角色权限
// 要求调用者拥有管理员角色权限
function grantRole(bytes32 role, address account) public onlyRole(getRoleAdmin(role));

// 撤销目标地址角色权限
// 要求调用者拥有管理员角色权限
function revokeRole(bytes32 role, address account) public onlyRole(getRoleAdmin(role));

// 放弃角色权限
// 要求调用者放弃本人所拥有权限
function renounceRole(bytes32 role, address account) public;
```



### access/AccessControlCrossChain.sol

继承 `AccessControl.sol` 、`CrossChainEnabled`.sol 合约，扩展跨链权限管理。

方法：

```solidity
// 校验调用者角色权限
// 如果为跨链调用，校验跨链调用者是否拥有跨链角色权限
// 如果非跨链调用，直接校验
function _checkRole(bytes32 role) internal view;

// 获取跨链角色，存在多个链相同地址导致权限问题。
// 例如同一账户地址在 A 链拥有高等级权限，而在 B 链没有权限控制，那就容易造成跨链调用的权限判断错误。
// 数据设计上，基于原来的角色异或位运算生成跨链角色，用于管理跨链调用者角色权限
function _crossChainRoleAlias(bytes32 role) internal pure returns (bytes32);
```



### access/AccessControlDefaultAdminRules

`AccessControl.sol` 扩展合约，继承 `AccessControl.sol` 功能，扩展增加管理员。

数据结构：

```solidity
    address private _pendingDefaultAdmin; // 待定管理员地址
    uint48 private _pendingDefaultAdminSchedule; // 待定管理员被确认的时间点

    uint48 private _currentDelay; // 默认周期时长
    address private _currentDefaultAdmin; // 默认管理员地址

    uint48 private _pendingDelay; // 待定周期时长
    uint48 private _pendingDelaySchedule; // 待定周期时长有效时间点，有效期内不可修改
```

方法：

```solidity
// IERC165-supportsInterface 用于校验合约是否实现继承的 interfaces
function supportsInterface(bytes4 interfaceId)

// IERC5313-owner
function owner()

// 覆写 AccessControl 实现，增加管理员角色不可操作的校验
function grantRole(bytes32 role, address account) public virtual override(AccessControl, IAccessControl);

// 覆写 AccessControl 实现，增加管理员角色不可操作的校验
function revokeRole(bytes32 role, address account) public virtual override(AccessControl, IAccessControl);

// 覆写 AccessControl 实现
// 要求待确认管理员地址为0地址
function renounceRole(bytes32 role, address account) public virtual override(AccessControl, IAccessControl);

// 获取当前默认管理员账户地址
function defaultAdmin() public view virtual returns (address);

// 获取待定管理员地址和被确认时间点
function pendingDefaultAdmin() public view virtual returns (address newAdmin, uint48 schedule);

// 获取确认周期时长
// 优先判断是否存在待定周期时长，如果存在则返回待定周期时长，否则返回默认周期时长
function defaultAdminDelay() public view virtual returns (uint48);

// 获取待定周期时长和有效时间点
// 未设置，默认0
function pendingDefaultAdminDelay() public view virtual returns (uint48 newDelay, uint48 schedule);

// 暂时没搞明白这个参数是干嘛的。
function defaultAdminDelayIncreaseWait() public view virtual returns (uint48);

// 申请管理员角色转移
// 要求调用者为当前管理员角色
function beginDefaultAdminTransfer();

// 撤销管理员角色转移
// 要求调用者为当前管理员角色
function cancelDefaultAdminTransfer();

// 接受管理员角色转移
// 要求调用者为新管理员角色
function acceptDefaultAdminTransfer();

// 更新待定周期时长
// 要求调用者为当前管理员角色
function changeDefaultAdminDelay();

// 重制待定周期时长
// 要求调用者为当前管理员角色
function rollbackDefaultAdminDelay();
```

