## Dreamix Server Contract ABI

```
github.com: https://github.com/burgerswap-org/meta-verse-nft-protocol
```

### ERC20Token
```js
    /**
     * @dev 查询用户余额
     * @param address 用户钱包地址
     * @return uint256
    */
    function balanceOf(address) view returns (uint256);

    /**
     * @dev 查询 token 名称
     * @return string
    */
    function name() view returns (string memory);

    /**
     * @dev 查询 token 符号
     * @return string
    */
    function symbol() view returns (string memory);

    /**
     * @dev 查询 token 精度位数
     * @return uint8
    */
    function decimals() view returns (uint8);

    /**
     * @dev 查询 token 总发行量
     * @return uint256
    */
    function totalSupply() view returns (uint256);

    /**
     * @dev 查询用户授权给花销者可用额度
     * @param address 用户地址
     * @param address 花销者地址
     * @return uint256
    */
    function allowance(address,address) view returns (uint256);

    /**
     * @dev 用户授权给其他用户可以支配用户的资金
     * @param address 花销者地址
     * @param uint256 批准数量
    */
    function approve(address,uint256);

    /**
     * @dev 用户转账给其他用户资金
     * @param address 接收者地址
     * @param uint256 数量
    */
    function transfer(address,uint256);

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
```js
    /**
     * @dev 获取 NFT 名称
     * @return string
    */
    function name() view returns (string memory);

    /**
     * @dev 获取 NFT 符号
     * @return string
    */
    function symbol() view returns (string memory);

    /**
     * @dev 获取合约 NFT 总量
     * @return uint256
    */
    function totalSupply() view returns (uint256);

    /**
     * @dev 通过下标获取 tokenId
     * @notice 下标范围可通过 {totalSupply} 方法获取，从0开始
     * @param uint256 nft 数组下标
     * @return uint256
    */
    function tokenByIndex(uint256) view returns (uint256);

    /**
     * @dev 获取用户拥有的 nft 总量
     * @param address 账户地址
     * @return uint256
     */
    function balanceOf(address) view returns (uint256);

    /**
     * @dev 通过下标获取用户 tokenId
     * @notice 下标范围可通过 {balanceOf} 方法获取，从0开始
     * @param address 账户地址
     * @param uint256 账户拥有 nft 数组下标
     * @return uint256
    */
    function tokenOfOwnerByIndex(address,uint256) view returns (uint256);

    /**
     * @dev 查询 tokenURI(元数据)
     * @param uint256 tokenId
     * @return string
    */
    function tokenURI(uint256) view returns (string memory);

    /**
     * @dev 查询 tokenId 所有者的账户地址
     * @param uint256 tokenId
     * @return address
    */
    function ownerOf(uint256) view returns (address);

    /**
     * @dev 查询 nft 所有者是否将自己所有的 nft 的转移权限批准给操作人
     * @param address nft 所有者的账户地址
     * @param address 操作人账户地址
     * @return bool
    */
    function isApprovedForAll(address,address) view returns (bool);

    /**
     * @dev 查询 nft 被批准人的账户地址
     * @param uint256 tokenId
     * @return address
    */
    function getApproved(uint256) view returns (address);

    /**
     * @dev 将指定 nft 批准给目标账户
     * @param address 被批准人账户地址
     * @param uint256 指定的 tokenId
    */
    function approve(address,uint256);

    /**
     * @dev 调用者拥有的 nft 对目标账户的批准状态
     * @notice 要求调用者账户地址与目标账户不能相同
     * @param address 操作人账户地址
     * @param bool 批准状态 [true: 已批准, false: 未批准]
    */
    function setApprovalForAll(address,bool);

    /**
     * @dev 将指定 nft 从所有者账户转移至目标账户
     * @param address nft 所有者账户地址
     * @param address nft 接受者账户地址
     * @param uint256 tokenId
    */
    function transferFrom(address,address,uint256);

    /**
     * @dev transferFrom mint batchMint 时提交事件
     * @param from address 转出账户地址
     * @param to address 接受账户地址
     * @param tokenId uint256 tokenId
    */
    event Transfer(address indexed from, address indexed to, uint256 indexed tokenId);
```

### ERC1155Token 
```js
    /**
     * @dev 查询 token 基础 URI
    */
    function uri(uint256 id) view returns (string memory);

    /**
     * @dev 查询 tokenURI(元数据)
     * @param tokenId uint256 tokenId
    */
    function tokenURI(uint256 tokenId) view returns (string memory);

    /**
     * @dev 根据 tokenId, 查询用户 token 的数量
     * @param account address 账户地址 
     * @param id uint256 ERC1155 token 唯一标识符
    */
    function balanceOf(address account, uint256 id) view returns (uint256);

    /**
     * @dev 批量查询用户 token 的数量
     * @notice 要求 accounts ids 数组长度一致
     * @param accounts address[] 账户地址数组
     * @param ids uint256[] ERC1155 token 唯一标识符
    */
    function balanceOfBatch(address[] calldata accounts, uint256[] calldata ids) view returns (uint256[] memory);

    /**
     * @dev 查询操作者地址是否拥有指定账户所有 token 的转移权限
     * @param account address token 拥有者账户地址
     * @param operator address 操作者账户地址
    */
    function isApprovedForAll(address account, address operator) view returns (bool);

    /**
     * @dev 设置调用者所拥有的 token 的转移权限
     * @param operator address 操作者账户地址
     * @param approved bool  批准状态 [true: 批准, false: 未批准]
    */
    function setApprovalForAll(address operator, bool approved);

    /**
     * @dev 从转出账户地址转移指定数量的 token 至接收账户地址
     * @notice 要求调用者拥有转出账户的批准，或者调用者为转出账户
     * @param from address 转出账户地址
     * @param to address 接受账户地址
     * @param id uint256 tokenId
     * @param amount uint256 转移数量
     * @param data string 交易信息，可为空 "0x"
    */
    function safeTransferFrom(address from, address to, uint256 id, uint256 amount, bytes calldata data);

    /**
     * @dev 批量从转出账户地址转移不同数量的不同 token 至接收账户地址
     * @notice 要求调用者拥有转出账户的批准，或者调用者为转出账户
     * @param from address 转出账户地址
     * @param to address 接受账户地址
     * @param ids uint256[] tokenId 数组
     * @param amounts uint256[] 转移数量数组
     * @param data string 交易信息，可为空 "0x"
    */
    function safeBatchTransferFrom(address from, address to, uint256[] calldata ids, uint256[] calldata amounts, bytes calldata data);

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

### AssetERC721 is ERC721Token
```js
    /**
     * @dev 查询 NFT 证书链接
    */
    function getLicenseURI() view returns (string memory);

    /**
     * @dev 查询 NFT 证书名称
    */
    function getLicenseName() view returns (string memory);

    /**
     * @dev 查询账户 tokenIds
     * @param user address 账户地址
     * @param cursor uint256 起始游标
     * @param size uint256 获取数量
    */
    function tokensOfOwnerBySize(address user, uint256 cursor, uint256 size) view returns (uint256[] memory, uint256);

    /**
     * @dev 配置基础 URI，如果存在则作为每个 tokenURI 的前缀
     * @notice 根据 NFT 的创建 mode，进行接口调用权限管理.
     * 例如 mode = 0, 则只能由创建者账户调用
     * @param _baseURI string
    */
    function setBaseURI(string memory _baseURI);

    /**
     * @dev 增发一个 token
     * @notice 根据 NFT 的创建 mode，进行接口调用权限管理.
     * 例如 mode = 0, 则只能由创建者账户调用
     * @param to address 接受者账户地址，用于接受增发的 token
     * @param tokenURI string NFT元数据
    */
    function mint(address to, string memory tokenURI);

    /**
     * @dev 批量增发 token
     * @notice 根据 NFT 的创建 mode，进行接口调用权限管理.
     * 例如 mode = 0, 则只能由创建者账户调用
     * 从起始至结束，单调递增，过程中出现与已有重复则全部增发失败
     * @param to address 接受者账户地址，用于接受增发的 token
     * @param amount uint256 增发数量
     * @param tokenURIs string[] NFT 元数据数组
    */
    function batchMint(address to, uint256 amount, string[] memory tokenURIs) external；

    /**
     * @dev 配置基础 URI，如果存在则作为每个 tokenURI 的前缀
     * @notice 根据 NFT 的创建 mode，进行接口调用权限管理，且只能烧毁本人 token。
     * @param tokenId uint256 指定的 tokenId，要求不可重复
    */
    function burn(uint256 tokenId);
```

### AssetERC1155 is ERC1155Token 
```js
    /**
     * @dev 查询 NFT 证书链接
    */
    function getLicenseURI() view returns (string memory);

    /**
     * @dev 查询 NFT 证书名称
    */
    function getLicenseName() view returns (string memory);

    /**
     * @dev 查询 token 基础 URI
    */
    function uri(uint256 id) view returns (string memory);

    /**
     * @dev 查询 tokenURI(元数据)
     * @param tokenId uint256 tokenId
    */
    function tokenURI(uint256 tokenId) view returns (string memory);

    /**
     * @dev 设置所有类型 token 的基础 URI
     * @param uri string 
    */
    function setURI(string memory uri);

    /**
     * @dev 向指定账户中增发指定类型的 token（创建 tokenId, 增发数量）
     * @param to address 接受者账户地址
     * @param amount uint256 增发数量
     * @param tokenURI string NFT 元数据
    */
    function mint(address to, uint256 amount, string memory tokenURI_);

    /**
     * @dev 向指定账户增发已存在 tokenId 的数量
     * @param to address 接受者账户地址
     * @param id uint256 tokenId
     * @param amount uint256 增发数量
    */
    function mintAmount(address to, uint256 id, uint256 amount);

    /**
     * @dev 批量向指定账户中增发指定范围类型的 token
     * @param to string 接受者账户地址
     * @param tokenIdAmount uint256 增发 tokenId 的数量
     * @param amounts uint256[] 每个 tokenId 增发个数的数组
     * @param tokenURIs string[] NFT 元数据数组
    */
    function batchMint(address to, uint256 tokenIdAmount, uint256[] memory amounts, string[] memory tokenURIs);

    /**
     * @dev 销毁token
     * @notice 要求调用者拥有被销毁账户的批准，或者调用者为被销毁账户
     * @param account string 被销毁账户地址
     * @param id uint256 token 类型 id
     * @param amount uint256 销毁数量
    */
    function burn(address account, uint256 id, uint256 amount);
```

### NFTEnglishAuction
英式拍卖合约，用于挂售 ERC721 或 ERC1155 类型 NFT
```js
    /**
     * @dev 查询总挂单数量
    */
    function getPoolCount() view returns (uint256);

    /**
     * @dev 通过游标查询挂单信息
     * @notice 游标取值范围可以通过 {getPoolCount} 方法获取
     * @param index uint256 挂单游标
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
     * }
    */
    // function pools(uint256) returns(Pool memory);
    function pools(uint256) returns(address creator, string name, address token0, address token1, uint256 tokenId, uint256 tokenAmount0, uint256 amountMax1, uint256 amountMin1, uint256 amountMinIncr1, uint256 openAt, uint256 closeAt, uint256 nftType);

    /**
     * @dev 查询挂单是否已被领取
     * @param index uint256 挂单游标
    */
    function claimedP(uint256) returns (bool);

    /**
     * @dev 查询挂单是否要求 BotToken 持有者才可以出价
     * @param index uint256 挂单游标
    */
    function onlyBotHolderP(uint256) returns (bool);

    /**
     * @dev 查询挂单当前最高价竞拍者地址
     * @param index uint256 挂单游标
    */
    function currentBidderP(uint256) returns (address);

    /**
     * @dev 查询挂单当前竞拍最高价
     * @param index uint256 挂单游标
    */
    function currentBidderAmount1P(uint256) returns (uint256);

    /**
     * @dev 查询挂单最低成交价
     * @param index uint256 挂单游标
    */
    function reserveAmount1P(uint256) returns (uint256);

    /**
     * @dev 查询目标用户是否为挂单创建人
     * @param target string 目标用户地址
     * @param index uint256 挂单游标
    */
    function myCreatedP(address, uint256) returns (bool);

    /**
     * @dev 查询目标用户某个挂单出价
     * @param user string 账户地址
     * @param index uint256 挂单游标
    */
    function myBidderAmount1P(address, uint256) returns (uint256);

    /**
     * @dev 查询挂单竞价数量
     * @param index uint256 挂单游标
    */
    function bidCountP(uint256) returns (uint256);

    /**
     * @dev 查询挂单下一次竞价出价数量，即当前最高竞价数量加上加价间隔
     * @param index uint256 挂单游标
    */
    function currentBidderAmount(uint256 index) view returns (uint256);

    /**
     * @dev 查询挂单是否被取消
     * @param index uint256 挂单游标
    */
    function creatorCanceledP(uint256) returns (bool);

    /**
     * @dev 查询 BotToken 合约地址
    */
    function getBotToken() view returns (address);

    /**
     * @dev 查询 BotToken 最少持有数量
    */
    function getMinValueOfBotHolder() view returns (uint256);

    /**
     * @dev 查询是否禁止挂 ERC721 类型的 NFT [true: 禁止, false:未禁止] 默认 false
    */
    function getDisableErc721() view returns (bool);

    /**
     * @dev 是否禁止挂 ERC1155 类型的 NFT [true: 禁止, false:未禁止] 默认 false
    */
    function getDisableErc1155() view returns (bool);


    /**
     * @dev 创建 ERC721 类型挂单
     * @notice 创建挂单之前，需要将出售的 token 批准给挂单合约，否则挂单失败
     * @param name string 名称
     * @param token0 address 换出 token 的合约地址（NFT 合约地址）
     * @param token1 address 换入 token 的合约地址（token 合约地址）
     * @param tokenId uint256 换出 token 的 tokenId
     * @param amountMax1 uint256 换出最高价格
     * @param amountMin1 uint256 换出最低价格
     * @param amountMinIncr1 uint256 单次出价最低加价数量
     * @param amountReserve1 uint256 
     * @param openAt uint256 挂单开售时间，unix timestamp
     * @param duration uint256 挂单持续时间，单位秒
     * @param onlyBot bool 是否开启限购
    */
    function createErc721(
        string memory name,
        address token0,
        address token1,
        uint256 tokenId,
        uint256 amountMax1,
        uint256 amountMin1,
        uint256 amountMinIncr1,
        uint256 amountReserve1,
        uint256 openAt,
        uint256 duration,
        bool onlyBot
    );

    /**
     * @dev 创建 ERC1155 类型挂单
     * @notice 创建挂单之前，需要将出售的 token 批准给挂单合约，否则挂单失败
     * @param name string 名称
     * @param token0 address 换出 token 的合约地址（NFT 合约地址）
     * @param token1 address 换入 token 的合约地址（token 合约地址）
     * @param tokenId uint256 换出 token 的 id
     * @param tokenAmount0 uint256 换出 token 数量
     * @param amountMax1 uint256 换出最高价格
     * @param amountMin1 uint256 换出最低价格
     * @param amountMinIncr1 uint256 单次出价最低加价数量
     * @param amountReserve1 uint256 
     * @param openAt uint256 挂单开售时间，unix timestamp
     * @param duration uint256 挂单持续时间，单位秒
     * @param onlyBot bool 是否开启限购
    */
    function createErc1155(
        string memory name,
        address token0,
        address token1,
        uint256 tokenId,
        uint256 tokenAmount0,
        uint256 amountMax1,
        uint256 amountMin1,
        uint256 amountMinIncr1,
        uint256 amountReserve1,
        uint256 openAt,
        uint256 duration,
        bool onlyBot
    );

    /**
     * @dev 对挂单出价
     * @notice 如果挂单换入 token 的合约地址不等于0地址, 出价前要求换入 token 已批准给挂单合约
     * @notice 如果出价低于当前最高价或者加价低于最低加价数量，则失败
     * @notice 如果出价大于等于挂单最高价，直接结单，自动执行 {creatorClaim} {bidderClaim}
     * @param index uint256 挂单游标
     * @param amount1 出价数量
    */
    function bid(uint256 index, uint256 amount1) payable;

    /**
     * @dev 取消挂单
     * @notice 目前只支持挂单开售前取消
     * @param index uint256 挂单游标
    */
    function cancel(uint256 index);

    /**
     * @dev 领取挂单，竞拍成功双方交换资产至各自账户，流拍双方资产原路退还
     * @notice 要求挂单在时间上已结束
     * @param index uint256 挂单游标
    */
    function claim(uint256 index);

    /**
     * @dev createErc721 createErc1155 时提交事件
     * @param sender address 卖家地址
     * @param index uint256 挂单游标
    */
    event Created(address indexed sender, uint256 indexed index);
```

### NFTFixedswap
定价售卖合约，用于出售 ERC721 或 ERC1155 类型 NFT
```js
    /**
     * @dev 查询总挂单数量
    */
    function getPoolCount() view returns (uint256);

    /**
     * @dev 通过游标查询挂单详情
     * @notice 游标取值范围可以通过 {getPoolCount} 方法获取
     * @param index uint256 挂单游标
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
    // function pools(uint256) returns(Pool memory);
    function pools(uint256) returns(address creator, string name, address token0, address token1, uint256 tokenId, uint256 amountTotal0, uint256 amountTotal1, uint256 nftType, uint256 openAt);

    /**
     * @dev 查询目标用户是否为挂单创建人
     * @param target string 目标用户地址
     * @param index uint256 挂单游标
    */
    function myCreatedP(address, uint256) returns (bool);

    /**
     * @dev 查询挂单是否要求 BotToken 持有者才可以出价
     * @param index uint256 挂单游标
    */
    function onlyBotHolderP(uint256) returns (bool);

    /**
     * @dev 查询挂单是否已取消挂单 [true: 是, false: 否]
     * @param index uint256 挂单游标
    */
    function creatorCanceledP(uint256) returns (bool);

    /**
     * @dev 查询挂单是否已结单 [true: 是, false: 否]
     * @param index uint256 挂单游标
    */
    function swappedP(uint256) returns (bool);

    /**
     * @dev 查询是否开启 token0 限售模式
     * @return bool [true: 开启, false: 未开启]
    */
    function checkToken0() returns (bool);

    /**
     * @dev 查询 token 是否在可售白名单
     * @param token string token 合约地址
     * @return bool [true: 可售, false: 不可售]
    */
    function token0List(address) returns (bool);

    /**
     * @dev 查询挂单是否被取消
     * @param index uint256 挂单游标
    */
    function creatorCanceledP(uint256) returns (bool);

    /**
     * @dev 查询 BotToken 合约地址
    */
    function getBotToken() view returns (address);

    /**
     * @dev 查询 BotToken 最少持有数量
    */
    function getMinValueOfBotHolder() view returns (uint256);

    /**
     * @dev 查询是否禁止挂 ERC721 类型的 NFT [true: 禁止, false:未禁止] 默认 false
    */
    function getDisableErc721() view returns (bool);

    /**
     * @dev 是否禁止挂 ERC1155 类型的 NFT [true: 禁止, false:未禁止] 默认 false
    */
    function getDisableErc1155() view returns (bool);

    /**
     * @dev 创建 ERC721 类型挂单
     * @notice 创建挂单之前，需要将出售的 token 批准给挂单合约，否则挂单失败
     * @param name string 名称
     * @param token0 address 换出 token 的合约地址（NFT 合约地址）
     * @param token1 address 换入 token 的合约地址（token 合约地址）
     * @param tokenId uint256 换出 token 的 tokenId
     * @param amountTotal1 uint256 换入 token 总量
     * @param openAt uint256 挂单开售时间，unix timestamp
     * @param onlyBot bool 是否开启限购
    */
    function createErc721(string memory name, address token0, address token1, uint256 tokenId, uint256 amountTotal1, uint256 openAt, bool onlyBot);


    /**
     * @dev 创建 ERC1155 类型挂单
     * @notice 创建挂单之前，需要将出售的 token 批准给挂单合约，否则挂单失败
     * @param name string 名称
     * @param token0 address 换出 token 的合约地址（NFT 合约地址）
     * @param token1 address 换入 token 的合约地址（token 合约地址）
     * @param tokenId uint256 换出 token 的 tokenId
     * @param amountTotal0 uint256 换出 token 总量
     * @param amountTotal1 uint256 换入 token 总量
     * @param openAt uint256 挂单开售时间，unix timestamp
     * @param onlyBot bool 是否开启限购
    */
    function createErc1155(string memory name, address token0, address token1, uint256 tokenId, uint256 amountTotal0, uint256 amountTotal1, uint256 openAt, bool onlyBot);


    /**
     * @dev 购买挂单
     * @notice 如果挂单换入 token 的合约地址不等于0地址, 出价前要求换入 token 已批准给挂单合约
     * @notice 可部分购买，换取等比例数量的换出 token
     * @notice 购买数量 + 已售出量 >= 换出总量 则结单
     * @param index uint256 挂单游标
     * @param amount0 购买的换出 token 的数量
    */
    function swap(uint256 index, uint256 amount0) payable;

    /**
     * @dev 取消挂单
     * @notice 要求挂单未结单
     * @param index uint256 挂单游标
    */
    function cancel(uint256 index);

    /**
     * @dev createErc721 createErc1155 时提交事件
     * @param sender address 卖家地址
     * @param index uint256 挂单游标
     * @param pool Pool 挂单详情
    */
    event Created(address indexed sender, uint256 indexed index);
```


### Land
土地 NFT 合约

//      *************** B 
//      *             *
//      *             *
//    A ***************
//  
//    A (x1, y1)
//    B (x2, y2)

```js
/// event
    /**
     * @dev 创建 NFT 时, 提交该事件
     * @param to address NFT 接受者账户地址
     * @param x1 uint256 A 点 x 轴坐标
     * @param y1 uint256 A 点 y 轴坐标
     * @param x2 uint256 B 点 x 轴坐标
     * @param y2 uint256 B 点 y 轴坐标
     * @param tokenId uint256 NFT tokenId
     */
    event Mint(address to, uint256 x1, uint256 y1, uint256 x2, uint256 y2, uint256 tokenId);

    /**
     * @dev 销毁 NFT 时, 提交该事件
     * @param from address NFT 所有者账户地址
     * @param x1 uint256 A 点 x 轴坐标
     * @param y1 uint256 A 点 y 轴坐标
     * @param x2 uint256 B 点 x 轴坐标
     * @param y2 uint256 B 点 y 轴坐标
     * @param tokenId uint256 NFT tokenId
     */
    event Burn(address from, uint256 x1, uint256 y1, uint256 x2, uint256 y2, uint256 tokenId);

    /**
     * @dev 合并两个相邻 NFT 时, 提交该事件
     * @param to address NFT 接受者账户地址
     * @param tokenId1 uint256 待合并 NFT tokenId
     * @param tokenId2 uint256 待合并 NFT tokenId
     * @param tokenId uint256 合并创建的 NFT tokenId
     */
    event MergeFromBlock(address to, uint256 tokenId1, uint256 tokenId2, uint256 tokenId);

    /**
     * @dev 拆分转移 NFT 时, 提交该事件
     * @param from address 待拆分 NFT 所有者账户地址
     * @param to address NFT 接受者账户地址
     * @param tokenId uint256 待拆分的 NFT tokenId
     * @param tokenId1 uint256 拆分得到 NFT tokenId，转移至 to 账户地址
     * @param tokenId2 uint256 拆分得到 NFT tokenId，保留在 from 账户地址
     */
    event SplitToTransfer(address from, address to, uint256 tokenId, uint256 tokenId1, uint256 tokenId2);

    /**
     * @dev 合并单元 NFT 时, 提交该事件
     * @param to address NFT 接受者账户地址
     * @param x1 uint256 A 点 x 轴坐标
     * @param y1 uint256 A 点 y 轴坐标
     * @param x2 uint256 B 点 x 轴坐标
     * @param y2 uint256 B 点 y 轴坐标
     * @param tokenId uint256 合并创建的 NFT tokenId
     */
    event MergeFromUnit(address to, uint256 x1, uint256 y1, uint256 x2, uint256 y2, uint256 tokenId);

    /**
     * @dev 拆分一个 NFT 为多个非单元 NFT 时, 提交该事件
     * @param to address NFT 接受者账户地址
     * @param tokenId uint256 待拆分的 NFT tokenId
     * @param tokenId1 uint256 拆分得到 NFT tokenId，一定存在
     * @param tokenId2 uint256 拆分得到 NFT tokenId，一定存在
     * @param tokenId3 uint256 拆分得到 NFT tokenId，选择存在，不存在默认 0
     * @param tokenId4 uint256 拆分得到 NFT tokenId，选择存在，不存在默认 0
     */
    event SplitToBlock(address to, uint256 tokenId, uint256 tokenId1, uint256 tokenId2, uint256 tokenId3, uint256 tokenId4);

    /**
     * @dev 拆分一个 NFT 为多个 NFT 时, 提交该事件
     * @param to address NFT 接受者账户地址
     * @param tokenId uint256 待拆分的 NFT tokenId
     */
    event SplitToUnit(address to, uint256 tokenId);


/// write
    /**
     * @dev 根据矩形 A B 两点坐标创建一个 NFT
     * @param to address NFT 接受者账户地址
     * @param x1 uint256 A 点 x 轴坐标
     * @param y1 uint256 A 点 y 轴坐标
     * @param x2 uint256 B 点 x 轴坐标
     * @param y2 uint256 B 点 y 轴坐标
     */
    function mint(address to, uint256 x1, uint256 y1, uint256 x2, uint256 y2);

    /**
     * @dev 销毁一个 NFT
     * @notice 要求操作者为 NFT 所有者账户或者被批准账户！！！
     * @param tokenId uint256 NFT tokenId
     */
    function burn(uint256 tokenId);

    /**
     * @dev 将两个相邻的矩形 NFT 合并成一个 NFT
     * @notice 条件：
     * @notice 1.要求两个矩形共用一条边，且该边长相同！！！
     * @notice 2.要求操作者为两个 NFT 所有者账户或者被批准账户！！！
     * @param to address NFT 接受者账户地址
     * @param tokenId1 uint256 NFT tokenId
     * @param tokenId2 uint256 NFT tokenId
     */
    function mergeFromBlock(address to, uint256 tokenId1, uint256 tokenId2);

    /**
     * @dev 根据矩形 A B 两点坐标，合并矩形范围内最小单元 NFT 为一个 NFT 
     * @param to address NFT 接受者账户地址
     * @param x1 uint256 A 点 x 轴坐标
     * @param y1 uint256 A 点 y 轴坐标
     * @param x2 uint256 B 点 x 轴坐标
     * @param y2 uint256 B 点 y 轴坐标
     */
    function mergeFromUnit(address to, uint256 x1, uint256 y1, uint256 x2, uint256 y2);

    /**
     * @dev 将目标 NFT 拆分转移
     * @param to address NFT 接受者账户地址
     * @param tokenId uint256 NFT tokenId
     * @param x1 uint256 待转移矩形 A 点 x 轴坐标
     * @param y1 uint256 待转移矩形 A 点 y 轴坐标
     * @param x2 uint256 待转移矩形 B 点 x 轴坐标
     * @param y2 uint256 待转移矩形 B 点 y 轴坐标
     */
    function splitToTransfer(address to, uint256 tokenId, uint256 x1, uint256 y1, uint256 x2, uint256 y2);

    /**
     * @dev 将目标 NFT 拆分为最多四个 NFT
     * @param to address NFT 接受者账户地址
     * @param tokenId uint256 NFT tokenId
     * @param x uint256 x 轴坐标，取值范围 [x1, x2]
     * @param y uint256 y 轴坐标，取值范围 [y1, y2]
     */
    function splitToBlock(address to, uint256 tokenId, uint256 x, uint256 y);

    /**
     * @dev 将目标 NFT 拆分为多个最小单位 NFT
     * @param to address NFT 接受者账户地址
     * @param tokenId uint256 NFT tokenId
     */
    function splitToUnit(address to, uint256 tokenId);

/// read
    /**
     * @dev 查询坐标矩形是否已经被创建为 NFT
     * @param x1 uint256 A 点 x 轴坐标
     * @param y1 uint256 A 点 y 轴坐标
     * @param x2 uint256 B 点 x 轴坐标
     * @param y2 uint256 B 点 y 轴坐标
     */
    function exist(uint256 x1, uint256 y1, uint256 x2, uint256 y2) view returns (bool);

    /**
     * @dev 查询 NFT 坐标
     * @param tokenId uint256 NFT tokenId
     * @return x1 uint256 A 点 x 轴坐标
     * @return y1 uint256 A 点 y 轴坐标
     * @return x2 uint256 B 点 x 轴坐标
     * @return y2 uint256 B 点 y 轴坐标
     */
    function tokenCoordinate(uint256 tokenId) pure returns(uint256 x1, uint256 y1, uint256 x2, uint256 y2);

    /**
     * @dev 计算 NFT 坐标
     * @param x1 uint256 A 点 x 轴坐标
     * @param y1 uint256 A 点 y 轴坐标
     * @param x2 uint256 B 点 x 轴坐标
     * @param y2 uint256 B 点 y 轴坐标
     * @return tokenId uint256 NFT tokenId
     */
    function calculateTokenId(uint256 x1, uint256 y1, uint256 x2, uint256 y2) pure returns (uint256 tokenId);
```

### LandSell
土地售卖合约，包括英式拍卖和定价售卖
```js
/// event
    /**
     * @dev 参与竞拍时提交该事件
     * @param operator address 竞拍人账户地址
     * @param x1 uint256 A 点 x 轴坐标
     * @param y1 uint256 A 点 y 轴坐标
     * @param x2 uint256 B 点 x 轴坐标
     * @param y2 uint256 B 点 y 轴坐标
     * @param amount uint256 参与竞拍价格
     */
    event Bid(address indexed operator, uint256 x1, uint256 y1, uint256 x2, uint256 y2, uint256 amount);

    /**
     * @dev 领取竞拍时提交该事件
     * @param operator address 竞拍人账户地址
     * @param x1 uint256 A 点 x 轴坐标
     * @param y1 uint256 A 点 y 轴坐标
     * @param x2 uint256 B 点 x 轴坐标
     * @param y2 uint256 B 点 y 轴坐标
     */
    event Claim(address indexed operator, uint256 x1, uint256 y1, uint256 x2, uint256 y2);

    /**
     * @dev 购买定价单时提交该事件
     * @param operator address 买家账户地址
     * @param x1 uint256 A 点 x 轴坐标
     * @param y1 uint256 A 点 y 轴坐标
     * @param x2 uint256 B 点 x 轴坐标
     * @param y2 uint256 B 点 y 轴坐标
     * @param amount uint256 购买价格
     */
    event Buy(address indexed operator, uint256 x1, uint256 y1, uint256 x2, uint256 y2, uint256 amount);


/// write
    /**
     * @dev 参与竞拍
     * @param x1 uint256 A 点 x 轴坐标
     * @param y1 uint256 A 点 y 轴坐标
     * @param x2 uint256 B 点 x 轴坐标
     * @param y2 uint256 B 点 y 轴坐标
     * @param amountMax uint256 拍卖最高价
     * @param amountMin uint256 拍卖起拍价
     * @param amountMinIncr uint256 单次出价最低加价数量
     * @param openAt uint256 起拍时间 unix timestamp
     * @param closeAt uint256 停拍时间 unix timestamp
     * @param amount uint256 参与竞拍价格
     * @param signature bytes 服务端私钥签名信息
     */
    function bid(
        uint256 x1,
        uint256 y1,
        uint256 x2,
        uint256 y2,
        uint256 amountMax,
        uint256 amountMin,
        uint256 amountMinIncr,
        uint256 openAt,
        uint256 closeAt,
        uint256 amount,
        bytes memory signature
    ) payable;

    /**
     * @dev 竞拍结束，领取竞拍 NFT
     * @param x1 uint256 A 点 x 轴坐标
     * @param y1 uint256 A 点 y 轴坐标
     * @param x2 uint256 B 点 x 轴坐标
     * @param y2 uint256 B 点 y 轴坐标
     */
    function cliam(uint256 x1, uint256 y1, uint256 x2, uint256 y2);

    /**
     * @dev 购买定价单
     * @param x1 uint256 A 点 x 轴坐标
     * @param y1 uint256 A 点 y 轴坐标
     * @param x2 uint256 B 点 x 轴坐标
     * @param y2 uint256 B 点 y 轴坐标
     * @param openAt uint256 起售时间 unix timestamp
     * @param closeAt uint256 停售时间 unix timestamp
     * @param amount uint256 参与竞拍价格
     * @param signature bytes 服务端私钥签名信息
     */
    function buy(
        uint256 x1,
        uint256 y1,
        uint256 x2,
        uint256 y2,
        uint256 amount,
        uint256 openAt,
        uint256 closeAt,
        bytes memory signature
    ) payable;


/// read
    /**
     * @dev 校验竞拍单，服务端私钥签名信息是否有效
     * @param x1 uint256 A 点 x 轴坐标
     * @param y1 uint256 A 点 y 轴坐标
     * @param x2 uint256 B 点 x 轴坐标
     * @param y2 uint256 B 点 y 轴坐标
     * @param amountMax uint256 拍卖最高价
     * @param amountMin uint256 拍卖起拍价
     * @param amountMinIncr uint256 单次出价最低加价数量
     * @param openAt uint256 起拍时间 unix timestamp
     * @param closeAt uint256 停拍时间 unix timestamp
     * @param signature bytes 服务端私钥签名信息
     * @return bool [true: 有效, false: 无效]
     */
    function verifyBidSignature(
        uint256 x1,
        uint256 y1,
        uint256 x2,
        uint256 y2,
        uint256 amountMax,
        uint256 amountMin,
        uint256 amountMinIncr,
        uint256 openAt,
        uint256 closeAt,
        bytes memory signature
    ) view returns (bool);

    /**
     * @dev 校验定价单，服务端私钥签名信息是否有效
     * @param x1 uint256 A 点 x 轴坐标
     * @param y1 uint256 A 点 y 轴坐标
     * @param x2 uint256 B 点 x 轴坐标
     * @param y2 uint256 B 点 y 轴坐标
     * @param amount uint256 定价
     * @param openAt uint256 起售时间 unix timestamp
     * @param closeAt uint256 停售时间 unix timestamp
     * @param signature bytes 服务端私钥签名信息
     * @return bool [true: 有效, false: 无效]
     */
    function verifyFixedSignature(
        uint256 x1,
        uint256 y1,
        uint256 x2,
        uint256 y2,
        uint256 amount,
        uint256 openAt,
        uint256 closeAt,
        bytes memory signature
    ) view returns (bool);

    /**
     * @dev 获取竞拍单信息
     * @param x1 uint256 A 点 x 轴坐标
     * @param y1 uint256 A 点 y 轴坐标
     * @param x2 uint256 B 点 x 轴坐标
     * @param y2 uint256 B 点 y 轴坐标
     * @return address 当前最高竞拍人账户地址
     * @return uint256 当前最高竞拍价
     * @return bool 当前竞拍单是否已被领取 [true: 已领取, false: 未领取]
     */
    function bidInfo(
        uint256 x1,
        uint256 y1,
        uint256 x2,
        uint256 y2
    ) view returns (address, uint256, bool);

    /**
     * @dev 获取竞拍单信息
     * @param tokenId uint256 A 点 x 轴坐标
     * @return address 当前最高竞拍人账户地址
     * @return uint256 当前最高竞拍价
     * @return bool 当前竞拍单是否已被领取 [true: 已领取, false: 未领取]
     */
    function bidInfoByTokenId(uint256 tokenId) view returns (address, uint256, bool);
```