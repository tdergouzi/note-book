# Dreamix JS-SDK

## 编译
```
 yarn install # 安装依赖（可能需要国外网络）
 
 yarn build # 编译sdk for browser,编译成功后sdk文件在 ./dist/metaversejssdk.js
 yarn build:module # 编译sdk for app,编译成功后sdk文件在 ./dist/metaversejssdk.*
```

## 前端新手入门
 依赖：需要先安装浏览器插件钱包，推荐Metamask
 1. 在项目导入所需js sdk
 ```
 const web3 = require("../test/web3.js")
 const sdk = require("../dist/metaversejssdk.js")
 ```
 2. 链接钱包
 ```
 window.metaversejssdk.chainWeb3.connect("m");
 ```

## 后端新手入门
 依赖：node
 1. 在项目导入所需源码
 ```
import ChainApi from '../backend/ChainApi.js';
var chainApi = new ChainApi(97);
 ```
 2. 运行 
 ```
 node --experimental-json-modules ./test/backend.js
 ```

## 项目目录文件说明
```
/backend/
        /ChainApi.js, 业务模块(module)功能入口
        /Web3Provider.js web3封装相关功能接口
/dist/metaversejssdk.js, 编译成功后sdk文件
/src/
    /abi/ , 项目合约abi
    /config/, 相关项目模块的配置文件
    /module/
           /ERC20Token.js, ERC20 代币相关接口
           /NFTFactory.js
    /ChainApi.js, 业务模块(module)功能入口
    /ChainWeb3.js, web3浏览器钱包封装相关功能接口
    /Web3Util.js, web3工具方法
    /WalletManage.js, 钱包工具
    /sss3.js, SSS 2/3 密钥工具
/test/
     /web3.js, web3 sdk文件
     /test/backend.js 后台测试文件


```

## Secret Sharing Scheme 简称：SSS

密钥共享模式 (Secret Sharing Scheme 简称：SSS) 通过将密钥分成多个部分并以冗余方式分开保管，发起交易则先将几个部分密钥组装出完整密钥后进行签名，这个方案也可以防止密钥被盗，
一个密钥分成N份，只要凑够k个（k<=N）就可以重建一个完整的密钥。k就是这个临界点个数，如2/3，N=3,k=2。
这样我们可以1份放到服务器，1份保持在设备客户端，1份给用户备份。
拆分和组装都是客户端负责，服务器端只负责存取用户的1份分片密码。

服务器只需要提供如下接口：

```js
/**
 * 存储密码分片
 * `account`, 钱包地址
 * `shareKey`, 其中一份分片密码
 */
sss/save(account, shareKey)

/**
 * 获取密码分片
 * `account`, 钱包地址
 */
sss/get(account)
```

## ChainWeb3.js
 钱包相关功能
```js
 /**
  * 链接钱包，所有与区块链相关操作都需要确保先钱包链接成功
  * @param to, 插件名称， 支持m(Metamask),b(Binance),c(Clover),w(WalletConnect),o(Onto)
  */
 connect(to = '')

 getSelectedAddress() // 用户钱包地址，只有链接成功才有值，默认''
 getNetworkVersion() // 区块链id，只有链接成功才有值，默认0
 isConnected() // 是否链接成功

 /**
  * 添加代币到钱包资产列表，注意，并不是所有钱包都支持，Metamask系列支持
  * @param address, 代币地址
  * @param symbol, 代币符号
  * @param decimals, 代币精度
  */
 addToken(address, symbol, decimals)
```

## 业务模块接口说明

### ERC20Token

ERC20 代币相关接口

```js
//// 读方法
    /**
     * @dev 查询用户余额
     * @param user, 用户钱包地址
     * @return 数量，去精度数据
    */
    async balanceOf(user)

    /**
     * @dev 返回token基本信息，
     * @return {
        symbol: '',
        totalSupply: 0, //带精度数据
        decimals: 18
     }
    */
    async info()

    /**
     * @dev 查询用户授权给花销者可用额度
     * @param spender, 花销者地址
     * @return 数量，去精度数据
    */
    async allowance(spender)


//// 写方法
    /**
    * 用户授权给其他用户可以支配用户的资金
    * @param spender, 花销者地址
    */
    async approve(spender)

    /**
    * 用户转账给其他用户资金
    * @param to, 接收者地址
    * @param amount, 数量，去精度数据
    */
    async transfer(to, amount)
```

### ERC721Token

ERC721 代币相关接口

```js
//// 读方法
    /**
     * @dev 获取合约 token 总量
    */
    async totalSupply()

    /**
     * @dev 通过下标获取 tokenId
     * @notice 下标范围可通过 {totalSupply} 方法获取，从0开始
     * @param index number token 数组下标
    */
    async tokenByIndex(index)

    /**
     * @dev 获取用户拥有的 token 总量
     * @param owner string 账户地址
     */
    async balanceOf(owner)

    /**
     * @dev 通过下标获取用户 tokenId
     * @notice 下标范围可通过 {balanceOf} 方法获取，从0开始
     * @param owner string 账户地址
     * @param index number 账户拥有 token 数组下标
    */
    async tokenOfOwnerByIndex(owner, index)

    /**
     * @dev 查询 tokenURI(元数据)
     * @param tokenId number token ID
    */
    async tokenURI(tokenId)

    /**
     * @dev 查询 tokenId 所有者的账户地址
     * @param tokenId number token ID
    */
    async ownerOf(tokenId)

    /**
     * @dev 查询 token 所有者是否将自己所有的 token 的转移权限批准给操作人
     * @param owner string token 所有者的账户地址
     * @param operator string 操作人账户地址
    */
    async isApprovedForAll(owner, operator)

    /**
     * @dev 查询 token 被批准人的账户地址
     * @param tokenId number token ID
    */
    async getApproved(tokenId)


//// 写方法
    /**
     * @dev 将指定 token 批准给目标账户
     * @notice 要求 token 所有者调用
     * @param to string 被批准人账户地址
     * @param tokenId number 指定的 token ID
    */
    async approve(to, tokenId)

    /**
     * @dev 调用者拥有的 token 对目标账户的批准状态
     * @notice 要求调用者账户地址与目标账户不能相同
     * @param operator string 操作人账户地址
     * @param approved bool 批准状态 [true: 已批准, false: 未批准]
    */
    async setApprovalForAll(operator, approved)

    /**
     * @dev 将指定 token 从所有者账户转移至目标账户
     * @notice 如果调用者不是 token 所有人，要求该 token 已经被批准给调用者账户地址
     * @param from string token 所有者账户地址
     * @param to string token 接受者账户地址
     * @param tokenId number token id
    */
    async transferFrom(from, to, tokenId)
}
```

### ERC1155Token

ERC1155 代币相关接口

```js
//// 读方法
    /**
     * @dev 根据 token id, 查询用户 token 的数量
     * @param account string 账户地址
     * @param id number ERC1155 token 唯一标识符
    */
    async balanceOf(account, id)

    /**
     * @dev 批量查询用户 token 的数量
     * @notice 要求 accounts ids 数组长度一致
     * @param accounts [string] 账户地址数组
     * @param ids [number] ERC1155 token 唯一标识符
    */
    async balanceOfBatch(accounts, ids)

    /**
     * @dev 查询操作者地址是否拥有指定账户所有 token 的转移权限
     * @param account string token 拥有者账户地址
     * @param operator string 操作者账户地址
    */
    async isApprovedForAll(account, operator)


//// 写方法
    /**
     * @dev 设置调用者所拥有的 token 的转移权限
     * @param operator string 操作者账户地址
     * @param approved bool  批准状态 [true: 批准, false: 未批准]
    */
    async setApprovalForAll(operator, approved)

    /**
     * @dev 从转出账户地址转移指定数量的 token 至接收账户地址
     * @notice 要求调用者拥有转出账户的批准，或者调用者为转出账户
     * @param from string 转出账户地址
     * @param to string 接受账户地址
     * @param id number token id
     * @param amount number 转移数量
    */
    async safeTransferFrom(from, to, id, amount)

    /**
     * @dev 批量从转出账户地址转移不同数量的不同 token 至接收账户地址
     * @notice 要求调用者拥有转出账户的批准，或者调用者为转出账户
     * @param from string 转出账户地址
     * @param to string 接受账户地址
     * @param ids [number] token id 数组
     * @param amounts [number] 转移数量数组
    */
    async safeBatchTransferFrom(from, to, ids, amounts)
```

### AssetERC721

ERC721 类型资产合约接口，继承 ERC721Token 接口

```js
//// 读方法
    /**
     * @dev 获取藏品信息
     * @return {symbol 符号, name 名称, licenseName a16z证书名称, licenseURI a16z证书链接}
    */
    async info()

    /**
     * @dev 查询账户 tokenIds
     * @param owner string 账户地址
     * @param cursor number 起始游标
     * @param size number 获取数量
     * @return {'0': tokenIds 数组, '1', 数组长度}
    */
    async tokensOfOwnerBySize(owner, cursor, size)

//// 写方法
    /**
     * @dev 增发一个 token
     * @notice 根据藏品的创建 mode，进行接口调用权限管理.
     * @param to string 接受者账户地址，用于接受增发的 token
     * @param tokenURI string token 元数据, 不传默认为空字符串
    */
    async mint(to, tokenURI)

    /**
     * @dev 批量增发 token
     * @notice 根据藏品的创建 mode，进行接口调用权限管理.
     * @param to string 接受者账户地址，用于接受增发的 token
     * @param amount number 增发数量
     * @param tokenURIs [string] token 元数据数组, 不传默认为空字符串数组
    */
     async batchMint(to, amount, tokenURIs)

    /**
     * @dev 配置基础 URI，如果存在则作为每个 tokenURI 的前缀
     * @notice 根据藏品的创建 mode，进行接口调用权限管理，且只能烧毁本人 token。
     * @param tokenId number 指定的 token ID，要求不可重复
    */
    async burn(tokenId)
```

### AssetERC1155

ERC1155 类型资产合约接口，继承 ERC1155Token 接口

```js
//// 读方法
    /**
     * @dev 获取藏品信息
     * @return {symbol 符号, name 名称, licenseName a16z证书名称, licenseURI a16z证书链接}
    */
     async info()

    /**
     * @dev 查询 tokenURI(元数据)
     * @param id number token ID
    */
    async tokenURI(id)

//// 写方法
    /**
     * @dev 向指定账户中增发指定类型的 token
     * @param account string 接受者账户地址
     * @param amount number 增发数量
     * @param tokenURI string token 元数据, 不传默认为空字符串
    */
    async mint(account, amount, tokenURI)

    /**
     * @dev 增发 token 的数量
     * @param account string 接受者账户地址
     * @param id number 增发数量
     * @param amount number 增发数量
    */
    async mintAmount(account, id, amount)

    /**
     * @dev 批量向指定账户中增发指定范围类型的 token
     * @param to string 接受者账户地址
     * @param tokenIdAmount number token id 的数量
     * @param amounts [number] 每个 token id 增发的数量数组
     * @param tokenURIs [string] 每个 token id 元数据, 不传默认为空字符串
    */
    async batchMint(to, tokenIdAmount, amounts, tokenURIs)

    /**
     * @dev 销毁token
     * @notice 要求调用者拥有被销毁账户的批准，或者调用者为被销毁账户
     * @param account string 被销毁账户地址
     * @param id number token 类型 id
     * @param amount number 销毁数量
    */
    async burn(account, id, amount)
```


### NFTEnglishAuction

NFT 英式拍卖合约，用于挂售 ERC721 或 ERC1155 类型 NFT

```js
//// 读方法
    /**
     * @dev 查询总挂单数量
    */
    async getPoolCount()

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
     *      onlyBotHolder: 否要求 BotToken 持有者才可以出价,
     *      reserveAmount1: 查询挂单最低成交价
     * }
    */
    async getPoolBaseInfo(index)

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
    async getPoolDynamicInfo(index)

    /**
     * @dev 查询挂单创建人是否已领取挂单
     * @param index number 挂单游标
    */
    async creatorClaimedPool(index)

    /**
     * @dev 查询挂单当前最高价竞拍者地址
     * @param index number 挂单游标
    */
    async currentBidderPool(index)

    /**
     * @dev 查询挂单当前竞拍最高价
     * @param index number 挂单游标
    */
    async currentBidderAmount1Pool(index)

    /**
     * @dev 查询用户某个挂单出价
     * @param user string 账户地址
     * @param index number 挂单游标
    */
    async myBidderAmount1Pool(user, index)

    /**
     * @dev 查询挂单竞价数量
     * @param index number 挂单游标
    */
    async bidCountPool(index)

    /**
     * @dev 查询挂单下一次竞价出价数量，即当前最高竞价数量加上加价间隔
     * @param index number 挂单游标
    */
    async currentBidderAmount(index)

    /**
     * @dev 查询目标用户是否为挂单创建人
     * @param target string 目标用户地址
     * @param index number 挂单游标
    */
    async isCreator(target, index)

    /**
     * @dev 查询合约配置信息
     * @return 
     * {
     *      minValue: BotToken 最少持有数量
     *      botToken: BotToken 合约地址， bsc 测试网为测试 USDT 地址
     *      disableErc721: 是否禁止挂 ERC721 类型的 NFT [true: 禁止, false:未禁止] 默认 false
     *      disableErc1155: 是否禁止挂 ERC1155 类型的 NFT [true: 禁止, false:未禁止] 默认 false
     * }
    */
    async getConfig()


//// 写方法
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
     * @param onlyBot bool 是否开启限购
    */
    async createErc721(
        name,
        token0,
        token1,
        tokenId,
        amountMax1,
        amountMin1,
        amountMinIncr1,
        amountReserve1,
        openAt,
        duration,
        onlyBot
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
     * @param onlyBot bool 是否开启限购
    */
    async createErc1155(
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
        duration,
        onlyBot
    )

    /**
     * @dev 对挂单出价
     * @notice 如果挂单换入 token 的合约地址不等于0地址, 出价前要求换入 token 已批准给挂单合约
     * @notice 如果出价低于当前最高价或者加价低于最低加价数量，则失败
     * @notice 如果出价大于等于挂单最高价，直接结单，自动执行 {creatorClaim} {bidderClaim}
     * @param index number 挂单游标
     * @param amount1 出价数量
    */
    async bid(index, amount1)

    /**
     * @dev 取消挂单
     * @notice 目前只支持挂单开售前取消
     * @param index number 挂单游标
    */
    async cancel(index)

    /**
     * @dev 领取挂单，竞拍成功双方交换资产至各自账户，流拍双方资产原路退还
     * @notice 要求挂单在时间上已结束
     * @param index number 挂单游标
    */
    async claim(index)
```

### NFTFixedswap

NFT 定价售卖合约，用于出售 ERC721 或 ERC1155 类型 NFT

```js
//// 读方法
    /**
     * @dev 查询总挂单数量
    */
    async getPoolCount()

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
    async getPool(index)

    /**
     * @dev 查询挂单状态
     * @param index number 挂单游标
     * @return 
     * {
     *      isCanceled: 是否已取消挂单 [true: 是, false: 否]
     *      isSwaped: 是否已结单 [true: 是, false: 否]
     * }
    */
    async getPoolStatus(index)

    /**
     * @dev 查询目标用户是否为挂单创建人
     * @param target string 目标用户地址
     * @param index number 挂单游标
    */
    async isCreator(target, index)

    /**
     * @dev 查询 token 是否可售
     * @param token string token 合约地址
     * @return bool [true: 可售, false: 不可售]
    */
    async checkToken0(token)

    /**
     * @dev 查询合约配置信息
     * @return 
     * {
     *      minValue: BotToken 最少持有数量
     *      botToken: BotToken 合约地址， bsc 测试网为测试 USDT 地址
     *      disableErc721: 是否禁止挂 ERC721 类型的 NFT [true: 禁止, false:未禁止] 默认 false
     *      disableErc1155: 是否禁止挂 ERC1155 类型的 NFT [true: 禁止, false:未禁止] 默认 false
     * }
    */
    async getConfig()


//// 写方法
    /**
     * @dev 创建 ERC721 类型挂单
     * @notice 创建挂单之前，需要将出售的 token 批准给挂单合约，否则挂单失败
     * @param name string 名称
     * @param token0 string 换出 token 的合约地址（NFT 合约地址）
     * @param token1 string 换入 token 的合约地址（token 合约地址）
     * @param tokenId number 换出 token 的 tokenId
     * @param amountTotal1 number 换入 token 总量
     * @param openAt number 挂单开售时间，unix timestamp
     * @param onlyBot bool 是否开启限购
    */
    async createErc721(
        name,
        token0,
        token1,
        tokenId,
        amountTotal1,
        openAt,
        onlyBot
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
     * @param onlyBot bool 是否开启限购
    */
    async createErc1155(
        name,
        token0,
        token1,
        tokenId,
        amountTotal0,
        amountTotal1,
        openAt,
        onlyBot
    )

    /**
     * @dev 购买挂单
     * @notice 如果挂单换入 token 的合约地址不等于0地址, 出价前要求换入 token 已批准给挂单合约
     * @notice 可部分购买，换取等比例数量的换出 token
     * @notice 购买数量 + 已售出量 >= 换出总量 则结单
     * @param index number 挂单游标
     * @param amount0 购买的换出 token 的数量
    */
    async swap(index, amount0)

    /**
     * @dev 取消挂单
     * @notice 要求挂单未结单
     * @param index number 挂单游标
    */
    async cancel(index)
```
