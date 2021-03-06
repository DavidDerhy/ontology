# Ontology Restful API

* [Introduction](#Introduction)
* [Restful API list](#Restful API list)
* [Errorcode](#Errorcode)

## Introduction

This document describes the restful api format for the http/https used in the Onchain Ontology.

## Restful API list

### Response parameters descri

| Field | Type | Description |
| :--- | :--- | :--- |
| Action | string | action name |
| Desc | string | description |
| Error | int64 | error code |
| Result | int/string/object | execute result |
| Version | string | version information |

### 1. Get the generate block time
return the time required to create a new block

##### GET

```
/api/v1/node/generateblocktime
```
#### Request Example:

```
curl -i http://server:port/api/v1/node/generateblocktime
```

#### Response example:

```
{
    "Action": "getgenerateblocktime",
    "Desc": "SUCCESS"
    "Error": 0,
    "Result": 6,
    "Version": "1.0.0"
}
```
### 2 Get the number of connected node

get the current number of connections for the node

GET

```
/api/v1/node/connectioncount
```

#### Request Example:

```
curl -i http://server:port/api/v1/node/connectioncount
```

#### Response Example:

```
{
    "Action": "getconnectioncount",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": 0,
    "Version": "1.0.0"
}
```
### 3 Get transactions by block height

return all transaction hash contained in the block corresponding to this height

GET

```
/api/v1/block/transactions/height/:height
```

#### Request Example:

```
curl -i http://server:port/api/v1/block/transactions/height/100
```

#### Response Example:

```
{
    "Action": "getblocktxsbyheight",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": {
        "Hash": "ea5e5219d2f1591f4feef89885c3f38c83d3a3474a5622cf8cd3de1b93849603",
        "Height": 100,
        "Transactions": [
            "37e017cb9de93aa93ef817e82c555812a0a6d5c3f7d6c521c7808a5a77fc93c7"
        ]
    },
    "Version": "1.0.0"
}
```
### 4 Get the block by block height

return block details based on block height

GET

```
/api/v1/block/details/height/:height
```

#### Request Example:

```
curl -i http://server:port/api/v1/block/details/height/22
```

#### Response Example:

```
{
    "Action": "getblockbyheight",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": {
        "Hash": "ea5e5219d2f1591f4feef89885c3f38c83d3a3474a5622cf8cd3de1b93849603",
        "Header": {
            "Version": 0,
            "PrevBlockHash": "fc3066adb581c5aee8edaa47eecda2b7cc039c8662757f8b1e3c3aed60314353",
            "TransactionsRoot": "37e017cb9de93aa93ef817e82c555812a0a6d5c3f7d6c521c7808a5a77fc93c7",
            "BlockRoot": "7154a6dcb3c23254334bc1f5d8f054c143a39ff28f46fdeb8a9c7488147ccec6",
            "Timestamp": 1522313652,
            "Height": 100,
            "ConsensusData": 18012644264110396442,
            "NextBookkeeper": "TABrSU6ABhj6Rdw5KozV53wvZNSUATgKHW",
            "Bookkeepers": [
                "120203fe4f9ba2022b68595dd163f4a92ac80f918919674de2d6e2a7e04a10c59d0066"
            ],
            "SigData": [
                "01a2369280b0ff75bed85f351d3ef0dd58add118328c1ed2f7d3320df32cb4bd55541f1bb8e11ad093bd24da3de4cd12464800310bfdb49dc62d42d97ca0549762"
            ],
            "Hash": "ea5e5219d2f1591f4feef89885c3f38c83d3a3474a5622cf8cd3de1b93849603"
        },
        "Transactions": [
            {
                "Version": 0,
                "Nonce": 0,
                "TxType": 0,
                "Payload": {
                    "Nonce": 1522313652068190000
                },
                "Attributes": [],
                "Fee": [],
                "NetworkFee": 0,
                "Sigs": [
                    {
                        "PubKeys": [
                            "120203fe4f9ba2022b68595dd163f4a92ac80f918919674de2d6e2a7e04a10c59d0066"
                        ],
                        "M": 1,
                        "SigData": [
                            "017d3641607c894dd85f455c71a94afaea2661acbe372ff8f3f4c7921b0c768756e3a6e9308a4c4c8b1b58e717f1486a2f10f5bc809b803a27c10a2cd579778a54"
                        ]
                    }
                ],
                "Hash": "37e017cb9de93aa93ef817e82c555812a0a6d5c3f7d6c521c7808a5a77fc93c7"
            }
        ]
    },
    "Version": "1.0.0"
}
```
### 5 Get block by blockhash

return block details based on block hash

GET

```
/api/v1/block/details/hash/:hash
```

#### Request Example:

```
curl -i http://server:port/api/v1/block/details/hash/ea5e5219d2f1591f4feef89885c3f38c83d3a3474a5622cf8cd3de1b93849603
```

#### Response Example:

```
{
    "Action": "getblockbyhash",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": {
        "Hash": "ea5e5219d2f1591f4feef89885c3f38c83d3a3474a5622cf8cd3de1b93849603",
        "Header": {
            "Version": 0,
            "PrevBlockHash": "fc3066adb581c5aee8edaa47eecda2b7cc039c8662757f8b1e3c3aed60314353",
            "TransactionsRoot": "37e017cb9de93aa93ef817e82c555812a0a6d5c3f7d6c521c7808a5a77fc93c7",
            "BlockRoot": "7154a6dcb3c23254334bc1f5d8f054c143a39ff28f46fdeb8a9c7488147ccec6",
            "Timestamp": 1522313652,
            "Height": 100,
            "ConsensusData": 18012644264110396442,
            "NextBookkeeper": "TABrSU6ABhj6Rdw5KozV53wvZNSUATgKHW",
            "Bookkeepers": [
                "120203fe4f9ba2022b68595dd163f4a92ac80f918919674de2d6e2a7e04a10c59d0066"
            ],
            "SigData": [
                "01a2369280b0ff75bed85f351d3ef0dd58add118328c1ed2f7d3320df32cb4bd55541f1bb8e11ad093bd24da3de4cd12464800310bfdb49dc62d42d97ca0549762"
            ],
            "Hash": "ea5e5219d2f1591f4feef89885c3f38c83d3a3474a5622cf8cd3de1b93849603"
        },
        "Transactions": [
            {
                "Version": 0,
                "Nonce": 0,
                "TxType": 0,
                "Payload": {
                    "Nonce": 1522313652068190000
                },
                "Attributes": [],
                "Fee": [],
                "NetworkFee": 0,
                "Sigs": [
                    {
                        "PubKeys": [
                            "120203fe4f9ba2022b68595dd163f4a92ac80f918919674de2d6e2a7e04a10c59d0066"
                        ],
                        "M": 1,
                        "SigData": [
                            "017d3641607c894dd85f455c71a94afaea2661acbe372ff8f3f4c7921b0c768756e3a6e9308a4c4c8b1b58e717f1486a2f10f5bc809b803a27c10a2cd579778a54"
                        ]
                    }
                ],
                "Hash": "37e017cb9de93aa93ef817e82c555812a0a6d5c3f7d6c521c7808a5a77fc93c7"
            }
        ]
    },
    "Version": "1.0.0"
}
```

### 6 Get the current block height

return the current block height

GET

```
/api/v1/block/height
```

#### Request Example:

```
curl -i http://server:port/api/v1/block/height
```


#### Response Example:

```
{
    "Action": "getblockheight",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": 327,
    "Version": "1.0.0"
}
```

### 7 Get blockhash by block height

return block hash based on block height

GET

```
/api/v1/block/hash/:height
```

#### Request Example:

```
curl -i http://server:port/api/v1/block/hash/100
```

#### Response Example:

```
{
    "Action": "getblockhash",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": "3b90ddc4d33c4954c3d87736120e94915f963546861987757f358c9376422255",
    "Version": "1.0.0"
}
```

### 8 get transaction by transaction hash

get transaction details based on transaction hash

GET

```
/api/v1/transaction/:hash
```

####Request Example:

```
curl -i http://server:port/api/v1/transaction/c5e0d387c6a97aef12f1750840d24b53d9fe7f22f16c7b7703d4a93a28370baa
```
#### Response Example:

```
{
    "Action": "gettransaction",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": {
        "Version": 0,
        "Nonce": 0,
        "TxType": 0,
        "Payload": {
            "Nonce": 1522313652068190000
        },
        "Attributes": [],
        "Fee": [],
        "NetworkFee": 0,
        "Sigs": [
            {
                "PubKeys": [
                    "120203fe4f9ba2022b68595dd163f4a92ac80f918919674de2d6e2a7e04a10c59d0066"
                ],
                "M": 1,
                "SigData": [
                    "017d3641607c894dd85f455c71a94afaea2661acbe372ff8f3f4c7921b0c768756e3a6e9308a4c4c8b1b58e717f1486a2f10f5bc809b803a27c10a2cd579778a54"
                ]
            }
        ],
        "Hash": "37e017cb9de93aa93ef817e82c555812a0a6d5c3f7d6c521c7808a5a77fc93c7"
    },
    "Version": "1.0.0"
}
```

### 9 send transaction

send transaction.

POST

```
/api/v1/transaction
```

#### Request Example:

```
curl  -H "Content-Type: application/json"  -X POST -d '{"Action":"sendrawtransaction", "Version":"1.0.0","Data":"00d00000000080fdcf2b0138c56b6c766b00527ac46c766b51527ac46151c56c766b52527ac46c766b00c31052656749644279507..."}'  http://server:port/api/v1/transaction
```

#### Post Params:

```
{
    "Action":"sendrawtransaction",
    "Version":"1.0.0",
    "Data":"80000001195876cb34364dc38b730077156c6bc3a7fc570044a66fbfeeea56f71327e8ab0000029b7cffdaa674beae0f930ebe6085af9093e5fe56b34a5c220ccdcf6efc336fc500c65eaf440000000f9a23e06f74cf86b8827a9108ec2e0f89ad956c9b7cffdaa674beae0f930ebe6085af9093e5fe56b34a5c220ccdcf6efc336fc50092e14b5e00000030aab52ad93f6ce17ca07fa88fc191828c58cb71014140915467ecd359684b2dc358024ca750609591aa731a0b309c7fb3cab5cd0836ad3992aa0a24da431f43b68883ea5651d548feb6bd3c8e16376e6e426f91f84c58232103322f35c7819267e721335948d385fae5be66e7ba8c748ac15467dcca0693692dac"
}
```

#### Response
```
{
    "Action": "sendrawtransaction",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": "22471ab3f4b4307a99f00c9a717dbf8b26f5bf63bf47f9c560477da8181de777",
    "Version": "1.0.0"
}
```
> Result: txhash

### 10 getStorage

Returns the stored value according to the contract script hashes and stored key.

GET
```
/api/v1/storage/:hash/:key
```
Request Example
```
curl -i http://localhost:20384/api/v1/storage/ff00000000000000000000000000000000000001/0144587c1094f6929ed7362d6328cffff4fb4da2
```
#### Response
```
{
    "Action": "getstorage",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": "58d15e17628000",
    "Version": "1.0.0"
}
```
> Result:Returns the stored value according to the contract script hashes and stored key.

### 11 GetBalanceByAddr

return balance of base58 account address.

GET
```
/api/v1/balance/:addr
```
> addr: Base58 encoded account address

Request Example
```
curl -i http://localhost:20384/api/v1/balance/TA5uYzLU2vBvvfCMxyV2sdzc9kPqJzGZWq
```

#### Response
```
{
    "Action": "getbalance",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": {
        "ont": "25000000000000000",
        "ong": "0"
    },
    "Version": "1.0.0"
}
```
### 12 get contractstate

According to the contract script hash, query the contract information.

GET

```
/api/v1/contract/:hash
```

#### Request Example:

```
curl -i http://server:port/api/v1/contract/fff49c809d302a2956e9dc0012619a452d4b846c
```

#### Response Example:

```
{
    "Action": "getcontract",
    "Desc": "SUCCESS",
    "Error": 0,
    "Version": "1.0.0",
    "Result": {
        "VmType": 255,
        "Code": "4f4e5420546f6b656e",
        "NeedStorage": true,
        "Name": "ONT",
        "CodeVersion": "1.0",
        "Author": "Ontology Team",
        "Email": "contact@ont.io",
        "Description": "Ontology Network ONT Token"
    }
}
```

#### 13 get smart contract event txhash list by height

Get a list of transaction hash with smartevent based on height

GET

```
/api/v1/smartcode/event/transactions/:height
```

#### Example usage:

```
curl -i http://localhost:20384/api/v1/smartcode/event/transactions/900
```

#### response
```
{
    "Action": "getsmartcodeeventbyheight",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": [
        "592d83c739d9d167b74b385161fee09bfe820eae5bc4a69411f8e00f4847b833"
    ],
    "Version": "1.0.0"
}
```
> Note: result is the txHash list.

### 14 get contract event by txhash

GET
```
/api/v1/smartcode/event/txhash/:hash
```
#### Request Example:
```
curl -i http://localhost:20384/api/v1/smartcode/event/txhash/3e23cf222a47739d4141255da617cd42925a12638ac19cadcc85501f907972c8
```
#### Response:
```
{
    "Action": "getsmartcodeeventbyhash",
    "Desc": "SUCCESS",
    "Error": 0,
    "Version": "1.0.0",
    "Result": [
        {
            "CodeHash":"80e7d2fc22c24c466f44c7688569cc6e6d6c6f92",
            "TxHash":"7c3e38afb62db28c7360af7ef3c1baa66aeec27d7d2f60cd22c13ca85b2fd4f3"
            "States": [
                "transfer",
                "TA63xZXqdPLtDeznWQ6Ns4UsbqprLrrLJk",
                "TA23xZXqdPLtDeznWQ6Ns4UsbqprLrrLfgf",
                100
            ]
        }
    ]
}
```
### 15 Get block height by transaction hash
get blockheight of txhash

GET
```
/api/v1/block/height/txhash/:hash
```
#### Request Example:
```
curl -i http://localhost:20384/api/v1/block/height/txhash/3e23cf222a47739d4141255da617cd42925a12638ac19cadcc85501f907972c8
```
#### Response
```
{
    "Action": "getblockheightbytxhash",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": 0,
    "Version": "1.0.0"
}
```

### 16 websocket configuration（unsolved）

POST

```
/api/v1/config/websocket/state
```

#### Request Example

```
curl -i http://server:port/api/v1/config/websocket/state
```

## Errorcode

| Field | Type | Description |
| :--- | :--- | :--- |
| 0 | int64 | SUCCESS |
| 41001 | int64 | SESSION\_EXPIRED: invalided or expired session |
| 41002 | int64 | SERVICE\_CEILING: reach service limit |
| 41003 | int64 | ILLEGAL\_DATAFORMAT: illegal dataformat |
| 41004 | int64 | INVALID\_VERSION: invalid version |
| 42001 | int64 | INVALID\_METHOD: invalid method |
| 42002 | int64 | INVALID\_PARAMS: invalid params |
| 43001 | int64 | INVALID\_TRANSACTION: invalid transaction |
| 43002 | int64 | INVALID\_ASSET: invalid asset |
| 43003 | int64 | INVALID\_BLOCK: invalid block |
| 44001 | int64 | UNKNOWN\_TRANSACTION: unknown transaction |
| 44002 | int64 | UNKNOWN\_ASSET: unknown asset |
| 44003 | int64 | UNKNOWN\_BLOCK: unknown block |
| 45001 | int64 | INTERNAL\_ERROR: internel error |
| 47001 | int64 | SMARTCODE\_ERROR: smartcode error |
