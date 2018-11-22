# 多比平台上币接口检查
    
## 分类

- 比特币(`BTC`)或者是比特币的分叉币（包含修改比特币源码之后新生成的币）
- 以太坊(`ETH`)或者是以太坊的分叉币（包含修改以太坊源码之后新生成的币）
- 以太坊的合约币

> 注： 此文档是根据多比业务需求列出的，其他项目如要使用，请合理参考。


## 需要提供的信息

- 源码仓库地址（如`Github`地址）
- `Linux` 下（如对 `Linux` 发行版本有特殊需求，请在文档里面说明）源码安装部署说明文档（仅支持 `Linux`），包括但不限于钱包部署，`RPC` 接口部署等，或者提供 `docker` 镜像
- `API`说明文档，包括但不限于区块数量、区块 `HASH` 、区块内容、交易详情和发送交易等 `RPC` 请求的 `URI` 、请求的方式（`GET` 或者 `POST` 等）、请求的字段名称说明和请求返回的字段名称说明
- 注意事项和特殊事项说明文档，包括但不限于链的特性（与主流公链 `BTC` `ETH` 等不同的地方）、链运行期间的特殊情况说明（如 `POS` 等）、矿工费收取规则、区块打包时间间隔、区块大小、当前区块高度和当前区块总大小等

> 合约币需要提供合约源码和其主链的源码，其余资料为其主链的资料

## API检查步骤

### 比特币系列

需要保证下列接口的功能与 BTC 相同，并且请求和返回的对象字段含义与 BTC 一样。

|      接口      |                        需要的信息                        |
|:--------------:|:--------------------------------------------------------|
|`getblockcount` |区块的数量                                                |
|`getblockhash`  |区块的 hash                                             |
|`getblock`      |区块的信息，并包含着 txid 数组                               |
|`gettransaction`|交易信息，并包含有基本的输入输出信息(vout,vin,details)|
|`getrawtransaction `|获取交易原始数据|
|`sendtoaddress` |可以发送交易并返回 txid，并且交易能被区块链确认             |
|`getnewaddress` |确定接口可以返回新建的地址                                 |
|`dumpprivkey` |获取地址的私钥|
|`decoderawtransaction` |从原始十六进制字符串反序列化到 JSON 对象|
|`createrawtransaction` |创建原始交易|
|`signrawtransaction` |签名原始交易|
|`sendrawtransaction` |发送原始交易|


### 以太坊系列（不包含合约币）

需要保证下列接口的功能与 ETH 相同，并且请求和返回的对象字段含义与 ETH 一样。

|           接口           |                 需要的信息                 |
|:-----------------------:|:-------------------------------------------|
|`eth_blockNumber`        |区块的数量                                   |
|`eth_getBlockByNumber`   |通过区块高度获取区块信息|
|`eth_getBlockByHash`     |通过区块 hash 获取区块信息|
|`eth_getTransactionByBlockNumberAndIndex`|通过区块高度和交易索引获取区块中的交易信息|
|`eth_getTransaction`     |通过 txid 获取交易信息|
|`eth_getTransactionReceipt`|通过 txid 获取交易信息|
|`eth_sendTransaction`    |可以发送交易并返回 txid，并且交易能被区块链确认|
|`eth_signTransaction`    |签名交易|
|`eth_sendRawTransaction` |发送原始交易|
|`personal_newAccount`    |确定接口可以返回新建的地址                     |
|`personal_unlockAccount` |确定接口可以解锁地址                          |


### 以太坊合约币

- 必须提供合约地址和合约代码

