
## Contract ABI

```
接口按照接口首字母顺序 A-Z 排序

合约内数据与用户无关
```

### ERC20Token

基础 ERC20 token 合约

```js
    /**
     * @dev constructor
    */
    constructor(string name, string symbol, uint256 totalSupply)

    /**
     * @dev 查询用户余额
     * @param 用户钱包地址
     * @return uint256
    */
    function balanceOf(address) view returns(uint256)

    /**
     * @dev 查询 token 名称
     * @return string
    */
    function name() view returns(string)

    /**
     * @dev 查询 token 符号
     * @return string
    */
    function symbol() view returns(string)

    /**
     * @dev 查询 token 精度位数
     * @return uint256
    */
    function decimals() view returns(uint256)

    /**
     * @dev 查询合约 owner 地址
     * @return address
    */
    function owner() view returns(address)

    /**
     * @dev 放弃合约所有权，合约所有人默认为0地址
     * @notice onlyOwner
    */
    function renounceOwnership()

    /**
     * @dev 查询 token 总发行量
     * @return uint256
    */
    function totalSupply() view returns(uint256)

    /**
     * @dev 查询用户授权给花销者可用额度
     * @param address 用户地址
     * @param address 花销者地址
     * @return uint256
    */
    function allowance(address,address) view returns(uint256)

    /**
     * @dev 用户授权给其他用户可以支配用户的资金
     * @param address 花销者地址
     * @param uint256 批准数量
    */
    function approve(address,uint256)

    /**
     * @dev 用户转账给其他用户资金
     * @param address 接收者地址
     * @param uint256 数量
    */
    function transfer(address,uint256)

    /**
     * @dev 增发 token 至指定的账户
     * @notice onlyOwner
     * @param address 接收者地址
     * @param uint256 增发数量
    */
    function mint(address,uint256)

    /**
     * @dev 用户销毁个人账户中 token 
     * @param uint256 销毁数量
    */
    function burn(uint256)

    /**
     * @dev 转移合约所有权至指定地址
     * @prama address 新的所有者地址
    */
    function transferOwnership(address)

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
     * @dev constructor
    */
    constructor(string name, string symbol, string baseURI)

    /**
     * @dev 查询 nft 基础URL
     * @return string
    */
    function _base_uri() view returns(string)

    /**
     * @dev 查询 nft 总量
     * @return uint256
    */
    function _totalSupply() view returns(uint256)

    /**
     * @dev 将指定 tokenId nft 批准给目标账户
     * @param address 被批准人账户地址
     * @param uint256 指定的 tokenId
    */
    function approve(address,uint256)

    /**
     * @dev 获取用户拥有的 nft 总量
     * @param address 账户地址
     * @return uint256
     */
    function balance(address) view returns(uint256)

    /**
     * @dev 销毁本人拥有的 nft
     * @param uint256 指定的 nft tokenId
    */
    function burn(uint256)

    /**
     * @dev 查询 nft 被批准人的账户地址
     * @param uint256 tokenId
     * @return address
    */    
    function getApproved(uint256) view returns(address)

    /**
     * @dev 查询目标地址是否将自己所有的 nft 的转移权限批准给指定地址
     * @param address nft 目标的账户地址
     * @param address nft 被批准账户地址
     * @return bool
    */
    function isApprovedForAll(address,address) view returns(bool)

    /**
     * @dev 增发一个 nft
     * @notice onlyOwner
     * @param address 接受者账户地址，用于接受增发的 nft
     * @param string tokenURI nft 元数据
    */
    function mint(address,string)

    /**
     * @dev 查询 nft 名称
     * @return string
    */
    function name() view returns(string)

    /**
     * @dev 查询 nft 合约所有者地址
     * @return string
    */
    function owner() view returns(address)

    /**
     * @dev 查询 nft 所有者地址
     * @param uint256 指定 nft tokenId
     * @return address
    */
    function ownerOf(uint256) view returns(address)

    /**
     * @dev 放弃合约管理权限，默认设置为0地址
     * @notice onlyOwner
    */
    function renounceOwnership()

    /**
     * @dev 设置目标账户是否拥有调用者所有 nft 的批准权限
     * @param address 被批准账户地址
     * @param bool 批准状态 [true: 批准, false: 未批准]
    */
    function setApprovalForAll(address,bool)

    /**
     * @dev 设置 nft 基础URL
     * @notice onlyOwner
     * @param string 基础URL
    */
    function setBaseURI(string)

    /**
     * @dev 查询 nft 符号
     * @return string
    */
    function symbol() view returns(string)

    /**
     * @dev 查询 nft 元数据
     * @param uint256 指定 nft tokenId
     * @return string
    */
    function tokenURI(uint256) view returns(string)

    /**
     * @dev 将指定 nft 从所有者账户转移至目标账户
     * @param address 转出者账户地址
     * @param address 接受者账户地址
     * @param uint256 转移 nft tokenId
    */
    function transferFrom(address,address,uint256)

    /**
     * @dev 转移合约管理权限
     * @notice onlyOwner
     * @param address 新管理者地址
    */
    function transferOwnership(address)

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
     * @dev constructor
    */
    constructor(string name, string symbol, string baseURI)

    /**
     * @dev 查询 nft 基础URL
     * @return string
    */
    function _baseURI() view returns(string)

    /**
     * @dev 查询 nft 名称
     * @return string
    */
    function _name() view returns(string)

    /**
     * @dev 查询 nft 符号
     * @return string
    */
    function _symbol() view returns(string)

    /**
     * @dev 查询 nft 总量
     * @return uint256
    */
    function _totalSupply() view returns(uint256)

    /**
     * @dev 获取用户 nft 数量
     * @param address 账户地址
     * @param uint256 指定 nft tokenId
     * @return uint256
    */
    function balanceOf(address,uint256) view returns(uint256)

    /**
     * @dev 批量获取用户 nft 数量
     * @param address[] 账户地址数组
     * @param uint256[] 指定 nft tokenId 数组
     * @return uint256[]
    */
    function balanceOfBatch(address[],uint256[]) view returns(uint256[])

    /**
     * @dev 销毁本人拥有 nft 的指定数量
     * @param uint256 指定的 nft tokenId
     * @param uint256 销毁数量
    */
    function burn(uint256,uint256)

    /**
     * @dev 查询目标地址是否将自己所有的 nft 的转移权限批准给指定地址
     * @param address nft 目标的账户地址
     * @param address nft 被批准账户地址
     * @return bool
    */
    function isApprovedForAll(address,address) view returns(bool)

    /**
     * @dev 向指定账户中增发 nft
     * @notice onlyOwner
     * @param address 接受者账户地址
     * @param uint256 增发数量
     * @param string nft 元数据
    */
    function mint(address,uint256,string)

    /**
     * @dev 向指定账户中增发指定数量的 nft
     * @notice onlyOwner
     * @param address 接受者账户地址
     * @param uint256 nft tokenId
     * @param uint256 增发数量
    */
    function mintAmount(address,uint256,uint256)

    /**
     * @dev 查询 nft 合约所有者地址
     * @return address
    */
    function owner() view returns(address)

    /**
     * @dev 放弃合约管理权限，默认设置为0地址
     * @notice onlyOwner
    */
    function renounceOwnership()

    /**
     * @dev 批量从转出账户地址转移不同数量的不同 nft 至接收账户地址
     * @param address 转出账户地址
     * @param address 接受账户地址
     * @param uint256[] nft tokenId 数组
     * @param uint256[] 转移数量数组
     * @param string 交易信息，可为空 "0x"
    */
    function safeBatchTransferFrom(address,address,uint256[],uint256[],bytes)

    /**
     * @dev 从转出账户地址转移指定数量的 nft 至接收账户地址
     * @param address 转出账户地址
     * @param address 接受账户地址
     * @param uint256 nft tokenId
     * @param uint256 转移数量
     * @param string 交易信息，可为空 "0x"
    */
    function safeTransferFrom(address,address,uint256,uint256,bytes)

    /**
     * @dev 设置目标账户是否拥有调用者所有 nft 的批准权限
     * @param address 被批准账户地址
     * @param bool 批准状态 [true: 批准, false: 未批准]
    */
    function setApprovalForAll(address,bool)

    /**
     * @dev 设置 nft 基础URL
     * @notice onlyOwner
     * @param string 基础URL
    */
    function setBaseURI(string)

    /**
     * @dev 转移合约管理权限
     * @notice onlyOwner
     * @param address 新管理者地址
    */
    function transferOwnership(address)

    /**
     * @dev 查询 nft 元数据
     * @param uint256 指定 nft tokenId
     * @return string
    */
    function uri(uint256) view returns(string)

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
     * @dev constructor
    */
    constructor()

    /**
     * @dev 对挂单出价
     * @notice 如果出价低于当前最高价或者加价低于最低加价数量，则失败
     * @notice 如果出价大于等于挂单最高价，直接结单，自动执行 {creatorClaim} {bidderClaim}
     * @param uint256 挂单游标
     * @param uint256 出价数量
    */
    function bid(uint256,uint256)

    /**
     * @dev 查询挂单竞价数量
     * @param uint256 挂单游标
     * @return uint256
    */
    function bidCountP(uint256) view returns(uint256)

    /**
     * @dev 取消挂单
     * @notice 目前只支持挂单开售前取消
     * @param uint256 挂单游标
    */
    function cancel(uint256)

    /**
     * @dev 领取挂单，竞拍成功双方交换资产至各自账户，流拍双方资产原路退还
     * @param uint256 挂单游标
    */
    function claim(uint256)

    /**
     * @dev 查询挂单是否已被领取
     * @param uint256 挂单游标
     * @return bool
    */
    function claimP(uint256) view returns(bool)

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
    function createErc1155(address,address,uint256,uint256,uint256,uint256,uint256,uint256,uint256,uint256)

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
    function createErc721(address,address,uint256,uint256,uint256,uint256,uint256,uint256,uint256)
    
    /**
     * @dev 查询挂单是否被取消
     * @param uint256 挂单游标
    */
    function creatorCanceledP(uint256) view returns(bool)

    /**
     * @dev 查询挂单下一次竞价出价数量，即当前最高竞价数量加上加价间隔
     * @param uint256 挂单游标
     * @return uint256
    */
    function currentBidderAmount(uint256) view returns(uint256)

    /**
     * @dev 查询挂单当前竞拍最高价
     * @param uint256 挂单游标
     * @return uint256
    */
    function currentBidderAmount1P(uint256) view returns(uint256)

    /**
     * @dev 查询挂单当前最高价竞拍者地址
     * @param uint256 挂单游标
     * @return address
    */
    function currentBidderP(uint256) view returns(address)
    
    /**
     * @dev 查询是否禁止挂 ERC721 类型的 NFT [true: 禁止, false:未禁止] 默认 false
     * @return bool
    */
    function disableErc1155() view returns(bool)

    /**
     * @dev 是否禁止挂 ERC1155 类型的 NFT [true: 禁止, false:未禁止] 默认 false
     * @return false
    */
    function disableErc721() view returns(bool)

    /**
     * @dev 查询总挂单数量
     * @return uint256
    */
    function getPoolCount() view returns(uint256)

    /**
     * @dev 查询目标用户是否为挂单创建人
     * @param string 目标用户地址
     * @param uint256 挂单游标
    */
    function isCreator(address,uint256) view returns(bool)

    /**
     * @dev 查询目标用户某个挂单出价
     * @param string 账户地址
     * @param uint256 挂单游标
     * @return uint256
    */
    function myBidderAmount1P(address,uint256) view returns(uint256)


    /**
     * @dev 查询合约所有者地址
     * @return address
    */
    function owner() view returns(address)

    /**
     * @dev 通过游标查询挂单信息
     * @notice 游标取值范围可以通过 {getPoolCount} 方法获取
     * @param uint256 挂单游标
     * @return {
     *      address: 挂单人账户地址
     *      address: 换出 token 的合约地址（NFT 合约地址）
     *      address: 换入 token 的合约地址（token 合约地址）
     *      uint256: 换出 token 的 tokenId
     *      uint256: 换出 token tokenId 的数量
     *      uint256: 换出最高价格
     *      uint256: 换出最低价格
     *      uint256: 单次出价最低加价数量
     *      uint256: 挂单开售时间
     *      uint256: 挂单结束时间
     *      uint256: 换出 token 的类型， [0:ERC721, 1:ERC1155]
     * }
    */
    function pools(uint256) view returns(address,address,address,uint256,uint256,uint256,uint256,uint256,uint256,uint256,uint256)

    /**
     * @dev 放弃合约管理权限，默认设置为0地址
     * @notice onlyOwner
    */
    function renounceOwnership()

    /**
     * @dev 查询挂单最低成交价
     * @param uint256 挂单游标
     * @reutrn uint256
    */
    function reserveAmount1P(uint256) view returns(uint256)

    /**
     * @dev 设置是否挂 ERC1155 类型 nft 订单
     * @notice onlyOwner
     * @param bool [true: 禁止, false: 允许]
    */
    function setDisableErc1155(bool)

    /**
     * @dev 设置是否挂 ERC721 类型 nft 订单
     * @notice onlyOwner
     * @param bool [true: 禁止, false: 允许]
    */
    function setDisableErc721(bool)

    /**
     * @dev 转移合约所有权至指定地址
     * @notice onlyOwner
     * @prama address 新的所有者地址
    */
    function transferOwnership(address)

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
     * @dev 没有 constructor，相关参数给空
    */

    /**
     * @dev 取消挂单
     * @param uint256 挂单游标
    */
    function cancel(uint256)

    /**
     * @dev 创建 ERC1155 类型挂单
     * @param address 换出 token 的合约地址（NFT 合约地址）
     * @param address 换入 token 的合约地址（token 合约地址）
     * @param uint256 换出 token 的 tokenId
     * @param uint256 换出 token 总量
     * @param uint256 换入 token 总量
     * @param uint256 挂单开售时间，unix timestamp
    */
    function createErc1155(address,address,uint256,uint256,uint256,uint256)

    /**
     * @dev 创建 ERC721 类型挂单
     * @notice 创建挂单之前，需要将出售的 token 批准给挂单合约，否则挂单失败
     * @param address 换出 token 的合约地址（NFT 合约地址）
     * @param address 换入 token 的合约地址（token 合约地址）
     * @param uint256 换出 token 的 tokenId
     * @param uint256 换入 token 总量
     * @param uint256 挂单开售时间，unix timestamp
    */
    function createErc721(address,address,uint256,uint256,uint256)

    /**
     * @dev 查询挂单是否已取消挂单
     * @param uint256 挂单游标
     * @return bool
    */
    function creatorCanceledP(uint256) view returns(bool)
    
    /**
     * @dev 查询是否禁止挂 ERC721 类型的 NFT [true: 禁止, false:未禁止] 默认 false
     * @notice onlyOwner
     * @return bool
    */
    function disableErc1155() view returns(bool)

    /**
     * @dev 是否禁止挂 ERC1155 类型的 NFT [true: 禁止, false:未禁止] 默认 false
     * @notice onlyOwner
     * @return false
    */
    function disableErc721() view returns(bool)

    /**
     * @dev 查询总挂单数量
     * @return uint256
    */
    function getPoolCount() view returns(uint256)

    /**
     * @dev 查询目标用户是否为挂单创建人
     * @param address 目标用户地址
     * @param uint256 挂单游标
     * @return bool
    */
    function isCreator(address,uint256) view returns(bool)

    /**
     * @dev 查询合约所有者地址
     * @return address
    */
    function owner() view returns(address)

    /**
     * @dev 通过游标查询挂单详情
     * @notice 游标取值范围可以通过 {getPoolCount} 方法获取
     * @param uint256 挂单游标
     * @return {
     *      address: 挂单人账户地址
     *      address: 换出 token 的合约地址（NFT 合约地址）
     *      address: 换入 token 的合约地址（token 合约地址）
     *      uint256: 换出 token 的 tokenId
     *      uint256: 换出 token 总量
     *      uint256: 换入 token 总量
     *      uint256: 挂单开售时间
     *      uint256: 换出 token 的类型， [0:ERC721, 1:ERC1155]
     * }
    */
    function pools(uint256) view returns(address,address,address,uint256,uint256,uint256,uint256,uint256)

    /**
     * @dev 放弃合约所有权，合约所有人默认为0地址
     * @notice onlyOwner
    */
    function renounceOwnership()

    /**
     * @dev 设置是否挂 ERC1155 类型 nft 订单
     * @notice onlyOwner
     * @param bool [true: 禁止, false: 允许]
    */    
    function setDisableErc1155(bool)

    /**
     * @dev 设置是否挂 ERC721 类型 nft 订单
     * @notice onlyOwner
     * @param bool [true: 禁止, false: 允许]
    */
    function setDisableErc721(bool)

    /**
     * @dev 购买挂单
     * @notice 如果挂单换入 token 的合约地址不等于0地址, 出价前要求换入 token 已批准给挂单合约
     * @notice 可部分购买，换取等比例数量的换出 token
     * @notice 购买数量 + 已售出量 >= 换出总量 则结单
     * @param uint256 挂单游标
     * @param uint256 购买的换出 token 的数量
    */
    function swap(uint256,uint256)

    /**
     * @dev 查询挂单已换出 token 数量
     * @return uint256
     */
    function swappedAmount0P(uint256) view returns(uint256)

    /**
     * @dev 查询挂单已换入 token 数量
     * @return uint256
     */
    function swappedAmount1P(uint256) view returns(uint256)

    /**
     * @dev 查询挂单是否已结单
     * @param uint256 挂单游标
     * @return bool
    */
    function swappedP(uint256) view returns(bool)

    /**
     * @dev 转移合约所有权至指定地址
     * @notice onlyOwner
     * @prama address 新的所有者地址
    */
    function transferOwnership(address)

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
     * @dev constructor
    */
    constructor(address treasury)

    /**
     * @dev 查询活动信息
     * @param uint256 活动游标
     * @return {
     *  uint256: 活动开始时间
     *  uint256: 活动结束时间
     *  uint256: 活动打卡最低次数
     *  uint256: 活动奖励 token 总量
     *  address: 活动奖励 token 地址
     * }
     */
    function activityInfo(uint256) view returns(uint256,uint256,uint256,uint256,address)

    /**
     * @dev 查询总活动数量
     * @return uint256
     */
    function activityLength() view returns(uint256)

    /**
     * @dev 查询活动已完成最低限度打卡次数总人数
     * @param uint256 活动游标
     * @return uint256
    */
    function activitySuccessAmount(uint256) view returns(uint256)

    /**
     * @dev 领取活动奖励
     * @param index 活动游标
     * @param user 用于接收奖励的账户地址
     */
    function claim(uint256,address)

    /**
     * @dev 创建活动
     * @notice onlyOwner
     * @param uint256 活动打开开始时间戳
     * @param uint256 总打卡天数
     * @param uint256 最低打卡天数
     * @param uint256 活动总奖励 token 数量
     * @param address 活动奖励 token 地址
    */
    function createActivity(uint256,uint256,uint256,uint256,address)

    /**
     * @dev 查询合约所有者地址
     * @return address
    */
    function owner() view returns(address)

    /**
     * @dev 活动打卡
     * @param index 活动游标
     */
    function punchIn(uint256)

    /**
     * @dev 放弃合约所有权，合约所有人默认为0地址
     * @notice onlyOwner
    */
    function renounceOwnership()

    /**
     * @dev 设置金库账户地址
     * @notice onlyOwner
     * @param address 新金库账户地址
     */
    function setTreasury(address)

    /**
     * @dev 转移合约所有权至指定地址
     * @notice onlyOwner
     * @prama address 新的所有者地址
    */
    function transferOwnership(address)

    /**
     * @dev 更新活动配置
     * @notice onlyOwner
     * @param uint256 活动游标
     * @param uint256 活动奖励 token 总量
     * @param address 活动奖励 token 地址
    */
    function updateActivity(uint256,uint256,address)

    /**
     * @dev 查询用户信息
     * @param uint256 活动游标
     * @param address 用户地址
     * @return {
     *  uint256: 上一次打卡时间戳
     *  uint256: 累计打卡次数
     *  bool: 是否已领取活动奖励
     * }
     */
    function userInfo(uint256,address) view returns(uint256,uint256,bool)

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
     * @dev constructor
    */
    constructor(address _treasury, address _lpToken, address _offeringToken, uint256 _startTimestamp, uint256 _endTimestamp, uint256 _offeringAmount, uint256 _raisingAmount)

    /**
     * @dev 查询 IFO 白名单账户地址
     * @param uint256 数组游标
     * @return address
    */
    function addressList(uint256) view returns(address)

    /**
     * @dev 质押募集 token，参与 IFO
     * @param uint256 token 数量
    */
    function deposit(uint256)

    /**
     * @dev 查询 IFO 结束时间戳
     * @return uint256
    */
    function endTimestamp() view returns(uint256)

    /**
     * @dev 查询白名单数组长度
     * @return uint256
    */
    function getAddressListLength() view returns(uint256)

    /**
     * @dev 查询用户当前已购买到的 token 的数量
     * @param address 账户地址
     * @return uint256
    */
    function getOfferingAmount(address) view returns(uint256)

    /**
     * @dev 查询用户当前退回募集 token 的数量
     * @param address 账户地址
     * @return uint256
    */
    function getRefundingAmount(address) view returns(uint256)

    /**
     * @dev 领取已成功购买 token
    */
    function harvest()

    /**
     * @dev 查询已领取用户数量
     * @return uint256
    */
    function harvestedCount() view returns(uint256)

    /**
     * @dev 查询用户是否已领取
     * @param address 账户地址
     * @return address
    */
    function hasHarvest(address) view returns(address)

    /**
     * @dev 查询募集 token 地址
     * @return address
    */
    function lpToken() view returns(address)

    /**
     * @dev 查询 IFO 出售 token 总量
     * @return uint256
    */
    function offeringAmount() view returns(uint256)

    /**
     * @dev 查询 IFO 出售 token 已被领取的总量
     * @return uint256
    */
    function offeringHarvested() view returns(uint256)

    /**
     * @dev 查询募集 token 地址
     * @return address
    */
    function offeringToken() view returns(address)

    /**
     * @dev 查询所有者账户地址
     * @return address
    */
    function owner() view returns(address)

    /**
     * @dev 查询预期募集 token 总量
     * @return uint256
    */
    function raisingAmount() view returns(uint256)

    /**
     * @dev 放弃合约所有权，合约所有人默认为0地址
     * @notice onlyOwner
    */
    function renounceOwnership()

    /**
     * @dev 配置 IFO 出售 token 总量
     * @notice onlyOwner
     * @return uint256
    */
    function setOfferingAmount(uint256)

    /**
     * @dev 配置 IFO 参数
     * @notice onlyOwner
     * @param uint256 开始块高度
     * @param uint256 结束块高度
     * @param uint256 募集 token 总量
    */
    function setParams(uint256,uint256,uint256)

    /**
     * @dev 查询 IFO 开始时间戳
     * @return uint256
    */
    function startTimestamp() view returns(uint256)

    /**
     * @dev 查询当前已募集 token 总量
     * @return uint256
    */
    function totalAmount() view returns(uint256)

    /**
     * @dev 转移合约所有权至指定地址
     * @prama address 新的所有者地址
    */
    function transferOwnership(address)

    /**
     * @dev 查询金库账户地址
     * @return address
    */
    function treasury() view returns(address)

    /**
     * @dev 查询用户信息
     * @param address 账户地址
     * @return {
     *  uint256: 质押募集 token 数量
     *  bool: 是否已领取购买 token
     * }
    */
    function userInfo(address) view returns(uint256,bool)

    /**
     * @dev 提取合约内 token
     * @notice onlyOwner
     * @param address token 地址
     * @param address 接收者账户地址
     * @param uint256 提取数量
    */
    function withdraw(address,address,uint256)

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

### SinglePool

SinglePool 为单币质押挖矿合约，创建者部署该合约后，可指定质押 token 和 奖励 token 相关配置。 用户可以参与质押挖矿，质押后自动锁仓一段时间，
锁仓结束，用户可提取质押 token。挖矿奖励可随时提取。

```js
    /**
     * @dev constructor
    */
    constructor (address _assetsAccount, address _depositToken, address _rewardToken, uint256 _startBlock, uint256 _mintPerBlock, uint256 _lockDuration)

    /**
     * @dev 查询金库账户地址
     * @return address
    */
    function assetsAccount() view returns(address)

    /**
     * @dev 质押 token 进行挖矿
     * @param uint256 质押 token 数量
     * @param address 质押账户地址
    */
    function deposit(uint256,address)

    /**
     * @dev 查询质押 token 地址
     * @return address
    */
    function depositToken() view returns(address)

    /**
     * @dev 查询当前质押 token 总量
     * @return uint256
    */
    function depositTokenSupply() view returns(uint256)

    /**
     * @dev 领取质押挖矿奖励 token
     * @param address 接收账户地址
    */
    function harvest(address)

    /**
     * @dev 查询质押锁仓时长
     * @return uint256
    */
    function lockDuration() view returns(uint256)

    /**
     * @dev 查询单个区块产 token 数量
     * @return uint256
    */
    function mintPerBlock() view returns(uint256)

    /**
     * @dev 查询合约所有者地址
     * @return address
    */
    function owner() view returns(address)

    /**
     * @dev 查询用户可领取奖励 token 数量
     * @param address 账户地址
     * @return uint256
    */
    function pendingReward(address) view returns(uint256)

    /**
     * @dev 查询当前挖矿待产出奖励 token 总量
     * @return {
     *  uint256: 待产出总量
     *  uint256: 当前区块高度
     * }
    */
    function pendingRewardInfo() view returns(uint256,uint256)

    /**
     * @dev 放弃合约所有权，合约所有人默认为0地址
     * @notice onlyOwner
    */
    function renounceOwnership()

    /**
     * @dev 查询奖励 token 地址
     * @return address
    */
    function rewardToken() view returns(address)

    /**
     * @dev 配置金库账户地址
     * @notice onlyOwner
     * @param address 新金库账户地址
    */
    function setAssetsAccount(address)

    /**
     * @dev 配置单个区块产奖励 token 数量
     * @notice onlyOwner
     * @param uint256 token 数量
    */
    function setEmissionRate(uint256)

    /**
     * @dev 配置锁仓时长
     * @notice onlyOwner
     * @param uint256 新锁仓时长
    */
    function setLockDuration(uint256)

    /**
     * @dev 查询质押活动开始区块高度
     * @return uint256
    */
    function startBlock() view returns(uint256)

    /**
     * @dev 转移合约所有权至指定地址
     * @prama address 新的所有者地址
    */
    function transferOwnership(address)

    /**
     * @dev 查询用户质押挖矿信息
     * @param address 账户地址
     * @return {
     *  uint256: 质押 token 数量
     *  uint256: 解锁时间戳
     *  uint256: 合约内数据
     * }
    */
    function userInfo(address) view returns(uint256,uint256,uint256)

    /**
     * @dev 提取质押 token 
     * @notice 提取质押 token 同时触发奖励领取操作
     * @param uint256 提取 token 数量
     * @param address 接收者账户地址
     */
    function withdraw(uint256,address)

    /**
     * @dev 用户质押时提交事件
     * @param user address caller 账户地址
     * @param to address 质押账户地址
     * @param amount uint256 质押 token 数量
     * @param unlockTime uint256 解锁时间戳
    */
    event Deposit(address indexed user, address indexed to, uint256 amount, uint256 unlockTime);

    /**
     * @dev 用户提取时提交事件
     * @param user address caller 账户地址
     * @param to address 接受者账户地址
     * @param amount uint256 质押 token 数量
    */
    event Withdraw(address indexed user, address indexed to, uint256 amount);

    /**
     * @dev 用户领取挖矿奖励时提交事件
     * @param user address caller 账户地址
     * @param to address 接收者账户地址
     * @param amount uint256 奖励 token 数量
    */
    event Harvest(address indexed user, address indexed to, uint256 amount);
```