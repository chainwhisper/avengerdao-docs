---
sidebar_position: 2
---

# API Contract

## Request to the Providers

This is the data that will be passed to the providers, from the meter bus, in order to document the request and label it.

When the MeterBus calls provider’s restful interface, MeterBus needs to set the following headers to pass the server’s authorization：

| **Header**            | **Description**                                  |
| --------------------- | ------------------------------------------------ |
| Content-Type          | application/json;charset=UTF-8                   |
| X-Signature-appid     | Appid, unique code                               |
| X-Signature-timestamp | Timestamp, millisecond                           |
| X-Signature-nonce     | Random uuid, replace “-” with “”，32 byte length |
| X-Signature-signature | Signature, check below for sign details          |

## Signature

INFO

Please note that the signature is optional here. You can still access our API without signature. However, you will be limited to a lower rate. If you foresee your application having a higher rate to the AvengerDAO API, please contact us for a dedicated appid and appSecret.

```js
signature = encodeHexString(HmacSHA256(
  appsecret,
  appid;
  timestamp;
  nonce;
  method;
  uri;
  query;
  body
))
```



Where uri is the path, multiple key-value pair in query and header should be **sorted** alphabetically by key, comma separated, example:

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| appid     | 13cc90dc5ffa4032acb3                                         |
| appsecret | cd0ec4b1ca934b188996034541d7e810                             |
| url       | /security-api/public/app/v1/detect                           |
| query     | empty                                                        |
| method    | POST                                                         |
| body      | `{  "chain_id":"56",  "address":"0x312bc7eaaf93f1c60dc5afc115fccde161055fb0"}` |
| timestamp | 1657246234465                                                |
| nonce     | 791f398e93f14b3e98f916703f777f44                             |

**then：**

```js
signature = encodeHexString(HmacSHA256(
  cd0ec4b1ca934b188996034541d7e810,
  ‘13cc90dc5ffa4032acb3;
  1657246234465;
  791f398e93f14b3e98f916703f777f44;
  POST;
  /security-api/public/app/v1/detect;
  {
    "address":"1",
    "chainId":"56"
  }’
))
```



## Final header

| **Header**            | **Description**                                              |
| --------------------- | ------------------------------------------------------------ |
| Content-Type          | application/json;charset=UTF-8                               |
| X-Signature-appid     | 13cc90dc5ffa4032acb3                                         |
| X-Signature-timestamp | 1657246234465                                                |
| X-Signature-nonce     | 791f398e93f14b3e98f916703f777f44                             |
| X-Signature-signature | 08850af5a48bbc255137d82ee7ab40e9e850a422dad1af9ca2391f2db8505e47 |
