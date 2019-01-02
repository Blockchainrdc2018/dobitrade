# 多比平台新币种上线接口检查

本文旨在新币种上线[多比交易平台](https://www.dobiex.io:_blank)需要提供的资料做出描述和解释。根据币种所依赖的链进行划分，不同的链需要提供的内容不用。

提供的文档、源码必须审核通过才能上线，审核结果会以邮件形式在 3-5 个工作日内回复。

## 环境

- 部署、运行的 Linux 操作系统应是如下其中之一：

    - CentOS 7.5
    - Debian 9
    - Ubuntu 16.04
    - Ubuntu 18.04

    如果不符合，必须提供 Docker 镜像或者 Dockerfile 等；

- 对硬件资源的要求（如 CPU 主频、内存、硬盘容量、带宽等）；

- 如果有使用第三方资源（比如 MySQL），请注明第三方软件的资源的要求；

- 只能在 Windows、Unix 或其他操作系统下部署的币暂不支持。

## 编译部署

- 出于安全考虑，必须开源或者提供源代码；

- 必须提供编译、安装部署的文档，包括：

    - 编译工具和版本等（比如 gcc 8.2）；
    - 网络端口的使用（比如 P2P）；
    - 文件资源的占用（比如区块数据存放目录、文件名）；

## 文档

- 配置文件、启动参数说明等;
- 网络协议、接口文档（如 RPC、API说明文档等）；
- 特殊事项说明文档，至少包括如下内容：
    - 矿工费收取规则；
    - 区块打包时间间隔；
    - 区块大小；
    - 截止于提供文档时，当前区块占用硬盘总大小、高度；
    - 链的特性，即与主流公链（`BTC`、`ETH`等）的区别。
- 如果提供 Docker：
    - Dockerfile 或者 image 下载地址；
    - docker 启动参数或 docker-compose 相关的说明文档；
- 解决技术问题联系方式，E-Mail、telegram、WhatsApp 等，用于及时联系。

## 主流链

### 以太坊(Ethereum, ETH)

#### ERC-20 合约币

ERC-20 合约币是根据 [ERC-20](https://en.wikipedia.org/wiki/ERC-20) 标准开发的合约币，需要提供如下内容：

1. 合约地址；
2. 合约源代码。

#### 分叉链

分叉链是指基于[以太坊](https://en.wikipedia.org/wiki/Ethereum)链本身开发，需要保证下列 rpc 接口的功能、参数和返回结果的字段的类型和意义等与以太坊相同：

|接口|描述|
|:---:|:---|
|`eth_blockNumber`|区块的数量|
|`eth_getBlockByNumber`|通过区块高度获取区块信息|
|`eth_getBlockByHash`|通过区块 hash 获取区块信息|
|`eth_getTransactionByBlockNumberAndIndex`|通过区块高度和交易索引获取区块中的交易信息|
|`eth_getTransaction`|通过 txid 获取交易信息|
|`eth_getTransactionReceipt`|通过 txid 获取交易信息|
|`eth_sendTransaction`|可以发送转账并返回 txid|
|`eth_signTransaction`|签名交易|
|`eth_sendRawTransaction`|发送原始交易|
|`personal_newAccount`|新建地址|
|`personal_unlockAccount`|解锁新建的地址|

### 比特币分叉币

需要保证下列接口的功能与 BTC 相同，并且请求和返回的对象字段含义与 BTC 一样。

|接口|描述|
|:---:|:---|
|`getblockcount`|区块的数量|
|`getblockhash`|区块的hash|
|`getblock`|区块的信息，并包含着txid数组|
|`gettransaction`|交易信息，并包含有基本的输入输出信息(vout,vin,details)|
|`getrawtransaction`|获取交易原始数据|
|`sendtoaddress`|可以发送交易并返回txid，并且交易能被区块链确认|
|`getnewaddress`|新建地址|
|`dumpprivkey`|获取地址的私钥|
|`decoderawtransaction`|原始十六进制字符串反序列化到JSON对象|
|`createrawtransaction`|创建原始交易|
|`signrawtransaction`|签名原始交易|
|`sendrawtransaction`|发送原始交易|

### EOS

合约币和分叉链都暂不支持
