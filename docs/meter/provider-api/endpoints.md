---
title: Endpoints
sidebar_position: 3
---
# Endpoints

There will be two types of endpoints, one will be for malicious BNB addresses, such as accounts or contracts, and a second endpoint will be for possible malicious domain names.

## Address security

Method: `POST`

URL: `<https://<domain>/api/v1/address-security>`

## Request body

| **Name** | **Required** | **Description**                                       | **Type** | **Example**                                |
| -------- | ------------ | ----------------------------------------------------- | -------- | ------------------------------------------ |
| chain_id | Required     | ID of the Blockchain being scanned such as BNB or ETH | int      | 56 (BSC mainnet)                           |
| address  | Required     | Address of contract or account                        | string   | 0x312bc7eaaf93f1c60dc5afc115fccde161055fb0 |

## Response

| **Name** | **NotNull** | **Description**          | **Type** | **Example**                                                  |
| -------- | ----------- | ------------------------ | -------- | ------------------------------------------------------------ |
| status   | Yes         | Result of operation      | string   | `OK`: The scanning process terminated as expected  `ERROR`: Exception thrown or unexpected situation met |
| code     | Yes         | Result code of operation | int      | `000000000`: success  `000001`: unknown server error occurred during detection  `000002`: Number of requests exceeded limit  `000003`: unknown appId  `000004`: X-Signature-signature header can't be null  `000005`: verify signature error  appid, timestamp, nonce, signature headers can not be null or emptynonce is illegaltimestamp has illegaltimestamp is expiredinvalid appidappid has expiredinvalid signaturereplay requestapp is out of count limit |
| data     | Yes         | Query Result             | json     | See "Data form"                                              |

## Data

| **Name**         | **Required** | **Description**                                              | **Type** | **Example**                                                  |
| ---------------- | ------------ | ------------------------------------------------------------ | -------- | ------------------------------------------------------------ |
| has_result       | Yes          | Whether there is already a definite result, if False it needs to be repeatedly requested in [polling_interval] million seconds. And if false of this field the trust_score will be a quick reference score. | boolean  | True                                                         |
| polling_interval | No           | Recommended waiting time(million seconds) to the next repeat request. | Integer  | 60000                                                        |
| address_type     | No           | Type of address, either wallet address (EOA) or smart contract address | String   | EOA  Contract                                                |
| trust_score      | Yes          | This is the contract or entity's trust                       | Integer  | Range: 0 - 100  The bigger the number, the higher the trust.    80 - 100: `High Trust`  60 - 79: `Medium Trust`  0 - 59: `Low Trust`  -1: means any async cache data has no result, can’t offer a score this time. Need wait [polling_interval] and request again. |
| risk_details     | Yes          | Details of risk  The definitions of those types of risks are below.  The return Json, shows the multiple aspects of the entity that have been validated and scored.  Each component has different types of weights in the security score. | Json     | See details below. All risk details should be listed regardless of their value. **(true or false)** |
| scanned_ts       | Yes          | Timestamp of audit, in seconds                               | Long     | `1654872331`                                                 |

### Sync/Async Response

#### Synchronous Response (returned when provider has a cached result)

- has_result: **true**
- address_type: **non-null**
- trust_score: **non-null**
- risk_details: **non-null**
- scanned_ts: **non-null**
- polling_interval: null

#### Asynchronous Response (returned when provider has to calculate result)

- has_result: **false**
- polling_interval: **non_null**
- scanned_ts: **non-null**
- address_type: null
- trust_score: null
- risk_details: null

### Risk_details

The risk_details will be composed of an array of objects, the object contains the following fields

- name : name of the check.
- value: check result
- risk_level: indicates the level of risk (LOW_TRUST, MEDIUM_TRUST, HIGH_TRUST, BASE_INFO, LOW_RISK, MEDIUM_RISK, HIGH_RISK)
- risk_desc: a short description for each detail

**Example:**

```json
{
  "status": "OK",
  "code": "000000000",
  "data": {
    "risk_details": [
      {
        "name": "is_open_source",
        "value": "true",
        "risk_level": "HIGH_RISK",
        "risk_desc": "Un-open-sourced contracts may hide various unknown mechanisms and are extremely risky."
      },
      {
        "name": "hidden_owner",
        "value": "true",
        "risk_level": "MEDIUM_RISK",
        "risk_desc": "The ability to hide the ownership of a contract can be used to manipulate the blockchain data."
      }
    ]
  }
}
```
