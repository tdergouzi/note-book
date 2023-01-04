
## Contract ABI

### ERC20Token

基础 ERC20 token 合约

```js
    /**
     * @dev 查询用户余额
     * @param 用户钱包地址
     * @return uint256
    */
    balanceOf(address)

    /**
     * @dev 查询 token 名称
     * @return string
    */
    name()

    /**
     * @dev 查询 token 符号
     * @return string
    */
    symbol()

    /**
     * @dev 查询 token 精度位数
     * @return uint256
    */
    decimals()

    /**
     * @dev 查询合约 owner 地址
     * @return address
    */
    owner()

    /**
     * @dev 放弃合约所有权，合约所有人默认为0地址
     * @notice onlyOwner
    */
    renounceOwnership()

    /**
     * @dev 查询 token 总发行量
     * @return uint256
    */
    totalSupply()

    /**
     * @dev 查询用户授权给花销者可用额度
     * @param address 用户地址
     * @param address 花销者地址
     * @return uint256
    */
    allowance(address,address)

    /**
     * @dev 用户授权给其他用户可以支配用户的资金
     * @param address 花销者地址
     * @param uint256 批准数量
    */
    approve(address,uint256)

    /**
     * @dev 用户转账给其他用户资金
     * @param address 接收者地址
     * @param uint256 数量
    */
    transfer(address,uint256)

    /**
     * @dev 增发 token 至指定的账户
     * @notice onlyOwner
     * @param address 接收者地址
     * @param uint256 增发数量
    */
    mint(address,uint256)

    /**
     * @dev 用户销毁个人账户中 token 
     * @param uint256 销毁数量
    */
    burn(uint256)

    /**
     * @dev 转移合约所有权至指定地址
     * @prama address 新的所有者地址
    */
    transferOwnership(address)

    /**
     * @dev 转账操作时提交事件
     * @param from, 转出者地址
     * @param to, 接收者地址
     * @param value, 数量
    */
    event Transfer(address indexed from, address indexed to, uint256 value);

    /**
     * @dev 批准操作时提交事件
     * @param owner, token 拥有者账户地址
     * @param spender, 接收者地址
     * @param value, 数量
    */
    event Approval(address indexed owner, address indexed spender, uint256 value);
```

### ERC721Token

基础 ERC721 nft 合约

```js
    /**
     * @dev 查询 nft 基础URL
     * @return string
    */
    _base_uri()

    /**
     * @dev 查询 nft 总量
     * @return uint256
    */
    _totalSupply()

    /**
     * @dev 将指定 tokenId nft 批准给目标账户
     * @param address 被批准人账户地址
     * @param uint256 指定的 tokenId
    */
    approve(address,uint256)

    /**
     * @dev 获取用户拥有的 nft 总量
     * @param address 账户地址
     * @return uint256
     */
    balance(address)

    /**
     * @dev 销毁本人拥有的 nft
     * @param uint256 指定的 nft tokenId
    */
    burn(uint256)

    /**
     * @dev 查询 nft 被批准人的账户地址
     * @param uint256 tokenId
     * @return address
    */    
    getApproved(uint256)

    /**
     * @dev 查询目标地址是否将自己所有的 nft 的转移权限批准给指定地址
     * @param address nft 目标的账户地址
     * @param address nft 被批准账户地址
     * @return bool
    */
    isApprovedForAll(address,address)

    /**
     * @dev 增发一个 nft
     * @notice onlyOwner
     * @param address 接受者账户地址，用于接受增发的 nft
     * @param string tokenURI nft 元数据
    */
    mint(address,string)

    /**
     * @dev 查询 nft 名称
     * @return string
    */
    name()

    /**
     * @dev 查询 nft 合约所有者地址
     * @return string
    */
    owner()

    /**
     * @dev 查询 nft 所有者地址
     * @param uint256 指定 nft tokenId
     * @return string
    */
    ownerOf(uint256)

    /**
     * @dev 放弃合约管理权限，默认设置为0地址
     * @notice onlyOwner
    */
    renounceOwnership()

    /**
     * @dev 设置目标账户是否拥有调用者所有 nft 的批准权限
     * @param address 被批准账户地址
     * @param bool 批准状态 [true: 批准, false: 未批准]
    */
    setApprovalForAll(address,bool)

    /**
     * @dev 设置 nft 基础URL
     * @notice onlyOwner
     * @param string 基础URL
    */
    setBaseURI(string)

    /**
     * @dev 查询 nft 符号
     * @return string
    */
    symbol()

    /**
     * @dev 查询 nft 元数据
     * @param uint256 指定 nft tokenId
     * @return string
    */
    tokenURI(uint256)

    /**
     * @dev 将指定 nft 从所有者账户转移至目标账户
     * @param address 转出者账户地址
     * @param address 接受者账户地址
     * @param uint256 转移 nft tokenId
    */
    transferFrom(address,address,uint256)

    /**
     * @dev 转移合约管理权限
     * @notice onlyOwner
     * @param address 新管理者地址
    */
    transferOwnership(address)

    /**
     * @dev transferFrom mint batchMint 时提交事件
     * @param from address 转出账户地址
     * @param to address 接受账户地址
     * @param tokenId uint256 token id
    */
    event Transfer(address indexed from, address indexed to, uint256 indexed tokenId);
```

### ERC1155Token

基础 ERC1155 nft 合约

```js
    /**
     * @dev 查询 nft 基础URL
     * @return string
    */
    _baseURI()

    /**
     * @dev 查询 nft 名称
     * @return string
    */
    _name()

    /**
     * @dev 查询 nft 符号
     * @return string
    */
    _symbol()

    /**
     * @dev 查询 nft 总量
     * @return uint256
    */
    _totalSupply()

    /**
     * @dev 获取用户 nft 数量
     * @param address 账户地址
     * @param uint256 指定 nft tokenId
     * @return uint256
    */
    balanceOf(address,uint256)

    /**
     * @dev 批量获取用户 nft 数量
     * @param address[] 账户地址数组
     * @param uint256[] 指定 nft tokenId 数组
     * @return uint256[]
    */
    balanceOfBatch(address[],uint256[])

    /**
     * @dev 销毁本人拥有 nft 的指定数量
     * @param uint256 指定的 nft tokenId
     * @param uint256 销毁数量
    */
    burn(uint256,uint256)

    /**
     * @dev 查询目标地址是否将自己所有的 nft 的转移权限批准给指定地址
     * @param address nft 目标的账户地址
     * @param address nft 被批准账户地址
     * @return bool
    */
    isApprovedForAll(address,address)

    /**
     * @dev 向指定账户中增发 nft
     * @notice onlyOwner
     * @param address 接受者账户地址
     * @param uint256 增发数量
     * @param string nft 元数据
    */
    mint(address,uint256,string)

    /**
     * @dev 向指定账户中增发指定数量的 nft
     * @notice onlyOwner
     * @param address 接受者账户地址
     * @param uint256 nft tokenId
     * @param uint256 增发数量
    */
    mintAmount(address,uint256,uint256)

    /**
     * @dev 查询 nft 合约所有者地址
     * @return string
    */
    owner()

    /**
     * @dev 放弃合约管理权限，默认设置为0地址
     * @notice onlyOwner
    */
    renounceOwnership()

    /**
     * @dev 批量从转出账户地址转移不同数量的不同 nft 至接收账户地址
     * @param address 转出账户地址
     * @param address 接受账户地址
     * @param uint256[] nft tokenId 数组
     * @param uint256[] 转移数量数组
     * @param string 交易信息，可为空 "0x"
    */
    safeBatchTransferFrom(address,address,uint256[],uint256[],bytes)

    /**
     * @dev 从转出账户地址转移指定数量的 nft 至接收账户地址
     * @param address 转出账户地址
     * @param address 接受账户地址
     * @param uint256 nft tokenId
     * @param uint256 转移数量
     * @param string 交易信息，可为空 "0x"
    */
    safeTransferFrom(address,address,uint256,uint256,bytes)

    /**
     * @dev 设置目标账户是否拥有调用者所有 nft 的批准权限
     * @param address 被批准账户地址
     * @param bool 批准状态 [true: 批准, false: 未批准]
    */
    setApprovalForAll(address,bool)

    /**
     * @dev 设置 nft 基础URL
     * @notice onlyOwner
     * @param string 基础URL
    */
    setBaseURI(string)

    /**
     * @dev 转移合约管理权限
     * @notice onlyOwner
     * @param address 新管理者地址
    */
    transferOwnership(address)

    /**
     * @dev 查询 nft 元数据
     * @param uint256 指定 nft tokenId
     * @return string
    */
    uri(uint256)

    /**
     * @dev safeBatchTransferFrom mint mintAmount burn 提交事件
     * @param operator address 交易发起者账户地址
     * @param from address 转出账户地址
     * @param to address 接收账户地址
     * @param id uint256 转出 tokenId
     * @param value uint256 转出数量
    */
    event TransferSingle(address indexed operator, address indexed from, address indexed to, uint256 id, uint256 value);

    /**
     * @dev batchMint 提交事件
     * @param operator address 交易发起者账户地址
     * @param from address 转出账户地址
     * @param to address 接收账户地址
     * @param ids uint256[] 转出 tokenId 数组
     * @param value uint256 转出数量数组
    */
    event TransferBatch(address indexed operator, address indexed from, address indexed to, uint256[] ids, uint256[] values);
```

### NFTEnglishAuction

英式拍卖合约，用于挂售 ERC721 或 ERC1155 类型 nft

```js
    /**
     * @dev 对挂单出价
     * @notice 如果出价低于当前最高价或者加价低于最低加价数量，则失败
     * @notice 如果出价大于等于挂单最高价，直接结单，自动执行 {creatorClaim} {bidderClaim}
     * @param uint256 挂单游标
     * @param uint256 出价数量
    */
    bid(uint256,uint256)

    /**
     * @dev 查询挂单竞价数量
     * @param uint256 挂单游标
    */
    bidCountP(uint256)

    /**
     * @dev 取消挂单
     * @notice 目前只支持挂单开售前取消
     * @param uint256 挂单游标
    */
    cancel(uint256)

    /**
     * @dev 领取挂单，竞拍成功双方交换资产至各自账户，流拍双方资产原路退还
     * @param uint256 挂单游标
    */
    claim(uint256)

    /**
     * @dev 查询挂单是否已被领取
     * @param uint256 挂单游标
    */
    claimP(uint256)

    /**
     * @dev 创建 ERC1155 类型挂单
     * @notice 创建挂单之前，需要将出售的 token 批准给挂单合约，否则挂单失败
     * @param address 换出 token 的合约地址（NFT 合约地址）
     * @param address 换入 token 的合约地址（token 合约地址）
     * @param uint256 换出 token 的 id
     * @param uint256 换出 token 数量
     * @param uint256 换出最高价格
     * @param uint256 换出最低价格
     * @param uint256 单次出价最低加价数量
     * @param uint256 挂单最低成交价格，低于此价格挂单流拍
     * @param uint256 挂单开售时间，unix timestamp
     * @param uint256 挂单持续时间，单位秒
    */    
    createErc1155(address,address,uint256,uint256,uint256,uint256,uint256,uint256,uint256,uint256)

    /**
     * @dev 创建 ERC721 类型挂单
     * @notice 创建挂单之前，需要将出售的 token 批准给挂单合约，否则挂单失败
     * @param address 换出 token 的合约地址（NFT 合约地址）
     * @param address 换入 token 的合约地址（token 合约地址）
     * @param uint256 换出 token 的 tokenId
     * @param uint256 换出最高价格
     * @param uint256 换出最低价格
     * @param uint256 单次出价最低加价数量
     * @param uint256 挂单最低成交价格，低于此价格挂单流拍
     * @param uint256 挂单开售时间，unix timestamp
     * @param uint256 挂单持续时间，单位秒
    */
    createErc721(address,address,uint256,uint256,uint256,uint256,uint256,uint256,uint256)
    
    /**
     * @dev 查询挂单是否被取消
     * @param uint256 挂单游标
    */
    creatorCanceledP(uint256)

    /**
     * @dev 查询挂单下一次竞价出价数量，即当前最高竞价数量加上加价间隔
     * @param uint256 挂单游标
     * @return uint256
    */
    currentBidderAmount(uint256)

    /**
     * @dev 查询挂单当前竞拍最高价
     * @param uint256 挂单游标
     * @return uint256
    */
    currentBidderAmount1P(uint256)

    /**
     * @dev 查询挂单当前最高价竞拍者地址
     * @param uint256 挂单游标
     * @return address
    */
    currentBidderP(uint256)
    
    /**
     * @dev 查询是否禁止挂 ERC721 类型的 NFT [true: 禁止, false:未禁止] 默认 false
     * @return bool
    */
    disableErc1155()

    /**
     * @dev 是否禁止挂 ERC1155 类型的 NFT [true: 禁止, false:未禁止] 默认 false
     * @return false
    */
    disableErc721()

    /**
     * @dev 查询总挂单数量
     * @return uint256
    */
    getPoolCount()

    /**
     * @dev 查询目标用户是否为挂单创建人
     * @param string 目标用户地址
     * @param uint256 挂单游标
    */
    isCreator(address,uint256)

    /**
     * @dev 查询目标用户某个挂单出价
     * @param string 账户地址
     * @param uint256 挂单游标
    */
    myBidderAmount1P(address,uint256)


    /**
     * @dev 查询合约所有者地址
     * @return address
    */
    owner()

    /**
     * @dev 通过游标查询挂单信息
     * @notice 游标取值范围可以通过 {getPoolCount} 方法获取
     * @param uint256 挂单游标
     * @return {
     *      creator: 挂单人账户地址
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
     * }
    */
    pools(uint256)

    /**
     * @dev 放弃合约管理权限，默认设置为0地址
     * @notice onlyOwner
    */
    renounceOwnership()

    /**
     * @dev 查询挂单最低成交价
     * @param uint256 挂单游标
     * @reutrn uint256
    */
    reserveAmount1P(uint256)

    /**
     * @dev 设置是否挂 ERC1155 类型 nft 订单
     * @notice onlyOwner
     * @param bool [true: 禁止, false: 允许]
    */
    setDisableErc1155(bool)

    /**
     * @dev 设置是否挂 ERC721 类型 nft 订单
     * @notice onlyOwner
     * @param bool [true: 禁止, false: 允许]
    */
    setDisableErc721(bool)

    /**
     * @dev 转移合约所有权至指定地址
     * @notice onlyOwner
     * @prama address 新的所有者地址
    */
    transferOwnership(address)

    /**
     * @dev 创建挂单时提交事件
     * @param sender address 卖家地址
     * @param index uint256 挂单游标
    */
    event Created(address indexed sender, uint256 indexed index);

    /**
     * @dev 对挂单出价时提交事件
     * @param sender address 买家地址
     * @param index uint256 挂单游标
     * @param amount1 uint256 出价数量
    */
    event Bid(address indexed sender, uint indexed index, uint amount1);

    /**
     * @dev 取消挂单时提交事件
     * @param sender address 卖家地址
     * @param index uint256 挂单游标
     * @param tokenId uint256 nft tokenId
     * @param amount0 uint256 nft 数量，ERC721 类型默认为1
    */
    event Canceled(address indexed sender, uint indexed index, uint tokenId, uint amount0);

    /**
     * @dev 领取已结束挂单时提交事件
     * @param index uint256 挂单游标
     * @param user0 address 挂单创建者地址
     * @param tokenId uint256 nft tokenId
     * @param amount0 uint256 nft 数量，ERC721 类型默认为1
     * @param user1 address 挂单当前出价者地址
     * @param amount1 uint256 出价数量
    */
    event Claimed(uint indexed index, address user0, uint tokenId, uint amount0, address user1, uint amount1);
```

### NFTFixedswap

定价售卖合约，用于出售 ERC721 或 ERC1155 类型 NFT

```js
    /**
     * @dev 取消挂单
     * @param uint256 挂单游标
    */
    cancel(uint256)

    /**
     * @dev 创建 ERC1155 类型挂单
     * @param address 换出 token 的合约地址（NFT 合约地址）
     * @param address 换入 token 的合约地址（token 合约地址）
     * @param uint256 换出 token 的 tokenId
     * @param uint256 换出 token 总量
     * @param uint256 换入 token 总量
     * @param uint256 挂单开售时间，unix timestamp
    */
    createErc1155(address,address,uint256,uint256,uint256,uint256)

    /**
     * @dev 创建 ERC721 类型挂单
     * @notice 创建挂单之前，需要将出售的 token 批准给挂单合约，否则挂单失败
     * @param address 换出 token 的合约地址（NFT 合约地址）
     * @param address 换入 token 的合约地址（token 合约地址）
     * @param uint256 换出 token 的 tokenId
     * @param uint256 换入 token 总量
     * @param uint256 挂单开售时间，unix timestamp
    */
    createErc721(address,address,uint256,uint256,uint256)

    /**
     * @dev 查询挂单是否已取消挂单
     * @param uint256 挂单游标
     * @return bool
    */
    creatorCanceledP(uint256)
    
    /**
     * @dev 查询是否禁止挂 ERC721 类型的 NFT [true: 禁止, false:未禁止] 默认 false
     * @notice onlyOwner
     * @return bool
    */
    disableErc1155()

    /**
     * @dev 是否禁止挂 ERC1155 类型的 NFT [true: 禁止, false:未禁止] 默认 false
     * @notice onlyOwner
     * @return false
    */
    disableErc721()

    /**
     * @dev 查询总挂单数量
     * @return uint256
    */
    getPoolCount()

    /**
     * @dev 查询目标用户是否为挂单创建人
     * @param string 目标用户地址
     * @param uint256 挂单游标
    */
    isCreator(address,uint256)

    /**
     * @dev 查询合约所有者地址
     * @return address
    */
    owner()

    /**
     * @dev 通过游标查询挂单详情
     * @notice 游标取值范围可以通过 {getPoolCount} 方法获取
     * @param uint256 挂单游标
     * @return {
     *      creator: 挂单人账户地址
     *      token0: 换出 token 的合约地址（NFT 合约地址）
     *      token1: 换入 token 的合约地址（token 合约地址）
     *      tokenId: 换出 token 的 tokenId
     *      amountTotal0: 换出 token 总量
     *      amountTotal1: 换入 token 总量
     *      openAt: 挂单开售时间
     *      nftType: 换出 token 的类型， [0:ERC721, 1:ERC1155]

     * }
    */
    // function pools(uint) external returns(Pool memory);
    pools(uint256)

    /**
     * @dev 放弃合约所有权，合约所有人默认为0地址
     * @notice onlyOwner
    */
    renounceOwnership()

    /**
     * @dev 设置是否挂 ERC1155 类型 nft 订单
     * @notice onlyOwner
     * @param bool [true: 禁止, false: 允许]
    */    
    setDisableErc1155(bool)

    /**
     * @dev 设置是否挂 ERC721 类型 nft 订单
     * @notice onlyOwner
     * @param bool [true: 禁止, false: 允许]
    */
    setDisableErc721(bool)

    /**
     * @dev 购买挂单
     * @notice 如果挂单换入 token 的合约地址不等于0地址, 出价前要求换入 token 已批准给挂单合约
     * @notice 可部分购买，换取等比例数量的换出 token
     * @notice 购买数量 + 已售出量 >= 换出总量 则结单
     * @param uint256 挂单游标
     * @param uint256 购买的换出 token 的数量
    */
    swap(uint256,uint256)

    /**
     * @dev 查询挂单已换出 token 数量
     * @return uint256
     */
    swappedAmount0P(uint256)

    /**
     * @dev 查询挂单已换入 token 数量
     * @return uint256
     */
    swappedAmount1P(uint256)

    /**
     * @dev 查询挂单是否已结单
     * @param uint256 挂单游标
     * @return bool
    */
    swappedP(uint256)

    /**
     * @dev 转移合约所有权至指定地址
     * @notice onlyOwner
     * @prama address 新的所有者地址
    */
    transferOwnership(address)

    /**
     * @dev 创建挂单时提交事件
     * @param sender address 卖家地址
     * @param index uint256 挂单游标
    */
    event Created(address indexed sender, uint indexed index);

    /**
     * @dev 取消挂单时提交事件
     * @param sender address 卖家地址
     * @param index uint256 挂单游标
     * @param unswappedAmount0 未成交 token0 的数量
    */
    event Canceled(address indexed sender, uint indexed index, uint unswappedAmount0);

    /**
     * @dev 挂单成交时提交事件， 成交并非结单
     * @param sender address 买家地址
     * @param index uint256 挂单游标
     * @param swappedAmount0 uint256 换出 token0 的数量
     * @param swappedAmount1 uint256 换入 token1 的数量
     * 
    */
    event Swapped(address indexed sender, uint indexed index, uint swappedAmount0, uint swappedAmount1);
```

### ActivityPunchIn

每日活动打卡合约

```js
    /**
     * @dev 查询活动信息
     * @param uint256 活动游标
     * @return {
     *  startTimestamp: 活动开始时间
     *  endTimestamp: 活动结束时间
     *  limitAmount: 活动打卡最低次数
     *  rewardAmount: 活动奖励 token 总量
     *  rewardToken: 活动奖励 token 地址
     * }
     */
    activityInfo(uint256)

    /**
     * @dev 查询总活动数量
     * @return uint256
     */
    activityLength()

    /**
     * @dev 查询活动已完成最低限度打卡次数总人数
     * @param uint256 活动游标
     * @return uint256
    */
    activitySuccessAmount(uint256)

    /**
     * @dev 领取活动奖励
     * @param index 活动游标
     * @param user 用于接收奖励的账户地址
     */
    claim(uint256,address)

    /**
     * @dev 创建活动
     * @notice onlyOwner
     * @param uint256 活动打开开始时间戳
     * @param uint256 总打卡天数
     * @param uint256 最低打卡天数
     * @param uint256 活动总奖励 token 数量
     * @param address 活动奖励 token 地址
    */
    createActivity(uint256,uint256,uint256,uint256,address)

    /**
     * @dev 查询合约所有者地址
     * @return address
    */
    owner()

    /**
     * @dev 活动打卡
     * @param index 活动游标
     */
    punchIn(uint256)

    /**
     * @dev 放弃合约所有权，合约所有人默认为0地址
     * @notice onlyOwner
    */
    renounceOwnership()

    /**
     * @dev 设置金库账户地址
     * @notice onlyOwner
     * @param address 新金库账户地址
     */
    setTreasury(address)

    /**
     * @dev 转移合约所有权至指定地址
     * @notice onlyOwner
     * @prama address 新的所有者地址
    */
    transferOwnership(address)

    /**
     * @dev 更新活动配置
     * @notice onlyOwner
     * @param uint256 活动游标
     * @param uint256 活动奖励 token 总量
     * @param address 活动奖励 token 地址
    */
    updateActivity(uint256,uint256,address)

    /**
     * @dev 查询用户信息
     * @param uint256 活动游标
     * @param address 用户地址
     * @return {
     *  lastTimestamp: 上一次打卡时间戳
     *  amount: 累计打卡次数
     *  isClaimed: 是否已领取活动奖励
     * }
     */
    userInfo(uint256,address)

    /**
     * @dev 所有者创建活动时提交事件
     * @param activityId uint256 活动游标
     * @param startTime uint256 活动开始时间戳
     * @param endTime uint256 活动结束时间戳
     * @param limitAmount uint256 活动最低打卡次数
    */
    event CreateActivity(uint256 activityId, uint256 startTime, uint256 endTime, uint256 limitAmount);

    /**
     * @dev 所有者更新活动时提交事件
     * @param activityId uint256 活动游标
     * @param rewardAmount uint256 活动奖励 token 总量
     * @param rewardToken address 活动奖励 token 地址
    */
    event UpdateActivity(uint256 activityId, uint256 rewardAmount, address rewardToken);

    /**
     * @dev 用户活动打卡时提交事件
     * @param activityId uint256 活动游标
     * @param user address 用户地址
     * @param timestamp uint256 活动打卡时间戳
    */
    event PunchInEvent(uint256 activityId, address user, uint256 timestamp);

    /**
     * @dev 用户领取活动奖励时提交事件
     * @param activityId uint256 活动游标
     * @param user address 用户地址
     * @param amount uint256 领取奖励数量
     * @param token address 领取奖励 token 的地址
    */
    event Claim(uint256 activityId, address user, uint256 amount, address token);
```


### IFO

IFO 为募集合约，创建者指定待募集 token 和本次 IFO 出售的 token，同时配置相关总量。白名单用户质押募集 token 参与 IFO，
活动结束合约自动根据目标募集 token 总量和实际募集总量计算每位用户实际能购买的 token 数量。用户实际购买数量少于预期数量，
会自动返回多余的募集 token。

```js
    /**
     * @dev 查询 IFO 白名单账户地址
     * @param uint256 数组游标
     * @return address
    */
    addressList(uint256)

    /**
     * @dev 质押募集 token，参与 IFO
     * @param uint256 token 数量
    */
    deposit(uint256)

    /**
     * @dev 查询 IFO 结束区块高度
     * @return uint256
    */
    endBlock()

    /**
     * @dev 查询白名单数组长度
     * @return uint256
    */
    getAddressListLength()

    /**
     * @dev 查询用户当前已购买到的 token 的数量
     * @param address 账户地址
     * @return uint256
    */
    getOfferingAmount(address)

    /**
     * @dev 查询用户当前退回募集 token 的数量
     * @param address 账户地址
     * @return uint256
    */
    getRefundingAmount(address)

    /**
     * @dev 领取已成功购买 token
    */
    harvest()

    /**
     * @dev 查询已领取用户数量
     * @return uint256
    */
    harvestedCount()

    /**
     * @dev 查询用户是否已领取
     * @param address 账户地址
     * @return address
    */
    hasHarvest(address)

    /**
     * @dev 查询募集 token 地址
     * @return address
    */
    lpToken()

    /**
     * @dev 查询 IFO 出售 token 总量
     * @return uint256
    */
    offeringAmount()

    /**
     * @dev 查询 IFO 出售 token 已被领取的总量
     * @return uint256
    */
    offeringHarvested()

    /**
     * @dev 查询募集 token 地址
     * @return address
    */
    offeringToken()

    /**
     * @dev 查询所有者账户地址
     * @return address
    */
    owner()

    /**
     * @dev 查询预期募集 token 总量
     * @return uint256
    */
    raisingAmount()

    /**
     * @dev 放弃合约所有权，合约所有人默认为0地址
     * @notice onlyOwner
    */
    renounceOwnership()

    /**
     * @dev 配置 IFO 出售 token 总量
     * @notice onlyOwner
     * @return uint256
    */
    setOfferingAmount(uint256)

    /**
     * @dev 配置 IFO 参数
     * @notice onlyOwner
     * @param uint256 开始块高度
     * @param uint256 结束块高度
     * @param uint256 募集 token 总量
    */
    setParams(uint256,uint256,uint256)

    /**
     * @dev 配置目标地址是否为白名单地址
     * @notice onlyOwner
     * @param address 目标账户地址
     * @param bool [true: 可参与, false: 禁止参与]
    */
    setWhite(address,bool)

    /**
     * @dev 批量配置目标地址是否为白名单地址
     * @notice onlyOwner
     * @param address[] 数组，元素同上
     * @param bool[] 数组，元素同上
    */
    setWhites(address[],bool[])

    /**
     * @dev 查询 IFO 开始块高度
     * @return number
    */
    startBlock()

    /**
     * @dev 查询当前已募集 token 总量
     * @return uint256
    */
    totalAmount()

    /**
     * @dev 转移合约所有权至指定地址
     * @prama address 新的所有者地址
    */
    transferOwnership(address)

    /**
     * @dev 查询金库账户地址
     * @return address
    */
    treasury()

    /**
     * @dev 查询用户信息
     * @param address 账户地址
     * @return {
     *  amount: 质押募集 token 数量
     *  claimed: 是否已领取购买 token
     * }
    */
    userInfo(address)

    /**
     * @dev 查询白名单地址总量
     * @return uint256
    */
    whiteCount()

    /**
     * @dev 查询地址是否为白名单地址
     * @param address 目标账户地址
     * @return bool
    */
    whiteList(address)

    /**
     * @dev 提取合约内 token
     * @notice onlyOwner
     * @param address token 地址
     * @param address 接收者账户地址
     * @param uint256 提取数量
    */
    withdraw(address,address,uint256)

    /**
     * @dev 用户质押募集 token 时提交事件
     * @param user address 质押账户地址
     * @param amount uint256 质押 token 数量
    */
    event Deposit(address indexed user, uint256 amount);

    /**
     * @dev 用户领取已购买 token 时提交事件
     * @param user address 领取账户地址
     * @param offeringAmount uint256 已购买的 token 数量
     * @param refundingAmount uint256 退回的 token 数量
    */
    event Harvest(address indexed user, uint256 offeringAmount, uint256 refundingAmount);
```