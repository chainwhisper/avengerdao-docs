# Endpoints

## 1.Subscribe

Method: `POST`

URL: `https://<domain>/api/v1/watch/subscribe`

### Request body

| **Name**          | **Required** | **Type**       | **Description**                                              | **Example**                                                  |
| ----------------- | ------------ | -------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| watch_entity_list | Yes          | `List<String>` | List of addresses that need to be monitored                  | [“0x9bd547446ea13c0c13df2c1885e1f5b019a77441”, “0x8315177ab297ba92a06054ce80a67ed4dbd7ed3a”] |
| watch_event_code  | Yes          | `String`       | code of an event that should be monitored . see here [Specification](../specification.md) | big_amount_txn                                               |
| threshold_config  | Yes          | `JSON` `Map`   | Configuration that should be used to filter alerts related to the particular event. | {"severity”: "LOW"} or {"current_value_gt": "60","current_value_lt": "20","current_value_eq": "10","delta_value": "10","delta_percent": "0.3"} Severity will also be stored on watch side. **current_value_gt** : When the event content contains the current_value field, and current_value > current_value_gt, an alarm notification is triggered **current_value_lt** : When the event content contains the current_value field, and current_value < current_value_lt, an alarm notification is triggered **current_value_eq** : When the event content contains the current_value field, and current_value == current_value_eq, an alarm notification is triggered **delta_value** : When the event content contains the delta_value field, and delta_value >= delta_value, an alarm notification is triggered **delta_percent** : When the event content contains the delta_percent field, and delta_percent >= delta_percent, an alarm notification is triggered |
| notify_config     | Yes          | `JSON` `Map`   | Defines what endpoint should be used to receive alerts and with what value. Currently only webhook is supported. | {"webhook": " [http://test.test](http://test.test/) "}       |

### Response

| **Name** | **NotNull** | **Description**          | **Type** | **Example**                                                  |
| -------- | ----------- | ------------------------ | -------- | ------------------------------------------------------------ |
| status   | Yes         | Result of operation      | `string` | `OK`：The scanning process terminated as expected  `ERROR`：Exception thrown or unexpected situation met |
| code     | Yes         | Result code of operation | `int`    | `000000000`: success  `000001`: unknown server error occurred during detection  `000002`: Number of requests exceeded limit  `000003`: unknown appId  `000004`: X-Signature-signature header can't be null  `000005`: verify signature error  appid, timestamp, nonce, signature headers can not be null or emptynonce is illegaltimestamp has illegaltimestamp is expiredinvalid appidappid has expiredinvalid signaturereplay requestapp is out of count limit |
| data     | Yes         | Query Result             | `json`   | See [Data](https://www.avengerdao.org/docs/watch/consumer-api/Endpoints#data) form |

**Data:**

| Name         | NotNull | Type | Description                                                  | Example                                                      |
| ------------ | ------- | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| watch_result | Yes     | Map  | Whether a result Map of subscription **key**-watch_entity (address) **value**-provider_watch_id(When the monitoring is successful, the unique identification code of the monitoring; if Failed, fill in a blank string, or null) | {"0x9bd547446ea13c0c13df2c1885e1f5b019a77441":"abc12345", "0x8315177ab297ba92a06054ce80a67ed4dbd7ed3a":"zxc456", "0x66666177ab297ba92a06054ce80a67ed4dbdffcc":"" } |

## 2.Unsubscribe

Method: `POST`

URL: `https://<domain>/api/v1/watch/unsubscribe`

### Request body

| **Name**                      | **Required** | **Type**       | **Description**                                  | **Example**                                                  |
| ----------------------------- | ------------ | -------------- | ------------------------------------------------ | ------------------------------------------------------------ |
| watch_id_list                 | Yes          | `List<String>` | the unique identification code of the monitoring | [“642272312405626880”, “642272312405626881”] **You can fill in one of watch_id_list and watch_entity_list. If both are filled in, watch_id_list is the main one, and watch_entity_list is ignored.** |
| watch_entity_list (addresses) | Yes          | `List<String>` | addresses that need to be monitored              | [“0x9bd547446ea13c0c13df2c1885e1f5b019a77441”, “0x8315177ab297ba92a06054ce80a67ed4dbd7ed3a”] **You can fill in one of watch_id_list and watch_entity_list. If both are filled in, watch_id_list is the main one, and watch_entity_list is ignored.** |
| watch_event_code              | No           | `String`       | code of an event that should be monitored        | big_amount_txn                                               |

### Response

| **Name** | **NotNull** | **Description**          | **Type** | **Example**                                                  |
| -------- | ----------- | ------------------------ | -------- | ------------------------------------------------------------ |
| status   | Yes         | Result of operation      | `string` | `OK`：The scanning process terminated as expected  `ERROR`：Exception thrown or unexpected situation met |
| code     | Yes         | Result code of operation | `int`    | `000000000`: success  `000001`: unknown server error occurred during detection  `000002`: Number of requests exceeded limit  `000003`: unknown appId  `000004`: X-Signature-signature header can't be null  `000005`: verify signature error  appid, timestamp, nonce, signature headers can not be null or emptynonce is illegaltimestamp has illegaltimestamp is expiredinvalid appidappid has expiredinvalid signaturereplay requestapp is out of count limit |
| data     | Yes         | Query Result             | `json`   | See [Data](https://www.avengerdao.org/docs/watch/consumer-api/Endpoints#data-1) form |

**Data:**

| Name                | NotNull | Type | Description                                                  | Example                                                      |
| ------------------- | ------- | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| watch_id_result     | Yes     | Map  | Whether a result Map of subscription **key**-watch_id **value**-SUCCESS / FAIL / NOT_FOUND | { "642272315572326400": "NOT_FOUND" }                        |
| watch_entity_result | Yes     | Map  | Whether a result Map of subscription **key**-watch_entity (address) **value**-SUCCESS / FAIL / NOT_FOUND | { "0x9bd547446ea13c0c13df2c1885e1f5b019a77441": "NOT_FOUND" } |

## 3.List Subscriptions

Method: `POST`

URL: `https://<domain>/api/v1/watch/subscriptions/list`

### Request body

| Name              | Required | Type           | Description                                                  | Example                                                      |
| ----------------- | -------- | -------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| watch_entity_list | No       | `List<String>` | List of addresses that need to be monitored                  | [“0x9bd547446ea13c0c13df2c1885e1f5b019a77441”, “0x8315177ab297ba92a06054ce80a67ed4dbd7ed3a”] |
| page_index        | No       | `Integer`      | When the number is large, it will be processed by paging, and the page number needs to be set. | Defaults 1                                                   |
| page_size         | No       | `Integer`      | When the number is large, it will be processed by paging, and the page number needs to be set. | Defaults 50， max 50                                         |

### Response

| **Name** | **NotNull** | **Description**          | **Type** | **Example**                                                  |
| -------- | ----------- | ------------------------ | -------- | ------------------------------------------------------------ |
| status   | Yes         | Result of operation      | `string` | `OK`：The scanning process terminated as expected  `ERROR`：Exception thrown or unexpected situation met |
| code     | Yes         | Result code of operation | `int`    | `000000000`: success  `000001`: unknown server error occurred during detection  `000002`: Number of requests exceeded limit  `000003`: unknown appId  `000004`: X-Signature-signature header can't be null  `000005`: verify signature error  appid, timestamp, nonce, signature headers can not be null or emptynonce is illegaltimestamp has illegaltimestamp is expiredinvalid appidappid has expiredinvalid signaturereplay requestapp is out of count limit |
| data     | Yes         | Query Result             | `json`   | See [Data](/watch/consumer-api/Endpoints#data-2) form |

**Data:**

| Name              | NotNull | Description                                       | Type                 | Example                 |
| ----------------- | ------- | ------------------------------------------------- | -------------------- | ----------------------- |
| subscription_list | Yes     | Whether a result of subscription is true or false | `List<Subscription>` | See “Subscription” form |
| page_index        | Yes     |                                                   | `Long`               |                         |
| page_size         | Yes     |                                                   | `Long`               |                         |
| total             | Yes     |                                                   | `Long`               |                         |

**Subscription:**

| Name             | NotNull | Description                  | Type               | Example                                    |
| ---------------- | ------- | ---------------------------- | ------------------ | ------------------------------------------ |
| watch_entity     | Yes     | addresses that was monitored | `String`           | 0x9bd547446ea13c0c13df2c1885e1f5b019a77441 |
| watch_event_list | Yes     |                              | `List<WatchEvent>` |                                            |

**WatchEvent:**

| Name                 | NotNull | Description                                                  | Type                          | Example                   |
| -------------------- | ------- | ------------------------------------------------------------ | ----------------------------- | ------------------------- |
| watch_event_code     | Yes     | code of an event that should be monitored                    | `String`                      | big_amount_txn            |
| provider_list        | No      | privoder list if list is empty,means that the subscription is still being processed and has not yet taken effect | `JSON` `List<String>`         | Hashdit                   |
| watch_threshold_list | Yes     | Subscription threshold, the smallest subscription unit       | `JSON` `List<WatchThreshold>` | See “WatchThreshold” form |

**WatchThreshold:**

| Name             | NotNull | Description                                                  | Type                  | Example                                                      |
| ---------------- | ------- | ------------------------------------------------------------ | --------------------- | ------------------------------------------------------------ |
| watch_id         | Yes     | Id of an event which is monitored.                           | `String`              | 123                                                          |
| watch_event_code | Yes     | code of an event that should be monitored                    | `String`              | big_amount_txn                                               |
| provider_list    | No      | privoder list if list is empty,means that the subscription is still being processed and has not yet taken effect | `JSON` `List<String>` | Hashdit                                                      |
| threshold_config | Yes     | Configuration that should be used to filter alerts related to the particular event. | `JSON` `Map`          | {"severity”: "LOW"} or {"currentValueGt": "60","currentValueLt": "20","deltaValue": "10","deltaPercent": "30%"} |
| notify_config    | Yes     | Defines what endpoint should be used to receive alerts and with what value. Currently only webhook is supported. | `JSON` `Map`          | {"webhook": " [http://test.test](http://test.test/) "}       |

## 4.Watch Events

Method: `POST`

URL: `https://<domain>/api/v1/watch/event/list`

### Request body

*Empty*

### Response

| **Name** | **NotNull** | **Description**          | **Type**             | **Example**                                                  |
| -------- | ----------- | ------------------------ | -------------------- | ------------------------------------------------------------ |
| status   | Yes         | Result of operation      | `string`             | `OK`：The scanning process terminated as expected  `ERROR`：Exception thrown or unexpected situation met |
| code     | Yes         | Result code of operation | `int`                | `000000000`: success  `000001`: unknown server error occurred during detection  `000002`: Number of requests exceeded limit  `000003`: unknown appId  `000004`: X-Signature-signature header can't be null  `000005`: verify signature error  appid, timestamp, nonce, signature headers can not be null or emptynonce is illegaltimestamp has illegaltimestamp is expiredinvalid appidappid has expiredinvalid signaturereplay requestapp is out of count limit |
| data     | Yes         | Query result             | `List<SupportEvent>` | See “SupportEvent” form                                      |

**SupportEvent:**

| Name                     | NotNull | Description                                                  | Type                  | Example                                                      |
| ------------------------ | ------- | ------------------------------------------------------------ | --------------------- | ------------------------------------------------------------ |
| watch_event_code         | Yes     | code of an event that should be monitored                    | `string`              | big_amount_txn                                               |
| support_entity_type_list | Yes     | watch entity type                                            | `JSON` `List<String>` | ["EOA","ERC20","ERC721","ERC1155","UNIVERSAL"] **UNIVERSAL**: no ERC CA , Dapp |
| mini_threshold           | Yes     | Minimum threshold to trigger an alarm                        | `string`              | 0.005                                                        |
| severity_config          | Yes     | The default monitoring level and the corresponding trigger threshold | `JSON` `Map`          | {"HIGH":{"delta_percent":"0.05"}, "MEDIUM":{"delta_percent":"0.2"}, "LOW":{"delta_percent":"0.5"}} |
| trigger_frequency        | Yes     | Alarm trigger frequency                                      | `string`              | Minutes (blocks)                                             |
| event_description        | No      | event description                                            | `string`              | large amount transfers                                       |

## 5.webhook callback[](https://www.avengerdao.org/docs/watch/consumer-api/Endpoints#5webhook-callback)

Method: `POST`

URL: `webhook url provided by user`

### Request body[](https://www.avengerdao.org/docs/watch/consumer-api/Endpoints#request-body-4)

| **Name**         | **Required** | **Type** | **Description**                                              | **Example**                                              |
| ---------------- | ------------ | -------- | ------------------------------------------------------------ | -------------------------------------------------------- |
| sources          | Yes          | `string` | Alarm Information Provider                                   | Hashdit                                                  |
| watchThresholdId | Yes          | `string` | The unique number of the subscription record used to identify which subscription the alert came from | 657425636074508288                                       |
| watchEntity      | Yes          | `string` | code of an event that should be monitored                    | 0x9bd547446ea13c0c13df2c1885e1f5b019a77441               |
| thresholdConfig  | Yes          | `string` | The threshold configuration of subscription records is used to compare whether the alarm content meets expectations | "{\"severity\":\"LOW\"}"                                 |
| chainId          | Yes          | `String` | chain id                                                     | 56                                                       |
| watchEntityType  | Yes          | `string` | watch entity type                                            | ERC20,ERC721,ERC777,ERC1155,ERC4626,Universal,Unverified |
| watchEventCode   | Yes          | `string` | code of an event that should be monitored                    | big_amount_txn                                           |
| timestamp        | Yes          | `string` | Timestamp of the alarm, unix time, Second                    | 1678956256                                               |
| eventValues      | Yes          | `Map`    | Details of the event                                         | see EventValues Map                                      |

**EventValues Map:**

map format, the content of each event is different, here is an example of trust_score_decrease

| Name         | Required | Type     | Description                                      | Example                                                      |
| ------------ | -------- | -------- | ------------------------------------------------ | ------------------------------------------------------------ |
| blockNumber  | Yes      | `string` | The height of the block where the event occurred | 95                                                           |
| cmcSlug      | Yes      | `string` |                                                  |                                                              |
| comment      | Yes      | `string` |                                                  |                                                              |
| txHash       | Yes      | `string` | The transaction hash of the alarm event          | 0x9b4e6239dba9121600eedd8cf1a789d56a53b016843918d3704a31afa3761971 |
| currentValue | Yes      | `string` | the value of this transfer                       | 0.3684                                                       |

```json
{
  "sources": "Hashdit",
  "watchThresholdId": "657425636074508288",
  "chainId": "56",
  "watchEntity": "0x0e09fabb73bd3ade0a17ecc321fd13a19e81ce82",
  "watchEntityType": "ERC20",
  "watchEventCode": "big_amount_txn_usd",
  "thresholdConfig": "{\"severity\":\"LOW\"}",
  "timestamp": "1673886407",
  "eventValues": {
    "blockNumber": "24840581",
    "cmcSlug": "pancakeswap",
    "comment": "",
    "txHash": "0x9b4e6239dba9121600eedd8cf1a789d56a53b016843918d3704a31afa3761971",
    "currentValue": "373.26463078223327"
  }
}
```



## 6.Query Alerts[](https://www.avengerdao.org/docs/watch/consumer-api/Endpoints#6query-alerts)

Method: `POST`

URL: `https://<domain>/api/v1/watch/alert/list`

### Request body[](https://www.avengerdao.org/docs/watch/consumer-api/Endpoints#request-body-5)

| **Name**           | **Required** | **Type** | **Description**                                              | **Example**                                                  |
| ------------------ | ------------ | -------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| id                 | No           | `string` | alert id                                                     | 123                                                          |
| watch_entity_value | No           | `string` | subscription addresses                                       | [0xee226379db83cffc681495730c11fdde79ba4c0c](https://bscscan.com/address/0xee226379db83cffc681495730c11fdde79ba4c0c)  0x4dbd4fc535ac27206064b68ffcf827b0a60bab3f  ... |
| watch_event_code   | No           | `string` | watch event type                                             | ERC20,ERC721,ERC777,ERC1155,ERC4626,Universal,Unverified     |
| start_time         | No           | `long`   | Start date for query                                         | 1661371200000                                                |
| end_time           | No           | `long`   | End date for query                                           | 1661630400000                                                |
| page_index         | No           | `int`    | When the number is large, it will be processed by paging, and the page number needs to be set. | Defaults 1                                                   |
| page_size          | No           | `int`    | When the number is large, it will be processed by paging, and the page number needs to be set. | Defaults 50 max 50                                           |

### Response[](https://www.avengerdao.org/docs/watch/consumer-api/Endpoints#response-4)

| **Name** | **NotNull** | **Description**          | **Type** | **Example**                                                  |
| -------- | ----------- | ------------------------ | -------- | ------------------------------------------------------------ |
| status   | Yes         | Result of operation      | `string` | `OK`：The scanning process terminated as expected  `ERROR`：Exception thrown or unexpected situation met |
| code     | Yes         | Result code of operation | `int`    | `000000000`: success  `000001`: unknown server error occurred during detection  `000002`: Number of requests exceeded limit  `000003`: unknown appId  `000004`: X-Signature-signature header can't be null  `000005`: verify signature error  appid, timestamp, nonce, signature headers can not be null or emptynonce is illegaltimestamp has illegaltimestamp is expiredinvalid appidappid has expiredinvalid signaturereplay requestapp is out of count limit |
| data     | Yes         | Query result             | `json`   | See “data” form                                              |

**Data:**

| Name       | NotNull | Type              | Description     | Example              |
| ---------- | ------- | ----------------- | --------------- | -------------------- |
| alert_list | Yes     | `List<AlertInfo>` | alert info list | See “AlertInfo” form |
| page_index | Yes     | `Long`            |                 |                      |
| page_size  | Yes     | `Long`            |                 |                      |
| total      | Yes     | `Long`            |                 |                      |

**AlertInfo:**

| Name               | NotNull | Type     | Description                               | Example                                    |
| ------------------ | ------- | -------- | ----------------------------------------- | ------------------------------------------ |
| id                 | Yes     | `Long`   | alert id                                  | 123                                        |
| watch_id           | Yes     | `String` | Id of an event which is monitored.        | 123                                        |
| watch_entity_value | Yes     | `String` | addresses that was monitored              | 0x9bd547446ea13c0c13df2c1885e1f5b019a77441 |
| watch_event_code   | Yes     | `String` | code of an event that should be monitored | big_amount_txn                             |
| notify_content     | Yes     | `String` | notification content                      |                                            |
| notify_status      | Yes     | `String` | notification status                       | INIT/SUCCESS/FAILED                        |
| notify_type        | Yes     | `String` | notification type                         | webhook                                    |
| notify_url         | Yes     | `String` | notification url                          | [http://test.test](http://test.test/)      |
| error_msg          | No      | `String` | Prompt message when notification fails    |                                            |
| alert_time         | Yes     | `Long`   | alert time;Unix timestamp                 | 1661371200000                              |