
# QuestProtocol



## 合约结构

```sh
QuestFactory.sol ---- 工厂合约，用于创建 Quest 和 Quest 数据管理
		RabbitHoleReceipt.sol ---- 功能模块合约，嵌入工厂合约，底层为可升级ERC721合约
				ReceiptRenderer.sol ---- 库合约，作为元数据功能模块嵌入 RabbitHoleReceipt.sol
		RabbitHoleTickets.sol ---- 功能模块合约，嵌入工厂合约，底层为可升级ERC1155合约
				TickRenderer.sol ---- 库合约，作为元数据功能模块嵌入 RabbitHoleTickets.sol

Erc1155Quest.sol ---- 底层为ERC1155合约，继承 Quest 基础合约
		Quest.sol ---- Quest 基础合约，用于实现 Quest 业务逻辑，例如活动基础信息管理、用户奖励信息管理、奖励领取等
		
Erc20Quest.sol ---- 底层为ERC20合约，继承 Quest 基础合约
		Quest.sol ---- Quest 基础合约，用于实现 Quest 业务逻辑，例如活动基础信息管理、用户奖励信息管理、奖励领取等
```



## 合约概述

QuestProtocol 协议主要有 `QuestFactory.sol` 和 `Quest.sol` 两个合约为核心创建。

平台方直接 deploy：

- `QuestFactory.sol` 简称工厂
- `RabbitHoleReceipt.sol` 任务完成凭证 NFT
- `RabbitHoleTickets.sol` 暂时未用

项目方调用工厂合约方法 create：

- `Erc20Quest.sol` 20 奖励任务
- `Erc20Quest.sol` 1155 奖励任务

项目方通过工厂合约创建新的任务，配置信息如下：

```solidity
// 奖励 ERC20 token 任务配置 
rewardTokenAddress_, // 奖励 token 地址
endTime_, // 结束时间戳
startTime_, // 开始时间戳
totalParticipants_, // 总参与人数上限
rewardAmountOrTokenId_, // 单个任务完成奖励 token 数量或 tokenId
questId_, // Quest ID
address(rabbitHoleReceiptContract), // RabbitHoleReceipt 合约实例地址
questFee, // Quest 费率万分比，默认 2000/10000
protocolFeeRecipient // 协议手续费接收地址


// 奖励 ERC1155 token 任务配置 
rewardTokenAddress_, // 奖励 token 地址
endTime_, // 结束时间戳
startTime_, // 开始时间戳
totalParticipants_, // 总参与人数上限
rewardAmountOrTokenId_, // 单个任务完成奖励 token 数量或 tokenId
questId_, // Quest ID
address(rabbitHoleReceiptContract) // RabbitHoleReceipt 合约实例地址
```

用户完成项目方指定任务后，可调用平台方工厂合约领取一个平台方凭证 RabbitHole Receipt NFT

RabbitHole Receipt NFT 信息：

​	NFT 地址:  `RabbitHoleReceipt.sol` 合约地址

​	NFT tokenId: 从 0 开始单调递增，

​	NFT 元数据查询时动态生成，内容如下： 

```solidity
uint tokenId_, // NFT tokenId
string memory questId_, // 任务 ID
uint totalParticipants_, // 任务总人数
bool claimed_, // 是否已用于领取任务奖励
uint rewardAmount_, // 任务奖励 token 数量
address rewardAddress_ // 任务奖励 token 地址
```

RabbitHole Receipt NFT 未做灵魂绑定，用户可用于二级市场交易或领取项目方任务奖励。



## 合约分析

### QuestFactory.sol

#### 创建任务

调用者: 	项目方用户

功能: 		创建带有 token 奖励的 任务合约

注意点: 

- QuestFactory 维护了一个奖励 token 白名单，要求新 Quest 奖励 token 在白名单内，白名单由平台方账户管理。
- token 奖励类型，支持 ERC20 或者 ERC1155

```solidity
    /// @dev Create either an erc20 or erc1155 quest, only accounts with the CREATE_QUEST_ROLE can create quests
    /// @param rewardTokenAddress_ The contract address of the reward token
    /// @param endTime_ The end time of the quest
    /// @param startTime_ The start time of the quest
    /// @param totalParticipants_ The total amount of participants (accounts) the quest will have
    /// @param rewardAmountOrTokenId_ The reward amount for an erc20 quest or the token id for an erc1155 quest
    /// @param contractType_ The type of quest, either erc20 or erc1155
    /// @param questId_ The id of the quest
    /// @return address the quest contract address
    function createQuest(
        address rewardTokenAddress_,
        uint256 endTime_,
        uint256 startTime_,
        uint256 totalParticipants_,
        uint256 rewardAmountOrTokenId_,
        string memory contractType_,
        string memory questId_
    ) public onlyRole(CREATE_QUEST_ROLE) returns (address){...}
```



#### 领取 RabbitHole Receipt NFT

调用者: 	普通用户

功能: 		完成项目方 Quest 任务后，领取平台方凭证 RabbitHole Receipt NFT

注意点:  

- 方法校验签名是否有效，是否为平台签名账户所签
- 调用者账户地址是否已领取
- Quest 任务状态是否正确
- Quest 是否已达到领取总量上限

```solidity
    /// @dev mint a RabbitHole Receipt. Note: this contract must be set as Minter on the receipt contract
    /// @param questId_ The id of the quest
    /// @param hash_ The hash of the message
    /// @param signature_ The signature of the hash
    function mintReceipt(string memory questId_, bytes32 hash_, bytes memory signature_) public {
        if (quests[questId_].numberMinted + 1 > quests[questId_].totalParticipants) revert OverMaxAllowedToMint();
        if (quests[questId_].addressMinted[msg.sender] == true) revert AddressAlreadyMinted();
        if (!QuestContract(quests[questId_].questAddress).hasStarted()) revert QuestNotStarted();
        if (block.timestamp < QuestContract(quests[questId_].questAddress).startTime()) revert QuestNotStarted();
        if (block.timestamp > QuestContract(quests[questId_].questAddress).endTime()) revert QuestEnded();
        if (keccak256(abi.encodePacked(msg.sender, questId_)) != hash_) revert InvalidHash();
        if (recoverSigner(hash_, signature_) != claimSignerAddress) revert AddressNotSigned();

        quests[questId_].addressMinted[msg.sender] = true;
        quests[questId_].numberMinted++;
        emit ReceiptMinted(msg.sender, questId_);
        rabbitHoleReceiptContract.mint(msg.sender, questId_);
    }
```



### Quest.sol

#### 领取任务奖励

调用者: 	普通用户

功能: 		账户拥有 RabbitHole Receipt NFT，领取对应 Quest 任务奖励

注意点: 

- 任务和合约会主动查询调用者账户拥有多少个该任务的 RabbitHole Receipt NFT
- 如果拥有多个 RabbitHole Receipt NFT，则一次性领取 NFT 数量对应倍数的奖励
- 领取奖励后，对应 NFT 的 tokenId 会被标记为已领取，避免二次领取

```solidity
    /// @notice Allows user to claim the rewards entitled to them
    /// @dev User can claim based on the (unclaimed) number of tokens they own of the Quest
    function claim() public virtual onlyQuestActive {
        if (isPaused) revert QuestPaused();

        uint[] memory tokens = rabbitHoleReceiptContract.getOwnedTokenIdsOfQuest(questId, msg.sender);

        if (tokens.length == 0) revert NoTokensToClaim();

        uint256 redeemableTokenCount = 0;
        for (uint i = 0; i < tokens.length; i++) {
            if (!isClaimed(tokens[i])) {
                redeemableTokenCount++;
            }
        }

        if (redeemableTokenCount == 0) revert AlreadyClaimed();

        uint256 totalRedeemableRewards = _calculateRewards(redeemableTokenCount);
        _setClaimed(tokens);
        _transferRewards(totalRedeemableRewards);
        redeemedTokens += redeemableTokenCount;

        emit Claimed(msg.sender, totalRedeemableRewards);
    }
```



## 总结

从交易手续费角度出发，普通用户的交易手续费变高了，需要先领取平台方任务凭证 NFT 然后再领取对应的任务奖励，除去任务本身交易，需要额外两笔交易。平台方任务凭证 NFT 合约本身集合 openzeppeling ERC721 多个模块，单独增发一个 NFT 的成本较高。

从资产角度出发，平台方凭证 NFT 可以作为普通资产在二级市场进行流通，用户可以通过直接购买平台方凭证 NFT，然后通过一笔交易一次性领取多笔任务奖励。



## 测试网

```sh
Owner: 0x07fF0ed51ABAf0ebeF2dDdabB463A0E17235de46

ReceiptRenderer: 0x89b7cB5Bc86c3FB9f17bB7d2990c3553A4D52323

RabbitHoleReceipt: 0x5d5a4c0dF6E4E16dc72bbb02567884090a436510
	royaltyRecipient_: 0x07fF0ed51ABAf0ebeF2dDdabB463A0E17235de46
	minterAddress_: 0x07fF0ed51ABAf0ebeF2dDdabB463A0E17235de46
	royaltyFee_: 2000
	
TicketRenderer: 0xC8B0fFe62b0712e6Aa158124fd3c6E5f96ED04C9

RabbitHoleTickets: 0x8f6A4a445293732714FaD075998b4688C53704Fa
	royaltyRecipient_: 0x07fF0ed51ABAf0ebeF2dDdabB463A0E17235de46
	minterAddress_: 0x07fF0ed51ABAf0ebeF2dDdabB463A0E17235de46
	royaltyFee_: 2000
	
RewardERC20Token: 0x2c30A11267b4f0e630396e915dB89b9F8c98a236
	initialSupply: 10000
	
Erc20Quest: 0xb5e6833d71adb475aA82F2A39d46Ecf20C500126
	rewardTokenAddress_: 0x2c30A11267b4f0e630396e915dB89b9F8c98a236
	endTime_: 1677346040
	startTime_: 1676346040
	totalParticipants_: 100
	rewardAmountInWeiOrTokenId_: 10
	questId_: "helloworld"
	receiptContractAddress_: 0x5d5a4c0dF6E4E16dc72bbb02567884090a436510
	questFee_: 2000
	protocolFeeRecipient_: 0x07fF0ed51ABAf0ebeF2dDdabB463A0E17235de46

RewardERC1155token: 0xD9067a87d94ddA8dCD9A02CbAdaAD450Eec755a8
	tokenId: 1
	amount: 100
	
Erc1155Quest: 0x9Be425407db241f4164387154280DE037A737984
	rewardTokenAddress_: 0xD9067a87d94ddA8dCD9A02CbAdaAD450Eec755a8
	endTime_: 1677346040
	startTime_: 1676346947
	totalParticipants_: 100
	rewardAmountInWeiOrTokenId_: 1
	questId_: "helloworldv2"
	receiptContractAddress_: 0x5d5a4c0dF6E4E16dc72bbb02567884090a436510
	
QuestFactory: 0x811fB2F054520Aa48F5Fb96EAC7cd82Fe9E494e6
	claimSignerAddress_: 0x07fF0ed51ABAf0ebeF2dDdabB463A0E17235de46
	rabbitHoleReceiptContract_: 0x5d5a4c0dF6E4E16dc72bbb02567884090a436510
	rabbitHoleTicketsContract_: 0x8f6A4a445293732714FaD075998b4688C53704Fa
	protocolFeeRecipient_: 0x07fF0ed51ABAf0ebeF2dDdabB463A0E17235de46
	erc20QuestAddress_: 0xb5e6833d71adb475aA82F2A39d46Ecf20C500126
	erc1155QuestAddress_: 0x9Be425407db241f4164387154280DE037A737984
```



## 待补充

1. 合约内费率机制分析