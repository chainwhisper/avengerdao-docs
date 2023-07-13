---
title: Endpoints
---
# Endpoints

## 1.Subscribe

watch-bus subscribes to the provider for the address to be monitored

Method: `POST`

URL: `https://<domain>/api/watch/subscribe`

### Request body

| **Name**    | **Required** | **Type**           | **Description**                             | **Example** |
| ----------- | ------------ | ------------------ | ------------------------------------------- | ----------- |
| entity_list | Yes          | `List<EntityInfo>` | List of addresses that need to be monitored |             |

**EntityInfo:**

| Name        | Required | Type     | Description                                                  | Example                                                  |
| ----------- | -------- | -------- | ------------------------------------------------------------ | -------------------------------------------------------- |
| entity      | Yes      | `string` | code of an event that should be monitored                    | 0x9bd547446ea13c0c13df2c1885e1f5b019a77441               |
| chain_id    | Yes      | `int`    | chain id                                                     | 56                                                       |
| entity_type | Yes      | `string` | watch entity type                                            | ERC20,ERC721,ERC777,ERC1155,ERC4626,Universal,Unverified |
| event_code  | Yes      | `string` | code of an event that should be monitored. see here [Specification](../specification.md) | big_amount_txn                                           |

```json
[
  {
    "entity": "0x225982667df43a03922c5f64ccd3b24a00782ec3",
    "chain_id": "56",
    "entity_type": "ERC20", 
    "event_code": "big_amount_txn"
  },

  {
    "entity": "0xe9e7CEA3DedcA5984780Bafc599bD69ADd087D56",
    "chain_id": "56",
    "entity_type": "ERC20",
    "event_code": "big_amount_txn"
  }
]
```



### Response

| **Name** | **NotNull** | **Type** | **Description**          | **Example**                                                  |
| -------- | ----------- | -------- | ------------------------ | ------------------------------------------------------------ |
| status   | Yes         | `string` | Result of operation      | `OK`：The scanning process terminated as expected  `ERROR`：Exception thrown or unexpected situation met |
| code     | Yes         | `int`    | Result code of operation | `000000000`: success  `000001`: unknown server error occurred during detection  `000002`: Number of requests exceeded limit  `000003`: unknown appId  `000004`: X-Signature-signature header can't be null  `000005`: verify signature error  appid, timestamp, nonce, signature headers can not be null or emptynonce is illegaltimestamp has illegaltimestamp is expiredinvalid appidappid has expiredinvalid signaturereplay requestapp is out of count limit |
| data     | Yes         | `json`   | Query result             | See Data form                                                |

**Data:**

| Name         | NotNull | Type               | Description                           | Example |
| ------------ | ------- | ------------------ | ------------------------------------- | ------- |
| watch_result | Yes     | `List<EntityInfo>` | return success watch_entity (address) |         |

**EntityInfo:**

| Name        | Required | Type     | Description                                | Example                                                  |
| ----------- | -------- | -------- | ------------------------------------------ | -------------------------------------------------------- |
| entity      | Yes      | `string` | code of an event that should be monitored  | 0x9bd547446ea13c0c13df2c1885e1f5b019a77441               |
| chain_id    | Yes      | `int`    | chain id                                   | 56                                                       |
| entity_type | Yes      | `string` | watch entity type                          | ERC20,ERC721,ERC777,ERC1155,ERC4626,Universal,Unverified |
| event_code  | Yes      | `string` | code of an event that should be monitored. | big_amount_txn                                           |

```json
{
  "code": "000000000",
  "status": "OK",
  "data": {
    "watch_result": [{
      "entity": "0x225982667df43a03922c5f64ccd3b24a00782ec3",
      "chain_id": "56",
      "entity_type": "ERC20",
      "event_code": "big_amount_txn"
      },
      {
        "entity": "0xe9e7CEA3DedcA5984780Bafc599bD69ADd087D56",
        "chain_id": "56",
        "entity_type": "ERC20",
        "event_code": "big_amount_txn"
      }
    ]
  }
}
```



## 2.Unsubscribe

watch-bus unsubscribes from provider

Method: `POST`

URL: `https://<domain>/api/v1/watch/unsubscribe`

### Request body

| **Name**    | **Required** | **Type**           | **Description**                             | **Example** |
| ----------- | ------------ | ------------------ | ------------------------------------------- | ----------- |
| entity_list | Yes          | `List<EntityInfo>` | List of addresses that need to be monitored |             |

### Response

| **Name** | **NotNull** | **Description**          | **Type** | **Example**                                                  |
| -------- | ----------- | ------------------------ | -------- | ------------------------------------------------------------ |
| status   | Yes         | Result of operation      | `string` | `OK`：The scanning process terminated as expected  `ERROR`：Exception thrown or unexpected situation met |
| code     | Yes         | Result code of operation | `int`    | `000000000`: success                                         |
| data     | Yes         | Query Result             | `json`   | See Data form                                                |

**Data:**

| Name         | NotNull | Type               | Description                           | Example |
| ------------ | ------- | ------------------ | ------------------------------------- | ------- |
| watch_result | Yes     | `List<EntityInfo>` | return success watch_entity (address) |         |

## 3.List subscriptions

watch-bus requests the subscribed address information from the provider

Method: `POST`

URL: `https://<domain>/api/watch/subscriptions/list`

### Request body

| Name        | Required | Type           | Description                                                  | Example                                                      |
| ----------- | -------- | -------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| entity_list | No       | `List<String>` | List of addresses that need to be monitored; entity_list is allowed to be empty, when entity_list=empty, all subscribed address information needs to be returned | [“0x9bd547446ea13c0c13df2c1885e1f5b019a77441”, “0x8315177ab297ba92a06054ce80a67ed4dbd7ed3a”] |
| page_index  | No       | `Integer`      | When the number is large, it will be processed by paging, and the page number needs to be set. | Defaults 1                                                   |
| page_size   | No       | `Integer`      | When the number is large, it will be processed by paging, and the page number needs to be set. | Defaults 50， max 50                                         |

### Response

| **Name** | **NotNull** | **Description**          | **Type** | **Example**                                                  |
| -------- | ----------- | ------------------------ | -------- | ------------------------------------------------------------ |
| status   | Yes         | Result of operation      | `string` | `OK`：The scanning process terminated as expected  `ERROR`：Exception thrown or unexpected situation met |
| code     | Yes         | Result code of operation | `int`    |                                                              |
| data     | Yes         | Query Result             | `json`   | See Data form                                                |

**Data:**

| Name              | NotNull | Type                 | Description                                       | Example                 |
| ----------------- | ------- | -------------------- | ------------------------------------------------- | ----------------------- |
| subscription_list | Yes     | `List<Subscription>` | Whether a result of subscription is true or false | See “Subscription” form |
| page_index        | Yes     | `Integer`            | current page number                               | 1                       |
| page_size         | Yes     | `Integer`            | page size                                         | 50                      |
| total             | Yes     | `Integer`            | total number of records                           | 10                      |

**Subscription:**

| Name             | NotNull | Type               | Description                  | Example                                    |
| ---------------- | ------- | ------------------ | ---------------------------- | ------------------------------------------ |
| watch_entity     | Yes     | `String`           | addresses that was monitored | 0x9bd547446ea13c0c13df2c1885e1f5b019a77441 |
| watch_event_list | Yes     | `List<WatchEvent>` |                              |                                            |

**WatchEvent:**

| Name       | NotNull | Type     | Description                                                  | Example        |
| ---------- | ------- | -------- | ------------------------------------------------------------ | -------------- |
| watch_id   | Yes     | `String` | Id of an event which is monitored, refers to a specific subscription object, expect to use watch_id to query all relevant information of a certain subscription, such as the creation time of the subscription, the address of the subscription ,etc. | 123            |
| event_code | Yes     | `String` | code of an event that should be monitored                    | big_amount_txn |

## 4. Watch Events

Get the list of events supported by the provider

Method: POST

URL: `https://<domain>/api/watch/event/list`

### Request body

**empty**

### Response

| **Name** | **NotNull** | **Description**          | **Type**             | **Example**                                                  |
| -------- | ----------- | ------------------------ | -------------------- | ------------------------------------------------------------ |
| status   | Yes         | Result of operation      | `string`             | `OK`：The scanning process terminated as expected  `ERROR`：Exception thrown or unexpected situation met |
| code     | Yes         | Result code of operation | `int`                |                                                              |
| data     | Yes         | Query Result             | `List<SupportEvent>` | See SupportEvent form                                        |

**SupportEvent:**

| **Name**                 | **NotNull** | **Description**       | **Type**                                                     | **Example**                                                  |
| ------------------------ | ----------- | --------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| event_code               | Yes         | `string`              | code of an event that should be monitored                    | big_amount_txn                                               |
| support_entity_type_list | Yes         | `JSON` `List<String>` | watch entity type                                            | ["EOA","ERC20","ERC721","ERC1155","UNIVERSAL"] **UNIVERSAL**: no ERC CA , Dapp |
| mini_threshold           | Yes         | `string`              | Minimum threshold to trigger an alarm                        | 0.005                                                        |
| trigger_frequency        | No          | `string`              | Notification timeliness, when an event occurs, how soon can the watch-bus be notified, such as within 1 minute after the event occurs, or within 1 hour | Minutes (blocks)                                             |
| event_description        | No          | `string`              | event description                                            | large amount transfers                                       |

## 5.Alert (provider callback watch-bus, recommend to use ws protocol)

Provider sends real-time alarm information to watch-bus

**Method:** `POST` *websocket will be used for integration.*

**URL:** `https://www.avengerdao.org/api/v1/watch/alert` *(provided by watch bus)*

**Authorization:** reference [Authorization](https://www.avengerdao.org/docs/meter/consumer-api/Authorization)

### Request body

| **Name**        | **Required** | **Type**          | **Description** | **Example** |
| --------------- | ------------ | ----------------- | --------------- | ----------- |
| alert_info_list | Yes          | `List<AlertInfo>` | List of alert   |             |

**AlertInfo:**

| Name              | Required | Type     | Description                               | Example                                                  |
| ----------------- | -------- | -------- | ----------------------------------------- | -------------------------------------------------------- |
| watch_entity      | Yes      | `string` | code of an event that should be monitored | 0x9bd547446ea13c0c13df2c1885e1f5b019a77441               |
| chain_id          | Yes      | `String` | chain id                                  | 56                                                       |
| watch_entity_type | Yes      | `string` | watch entity type                         | ERC20,ERC721,ERC777,ERC1155,ERC4626,Universal,Unverified |
| watch_event_code  | Yes      | `string` | code of an event that should be monitored | big_amount_txn                                           |
| timestamp         | Yes      | `long`   | Timestamp of the alarm, unix time, Second | 1678956256                                               |
| event_values      | Yes      | `Map`    | Details of the event                      | see EventValues Map                                      |

**EventValues Map:**

map format, the content of each event is different, here is an example of trust_score_decrease

| Name          | Required | Type     | Description                          | Example    |
| ------------- | -------- | -------- | ------------------------------------ | ---------- |
| last_value    | Yes      | `string` | last value                           | 95         |
| last_ts       | Yes      | `string` | last value timestamp                 | 1665391590 |
| current_value | Yes      | `string` | curruent value                       | 60         |
| delta_value   | Yes      | `string` | delta value greate than some value   | 35         |
| delta_percent | Yes      | `string` | delta percent greate than some value | 0.3684     |
| comment       | No       | `string` |                                      |            |

```json
[
  {
  "chain_id": "56",
  "watch_entity_type":"ERC20",
  "address": "0x171C3688e1aB772e7178F19481dc8F8030F76fC9",
  "timestamp": 1665395590,
  "watch_event_code": "trust_score_decrease",
  "event_values": {
    "last_value": "95",
    "last_ts": "1665391590",
    "current_value": "60",
    "delta_value": "35",
    "delta_percent": "0.3684",
    "comment": "some comments"
   }
  },
  
  {
    "chain_id": "56",
    "watch_entity_type":"ERC20",
    "address": "0xbb4CdB9CBd36B01bD1cBaEBF2De08d9173bc095c",
    "timestamp": 1665395590,
    "watch_event_code": "trust_score_decrease",
    "event_values": {
      "last_value": "99",
      "last_ts": "1665391590",
      "current_value": "98",
      "delta_value": "1",
      "delta_percent": "0.01",
      "comment": "some comments"
    }
  }
]
```