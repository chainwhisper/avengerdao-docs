---
title: Authorization
sidebar_position: 1
---

# Authorization

When the client calls server’s restful interface, client need to set the following headers to pass the server’s authorization：

| **Header**            | **Description**                                  |
| --------------------- | ------------------------------------------------ |
| Content-Type          | application/json;charset=UTF-8                   |
| X-Signature-appid     | Appid, unique code                               |
| X-Signature-timestamp | Timestamp, millisecond                           |
| X-Signature-nonce     | Random uuid, replace “-” with “”，32 byte length |
| X-Signature-signature | Signature,lowercase,check below for sign details |

## Signature

:::tip
Please note that the signature is optional here. You can still access our API without signature. However, you will be limited to a lower rate. If you foresee your application having a higher rate to the AvengerDAO API, please contact us for a dedicated appid and appSecret.
:::


```js
signature = encodeHexString(
  HmacSHA256(
    appsecret,
    appid;
    timestamp;
    nonce;
    method;
    uri;
    query;
    body
  )
)
```



Where uri is the path, multiple key-value pair in query and header should be sorted alphabetically by key, comma separated, example:


import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

<Tabs>
<TabItem value="js" label="JavaScript">

```js
function helloWorld() {
  console.log('Hello, world!');
}
```

</TabItem>
<TabItem value="py" label="Python">

```py
def hello_world():
  print("Hello, world!")
```

</TabItem>
<TabItem value="java" label="Java">

```java
class HelloWorld {
  public static void main(String args[]) {
    System.out.println("Hello, World");
  }
}
```

</TabItem>
</Tabs>


| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| appid     | 13cc90dc5ffa4032acb3                                         |
| appsecret | cd0ec4b1ca934b188996034541d7e810                             |
| url       | /api/v1/address-security                                     |
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
  /api/v1/address-security;
  {
    "address":"0xbb4CdB9CBd36B01bD1cBaEBF2De08d9173bc095c",
    "chainId":"56"
  }’
))
```



**Note:** **The query can be empty. When the query is empty, you do not need to fill in the empty query and “;” in the concatenated string, but directly omit the query and “;”**

## Final header[](https://www.avengerdao.org/docs/meter/consumer-api/Authorization#final-header)

| **Header**            | **Description**                                              |
| --------------------- | ------------------------------------------------------------ |
| Content-Type          | application/json;charset=UTF-8                               |
| X-Signature-appid     | 13cc90dc5ffa4032acb3                                         |
| X-Signature-timestamp | 1657246234465                                                |
| X-Signature-nonce     | 791f398e93f14b3e98f916703f777f44                             |
| X-Signature-signature | bece3956c35911e598635345c0f428122e5423efc9fac68edf9dd377163a9897 |

[
](https://www.avengerdao.org/docs/category/consumer-api)