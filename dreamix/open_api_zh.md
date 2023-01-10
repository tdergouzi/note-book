# Dreamix OpenAPI

## ERC20Token

### info

desc: get token infomation - name symbol decimals total

url: {apiAddress}/ERC20Token/info

method: Get

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name    | required | type   | des                    |
| ------- | -------- | ------ | ---------------------- |
| chainId | true     | number | chain id               |
| token   | true     | string | token contract address |

```json
{
    "chainId": 97,
    "token": "0x06bF890dfF5b422c35c9683f47d2d7663f6E1c24"
}
```

response
```json
{
    "status": true,
    "message": "Success",
    "data": {
        "info": {
            "address": "0x06bF890dfF5b422c35c9683f47d2d7663f6E1c24",
            "symbol": "BURGER",
            "totalSupply": "276028627806820425137234446",
            "decimals": "18"
        }
    }
}
```
- - -

### balanceOf

desc: get user token amount

url: {apiAddress}/ERC20Token/balanceOf

method: Get

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name    | required | type   | des                    |
| ------- | -------- | ------ | ---------------------- |
| chainId | true     | number | chain id               |
| token   | true     | string | token contract address |
| user    | true     | string | user address           |

```json
{
    "chainId": 97,
    "token": "0x06bF890dfF5b422c35c9683f47d2d7663f6E1c24",
    "user": "0x07fF0ed51ABAf0ebeF2dDdabB463A0E17235de46"
}
```

response
```json
{
    "status": true,
    "message": "Success",
    "data": {
        "balance": "4000.547047073682962673"
    }
}
```
- - -

### totalSupply

desc: get amount of all token

url: {apiAddress}/ERC20Token/totalSupply

method: Get

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name    | required | type   | des                    |
| ------- | -------- | ------ | ---------------------- |
| chainId | true     | number | chain id               |
| token   | true     | string | token contract address |

```json
{
    "chainId": 97,
    "token": "0x06bF890dfF5b422c35c9683f47d2d7663f6E1c24"
}
```

response
```json
{
    "status": true,
    "data": {
        "totalSupply": "276028627.806820425137234446"
    }
}
```
- - -

### allowance

desc: get amount of approved to spender

url: {apiAddress}/ERC20Token/allowance

method: Get

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name    | required | type   | des                     |
| ------- | -------- | ------ | ----------------------- |
| chainId | true     | number | chain id                |
| token   | true     | string | token contract address  |
| user    | true     | string | user account address    |
| spender | true     | string | spender account address |

```json
{
    "chainId": 97,
    "token": "0x06bF890dfF5b422c35c9683f47d2d7663f6E1c24",
    "user": "0x07fF0ed51ABAf0ebeF2dDdabB463A0E17235de46",
    "spender": "0x07fF0ed51ABAf0ebeF2dDdabB463A0E17235de46"
}
```

response
```json
{
    "status": true,
    "message": "Success",
    "data": {
        "allowance": "0"
    }
}
```
- - -


## ERC721Token

#### info

desc: get token infomation - name symbol

url: {apiAddress}/ERC721Token/info

method: Get

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name    | required | type   | des                    |
| ------- | -------- | ------ | ---------------------- |
| chainId | true     | number | chain id               |
| token   | true     | string | token contract address |

```json
{
    "chainId": 97,
    "token": "0x5aA9626653D0d481AE8555ddC7fa39AeFEC4308D"
}
```

response
```json
{
    "status": true,
    "message": "Success",
    "data": {
        "info": {
            "symbol": "HNFT",
            "name": "Hero NFT",
            "mode": "0" // NFT 管理权限模式
        }
    }
}
```
- - -

#### balanceOf

desc: get user token amount

url: {apiAddress}/ERC721Token/balanceOf

method: Get

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name    | required | type   | des                    |
| ------- | -------- | ------ | ---------------------- |
| chainId | true     | number | chain id               |
| token   | true     | string | token contract address |
| user    | true     | string | user account address   |

```json
{
    "chainId": 97,
    "token": "0x5aA9626653D0d481AE8555ddC7fa39AeFEC4308D",
    "user": "0xde51312CdF679e042B41dC8dd5F00984d0f5bbE2"
}
```

response
```json
{
    "status": true,
    "message": "Success",
    "data": {
        "balance": "3"
    }
}
```
- - -

#### totalSupply

desc: get amount of all token

url: {apiAddress}/ERC721Token/totalSupply

method: Get

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name    | required | type   | des                    |
| ------- | -------- | ------ | ---------------------- |
| chainId | true     | number | chain id               |
| token   | true     | string | token contract address |

```json
{
    "chainId": 97,
    "token": "0x5aA9626653D0d481AE8555ddC7fa39AeFEC4308D"
}
```

response
```json
{
    "status": true,
    "message": "Success",
    "data": {
        "totalSupply": "5"
    }
}
```
- - -

#### tokenOfOwnerByIndex

desc: get tokenId by the index of user's token array

url: {apiAddress}/ERC721Token/tokenOfOwnerByIndex

method: Get

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name    | required | type   | des                    |
| ------- | -------- | ------ | ---------------------- |
| chainId | true     | number | chain id               |
| token   | true     | string | token contract address |
| user    | true     | string | user account address   |
| index   | true     | number | token index            |

```json
{
    "chainId": 97,
    "token": "0x5aA9626653D0d481AE8555ddC7fa39AeFEC4308D",
    "user": "0xde51312CdF679e042B41dC8dd5F00984d0f5bbE2",
    "index": 2
}
```

response
```json
{
    "status": true,
    "message": "Success",
    "data": {
        "tokenId": "3"
    }
}
```
- - -

#### tokensOfOwnerBySize

desc: batch get user's tokenIds

url: {apiAddress}/ERC721Token/tokensOfOwnerBySize

method: Get

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name    | required | type   | des                    |
| ------- | -------- | ------ | ---------------------- |
| chainId | true     | number | chain id               |
| token   | true     | string | token contract address |
| user    | true     | string | user account address   |
| cursor  | false    | number | default 0              |
| size    | true     | number | -                      |

```json
{
    "chainId": 97,
    "token": "0x5aA9626653D0d481AE8555ddC7fa39AeFEC4308D",
    "user": "0xde51312CdF679e042B41dC8dd5F00984d0f5bbE2",
    "size": 5
}
```

response
```json
{
    "status": true,
    "message": "Success",
    "data": {
        "tokenIds": [
            "5",
            "4",
            "3"
        ],
        "count": "3"
    }
}
```
- - -

#### tokenURI

desc: get token uri (metadata)

url: {apiAddress}/ERC721Token/tokenURI

method: Get

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name    | required | type   | des                    |
| ------- | -------- | ------ | ---------------------- |
| chainId | true     | number | chain id               |
| token   | true     | string | token contract address |
| tokenId | true     | number | -                      |

```json
{
    "status": true,
    "message": "Success",
    "data": {
        "tokenURI": "test/baseURI/3"
    }
}
```

response
```json
{
    "tokenURI": "test/baseURI/3"
}
```
- - -

#### ownerOf

desc: get the owner address of token

url: {apiAddress}/ERC721Token/ownerOf

method: Get

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name    | required | type   | des                    |
| ------- | -------- | ------ | ---------------------- |
| chainId | true     | number | chain id               |
| token   | true     | string | token contract address |
| tokenId | true     | number | -                      |

```json
{
    "chainId": 97,
    "token": "0x5aA9626653D0d481AE8555ddC7fa39AeFEC4308D",
    "tokenId": "3"
}
```

response
```json
{
    "status": true,
    "message": "Success",
    "data": {
        "owner": "0xde51312CdF679e042B41dC8dd5F00984d0f5bbE2"
    }
}
```
- - -

#### isApprovedForAll

desc: check if the user approved all of tokens to spender

url: {apiAddress}/ERC721Token/isApprovedForAll

method: Get

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name    | required | type   | des                     |
| ------- | -------- | ------ | ----------------------- |
| chainId | true     | number | chain id                |
| token   | true     | string | token contract address  |
| user    | true     | string | user account address    |
| spender | true     | string | spender account address |


```json
{
    "chainId": 97,
    "token": "0x5aA9626653D0d481AE8555ddC7fa39AeFEC4308D",
    "user": "0xde51312CdF679e042B41dC8dd5F00984d0f5bbE2",
    "spender": "0xde51312CdF679e042B41dC8dd5F00984d0f5bbE2"
}
```

response
```json
{
    "status": true,
    "message": "Success",
    "data": {
        "result": false
    }
}
```
- - -

#### getApproved

desc: get the spender address of owner, if not exist, return zero address (0x0000...)

url: {apiAddress}/ERC721Token/getApproved

method: Get

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name    | required | type   | des                    |
| ------- | -------- | ------ | ---------------------- |
| chainId | true     | number | chain id               |
| token   | true     | string | token contract address |
| tokenId | true     | number | -                      |

```json
{
    "chainId": 97,
    "token": "0x5aA9626653D0d481AE8555ddC7fa39AeFEC4308D",
    "tokenId": 3
}
```

response
```json
{
    "status": true,
    "message": "Success",
    "data": {
        "spender": "0x0000000000000000000000000000000000000000"
    }
}
```
- - -


## ERC1155

#### uri

desc: get ERC1155 base uri

uri: {apiAddress}/ERC1155Token/uri

method: Get

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name    | required | type   | des                    |
| ------- | -------- | ------ | ---------------------- |
| chainId | true     | number | chain id               |
| token   | true     | string | token contract address |

```json
{
    "chainId": 97,
    "token": "0xe8F670334486692d843b50e76AeAf7294cE8A9C2"
}
```

respnse
```json
{
    "status": true,
    "message": "Success",
    "data": {
        "uri": "test/baseURI/"
    }
}
```
- - -

#### balanceOf

desc: get amount of token in tokenId

uri: {apiAddress}/ERC1155Token/balanceOf 

method: Get

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name    | required | type   | des                    |
| ------- | -------- | ------ | ---------------------- |
| chainId | true     | number | chain id               |
| token   | true     | string | token contract address |
| user    | true     | string | user account address   |
| tokenId | true     | number | -                      |

```json
{
    "chainId": 97,
    "token": "0xe8F670334486692d843b50e76AeAf7294cE8A9C2",
    "user": "0xde51312CdF679e042B41dC8dd5F00984d0f5bbE2",
    "tokenId": "1"
}
```

respnse
```json
{
    "status": true,
    "message": "Success",
    "data": {
        "balance": "10"
    }
}
```
- - -

#### balanceOfBatch

desc: batch get token amount array of token in tokenIds

uri: {apiAddress}/ERC1155Token/balanceOfBatch 

method: Get

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name     | required | type     | des                        |
| -------- | -------- | -------- | -------------------------- |
| chainId  | true     | number   | chain id                   |
| token    | true     | string   | token contract address     |
| users    | true     | [string] | user account address array |
| tokenIds | true     | [number] | tokenId array              |

```json
{
    "chainId": 97,
    "token": "0xe8F670334486692d843b50e76AeAf7294cE8A9C2",
    "users": [
        "0xde51312CdF679e042B41dC8dd5F00984d0f5bbE2",
        "0xde51312CdF679e042B41dC8dd5F00984d0f5bbE2"
    ],
    "tokenIds": [
        "1",
        "2"
    ]
}
```

respnse
```json
{
    "status": true,
    "message": "Success",
    "data": {
        "balanceArr": [
            "10",
            "10"
        ]
    }
}
```
- - -

#### isApprovedForAll

desc: check if the user approved all token to spender

uri: {apiAddress}/ERC1155Token/isApprovedForAll 

method: Get

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name    | required | type   | des                     |
| ------- | -------- | ------ | ----------------------- |
| chainId | true     | number | chain id                |
| token   | true     | string | token contract address  |
| user    | true     | string | user account address    |
| spender | true     | string | spender account address |

```json
{
    "chainId": 97,
    "token": "0xe8F670334486692d843b50e76AeAf7294cE8A9C2",
    "user": "0xde51312CdF679e042B41dC8dd5F00984d0f5bbE2",
    "spender": "0xde51312CdF679e042B41dC8dd5F00984d0f5bbE2"
}
```

respnse
```json
{
    "status": true,
    "message": "Success",
    "data": {
        "result": false
    }
}
```
- - -


## NFTEnglishAuction

#### getPoolCount

desc: get count of all pool in EnglishAuction contract

uri: {apiAddress}/NFTEnglishAuction/getPoolCount 

method: Get

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name    | required | type   | des      |
| ------- | -------- | ------ | -------- |
| chainId | true     | number | chain id |

```json
{
    "chainId": 97
}
```

respnse
```json
{
    "status": true,
    "message": "Success",
    "data": {
        "poolCount": "2"
    }
}
```
- - -

#### getPoolBaseInfo

desc: get pool base info, includes creator amount 

uri: {apiAddress}/NFTEnglishAuction/getPoolBaseInfo 

method: Get

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name    | required | type   | des                      |
| ------- | -------- | ------ | ------------------------ |
| chainId | true     | number | chain id                 |
| index   | true     | number | range [0, poolLength -1] |

```json
{
    "chainId": 97,
    "index": 0
}
```

respnse
```json
{
    "status": true,
    "message": "Success",
    "data": {
        "baseInfo": {
            "creator": "0xde51312CdF679e042B41dC8dd5F00984d0f5bbE2", // 挂单人地址
            "name": "TestPool1", // 挂单名称
            "token0": "0x5aA9626653D0d481AE8555ddC7fa39AeFEC4308D", // 换出 token 合约地址
            "token1": "0x337610d27c682E347C9cD60BD4b3b107C9d34dDd", // 换入 token 合约地址
            "tokenId": "1", // 换出 tokenId
            "tokenAmount0": "1", // 换出 token 数量
            "amountMax1": "10000000000000000000", // 换入 token 最大数量
            "amountMin1": "1000000000000000000", // 换入 token 最小数量
            "amountMinIncr1": "1000000000000000000", // 竞拍加价数量
            "openAt": "1645611075", // 订单开售时间
            "closeAt": "1645697475", // 订单结束时间
            "nftType": "0", // 换出 token 类型 [0: ERC721, 1: ERC1155]
            "onlyBotHolder": false, // 是否持币限购
            "reserveAmount1": "2000000000000000000" // 订单成交最低价
        }
    }
}
```
- - -

#### getPoolDynamicInfo

desc: get pool trade info

uri: {apiAddress}/NFTEnglishAuction/getPoolDynamicInfo 

method: Get

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name    | required | type   | des                      |
| ------- | -------- | ------ | ------------------------ |
| chainId | true     | number | chain id                 |
| index   | true     | number | range [0, poolLength -1] |

```json
{
    "chainId": 97,
    "index": 0
}
```

respnse
```json
{
    "status": true,
    "message": "Success",
    "data": {
        "dynamicInfo": {
            "bidCount": "0", // 当前挂单竞价数量
            "currentBidder": "0x0000000000000000000000000000000000000000", // 当前最高出价人地址
            "currentBidderAmount1": "0", // 当前最高出价
            "currentBidderAmount": "1000000000000000000", // 下一次出价
            "claimed": false, // 订单是否已被领取，true：表示双方已领取
        }
    }
}
```
- - -

#### isCreator

desc: check if the user is the pool's creator

uri: {apiAddress}/NFTEnglishAuction/isCreator 

method: Get

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name    | required | type   | des                      |
| ------- | -------- | ------ | ------------------------ |
| chainId | true     | number | chain id                 |
| user    | true     | string | user account address     |
| index   | true     | number | range [0, poolLength -1] |

```json
{
    "chainId": 97,
    "index": 0
}
```

respnse
```json
{
    "status": true,
    "message": "Success",
    "data": {
        "result": true
    }
}
```
- - -

#### myBidderAmount1Pool

desc: get user bid amount

uri: {apiAddress}/NFTEnglishAuction/myBidderAmount1Pool 

method: Get

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name    | required | type   | des                      |
| ------- | -------- | ------ | ------------------------ |
| chainId | true     | number | chain id                 |
| user    | true     | string | user account address     |
| index   | true     | number | range [0, poolLength -1] |

```json
{
    "chainId": 97,
    "index": 0
}
```

respnse
```json
{
    "status": true,
    "message": "Success",
    "data": {
        "amount": "0"
    }
}
```
- - -

#### getConfig

desc: get EnglishAuction contract config

uri: {apiAddress}/NFTEnglishAuction/getConfig 

method: Get

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name    | required | type   | des      |
| ------- | -------- | ------ | -------- |
| chainId | true     | number | chain id |

```json
{
    "chainId": 97
}
```

respnse
```json
{
    "status": true,
    "message": "Success",
    "data": {
        "config": {
            "minValue": "1000000000000000000", // 限购最小数量
            "botToken": "0x07fF0ed51ABAf0ebeF2dDdabB463A0E17235de46", // 限购持有 token 合约地址
            "disableErc721": false, // 是否禁售 ERC721 类型 token
            "disableErc1155": false // 是否禁售 ERC1155 类型 token
        }
    }
}
```
- - -


## NFTFixedswap

#### getPoolCount

desc: get count of all pool in Fixedswap contract

uri: {apiAddress}/NFTFixedswap/getPoolCount 

method: Get

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name    | required | type   | des      |
| ------- | -------- | ------ | -------- |
| chainId | true     | number | chain id |

```json
{
    "chainId": 97
}
```

respnse
```json
{
    "status": true,
    "message": "Success",
    "data": {
        "poolCount": "0"
    }
}
```
- - - 

#### getPool

desc: get pool base info

uri: {apiAddress}/NFTFixedswap/getPool 

method: Get

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name    | required | type   | des                      |
| ------- | -------- | ------ | ------------------------ |
| chainId | true     | number | chain id                 |
| index   | true     | number | range [0, poolLength -1] |

```json
{
    "chainId": 97,
    "index": 0
}
```

respnse
```json
// TODO
```
- - - 

#### getPoolStatus

desc: get pool trade info

uri: {apiAddress}/NFTFixedswap/getPoolStatus 

method: Get

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name    | required | type   | des                      |
| ------- | -------- | ------ | ------------------------ |
| chainId | true     | number | chain id                 |
| index   | true     | number | range [0, poolLength -1] |

```json
{
    "chainId": 97,
    "index": 0
}
```

respnse
```json
// TODO
```
- - - 

#### isCreator

desc: get pool trade info

uri: {apiAddress}/NFTFixedswap/isCreator 

method: Get

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name    | required | type   | des                      |
| ------- | -------- | ------ | ------------------------ |
| chainId | true     | number | chain id                 |
| user    | true     | string | user account address     |
| index   | true     | number | range [0, poolLength -1] |

```json
{
    "chainId": 97,
    "user": "0xde51312CdF679e042B41dC8dd5F00984d0f5bbE2",
    "index": 0
}
```

respnse
```json
{
    "status": true,
    "message": "Success",
    "data": { 
        "result": true
    }
}
```
- - -

#### checkToken0

desc: check if the token can be sold

uri: {apiAddress}/NFTFixedswap/checkToken0 

method: Get

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name    | required | type   | des                |
| ------- | -------- | ------ | ------------------ |
| chainId | true     | number | chain id           |
| token   | true     | string | sell token address |

```json
{
    "chainId": 97,
    "token": "0xfF93668AA923189C6F9D66eDdf6db75b20110fFF"
}
```

respnse
```json
{
    "status": true,
    "message": "Success",
    "data": {
        "result": true
    }
}
```
- - -

#### getConfig

desc: get Fixedswap contract config

uri: {apiAddress}/NFTFixedswap/getConfig 

method: Get

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name    | required | type   | des      |
| ------- | -------- | ------ | -------- |
| chainId | true     | number | chain id |


```json
{
    "chainId": 97
}
```

respnse
```json
{
    "status": true,
    "message": "Success",
    "data": {
        "config": {
            "minValue": "1000000000000000000",
            "botToken": "0x07fF0ed51ABAf0ebeF2dDdabB463A0E17235de46",
            "disableErc721": false,
            "disableErc1155": false
        }
    }
}
```
- - -


## Ipfs

ipfs https://ipfsr.dreamix.com/ipfs/{hash}

#### update-data

desc: upload source data to ipfs

url: {apiAddress}/Ipfs/upload-data

method: Post

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name | required | type  | des         |
| ---- | -------- | ----- | ----------- |
| data | true     | array | source data |

```json
{
    "data": [
        {
            "name": "Azuki #9572",
            "image": "https://ikzttp.mypinata.cloud/ipfs/QmYDvPAXtiJg7s8JdRBSLWdgSphQdac8j1YuQNNxcGE1hg/9572.png",
            "attributes": [
                {
                    "trait_type": "Type",
                    "value": "Human"
                },
                {
                    "trait_type": "Hair",
                    "value": "Brown Half Bun"
                },
                {
                    "trait_type": "Clothing",
                    "value": "Dress Shirt"
                },
                {
                    "trait_type": "Eyes",
                    "value": "Ruby"
                },
                {
                    "trait_type": "Mouth",
                    "value": "Smoking"
                },
                {
                    "trait_type": "Offhand",
                    "value": "Floorsweeper"
                },
                {
                    "trait_type": "Background",
                    "value": "Red"
                }
            ]
        },
        {
            "name": "Azuki #9573",
            "image": "https://ikzttp.mypinata.cloud/ipfs/QmYDvPAXtiJg7s8JdRBSLWdgSphQdac8j1YuQNNxcGE1hg/9573.png",
            "attributes": [
                {
                    "trait_type": "Type",
                    "value": "Human"
                },
                {
                    "trait_type": "Hair",
                    "value": "Magenta Messy"
                },
                {
                    "trait_type": "Headgear",
                    "value": "Backwards Cap"
                },
                {
                    "trait_type": "Face",
                    "value": "Eye Patch"
                },
                {
                    "trait_type": "Clothing",
                    "value": "Vest"
                },
                {
                    "trait_type": "Eyes",
                    "value": "Closed"
                },
                {
                    "trait_type": "Mouth",
                    "value": "Smirk"
                },
                {
                    "trait_type": "Offhand",
                    "value": "Blue Bean"
                },
                {
                    "trait_type": "Background",
                    "value": "Off White D"
                }
            ]
        }
    ]
}
```

response
```json
{
    "status": true,
    "message": "Success",
    "data": [
        {
            "path": "QmNeHYXzPsfWjSDfJci6XtPmtC5gYa43qCZWTKYxZ4RrPp",
            "cid": "https://ipfsr.burgerswap.org/ipfs/QmNeHYXzPsfWjSDfJci6XtPmtC5gYa43qCZWTKYxZ4RrPp",
            "size": 648
        },
        {
            "path": "QmRZqw45MvRnmy31kArBivxnKvSeCGY39ZaX3k6feoAtTr",
            "cid": "https://ipfsr.burgerswap.org/ipfs/QmRZqw45MvRnmy31kArBivxnKvSeCGY39ZaX3k6feoAtTr",
            "size": 789
        }
    ]
}
```
- - -

#### upload-files

desc: upload multi files to ipfs, includes image text files

url: {apiAddress}/Ipfs/upload-files

method: Post

request-header
| name         | required | type                | des               |
| ------------ | -------- | ------------------- | ----------------- |
| Content-Type | true     | multipart/form-data | require args type |

request-body
| name  | required | type   | des          |
| ----- | -------- | ------ | ------------ |
| files | true     | [file] | source files |

response
```json
{
    "status": true,
    "message": "Files are uploaded",
    "data": [
        {
            "name": "1.jpg",
            "mimetype": "image/jpeg",
            "size": 78128,
            "path": "https://ipfsr.burgerswap.org/ipfs/QmQ4zgVJ55MEAoTeXcnMyYMuk1QxZjBLKJpkz4qvDZGfUd"
        },
        {
            "name": "2.jpg",
            "mimetype": "image/jpeg",
            "size": 180691,
            "path": "https://ipfsr.burgerswap.org/ipfs/QmdNhkwgMW7twYLzHmY7sGPESFPRLcHF8aTzmrnotZ8FDP"
        }
    ]
}
```
- - -

## Land

土地相关接口

#### calculateTokenId
desc: calculate token ID according to coordinate

uri: {apiAddress}/Land/calculateTokenId 

method: Get

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name    | required | type   | des            |
| ------- | -------- | ------ | -------------- |
| chainId | true     | number | chain id       |
| x1      | true     | number | A x coordinate |
| y1      | true     | number | A y coordinate |
| x2      | true     | number | B x coordinate |
| y2      | true     | number | B y coordinate |

```json
{
    "chainId": 97,
    "x1": "1",
    "y1": "1",
    "x2": "2",
    "y2": "2"
}
```

respnse
```json
{
    "status": true,
    "message": "Success",
    "data": {
        "tokenId": "562958543421441"
    }
}
```
- - - 

#### tokenCoordinate
desc: get coordinate of token ID

uri: {apiAddress}/Land/tokenCoordinate 

method: Get

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name    | required | type   | des      |
| ------- | -------- | ------ | -------- |
| chainId | true     | number | chain id |
| tokenId | true     | number | token ID |

```json
{
    "chainId": 97,
    "tokenId": "562958543421441"
}
```

respnse
```json
{
    "status": true,
    "message": "Success",
    "data": {
        "coordinate": {
            "0": "1",
            "1": "1",
            "2": "2",
            "3": "2",
            "x1": "1",
            "y1": "1",
            "x2": "2",
            "y2": "2"
        }
    }
}
```
- - - 

#### exist
desc: check existence for token ID

uri: {apiAddress}/Land/exist 

method: Get

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name    | required | type   | des            |
| ------- | -------- | ------ | -------------- |
| chainId | true     | number | chain id       |
| x1      | true     | number | A x coordinate |
| y1      | true     | number | A y coordinate |
| x2      | true     | number | B x coordinate |
| y2      | true     | number | B y coordinate |

```json
{
    "chainId": 97,
    "x1": "1",
    "y1": "1",
    "x2": "2",
    "y2": "2"
}
```

respnse
```json
{
    "status": true,
    "message": "Success",
    "data": {
        "result": false // 未被创建
    }
}
```
- - - 

## LandSell
官方土地售卖相关接口

#### bidInfo
desc: get bid info in land selling

uri: {apiAddress}/LandSell/bidInfo 

method: Get

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name    | required | type   | des            |
| ------- | -------- | ------ | -------------- |
| chainId | true     | number | chain id       |
| x1      | true     | number | A x coordinate |
| y1      | true     | number | A y coordinate |
| x2      | true     | number | B x coordinate |
| y2      | true     | number | B y coordinate |

```json
{
    "chainId": 97,
    "x1": "1",
    "y1": "1",
    "x2": "2",
    "y2": "2"
}
```

respnse
```json
{
    "status": true,
    "message": "Success",
    "data": {
        "info": {
            "0": "0x0000000000000000000000000000000000000000", // 当前竞拍人账户地址
            "1": "0", // 当前竞拍最高出价
            "2": false // 竞拍人是否已领取
        }
    }
}
```
- - - 

#### bidInfoByTokenId
desc: get bid info in land selling

uri: {apiAddress}/LandSell/bidInfoByTokenId 

method: Get

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name    | required | type   | des          |
| ------- | -------- | ------ | ------------ |
| chainId | true     | number | chain id     |
| tokenId | true     | number | NFT token ID |

```json
{
    "chainId": 97,
    "tokenId": "562958543421441"
}
```

respnse
```json
{
    "status": true,
    "message": "Success",
    "data": {
        "info": {
            "0": "0x0000000000000000000000000000000000000000", // 当前竞拍人账户地址
            "1": "0", // 当前竞拍最高出价
            "2": false // 竞拍人是否已领取
        }
    }
}
```
- - - 

#### getSignatureForBid
desc: get bid signature

uri: {apiAddress}/LandSell/getSignatureForBid 

method: Get

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name          | required | type   | des                 |
| ------------- | -------- | ------ | ------------------- |
| chainId       | true     | number | chain id            |
| x1            | true     | number | Land A x coordinate |
| y1            | true     | number | Land A y coordinate |
| x2            | true     | number | Land B x coordinate |
| y2            | true     | number | Land B x coordinate |
| amountMax     | true     | number | max price           |
| amountMin     | true     | number | min price           |
| amountMinIncr | true     | number | amount min increase |
| openAt        | true     | number | bid start timestamp |
| closeAt       | true     | number | bid end timestamp   |

```json
{
    "chainId": 97,
    "x1": "0",
    "y1": "0",
    "x2": "2",
    "y2": "2",
    "amountMax": "5000000000000000000",
    "amountMin": "2000000000000000000",
    "amountMinIncr": "1000000000000000000",
    "openAt": "1650271365",
    "closeAt": "1650357865"
}
```

respnse
```json
{
    "status": true,
    "message": "Success",
    "data": {
        "signature": "0xb4d7a219b653382d74b2c06892503502759f5070cfb114a36d17dd43527169da4ffa63b64eebf143880e143c40ea6f3b15e404db71e2f55a2b8eb521d3195a5b1b"
    }
}
```
- - - 

#### getSignatureForBuy
desc: get fixedswap signature

uri: {apiAddress}/LandSell/getSignatureForBuy 

method: Get

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name    | required | type   | des                 |
| ------- | -------- | ------ | ------------------- |
| chainId | true     | number | chain id            |
| x1      | true     | number | Land A x coordinate |
| y1      | true     | number | Land A y coordinate |
| x2      | true     | number | Land B x coordinate |
| y2      | true     | number | Land B x coordinate |
| amount  | true     | number | price               |
| openAt  | true     | number | bid start timestamp |
| closeAt | true     | number | bid end timestamp   |

```json
{
    "chainId": 97,
    "x1": "0",
    "y1": "0",
    "x2": "2",
    "y2": "2",
    "amount": "5000000000000000000",
    "openAt": "1650271365",
    "closeAt": "1650357865"
}
```

respnse
```json
{
    "status": true,
    "message": "Success",
    "data": {
        "signature": "0x2772534f0fe3007faf954999ad087bc9e898c090d3d59aa37b57d7d7f1802d6e46ec36d5ba3340d8f7be4fafc579e056898787df8a56d3ff80010a3f43aede3d1c"
    }
}
```
- - - 

## Info
链上交互信息接口

#### interact/uniswap
desc: get interaction count with uniswap

uri: {apiAddress}/info/interact/uniswap

method: Get

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name | required | type   | des                 |
| ---- | -------- | ------ | ------------------- |
| user | true     | string | user wallet address |


```json
{
    "user": "0x0000000000000d9054f605ca65a2647c2b521422"
}
```

respnse
```json
{
    "status": true,
    "message": "Success",
    "data": {
        "id": "0x0000000000000d9054f605ca65a2647c2b521422", // user address
        "blockNumber": "12723883", // updated block number
        "timestamp": "1624901720", // updated timestamp
        "interactedTimes": "618" // interaction count
    }
}
```
- - - 

#### interact/opensea
desc: get interaction count with opensea

uri: {apiAddress}/info/interact/opensea

method: Get

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name | required | type   | des                 |
| ---- | -------- | ------ | ------------------- |
| user | true     | string | user wallet address |


```json
{
    "user": "0x0000000000006e543164be036824fcf832e67e47"
}
```

respnse
```json
{
    "status": true,
    "message": "Success",
    "data": {
        "id": "0x0000000000006e543164be036824fcf832e67e47",
        "blockNumber": "15091335",
        "timestamp": "1657142066",
        "interactedTimes": "2"
    }
}
```
- - - 

#### interact/gitcoin
desc: get interaction count with gitcoin

uri: {apiAddress}/info/interact/gitcoin

method: Get

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name | required | type   | des                 |
| ---- | -------- | ------ | ------------------- |
| user | true     | string | user wallet address |


```json
{
    "user": "0x00000000000360176d958e11c140308cd0863679"
}
```

respnse
```json
{
    "status": true,
    "message": "Success",
    "data": {
        "id": "0x00000000000360176d958e11c140308cd0863679",
        "blockNumber": "13193865",
        "timestamp": "1631221207",
        "interactedTimes": "2"
    }
}
```
- - - 

#### interact/ens
desc: get interaction count with ens

uri: {apiAddress}/info/interact/ens

method: Get

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name | required | type   | des                 |
| ---- | -------- | ------ | ------------------- |
| user | true     | string | user wallet address |


```json
{
    "user": "0x00000000000040c8d72ad3a15ce5408f99cd61b4"
}
```

respnse
```json
{
    "status": true,
    "message": "Success",
    "data": {
        "id": "0x00000000000040c8d72ad3a15ce5408f99cd61b4",
        "blockNumber": "15280149",
        "timestamp": "1659673446",
        "interactedTimes": "1"
    }
}
```
- - - 


## Admin

#### login

url: {apiAddress}/admin/login

method: post

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name    | required | type   | des                    |
| ------- | -------- | ------ | ---------------------- |
| chainId | true     | number | chain id               |
| user    | true     | string | user wallet address    |
| msg     | true     | string | message json array     |
| signature    | true     | string | signed data    |

```json
{
    "chainId":97,
    "user": "0x0b8996ca85955f6545bfaa63c931b7328886db69",
    "msg": [{"type": "string", "name": "title", "value": "0x0b8996ca85955f6545bfaa63c931b7328886db69"}],
    "signature": "0xf78f7ffa267e8e759a5073d34b6a9cd802d49cfe11af327da217c2e5b7d4fd31646f6dbbc3d5aedbd66e6ea3e516365b041bbf1d5402146231e3c2be8779cf881b"
}

```

response
```json
{
    "status": true,
    "message": "Success",
    "data":true
}
```
- - -

#### logout

url: {apiAddress}/admin/logout

method: post

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

request-body
| name    | required | type   | des                    |
| ------- | -------- | ------ | ---------------------- |
| user    | true     | string | user wallet address    |

```json
{
    "user": "0x06bF890dfF5b422c35c9683f47d2d7663f6E1c24",
}
```

response
```json
{
    "status": true,
    "message": "Success",
    "data":true
}
```
- - -


#### /resource/typeList

url: {apiAddress}/admin/resource/typeList

method: get

response
```json
{
    "status": true,
    "message": "Success",
    "data": [
        "type1",
        "type2"
    ]
}
```
- - -

#### /resource/get

url: {apiAddress}/admin/resource/get

method: get

request-query
| name    | required | type   | des                    |
| ------- | -------- | ------ | ---------------------- |
| id      | true     | number |  record id    |


response
```json
{
    "status": true,
    "message": "Success",
    "data": {
        "id": 1,
        "chainId": 97,
        "name": "name1",
        "type": "type1",
        "owner": "0x2d4e68caf597d1e980b5e8684164460161f8c29b",
        "creator": "0x2d4e68caf597d1e980b5e8684164460161f8c29b",
        "price": 1.25,
        "logo": "http://burgerswap.org",
        "status": 1,
        "launchTime": 1649216065613,
        "updateTime": "2022-04-06T03:43:33.000Z",
        "isDel": 0
    }
}
```
- - -


#### /resource/query

url: {apiAddress}/admin/resource/query

method: get

request-query
| name    | required | type   | des                    |
| ------- | -------- | ------ | ---------------------- |
| _page  | option   | number |  default is 1    |
| _limit | option   | number |  default is 10   |
| id      | true     | number |  record id    |
...

response
```json
{
    "status": true,
    "message": "Success",
    "data": [
        {
            "id": 2,
            "chainId": 97,
            "name": "name2",
            "type": "type1",
            "owner": "0x2d4e68caf597d1e980b5e8684164460161f8c29b",
            "creator": "0x2d4e68caf597d1e980b5e8684164460161f8c29b",
            "price": 1.23,
            "logo": "http://burgerswap.org",
            "status": 1,
            "launchTime": 1649216188709,
            "updateTime": "2022-04-06T03:36:29.000Z",
            "isDel": 0
        },
        {
            "id": 1,
            "chainId": 97,
            "name": "name1",
            "type": "type1",
            "owner": "0x2d4e68caf597d1e980b5e8684164460161f8c29b",
            "creator": "0x2d4e68caf597d1e980b5e8684164460161f8c29b",
            "price": 1.25,
            "logo": "http://burgerswap.org",
            "status": 1,
            "launchTime": 1649216065613,
            "updateTime": "2022-04-06T03:43:33.000Z",
            "isDel": 0
        }
    ]
}
```
- - -

#### /resource/add

url: {apiAddress}/admin/resource/add

method: post

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

```json
{
    "chainId": 97,
    "name":"name2",
    "type": "type1",
    "owner": "0x2d4e68caf597d1e980b5e8684164460161f8c29b",
    "creator": "0x2d4e68caf597d1e980b5e8684164460161f8c29b",
    "price": 1.23,
    "logo": "http://burgerswap.org",
    "status": 1
}

```

response
```json
{
    "status": true,
    "message": "Success",
    "data": {
        "id": 2,
        "chainId": 97,
        "name": "name2",
        "type": "type1",
        "owner": "0x2d4e68caf597d1e980b5e8684164460161f8c29b",
        "creator": "0x2d4e68caf597d1e980b5e8684164460161f8c29b",
        "price": 1.23,
        "logo": "http://burgerswap.org",
        "status": 1,
        "launchTime": 1649216188709,
        "updateTime": "2022-04-06T03:36:29.000Z",
        "isDel": 0
    }
}
```
- - -


#### /resource/modify

url: {apiAddress}/admin/resource/modify

method: post

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

```json
{
    "id": 1,
    "chainId": 97,
    "name":"name1",
    "type": "type1",
    "owner": "0x2d4e68caf597d1e980b5e8684164460161f8c29b",
    "creator": "0x2d4e68caf597d1e980b5e8684164460161f8c29b",
    "price": 1.25,
    "logo": "http://burgerswap.org",
    "status": 1,
    "launchTime": 1649216065613
}

```

response
```json
{
    "status": true,
    "message": "Success",
    "data": {
        "id": 1,
        "chainId": 97,
        "name": "name1",
        "type": "type1",
        "owner": "0x2d4e68caf597d1e980b5e8684164460161f8c29b",
        "creator": "0x2d4e68caf597d1e980b5e8684164460161f8c29b",
        "price": 1.25,
        "logo": "http://burgerswap.org",
        "status": 1,
        "launchTime": 1649216065613,
        "updateTime": "2022-04-06T03:43:33.000Z",
        "isDel": 0
    }
}
```
- - -

#### /resource/delselected

url: {apiAddress}/admin/resource/delselected

method: post

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

params: [id1, id2, ...]

```json
[1,2]

```

response
```json
{
    "status": true,
    "message": "Success",
    "data": "1,2"
}
```
- - -


#### /resource/restoreselected

url: {apiAddress}/admin/resource/restoreselected

method: post

request-header
| name         | required | type             | des               |
| ------------ | -------- | ---------------- | ----------------- |
| Content-Type | true     | application/json | require args type |

params: [id1, id2, ...]

```json
[1,2]

```

response
```json
{
    "status": true,
    "message": "Success",
    "data": "1,2"
}
```
- - -

## Resource

```sql
CREATE TABLE `resource` (
  `id` bigint NOT NULL AUTO_INCREMENT,
  `chainId` int DEFAULT '0',
  `name` varchar(255) CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci NOT NULL DEFAULT '',
  `type` varchar(255) CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci NOT NULL DEFAULT '',
  `owner` varchar(255) CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci NOT NULL DEFAULT '' COMMENT 'owner wallet address',
  `creator` varchar(255) CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci NOT NULL DEFAULT '' COMMENT 'creator wallet address',
  `price` decimal(10,2) unsigned DEFAULT '0.00',
  `logo` text CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci NOT NULL COMMENT 'log url',
  `status` int NOT NULL DEFAULT '0' COMMENT '0 close, 1 open',
  `launchTime` bigint DEFAULT '0',
  `updateTime` datetime DEFAULT NULL ON UPDATE CURRENT_TIMESTAMP,
  `isDel` tinyint DEFAULT '0',
  PRIMARY KEY (`id`),
  UNIQUE KEY `unt` (`name`,`type`,`chainId`) USING BTREE
) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;
```

#### /resource/typeList

url: {apiAddress}/resource/typeList

method: get

response
```json
{
    "status": true,
    "message": "Success",
    "data": [
        "type1",
        "type2"
    ]
}
```
- - -

#### /resource/get

url: {apiAddress}/resource/get

method: get

request-query
| name    | required | type   | des                    |
| ------- | -------- | ------ | ---------------------- |
| id      | true     | number |  record id    |


response
```json
{
    "status": true,
    "message": "Success",
    "data": {
        "id": 1,
        "chainId": 97,
        "name": "name1",
        "type": "type1",
        "owner": "0x2d4e68caf597d1e980b5e8684164460161f8c29b",
        "creator": "0x2d4e68caf597d1e980b5e8684164460161f8c29b",
        "price": 1.25,
        "logo": "http://burgerswap.org",
        "status": 1,
        "launchTime": 1649216065613,
        "updateTime": "2022-04-06T03:43:33.000Z",
        "isDel": 0
    }
}
```
- - -


#### /resource/query

url: {apiAddress}/resource/query

method: get

request-query
| name    | required | type   | des                    |
| ------- | -------- | ------ | ---------------------- |
| _page  | option   | number |  default is 1    |
| _limit | option   | number |  default is 10   |
| id      | true     | number |  record id    |
...

response
```json
{
    "status": true,
    "message": "Success",
    "data": [
        {
            "id": 2,
            "chainId": 97,
            "name": "name2",
            "type": "type1",
            "owner": "0x2d4e68caf597d1e980b5e8684164460161f8c29b",
            "creator": "0x2d4e68caf597d1e980b5e8684164460161f8c29b",
            "price": 1.23,
            "logo": "http://burgerswap.org",
            "status": 1,
            "launchTime": 1649216188709,
            "updateTime": "2022-04-06T03:36:29.000Z",
            "isDel": 0
        },
        {
            "id": 1,
            "chainId": 97,
            "name": "name1",
            "type": "type1",
            "owner": "0x2d4e68caf597d1e980b5e8684164460161f8c29b",
            "creator": "0x2d4e68caf597d1e980b5e8684164460161f8c29b",
            "price": 1.25,
            "logo": "http://burgerswap.org",
            "status": 1,
            "launchTime": 1649216065613,
            "updateTime": "2022-04-06T03:43:33.000Z",
            "isDel": 0
        }
    ]
}
```
- - -