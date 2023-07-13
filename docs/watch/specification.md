---
title: Specification
sidebar_position: 4
---

# Specification

The events currently supported by watch-bus, and it is still being added continuously.

| **Classification** | **event**              | **event content**                                           | **EOA** | **ERC20** | **ERC721** | **UNIVERSAL** | **threshold gradient** | **Trigger frequency** | **Event description**                                        | **severity**                                                 |
| ------------------ | ---------------------- | ----------------------------------------------------------- | ------- | --------- | ---------- | ------------- | ---------------------- | --------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| transaction        | big_amount_txn         | block_number, tx_hash, **current_value**, comment           |         | ✓         |            |               | 1,000 USD              | Minutes (blocks)      | large amount transfer **current_value** : the value of this transfer | LOW: current_value_gt:1000000 MEDIUM: current_value_gt:100000 HIGH: current_value_gt:1000 |
|                    | big_amount_txn_percent | cmc_slug, block_number, tx_hash, **current_value**, comment |         | ✓         |            |               | 0.01                   | Minutes (blocks)      | The proportion of large-scale transfers in the total supply **current_value** : The ratio of the value of this transfer to the total supply **total_supply** : The total supply of money, each token has a total supply, the currency can be continuously issued, or continuously deflated and destroyed, but each moment will have a total supply at that time | LOW: current_value_gt:0.2 MEDIUM: current_value_gt:0.05 HIGH: current_value_gt:0.01 |
|                    | big_amount_txn_usd     | cmc_slug, block_number, tx_hash, **current_value**, comment |         | ✓         |            |               | 100 USD                | hour level            | Large-value transfers (in USD)                               | LOW: current_value_gt:500000 MEDIUM: current_value_gt:100000 HIGH: current_value_gt:10000 |
| contract           | risk_function_call     | block_number, tx_hash, **current_value**, comment           |         | ✓         | ✓          | ✓             | 0                      | Minutes (blocks)      | Call a high-risk function **current_value**： function_sig If you set current_value=0, it means that any function call will trigger the threshold, otherwise only when current_value=function_sig, the alarm will be triggered "function_sig": "transfer(address,uint256)" | LOW: current_value_eq:0 MEDIUM: current_value_eq: 0 HIGH:current_value_eq: 0 |
|                    | abnormal_function_call | block_number, tx_hash, **current_value**, comment           |         | ✓         | ✓          | ✓             | 0                      | Minutes (blocks)      | function call exception **current_value**： function_sig If you set current_value=0, it means that any function call will trigger the threshold, otherwise only when current_value=function_sig, the alarm will be triggered "function_sig": "transfer(address,uint256)" | LOW: current_value_eq:0 MEDIUM: current_value_eq: 0 HIGH:current_value_eq: 0 |

**UNIVERSAL** : no ERC CA , Dapp