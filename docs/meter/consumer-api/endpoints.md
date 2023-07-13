---
title: Endpoints
sidebar_position: 2
---

# Endpoints

## Address security[](https://www.avengerdao.org/docs/meter/consumer-api/Endpoints#address-security)

Method: `POST`

URL: `https://avengerdao.org/api/v1/address-security`

### Request parameters[](https://www.avengerdao.org/docs/meter/consumer-api/Endpoints#request-parameters)

| **Name**                  | **Required** | **Description**                                              | **Type**     | **Example**                                |
| ------------------------- | ------------ | ------------------------------------------------------------ | ------------ | ------------------------------------------ |
| address                   | Yes          | Address needed to be scanned                                 | string       | 0xB8c77482e45F1F44dE1745F52C74426C631bDD52 |
| threshold                 | No           | The minimum **percentage** of valid provider responses required | double       | 70.0                                       |
| min_producers             | No           | The minimum **number** of valid provider responses required  | int          | 2                                          |
| selected_provider_list    | No           | Only return results from selected providers                  | string array | ["Hashdit","GoPlus"]                       |
| display_non_false_details | No           | Only return non-false risk details                           | boolean      | true                                       |

### Response[](https://www.avengerdao.org/docs/meter/consumer-api/Endpoints#response)

| **Name**   | **NotNull** | **Description**          | **Type** | **Example**                                                  |
| ---------- | ----------- | ------------------------ | -------- | ------------------------------------------------------------ |
| status     | Yes         | Result of operation      | string   | OK                                                           |
| code       | Yes         | Result code of operation | int      | `000000000`: success  `000001`: unknown server error occurred during detection  `000002`: Number of requests exceeded limit  `000003`: unknown appId  `000004`: X-Signature-signature header can't be null  `000005`: verify signature error  appid, timestamp, nonce, signature headers can not be null or emptynonce is illegaltimestamp has illegaltimestamp is expiredinvalid appidappid has expiredinvalid signaturereplay requestapp is out of count limit |
| error_data | No          | If code not 000000000    | string   | Risk Score calculation error!                                |
| data       | Yes         | Query Result             | json     | See "Data form"                                              |

#### Data[](https://www.avengerdao.org/docs/meter/consumer-api/Endpoints#data)

| **Name**          | **Required** | **Description**                                              | **Type**                           | **Example**                                                  |
| ----------------- | ------------ | ------------------------------------------------------------ | ---------------------------------- | ------------------------------------------------------------ |
| address           | Yes          | The scanned address                                          | String                             | 0xB8c77482e45F1F44dE1745F52C74426C631bDD52                   |
| address_type      | Yes          | Whether the address is an EOA account or Contract.  The `risk_detail` field below may vary depending on this field. | String                             | EOA  Contract  ERC20-TokenNFT…                               |
| trust_score       | Yes          | Likelihood and impact of the trust                           | Likelihood and impact of the trust | Range: 0 - 100  The bigger the number, the higher the trust. |
| risk_type_checked | Yes          | Type of the risk checked                                     | Json                               | ["basic information","permission control","code vulnerabilities","business logic vulnerabilities"] |
| sources           | Yes          | list of suppliers for risk_detail                            | Json(Array)                        | ["Certik","GoPlus"]                                          |
| trust_level       | Yes          | Verbal designation for likelihood and impact of the trust:  100: `Very High trust`  91 - 99: `High trust`  61 - 90: `Medium trust`  21 - 60: `Low trust`  0 - 20: `Very Low trust` | String                             | Low                                                          |
| band              | Yes          | Banding Rating System  5/5: `Very Low Risk`  4/5: `Low Risk`  3/5: `Medium Risk`  2/5: `High Risk`  1/5: `Significant Risk` | String                             | 3/5                                                          |
| polling_interval  | Yes          | Amount of time before another request for audit results can be sent. | Integer                            | 600                                                          |
| risk_details      | Yes          | Aggregated risk details                                      | Json                               | See details below. Only risky facts will be listed.          |
| scanned_ts        | Yes          | The last risk scan time of the address                       | Long                               | `1654872331`                                                 |
| new_address_type  | Yes          | more detailed `address_type`，in the future it will instead of `address_type` | String                             | EOA ERC20 ERC721 ERC1155 ERC4626                             |
| chain_id          | Yes          | The address chain id                                         | Integer                            | 56                                                           |
| provider_scores   | Yes          | The individual provider scores                               | Json                               | {"Hashdit":80,"GoPlus":75}                                   |

#### Risk_details[](https://www.avengerdao.org/docs/meter/consumer-api/Endpoints#risk_details)

The risk_details will comprise of an array of objects, the object contain the following fields

- name : name of the check.
- value: check result
- risk_type_checked : (Optional) a list of risk type that risk fact belongs to
- sources: a list of provider names
- risk_level: indicates the level of risk (LOW_TRUST, MEDIUM_TRUST, HIGH_TRUST, BASE_INFO, LOW_RISK, MEDIUM_RISK, HIGH_RISK)
- risk_desc: a short description for each detail

**E.g.:**

```json
{
  "risk_details": [
    {
      "name": "is_open_source",
      "value": "true",
      "risk_type_checked": [
        "basic information"
      ],
      "sources": ["GoPlus", "Hashdit"],
      "risk_level": "HIGH_RISK",
      "risk_desc": "Un-open-sourced contracts may hide various unknown mechanisms and are extremely risky."
    },
    {
      "name": "hidden_owner",
      "value": "true",
      "risk_type_checked": [
        "permission control"
      ],
      "sources": ["GoPlus", "Hashdit"],
      "risk_level": "MEDIUM_RISK",
      "risk_desc": "The ability to hide the ownership of a contract can be used to manipulate the blockchain data."
    }
  ]
}
```



## Security Providers[](https://www.avengerdao.org/docs/meter/consumer-api/Endpoints#security-providers)

Method: `GET`

URL: `https://avengerdao.org/api/v1/providers`

### Response[](https://www.avengerdao.org/docs/meter/consumer-api/Endpoints#response-1)

| **Name**   | **NotNull** | **Description**          | **Type**     | **Example**                                                  |
| ---------- | ----------- | ------------------------ | ------------ | ------------------------------------------------------------ |
| status     | Yes         | Result of operation      | string       | OK                                                           |
| code       | Yes         | Result code of operation | int          | `000000000`: success  `000001`: unknown server error occurred during detection  `000002`: Number of requests exceeded limit  `000003`: unknown appId  `000004`: X-Signature-signature header can't be null  `000005`: verify signature error |
| error_data | No          | If code not 000000000    | string       | Internal error!                                              |
| data       | Yes         | Query Result             | string array | [ "Hashdit", "GoPlus" ]                                      |

## Transaction-security[](https://www.avengerdao.org/docs/meter/consumer-api/Endpoints#transaction-security)

Method: `POST`

URL: `https://avengerdao.org/api/v1/transaction-security`

### Request parameters[](https://www.avengerdao.org/docs/meter/consumer-api/Endpoints#request-parameters-1)

| **Name**        | **Required** | **Description**                                              | **Type** | **Example**                                |
| --------------- | ------------ | ------------------------------------------------------------ | -------- | ------------------------------------------ |
| chain_id        | No           | Chain id ( Network ) of address.                             | int      | 56                                         |
| network         | Yes          | We currently support 4 networks: BTC, BSC, ETH, TRX          | string   | BSC                                        |
| src_address     | No           | Address of TW user initiating transaction                    | string   | 0x8c18f231ce0fc513987ec402a595409e6b394949 |
| dest_address    | Yes          | Address of counterparty                                      | string   | 0x8c18f231ce0fc513987ec402a595409e6b394949 |
| memo            | No           | Memo is an additional address feature necessary for identifying a transaction recipient beyond a wallet address | string   | memo                                       |
| token_code      | No           | Currency token code like BTC,ETH                             | string   | BTC                                        |
| token_amount    | No           | Transaction Amount for the token                             | double   | 1.2                                        |
| fiat_amount_usd | No           | Fiat amount in USD equivalent of token amount                | double   | 50                                         |
| request_detail  | No           | Nested Json , Address type(CA, EOA), DApps type(DeFi, NFT, Bridge. etc.), Operation Type(withdraw, deposit) | string   | JsonString                                 |
| ip_address      | No           | TW User IP address. IP Address of user initiating transaction. | string   | 192.2.150.236                              |
| device_id       | No           | Device ID of user initiating transaction. A device ID is a unique, anonymized string of numbers and letters that identifies every individual smartphone. | string   | 00000000-00000000-01234567-89ABCDEF        |

### Response[](https://www.avengerdao.org/docs/meter/consumer-api/Endpoints#response-2)

| **Name**   | **NotNull** | **Description**          | **Type** | **Example**                                                  |
| ---------- | ----------- | ------------------------ | -------- | ------------------------------------------------------------ |
| status     | Yes         | Result of operation      | string   | OK                                                           |
| code       | Yes         | Result code of operation | int      | `000000000`: success  `000001`: unknown server error occurred during detection  `000002`: Number of requests exceeded limit  `000003`: unknown appId  `000004`: X-Signature-signature header can't be null  `000005`: verify signature error  appid, timestamp, nonce, signature headers can not be null or emptynonce is illegaltimestamp has illegaltimestamp is expiredinvalid appidappid has expiredinvalid signaturereplay requestapp is out of count limit |
| error_data | No          | If code not 000000000    | string   | Transaction Risk Score calculation error !                   |
| data       | Yes         | Query Result             | json     | See "Data form"                                              |

#### Data[](https://www.avengerdao.org/docs/meter/consumer-api/Endpoints#data-1)

| **Name**      | **Required** | **Description**                                              | **Type** | **Example**                                                  |
| ------------- | ------------ | ------------------------------------------------------------ | -------- | ------------------------------------------------------------ |
| trace_id      | Yes          | unique trace_id                                              | String   | e7bb2eefc3a842368c3b74e1f686301d                             |
| risk_level    | Yes          | risk level of the transaction:  `HIGHLY_SUSPICIOUS`  `SUSPICIOUS`  `MLOW_RISK` | String   | HIGHLY_SUSPICIOUS                                            |
| remark        | No           | remark                                                       | String   | The target address in this transaction is either confirmed or highly likely to be involved in fraudulent activities |
| source_detail | No           | source details                                               | Json     | See details below.                                           |

#### SourceDetail[](https://www.avengerdao.org/docs/meter/consumer-api/Endpoints#sourcedetail)

| **Name**                  | **Required** | **Description**                                              | **Type** | **Example**        |
| ------------------------- | ------------ | ------------------------------------------------------------ | -------- | ------------------ |
| source                    | No           | risk source                                                  | String   | DS_GRAYLIST        |
| risk_level                | No           | risk level of the transaction:  `HIGHLY_SUSPICIOUS`  `SUSPICIOUS`  `MLOW_RISK` | String   | SUSPICIOUS         |
| category_sub_category_map | No           | category                                                     | Json     | See details below. |

**E.g.:**

```json
{
  "source_detail":[
    {
      "source":"DS_GRAYLIST",
      "category_sub_category_map":{
        "HACKER":[
          "RANSOMWARE",
          "PHISHING"
        ],
        "SCAM":[
          "FAKE_INVESTMENT",
          "JOB_SCAM"
        ]
      },
      "risk_level":"SUSPICIOUS"
    },
    {
      "source":"ROC_BLACKLIST",
      "category_sub_category_map":{
        "AML":[
          "AML"
        ]
      },
      "risk_level":"HIGHLY_SUSPICIOUS"
    }
  ]
}
```



#### RiskLevel[](https://www.avengerdao.org/docs/meter/consumer-api/Endpoints#risklevel)

| **Risk Level**    | **Implication**                                              | **Suggested Action**                       |
| ----------------- | ------------------------------------------------------------ | ------------------------------------------ |
| HIGHLY_SUSPICIOUS | The target address in this transaction is either confirmed or highly likely to be involved in fraudulent activities. | Pop out a strong WARNING message to user   |
| SUSPICIOUS        | The target address in this transaction is likely to be involved in fraudulent or other illicit activities. | Pop out a moderate WARNING message to user |
| LOW_RISK          | The target address in this transaction is currently not known to be involved in any illicit activities to the best of our knowledge. Please note there is still a chance that the illicit activities haven't been detected by us yet. | No intervention with users                 |

Note: the risk level of an individual address is subject to change along the time, while it does new activities and we collect new data around it.

#### Category[](https://www.avengerdao.org/docs/meter/consumer-api/Endpoints#category)

| **Risk_Category** | **Risk_Subcategory** | **Description**                                              |
| ----------------- | -------------------- | ------------------------------------------------------------ |
| SCAM              | FAKE_INVESTMENT      | Operations are from account owner due to investment scam     |
| SCAM              | FAKE_GIVEAWAY        | Operations are from account owner due to give away scam      |
| SCAM              | KNOWN_PERSON         | User scammed by a known person                               |
| SCAM              | FAKE_SUPPORT         | Someone claims they are Customer Support from a certain party to scam user |
| SCAM              | JOB_SCAM             | Scammer recommend job/income opportunity for victim but ask for additional fee for that |
| SCAM              | PONZI_SCHEME         | Scammer(group) introduce their fake service/product with multiple VIP user levels and ask victim to recommend more friends into Ponzi Scheme |
| SCAM              | SOCIAL_SCAM          | Victims claim that he got to know the scammer via a social communication platform. |
| SCAM              | OTHER_SCAM           | Common scam, can't be classified to the above sub_category.  |
| HACKER            | RANSOMWARE           | A type of malware that threatens to publish the victim's personal data or permanently block access to it unless a ransom is paid. |
| HACKER            | PHISHING             | User received phishing URL by SMS, email, etc.               |
| HACKER            | SEXTORTION           | Sexual exploitation in which threatened release of sexual images or information. |
| HACKER            | DARK_MARKET          | Malicious addresses from the dark market trading.            |
| HACKER            | OTHER_HACKER         | Taking another person's property without that person's permission, and can’t be classified to the above sub_category. |
| AML               | AML                  | Addresses reported for money laundering, gambling, related to criminal organization or terrorist organization etc |
| OTHER             | OTHER                | Can’t be categorized due to historical reasons               |

[
](https://www.avengerdao.org/docs/meter/consumer-api/Authorization)