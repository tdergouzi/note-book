
## Contract SDK

### Factory

Factory 为合约工厂模块，用于用户自行部署对应的合约。

```js
    /**
     * @dev 部署 token 合约
     * @param name string token 名称
     * @param symbol string token 符号
     * @param totalSupply number token 发行总量
     */
    deployERC20Token(name, symbol, totalSupply)


    /**
     * @dev 部署 721 nft 合约
     * @param name string nft 名称
     * @param symbol string nft 符号
     */
    deployERC721Token(name, symbol)


    /**
     * @dev 部署 1155 nft 合约
     * @param name string token 名称
     * @param symbol string token 符号
     * @param uri string 基础 tokenURI，tokenURI 前缀
     */
    deployERC1155Token(name, symbol, uri)


    /**
     * @dev 部署活动打卡合约
     * @param treasury string 金库账户地址
     */
    deployActivityPunchIn(treasury)


    /**
     * @dev 部署 nft 英式拍卖合约
     */
    deployNFTEnglishAuction()


    /**
     * @dev 部署 nft 定价售卖合约
     */
    deployNFTFixedswap()


    /**
     * @dev 部署 IFO 合约
     * @param treasury string 金库账户地址
     * @param lpToken string 募集 token 地址
     * @param offeringToken string IFO 出售 token 地址
     * @param startBlock number 活动开始块高度
     * @param endBlock number 活动结束块高度
     * @param offeringAmount number IFO 出售 token 总量
     * @param raisingAmount number IFO 募集 token 总量
     */
    deployIFO(treasury, lpToken, offeringToken, startBlock, endBlock, offeringAmount, raisingAmount)


    /**
     * @dev 部署单币挖矿合约
     * @param treasury string 金库账户地址
     * @param depositToken string 质押 token 地址
     * @param rewardToken string 奖励 token 地址
     * @param startBlock number 活动开始块高度
     * @param mintPerBlock number 单个块产出奖励 token 数量
     * @param lockDuration number 质押 token 锁仓时长
     */
    deploySinglePool(treasury, depositToken, rewardToken, startBlock, mintPerBlock, lockDuration)

```


### ERC20Token

ERC20Token 基础 20 token 合约。目前该合约增发权限仅创建者。

```js
    /**
     * @dev 增发 token
     * @notice 合约拥有者才能调用
     * @param to string 接收 token 的地址
     * @param amount number token 数量（不带位数）
     */
    mint(to, amount)


    /**
     * @dev 查询地址余额
     * @param user string 用户地址
     */
    balanceOf(user)


    /**
     * @dev 查询 token 信息，包括名称，符号，位数
     */
    info()


    /**
     * @dev 批准额度
     * @param spender string 被批准者账户地址
     */
    approve(spender)


    /**
     * @dev 查询被批准额度
     * @param spender string 被批准者账户地址
     */
    allowance(spender)


    /**
     * @dev 转移 token
     * @param to string 接收 token 的地址
     * @param amount number token 数量（不带位数） 
     */
    transfer(to, amount)


    /**
     * @dev 销毁 token
     * @param amount number token 数量（不带位数） 
     */
    burn(amount)
```


### ERC721Token

ERC721Token 基础 721 类型 NFT 合约。目前该合约增发权限仅创建者。

```js
    /**
     * @dev 配置基础 URI，如果存在则作为每个 tokenURI 的前缀
     * @notice 拥有者权限调用
     * @param baseURI string 基础 URI
    */
    setBaseURI(baseURI)


    /**
     * @dev 增发一个 token
     * @notice 拥有者权限调用
     * @param to string 接受者账户地址，用于接受增发的 token
     * @param tokenURI string token 元数据, 不传默认为空字符串
    */
    mint(to, tokenURI)


    /**
     * @dev 获取 nft 信息
    */
    info()


    /**
     * @dev 获取合约 token 总量
     */
    totalSupply()


    /**
     * @dev 获取用户拥有的 token 总量
     * @param owner string 账户地址
     */
    balanceOf(owner)


    /**
     * @dev 查询 tokenURI(元数据)
     * @param tokenId number token ID
     */
    tokenURI(tokenId)


    /**
     * @dev 查询 tokenId 所有者的账户地址
     * @param tokenId number token ID
     */
    ownerOf(tokenId)


    /**
     * @dev 查询 token 所有者是否将自己所有的 token 的转移权限批准给操作人
     * @param owner string token 所有者的账户地址
     * @param operator string 操作人账户地址
     */
    isApprovedForAll(owner, operator)


    /**
     * @dev 查询 token 被批准人的账户地址
     * @param tokenId number token ID
     */
    getApproved(tokenId)


    /**
     * @dev 将指定 token 批准给目标账户
     * @notice 要求 token 所有者调用
     * @param to string 被批准人账户地址
     * @param tokenId number 指定的 token ID
    */
    approve(to, tokenId)


    /**
     * @dev 调用者拥有的 token 对目标账户的批准状态
     * @notice 要求调用者账户地址与目标账户不能相同
     * @param operator string 操作人账户地址
     * @param approved bool 批准状态 [true: 已批准, false: 未批准]
    */
    setApprovalForAll(operator, approved)


    /**
     * @dev 将指定 token 从所有者账户转移至目标账户
     * @notice 如果调用者不是 token 所有人，要求该 token 已经被批准给调用者账户地址
     * @param from string token 所有者账户地址
     * @param to string token 接受者账户地址
     * @param tokenId number token id
    */
    transferFrom(from, to, tokenId)


    /**
     * @dev 销毁 nft
     * @notice 用户只能销毁自己的 nft
     * @param tokenId number 指定的 token ID
    */
    burn(tokenId)
```


### ERC1155Token

ERC1155Token 基础 1155 类型 NFT 合约。目前该合约增发权限仅创建者。

```js
    /**
     * @dev 配置基础 URI，如果存在则作为每个 tokenURI 的前缀
     * @notice 拥有者权限调用
     * @param baseURI string 基础 URI
    */
    setBaseURI(baseURI)


    /**
     * @dev 向指定账户中增发指定类型的 token
     * @notice 拥有者权限调用
     * @param account string 接受者账户地址
     * @param amount number 增发数量
     * @param tokenURI string token 元数据, 不传默认为空字符串
    */
    mint(account, amount, tokenURI)


    /**
     * @dev 增发 token 的数量
     * @notice 拥有者权限调用
     * @param account string 接受者账户地址
     * @param id number 增发数量
     * @param amount number 增发数量
    */
    mintAmount(account, id, amount)


    /**
     * @dev 获取 nft 信息
    */
     info()


    /**
     * @dev 查询 tokenURI(元数据)
     * @param id number token ID
    */
    tokenURI(id)


    /**
     * @dev 根据 token id, 查询用户 token 的数量
     * @param account string 账户地址
     * @param id number ERC1155 token 唯一标识符
    */
    balanceOf(account, id)


    /**
     * @dev 批量查询用户 token 的数量
     * @notice 要求 accounts ids 数组长度一致
     * @param accounts [string] 账户地址数组
     * @param ids [number] ERC1155 token 唯一标识符
    */
    balanceOfBatch(accounts, ids)


    /**
     * @dev 查询操作者地址是否拥有指定账户所有 token 的转移权限
     * @param account string token 拥有者账户地址
     * @param operator string 操作者账户地址
    */
    isApprovedForAll(account, operator)


    /**
     * @dev 设置调用者所拥有的 token 的转移权限
     * @param operator string 操作者账户地址
     * @param approved bool  批准状态 [true: 批准, false: 未批准]
    */
    setApprovalForAll(operator, approved)


    /**
     * @dev 从转出账户地址转移指定数量的 token 至接收账户地址
     * @notice 要求调用者拥有转出账户的批准，或者调用者为转出账户
     * @param from string 转出账户地址
     * @param to string 接受账户地址
     * @param id number token id
     * @param amount number 转移数量
    */
    safeTransferFrom(from, to, id, amount)


    /**
     * @dev 批量从转出账户地址转移不同数量的不同 token 至接收账户地址
     * @notice 要求调用者拥有转出账户的批准，或者调用者为转出账户
     * @param from string 转出账户地址
     * @param to string 接受账户地址
     * @param ids [number] token id 数组
     * @param amounts [number] 转移数量数组
    */
    safeBatchTransferFrom(from, to, ids, amounts)


    /**
     * @dev 销毁token
     * @notice 要求调用者拥有被销毁账户的批准，或者调用者为被销毁账户
     * @param account string 被销毁账户地址
     * @param id number token 类型 id
     * @param amount number 销毁数量
    */
    burn(account, id, amount)
```


### NFTEnglishAuction

NFTEnglishAuction 为 NFT 英式拍卖售卖市场合约，创建者部署合约后，用户可自由在本合约内交易 NFT 英式拍卖单。用户可参与订单竞拍，最终订单结束，最高出价者购得 NFT。

```js
    /**
     * @dev 设置是否禁止挂售721 nft
     * @notice 拥有者权限调用
     * @param res bool [true: 禁止，false: 允许]
     */
    setDisableErc721(res)


    /**
     * @dev 设置是否禁止挂售1155 nft
     * @notice 拥有者权限调用
     * @param res bool [true: 禁止，false: 允许]
     */
    setDisableErc1155(res)


    /**
     * @dev 查询总挂单数量
    */
    getPoolCount()


    /**
     * @dev 通过游标查询挂单信息
     * @notice 游标取值范围可以通过 {getPoolCount} 方法获取
     * @param index number 挂单游标
     * @return 
     * {
     *      creator: 挂单人账户地址
     *      name: 名称
     *      token0: 换出 token 的合约地址（NFT 合约地址）
     *      token1: 换入 token 的合约地址（token 合约地址）
     *      tokenId: 换出 token 的 tokenId
     *      tokenAmount0: 换出 token tokenId 的数量
     *      amountMax1: 换出最高价格
     *      amountMin1: 换出最低价格
     *      amountMinIncr1: 单次出价最低加价数量
     *      openAt: 挂单开售时间
     *      closeAt: 挂单结束时间
     *      nftType: 换出 token 的类型， [0:ERC721, 1:ERC1155]
     *      reserveAmount1: 查询挂单最低成交价
     * }
    */
    getPoolBaseInfo(index)


    /**
     * @dev 通过游标查询挂单动态信息
     * @notice 游标取值范围可以通过 {getPoolCount} 方法获取
     * @param index number 挂单游标
     * @return 
     * {
     *      bidCount: 挂单竞价数量
     *      currentBidder: 当前最高价竞拍者地址
     *      currentBidderAmount1: 当前竞拍最高价
     *      currentBidderAmount: 挂单下一次竞价出价数量
     *      creatorClaimed: 挂单创建人是否已领取挂单
     *      bidderClaimed: 竞拍获胜者是否已领取挂单
     * }
    */
    getPoolDynamicInfo(index)


    /**
     * @dev 查询挂单创建人是否已领取挂单
     * @param index number 挂单游标
    */
    creatorClaimedPool(index)


    /**
     * @dev 查询挂单当前最高价竞拍者地址
     * @param index number 挂单游标
    */
    currentBidderPool(index)


    /**
     * @dev 查询挂单当前竞拍最高价
     * @param index number 挂单游标
    */
    currentBidderAmount1Pool(index)


    /**
     * @dev 查询用户某个挂单出价
     * @param user string 账户地址
     * @param index number 挂单游标
    */
    myBidderAmount1Pool(user, index)


    /**
     * @dev 查询挂单竞价数量
     * @param index number 挂单游标
    */
    bidCountPool(index)


    /**
     * @dev 查询挂单下一次竞价出价数量，即当前最高竞价数量加上加价间隔
     * @param index number 挂单游标
    */
    currentBidderAmount(index)


    /**
     * @dev 查询目标用户是否为挂单创建人
     * @param target string 目标用户地址
     * @param index number 挂单游标
    */
    isCreator(target, index)


    /**
     * @dev 查询合约配置信息
     * @return 
     * {
     *      disableErc721: 是否禁止挂 ERC721 类型的 NFT [true: 禁止, false:未禁止] 默认 false
     *      disableErc1155: 是否禁止挂 ERC1155 类型的 NFT [true: 禁止, false:未禁止] 默认 false
     * }
    */
    getConfig()


    /**
     * @dev 创建 ERC721 类型挂单
     * @notice 创建挂单之前，需要将出售的 token 批准给挂单合约，否则挂单失败
     * @param name string 名称
     * @param token0 string 换出 token 的合约地址（NFT 合约地址）
     * @param token1 string 换入 token 的合约地址（token 合约地址）
     * @param tokenId number 换出 token 的 tokenId
     * @param amountMax1 number 换出最高价格
     * @param amountMin1 number 换出最低价格
     * @param amountMinIncr1 number 单次出价最低加价数量
     * @param amountReserve1 number 
     * @param openAt number 挂单开售时间，unix timestamp
     * @param duration number 挂单持续时间，单位秒
    */
    createErc721(
        name,
        token0,
        token1,
        tokenId,
        amountMax1,
        amountMin1,
        amountMinIncr1,
        amountReserve1,
        openAt,
        duration
    )


    /**
     * @dev 创建 ERC1155 类型挂单
     * @notice 创建挂单之前，需要将出售的 token 批准给挂单合约，否则挂单失败
     * @param name string 名称
     * @param token0 string 换出 token 的合约地址（NFT 合约地址）
     * @param token1 string 换入 token 的合约地址（token 合约地址）
     * @param tokenId number 换出 token 的 id
     * @param tokenAmount0 number 换出 token 数量
     * @param amountMax1 number 换出最高价格
     * @param amountMin1 number 换出最低价格
     * @param amountMinIncr1 number 单次出价最低加价数量
     * @param amountReserve1 number 
     * @param openAt number 挂单开售时间，unix timestamp
     * @param duration number 挂单持续时间，单位秒
    */
    createErc1155(
        name,
        token0,
        token1,
        tokenId,
        tokenAmount0,
        amountMax1,
        amountMin1,
        amountMinIncr1,
        amountReserve1,
        openAt,
        duration
    )


    /**
     * @dev 对挂单出价
     * @notice 如果挂单换入 token 的合约地址不等于0地址, 出价前要求换入 token 已批准给挂单合约
     * @notice 如果出价低于当前最高价或者加价低于最低加价数量，则失败
     * @notice 如果出价大于等于挂单最高价，直接结单，自动执行 {creatorClaim} {bidderClaim}
     * @param index number 挂单游标
     * @param amount1 出价数量
    */
    bid(index, amount1)


    /**
     * @dev 取消挂单
     * @notice 目前只支持挂单开售前取消
     * @param index number 挂单游标
    */
    cancel(index)
    

    /**
     * @dev 领取挂单，竞拍成功双方交换资产至各自账户，流拍双方资产原路退还
     * @notice 要求挂单在时间上已结束
     * @param index number 挂单游标
    */
    claim(index)
```


### NFTFixedswap

NFTFixedswap 为 NFT 定价售卖市场合约，创建者部署合约后，用户可自由在本合约内交易 NFT 定价单。

```js
    /**
     * @dev 设置是否禁止挂售721 nft
     * @notice 拥有者权限调用
     * @param res bool [true: 禁止，false: 允许]
     */
    setDisableErc721(res)


    /**
     * @dev 设置是否禁止挂售1155 nft
     * @notice 拥有者权限调用
     * @param res bool [true: 禁止，false: 允许]
     */
    setDisableErc1155(res)


    /**
     * @dev 查询总挂单数量
    */
    getPoolCount()

    /**
     * @dev 通过游标查询挂单详情
     * @notice 游标取值范围可以通过 {getPoolCount} 方法获取
     * @param index number 挂单游标
     * @return 
     * {
     *      creator: 挂单人账户地址
     *      name: 名称
     *      token0: 换出 token 的合约地址（NFT 合约地址）
     *      token1: 换入 token 的合约地址（token 合约地址）
     *      tokenId: 换出 token 的 tokenId
     *      amountTotal0: 换出 token 总量
     *      amountTotal1: 换入 token 总量
     *      openAt: 挂单开售时间
     *      nftType: 换出 token 的类型， [0:ERC721, 1:ERC1155]
     *      swapAmount0: 已换出 token 数量
     *      swapAmount1: 已换入 token 数量
     * }
    */
    getPool(index)


    /**
     * @dev 查询挂单状态
     * @param index number 挂单游标
     * @return 
     * {
     *      isCanceled: 是否已取消挂单 [true: 是, false: 否]
     *      isSwaped: 是否已结单 [true: 是, false: 否]
     * }
    */
    getPoolStatus(index)


    /**
     * @dev 查询目标用户是否为挂单创建人
     * @param target string 目标用户地址
     * @param index number 挂单游标
    */
    isCreator(target, index)


    /**
     * @dev 查询合约配置信息
     * @return 
     * {
     *      disableErc721: 是否禁止挂 ERC721 类型的 NFT [true: 禁止, false:未禁止] 默认 false
     *      disableErc1155: 是否禁止挂 ERC1155 类型的 NFT [true: 禁止, false:未禁止] 默认 false
     * }
    */
    getConfig()


    /**
     * @dev 创建 ERC721 类型挂单
     * @notice 创建挂单之前，需要将出售的 token 批准给挂单合约，否则挂单失败
     * @param name string 名称
     * @param token0 string 换出 token 的合约地址（NFT 合约地址）
     * @param token1 string 换入 token 的合约地址（token 合约地址）
     * @param tokenId number 换出 token 的 tokenId
     * @param amountTotal1 number 换入 token 总量
     * @param openAt number 挂单开售时间，unix timestamp
    */
    createErc721(
        name,
        token0,
        token1,
        tokenId,
        amountTotal1,
        openAt
    )

    /**
     * @dev 创建 ERC1155 类型挂单
     * @notice 创建挂单之前，需要将出售的 token 批准给挂单合约，否则挂单失败
     * @param name string 名称
     * @param token0 string 换出 token 的合约地址（NFT 合约地址）
     * @param token1 string 换入 token 的合约地址（token 合约地址）
     * @param tokenId number 换出 token 的 tokenId
     * @param amountTotal0 number 换出 token 总量
     * @param amountTotal1 number 换入 token 总量
     * @param openAt number 挂单开售时间，unix timestamp
    */
    createErc1155(
        name,
        token0,
        token1,
        tokenId,
        amountTotal0,
        amountTotal1,
        openAt
    )

    /**
     * @dev 购买挂单
     * @notice 如果挂单换入 token 的合约地址不等于0地址, 出价前要求换入 token 已批准给挂单合约
     * @notice 可部分购买，换取等比例数量的换出 token
     * @notice 购买数量 + 已售出量 >= 换出总量 则结单
     * @param index number 挂单游标
     * @param amount0 购买的换出 token 的数量
    */
    swap(index, amount0)

    /**
     * @dev 取消挂单
     * @notice 要求挂单未结单
     * @param index number 挂单游标
    */
    cancel(index)
```


### ActivityPunchIn

ActivityPunchIn 为活动打卡合约，创建者部署合约后可创建打卡活动，指定打卡开始结束时间，合约默认24小时内只能打卡一次，创建者可配置最低打卡次数和总奖励 token 数量
用户直接参与打卡，最后根据活动实际打卡完成总人数，平分总奖励 token。

```js
    /**
     * @dev 设置金库账户地址
     * @notice 拥有者权限调用
     * @param treasury string 新金库账户地址
     */
    setTreasury(treasury)


    /**
     * @dev 查询总活动数量
     */
    activityLength()


    /**
     * @dev 查询活动信息
     * @param index 活动游标
     * @return {
     *  startTimestamp: 活动开始时间
     *  endTimestamp: 活动结束时间
     *  limitAmount: 活动打卡最低次数
     *  rewardAmount: 活动奖励 token 总量
     *  rewardToken: 活动奖励 token 地址
     *  successAmount: 当前活动满足打卡次数人数
     * }
     */
    activityInfo(index)


    /**
     * @dev 查询用户信息
     * @param index 活动游标
     * @param user 用户地址
     * @return {
     *  lastTimestamp: 上一次打卡时间戳
     *  amount: 累计打卡次数
     *  isClaimed: 是否已领取活动奖励
     * }
     */
    userInfo(index, user)


    /**
     * @dev 活动打卡
     * @param index 活动游标
     */
    punchIn(index)
 

    /**
     * @dev 领取活动奖励
     * @param index 活动游标
     * @param user 用于接收奖励的账户地址
     */
    claim(index, user)
```


### IFO

IFO 为募集合约，创建者指定待募集 token 和本次 IFO 出售的 token，同时配置相关总量。用户质押募集 token 参与 IFO，
活动结束合约自动根据目标募集 token 总量和实际募集总量计算每位用户实际能购买的 token 数量。用户实际购买数量少于预期数量，
会自动返回多余的募集 token。

```js
    /**
     * @dev 设置 ifo 出售 token 总量
     * @notice 拥有者权限调用
     * @param offerAmount number 新的出售 token 总量
     */
    setOfferingAmount(offerAmount)


    /**
     * @dev 设置 ifo 配置
     * @notice 拥有者权限调用
     * @param startTimestamp number ifo 开始时间戳
     * @param endTimestamp number ifo 结束时间戳
     * @param raisingAmount number ifo 募集 token 总量
     */
    setParams(startTimestamp, endTimestamp, raisingAmount)


    /**
     * @dev 提取募集 token
     * @notice 拥有者权限调用
     * @param token string 提取 token 地址
     * @param to string 账户地址用于接收提取的 token
     * @param amount number 提取数量
     */
    withdraw(token, to, amount)


    /**
     * @dev 查询 ifo 配置信息
     * @return {
     *  treasury: 金库合约地址
     *  lpToken: 待募集 token 地址
     *  offeringToken: 被出售 token 地址
     *  startTimestamp: 活动开始时间戳
     *  endTimestamp: 活动结结束时间戳
     *  raisingAmount: 募集 token 总量
     *  offeringAmount: 出售 token 总量 
     *  totalAmount: 已募集 token 总量
     *  offeringHarvested: 已售出 token 总量
     *  harvestedCount: 已领取总人数
     * }
     */
    ifoInfo()


    /**
     * @dev 质押募集 token，参与 ifo
     * @param amount number 募集 token 数量
     */
    deposit(amount)


    /**
     * @dev 领取被出售 token
     */
    harvest()


    /**
     * @dev 查询用户是否已领取
     * @param user string 账户地址
     */
    hasHarvest(user)


    /**
     * @dev 查询用户当前已购买到的 token 的数量
     * @param user string 账户地址
     */
    getOfferingAmount(user)


    /**
     * @dev 查询用户当前退回募集 token 的数量
     * @param user string 账户地址
     */
    getRefundingAmount(user)


    /**
     * @dev 查询用户是否能领取已购买的 token
     * @param user string 账户地址
     */
    canHarvest(user)


    /**
     * @dev 查询用户 ifo 信息
     * @param user string 账户地址
     * @return {
     *  amount: 已质押募集 token 数量
     *  claimed: 是否已领取
     *  offer: 已购买到的 token 的数量
     *  refund: 当前退回募集 token 的数量
     *  canHarvest: 是否能领取
     * }
     */
    userInfo(user)
```


### SinglePool

SinglePool 为单币质押挖矿合约，创建者部署该合约后，可指定质押 token 和 奖励 token 相关配置。 用户可以参与质押挖矿，质押后自动锁仓一段时间，
锁仓结束，用户可提取质押 token。挖矿奖励可随时提取。

```js
    /**
     * @dev 设置产矿数率
     * @notice 拥有者权限调用
     * @param mintPerBlock number 单个区块生成奖励 token 数量
     */
    setEmissionRate(mintPerBlock)


    /**
     * @dev 设置金库账户地址
     * @notice 拥有者权限调用
     * @param treasury string 金库账户地址
     */
    setAssetsAccount(treasury)


    /**
     * @dev 设置锁仓时长
     * @notice 拥有者权限调用
     * @param lockDuration number 锁仓时长，单位秒
     */
    setLockDuration(lockDuration)


    /**
     * @dev 查询质押 token 信息
     * @return {
     *  name: 名称
     *  symbol: 符号
     *  decimals：位数
     * }
     */
    getDepositTokenInfo()


    /**
     * @dev 查询奖励 token 信息
     * @return {
     *  name: 名称
     *  symbol: 符号
     *  decimals：位数
     * }
     */
    getRewardTokenInfo()
    

    /**
     * @dev 查询用户质押 token 批准给单币挖矿合约的额度
     * @param user string 用户地址
     */
    allowance(user)
     

    /**
     * @dev 批准质押 token 给单币挖矿合约
     */
    approve()
    

    /**
     * @dev 查询用户质押 token 余额
     * @param user string 用户地址
     */
    balance(user)


    /**
     * @dev 查询当前总质押量
     */
    getDepositTotalSupply()


    /**
     * @dev 查询用户信息
     * @param user string 用户地址
     * @return {
     *  depositTokenAllowance: 用户质押 token 批准额度
     *  lockedAmount: 质押数量
     *  unlockTime: 解锁时间戳
     *  pendingAmount: 可领取奖励 token 数量
     *  balnace: 用户质押 token 余额
     * }
     */
    getUserInfo()


    /**
     * @dev 质押 token 进行挖矿
     * @notice 调用该方法之前，必须先将质押 token 批准给本合约
     * @param amount number 质押 token 数量
     */
    deposit(amount)


    /**
     * @dev 提取质押 token 
     * @notice 提取质押 token 同时触发奖励领取操作
     * @param amount number 待领取质押 token 数量
     */
    withdraw(amount)


    /**
     * @dev 领取质押挖矿奖励 token
     */
    harvest()
```