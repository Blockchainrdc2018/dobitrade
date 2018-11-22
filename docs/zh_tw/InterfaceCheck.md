# 多比平臺上幣接口檢查
    
## 分類

- 比特幣(`BTC`)或者是比特幣的分叉幣（包含修改比特幣源碼之後新生成的幣）
- 以太坊(`ETH`)或者是以太坊的分叉幣（包含修改以太坊源碼之後新生成的幣）
- 以太坊的合約幣

> 註： 此文檔是根據多比業務需求列出的，其他項目如要使用，請合理參考。


## 需要提供的信息

- 源碼倉庫地址（如`Github`地址）
- `Linux` 下（如對 `Linux` 發行版本有特殊需求，請在文檔裏面說明）源碼安裝部署說明文檔（僅支持 `Linux`），包括但不限於錢包部署，`RPC` 接口部署等，或者提供 `docker` 鏡像
- `API`說明文檔，包括但不限於區塊數量、區塊 `HASH` 、區塊內容、交易詳情和發送交易等 `RPC` 請求的 `URI` 、請求的方式（`GET` 或者 `POST` 等）、請求的字段名稱說明和請求返回的字段名稱說明
- 註意事項和特殊事項說明文檔，包括但不限於鏈的特性（與主流公鏈 `BTC` `ETH` 等不同的地方）、鏈運行期間的特殊情況說明（如 `POS` 等）、礦工費收取規則、區塊打包時間間隔、區塊大小、當前區塊高度和當前區塊總大小等

> 合約幣需要提供合約源碼和其主鏈的源碼，其余資料為其主鏈的資料

## API檢查步驟

### 比特幣系列

需要保證下列接口的功能與 BTC 相同，並且請求和返回的對象字段含義與 BTC 壹樣。

|      接口      |                        需要的信息                        |
|:--------------:|:--------------------------------------------------------|
|`getblockcount` |區塊的數量                                                |
|`getblockhash`  |區塊的 hash                                             |
|`getblock`      |區塊的信息，並包含著 txid 數組                               |
|`gettransaction`|交易信息，並包含有基本的輸入輸出信息(vout,vin,details)|
|`getrawtransaction `|獲取交易原始數據|
|`sendtoaddress` |可以發送交易並返回 txid，並且交易能被區塊鏈確認             |
|`getnewaddress` |確定接口可以返回新建的地址                                 |
|`dumpprivkey` |獲取地址的私鑰|
|`decoderawtransaction` |從原始十六進制字符串反序列化到 JSON 對象|
|`createrawtransaction` |創建原始交易|
|`signrawtransaction` |簽名原始交易|
|`sendrawtransaction` |發送原始交易|


### 以太坊系列（不包含合約幣）

需要保證下列接口的功能與 ETH 相同，並且請求和返回的對象字段含義與 ETH 壹樣。

|           接口           |                 需要的信息                 |
|:-----------------------:|:-------------------------------------------|
|`eth_blockNumber`        |區塊的數量                                   |
|`eth_getBlockByNumber`   |通過區塊高度獲取區塊信息|
|`eth_getBlockByHash`     |通過區塊 hash 獲取區塊信息|
|`eth_getTransactionByBlockNumberAndIndex`|通過區塊高度和交易索引獲取區塊中的交易信息|
|`eth_getTransaction`     |通過 txid 獲取交易信息|
|`eth_getTransactionReceipt`|通過 txid 獲取交易信息|
|`eth_sendTransaction`    |可以發送交易並返回 txid，並且交易能被區塊鏈確認|
|`eth_signTransaction`    |簽名交易|
|`eth_sendRawTransaction` |發送原始交易|
|`personal_newAccount`    |確定接口可以返回新建的地址                     |
|`personal_unlockAccount` |確定接口可以解鎖地址                          |


### 以太坊合約幣

- 必須提供合約地址和合約代碼

