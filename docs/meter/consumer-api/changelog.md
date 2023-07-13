---
sidebar_position: 4
---

# Consumer Change Log

## 04/25/2023

| **Change**                                                   | **Description**                                              | **Location**                                                 | **Type**        |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | --------------- |
| Added 'provider_scores' field in address-security response   | The individual provider scores have been added to the data response object of the address-security endpoint. | [risk_detail object](https://www.avengerdao.org/docs/meter/consumer-api/Endpoints#data) | Additive change |
| Added 'display_non_false_details' field in address-security response | A flag for filtering non-false risk details been added to the address-security request endpoint. | [request](https://www.avengerdao.org/docs/meter/consumer-api/Endpoints#request-parameters) | Additive change |

## 04/04/2023

| **Change**                                          | **Description**                                              | **Location**                                                 | **Type**        |
| --------------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | --------------- |
| Added 'chain_id' field in address-security response | The chain id field has been added to the data response object of the address-security endpoint. | [risk_detail object](https://www.avengerdao.org/docs/meter/consumer-api/Endpoints#data) | Additive change |

## 03/31/2023

| **Change**                                                  | **Description**                                              | **Location**                                                 | **Type**        |
| ----------------------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | --------------- |
| Added 'new_address_type' field in address-security response | The new_address_type field has been added to the data response object of the address-security endpoint. | [address-security response](https://www.avengerdao.org/docs/meter/consumer-api/Endpoints#data) | Additive change |
| Added 'transaction-security' api                            | The api is for blacklist address enquiry by leveraging the existing blacklist database. | [transaction-security](https://www.avengerdao.org/docs/meter/consumer-api/Endpoints#Transaction-security) | Additive change |

## 03/13/2023

| **Change**                                            | **Description**                                              | **Location**                                                 | **Type**                                 |
| ----------------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ---------------------------------------- |
| Added 'risk_level' field in address-security response | The risk level field has been added to the risk_detail response object of the address-security endpoint. | [risk_detail object](https://www.avengerdao.org/docs/meter/consumer-api/Endpoints#risk_details) | Additive change                          |
| Added 'risk_desc' field in address-security response  | The risk description field has been added to the risk_detail response object of the address-security endpoint. | [risk_detail object](https://www.avengerdao.org/docs/meter/consumer-api/Endpoints#risk_details) | Additive change                          |
| Removed 'labels' field from address-security response | The labels field has been removed from the risk_detail response object of the address-security endpoint. | [risk_detail object](https://www.avengerdao.org/docs/meter/consumer-api/Endpoints#risk_details) | Subtractive change (potentially braking) |

## 02/09/2023

| **Change**                                         | **Description**                                              | **Location**                                                 | **Type**        |
| -------------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | --------------- |
| Added 'address' field in address-security response | The scanned address has been added to the response of the address-security endpoint. | [address-security response](https://www.avengerdao.org/docs/meter/consumer-api/Endpoints#data) | Additive change |

[
](https://www.avengerdao.org/docs/meter/consumer-api/RiskBand)