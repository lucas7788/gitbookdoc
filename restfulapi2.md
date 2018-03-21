# Ontology Restful API

* [Introduction](#Introduction)
* [Errorcode](#Errorcode)

## Introduction

This document describes the restful api format for the http/https used in the Onchain Ontology.

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

### 1.Get the generate block time
##### Get

```
/api/v1/node/generateblocktime
```
#### Example usage:

```
curl -i http://server:port/api/v1/node/generateblocktime
```

#### Respone

| Field | Type | Description |
| :--- | :--- | :--- |
| Action | string | action name |
| Desc | string | description |
| Error | int64 | error code |
| Result | int | execute result |
| Version | string | version information |

#### Response example

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

GET

```
/api/v1/node/connectioncount
```

#### Example usage:

```
curl -i http://server:port/api/v1/node/connectioncount
```

#### Respone

| Field | Type | Description |
| :--- | :--- | :--- |
| Action | string | action name |
| Desc | string | description information |
| Error | int64 | error code |
| Result | uint | program execution result |
| Version | string | version information |

#### Response example

```
{
    "Action": "connectioncount",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": 0,
    "Version": "1.0.0"
}
```
### 3 Get transactions by block height

GET

```
/api/v1/block/transactions/height/:height
```

#### Example usage:

```
curl -i http://server:port/api/v1/block/transactions/height/100
```

#### Respone

| Field | Type | Description |
| :--- | :--- | :--- |
| Action | string | action name |
| Desc | string | description |
| Error | int64 | error code |
| Result | object | program execution result |
| Version | string | version information |

#### Response example

```
{
    "Action": "getblocktransactionsbyheight",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": {
        "Hash": "8723534588ea3202c0949ce5e39876cfcec83f3e9a3ed20168133714944d1227",
        "Height": 22,
        "Transactions": [
        "8c4a7568701fe58211adfe2cba2a7a5438f0670af5f24be8442c57f36e625996"        
        ]
    },    
    "Version": "1.0.0"
}
```
### 4 Get the block by block height

GET

```
/api/v1/block/details/height/:height
```

####Example usage:

```
curl -i http://server:port/api/v1/block/details/height/22
```

#### Respone

| Field | Type | Description |
| :--- | :--- | :--- |
| Action | string | action name |
| Desc | string | description |
| Error | int64 | error code |
| Result | object | program execution result |
| Version | string | version information |

#### Response example

```
{
    "Action": "getblockbyheight",
    "Desc": "SUCCESS",
    "Error": 0,
    "Result": {
        "Hash": "8723534588ea3202c0949ce5e39876cfcec83f3e9a3ed20168133714944d1227",
        "BlockData": {
            "Version": 0,
            "PrevBlockHash": "a26c7b7659069b1ccf40793c8d5af1af7ca44e55ffc0aadc5e51ec1ee0b5bf92",
            "TransactionsRoot": "8c4a7568701fe58211adfe2cba2a7a5438f0670af5f24be8442c57f36e625996",
            "BlockRoot": "1ce9d347ddc4e03b587d10e89f96c0d0c8f2f9b4f0ab12c212198e7cbd12d68f",
            "StateRoot": "49c6405eae477bb053406c0a4f56a830289798e2d70dc77e0a1d927fa9fb93c4",
            "Timestamp": 1521432329,
            "Height": 22,
            "ConsensusData": 11160228784438648574,
            "NextBookKeeper": "027c557d2e735b9a369d20dd099bfd42db5cdb74",
            "BookKeepers": [
                {
                    "X": "11045594958442581564679839478917319740817938700262919124154204990772552987783",
                    "Y": "28445199876541353997545685344458930058882115795876754515124389392470701852812"
                }
            ],
            "SigData": [
                "2c9a4c3ed2663cf542e58be466350f5244b2792e4e23f2e0bdc06f1ef69a9382c33ab7f31d1f8658f2ca90d578f1e55c20377659c62ce2ff0a526c6ac14cff41"
            ],
            "Hash": "8723534588ea3202c0949ce5e39876cfcec83f3e9a3ed20168133714944d1227"
        },
        "Transactions": [
            {
                "Version": 0,
                "Nonce": 0,
                "TxType": 0,
                "Payload": {
                    "Nonce": 1521432329060775000,
                    "Issuer": {
                        "X": "",
                        "Y": ""
                    }
                },
                "Attributes": [],
                "Fee": null,
                "NetworkFee": "0",
                "Sigs": null,
                "Hash": "8c4a7568701fe58211adfe2cba2a7a5438f0670af5f24be8442c57f36e625996"
            }
        ]
    },
    "Version": "1.0.0"
}
```
