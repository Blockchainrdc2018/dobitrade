# Dobitrade platform interface review for new coin listing 

This article aims to describe and explain the information that needs to be provided for upcoming new coin on [dobitrade](https://www.dobitrade.com/). According to the chain on which the coin depends, we need different content concerned for different chains.

All coins have to provide documents and source code before being listed officially. We’ll keep you informed of the approval result within 3-5 work days via email.

## Environment

- Deploy, runtime, Linux OS used for deploy or runing should be one of:

    - CentOS 7.5
    - Debian 9
    - Ubuntu 16.04
    - Ubuntu 18.04

    If not, Docker image or Dockerfile must be provided;

- Requirements of Hardware (CPU, RAM, Hard disk, net bandwith, etc.);

- If thirdparty resource(eg. MySQL), please list the requements of that;

- Non-Linux is not supported.

## Compiling and deploy

- Open source or providing source code, due to safety concerns;

- Documents of compiling and deploy are required, and must include:

    - Compiling tools and its version(eg. gcc 8.2)
    - Ports used for network(eg. P2P)
    - File resource(eg. where stores blocks data, names of files)

## Documents

- Configuration files, startup parameters;
- Network protocols, Interface documents(eg. RPC, API documents)
- Special matters documents, at least including:
    - Rules of mining fee
    - Intervals of packaging block;
    - Size of a block;
    - Up to handle the documents, heigth of blocks and its total size;
    - The diffiences between the focked chain and the mainstream chain(`BTC` or `ETH`);
- If Docker provided:
    - Dockerfile or link of dowloading image
    - Documents about docker startup parameters or docker-compose;
- Contanct information, E-Mail, telegram, WhatsApp etc., used for contacting to solve tech-problems.

## Mainstream chains

### Ethereum(ETH) 

#### ERC-20 contract token

ERC-20 contract token is the contract token develeped under the [ERC-20](https://en.wikipedia.org/wiki/ERC-20) standard, need to provide the following content:

1. Contract Address;
2. Contract source code.

#### Forked chain

Forked chain means that developing the chain based on [Ethereum](https://en.wikipedia.org/wiki/Ethereum), need to ensure that RPC interfaces' functions, parametes and the type and meaning of the fiels of the results are the same as ETH, which are listed:

|Interface|Description|
|:---:|:---|
|`eth_blockNumber`|number of blocks|
|`eth_getBlockByNumber`|get the block information by number|
|`eth_getBlockByHash`|get the block information by hash|
|`eth_getTransactionByBlockNumberAndIndex`|get transaction by block number and index|
|`eth_getTransaction`|get transaction|
|`eth_getTransactionReceipt`|get transactions' receipt|
|`eth_sendTransaction`|send transactions|
|`eth_signTransaction`|sign transactions|
|`eth_sendRawTransaction`|send raw transactions|
|`personal_newAccount`|get new account address|
|`personal_unlockAccount`|unlock the new created address|

### 比特币分叉币

Forked chain means that developing the chain based on [BTC](https://bitcoin.org/), need to ensure that RPC interfaces' functions, parametes and the type and meaning of the fiels of the results are the same as ETH, which are listed:

|Interface|Description|
|:---:|:---|
|`getblockcount`|block counts|
|`getblockhash`|block hash|
|`getblock`|get block information, which including the array of txid|
|`gettransaction`|get transaction information, which including basic input and output information(vout, vin, details)|
|`getrawtransaction`|get raw transaction information|
|`sendtoaddress`|send transaction and then return txid|
|`getnewaddress`|get new address|
|`dumpprivkey`|dump the private key|
|`decoderawtransaction`|deserializtion from HEX to JSON object|
|`createrawtransaction`|create raw transaction|
|`signrawtransaction`|sign raw transaction|
|`sendrawtransaction`|send raw transaction|

### EOS

Contract token or forked from EOS chain are not supported yet.
