# 多比平臺新幣種上線接口檢查

本文旨在新幣種上線[多比交易平臺](https://www.dobiex.io/)需要提供的資料做出描述和解釋。根據幣種所依賴的鏈進行劃分，不同的鏈需要提供的內容不用。

提供的文檔、源碼必須審核通過才能上線，審核結果會以郵件形式在 3-5 個工作日內回復。

## 環境

- 部署、運行的 Linux 操作系統應是如下其中之壹：

    - CentOS 7.5
    - Debian 9
    - Ubuntu 16.04
    - Ubuntu 18.04

    如果不符合，必須提供 Docker 鏡像或者 Dockerfile 等；

- 對硬體資源的要求（如 CPU 主頻、內存、硬盤容量、帶寬等）；

- 如果有使用第三方資源（比如 MySQL），請註明第三方軟件的資源的要求；

- 只能在 Windows、Unix 或其他操作系統下部署的幣暫不支持。

## 編譯部署

- 出於安全考慮，必須開源或者提供源代碼；

- 必須提供編譯、安裝部署的文檔，包括：

    - 編譯工具和版本等（比如 gcc 8.2）；
    - 網絡端口的使用（比如 P2P）；
    - 文件資源的占用（比如區塊數據存放目錄、文件名）；

## 文檔

- 配置文件、啟動參數說明等;
- 網絡協議、接口文檔（如 RPC、API說明文檔等）；
- 特殊事項說明文檔，至少包括如下內容：
    - 礦工費收取規則；
    - 區塊打包時間間隔；
    - 區塊大小；
    - 截止於提供文檔時，當前區塊占用硬盤總大小、高度；
    - 鏈的特性，即與主流公鏈（`BTC`、`ETH`等）的區別。
- 如果提供 Docker：
    - Dockerfile 或者 image 下載地址；
    - docker 啟動參數或 docker-compose 相關的說明文檔；
- 解決技術問題聯系方式，E-Mail、telegram、WhatsApp 等，用於及時聯系。

## 主流鏈

### 以太坊(Ethereum, ETH) 

#### ERC-20 合約幣

ERC-20 合約幣是根據 [ERC-20](https://en.wikipedia.org/wiki/ERC-20) 標準開發的合約幣，需要提供如下內容：

1. 合約地址；
2. 合約源代碼。

#### 分叉鏈

分叉鏈是指基於[以太坊](https://en.wikipedia.org/wiki/Ethereum)鏈本身開發，需要保證下列 rpc 接口的功能、參數和返回結果的字段的類型和意義等與以太坊相同：

|接口|描述|
|:---:|:---|
|`eth_blockNumber`|區塊的數量|
|`eth_getBlockByNumber`|通過區塊高度獲取區塊信息|
|`eth_getBlockByHash`|通過區塊 hash 獲取區塊信息|
|`eth_getTransactionByBlockNumberAndIndex`|通過區塊高度和交易索引獲取區塊中的交易信息|
|`eth_getTransaction`|通過 txid 獲取交易信息|
|`eth_getTransactionReceipt`|通過 txid 獲取交易信息|
|`eth_sendTransaction`|可以發送交易並返回 txid，並且交易能被區塊鏈確認|
|`eth_signTransaction`|簽名交易|
|`eth_sendRawTransaction`|發送原始交易|
|`personal_newAccount`|新建地址|
|`personal_unlockAccount`|解鎖新建的地址|

### 比特幣分叉幣

需要保證下列接口的功能與 BTC 相同，並且請求和返回的對象字段含義與 BTC 壹樣。

|接口|描述|
|:---:|:---|
|`getblockcount`|區塊的數量|
|`getblockhash`|區塊的hash|
|`getblock`|區塊的信息，並包含著txid數組|
|`gettransaction`|交易信息，並包含有基本的輸入輸出信息(vout,vin,details)|
|`getrawtransaction`|獲取交易原始數據|
|`sendtoaddress`|可以發送交易並返回txid，並且交易能被區塊鏈確認|
|`getnewaddress`|新建的地址|
|`dumpprivkey`|獲取地址的私鑰|
|`decoderawtransaction`|原始十六進制字符串反序列化到JSON對象|
|`createrawtransaction`|創建原始交易|
|`signrawtransaction`|簽名原始交易|
|`sendrawtransaction`|發送原始交易|

### EOS

合約幣和分叉鏈都暫不支持