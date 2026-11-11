# @system.cipher (Cipher Algorithm)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=2d99b235700beb6fbf6e85916d19bb529b5ce6fc translatedAt=2026-11-10T08:00:44.168Z pushedAt=2026-11-10T11:18:49.132Z nl=1 -->

> **NOTE**
>
> The initial APIs of this module are supported since API version 3. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module are deprecated since API version 9. You are advised to use [@ohos.security.cryptoFramework Cipher](js-apis-cryptoFramework.md#cipher) instead.

## Modules to Import


```js
import cipher from '@system.cipher';
```

## CipherResponse

Defines the response to the cipher interface called.

**System capability**: SystemCapability.Security.Cipher

| Name| Type  | Read-Only| Optional|Description        |
| ------ | ------ | ---- | ---- | ------------ |
| text   | string | No  | No  | Response content.|


## CipherRsaOptions

Defines the input parameters of **cipher.rsa()**.

**System capability**: SystemCapability.Security.Cipher

| Name | Type | Read-Only | Optional | Description |
| ---- | ---------- | ---- | ---- | ------ |
| action | string | No | No | Type of the encryption/decryption operation. The options are as follows:<br/>1. encrypt: encrypts data;<br/>2. decrypt: decrypts data. |
| text | string | No | No | Text to be encrypted or decrypted. The text to be encrypted must be a common text and cannot exceed the length calculated based on the formula (keySize/8 - 66). **keySize** indicates the key length. For example, if the key length is 1024 bytes, the text cannot exceed 62 bytes (1024/8 - 66 = 62). The text to be decrypted must be a binary value encoded in Base64. The default format is used for Base64 encoding. |
| key | string | No | No | RSA key used for encryption/decryption. For encryption, **key** is the public key; for decryption, **key** is the private key. |
| transformation | string | No | Yes | Padding mode of the RSA algorithm. The default value is RSA/None/OAEPWithSHA256AndMGF1Padding. |
| success | (data: [CipherResponse](#cipherresponse)) => void | No | Yes | Callback invoked when the API call is successful. |
| fail | (data: string, code: number) => void | No | Yes | Called when the operation fails. |
| complete | () => void | No | Yes | Callback invoked when the API call is complete. |

## CipherAesOptions

Defines the input parameters of **cipher.aes()**.

**System capability**: SystemCapability.Security.Cipher

| Name | Type | Read-Only | Optional | Description |
| ---- | ---------- | ---- | ---- | ------ |
| action | string | No | No | Type of the encryption/decryption operation. The options are as follows:<br/>1. encrypt: encrypts data;<br/>2. decrypt: decrypts data. |
| text | string | No | No | Text to be encrypted or decrypted. The text to be encrypted must be a common text. The text to be decrypted must be a binary value encoded in Base64. The default format is used for Base64 encoding. |
| key | string | No | No | Key used for encryption or decryption, which is a string generated after Base64 encoding. |
| transformation | string | No | Yes | Encryption mode and padding mode of the AES algorithm. The default value is AES/CBC/PKCS5Padding. |
| iv | string | No | Yes | Initialization vector for AES encryption/decryption, which is a string generated after Base64 encoding. The default value is the value of **key**. |
| ivOffset | string | No | Yes | Offset of the initialization vector for AES encryption/decryption. The default value is 0, and only 0 is supported. |
| ivLen | string | No | Yes | Byte length of the initialization vector for AES encryption/decryption. This is a reserved field. The default value is 16, and only 16 is supported. |
| success | (data: [CipherResponse](#cipherresponse)) => void | No | Yes | Callback invoked when the API call is successful. |
| fail | (data: string, code: number) => void | No | Yes | Called when the operation fails. |
| complete | () => void | No | Yes | Callback invoked when the API call is complete. |

## cipher.rsa

rsa(options: CipherRsaOptions): void

Encrypts or decrypts data using RSA.

**System capability**: SystemCapability.Security.Cipher

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| options | [CipherRsaOptions](#cipherrsaoptions) | Yes| Parameters set for RSA encryption or decryption.|

**Example**

```js
export default {
  rsa() {
    cipher.rsa({
      // Encrypt.
      action: 'encrypt',
      // Text content to be encrypted.
      text: 'hello',
      // Public key for encryption, encoded in Base64.
      key:
     'MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQCx414QSP3RsYWYzf9mkBMiBAXo\n' +
     '6S7Lpva1fKlcuVxjoFC1iMnzD4mC0uiL4k5MNi43J64c7dbqi3qAJjdAtuwQ6NZJ\n' +
     '+Enz0RzmVFh/4yk6lmqRzuEFQqhQqSZzaLq6sq2N2G0Sv2Xl3sLvqAfe2HNm2oBw\n' +
     'jBpApTJ3TeneOo6Z5QIDAQAB',
      success: function(data) {
        console.info(`handling success:${data.text}`);
      },
      fail: function(data, code) {
        console.error(`### cipher.rsa encrypt fail ### ${code}:${data}`);
      },
      complete: function() {
        console.info(`operation complete!`);
      }
      });
      cipher.rsa({
        // Decrypt:
        action: 'decrypt',
        // Content to be decrypted, which is a binary value encoded in Base64 and becomes the text content "hello" after decryption.
        text:
       'EPeCFPib6ayKbA0M6oSywARvFZ8dFYfjQv3nY8ikZGtS9UHq2sLPvAfpeIzggSiCxqbWeCftP1XQ\n' +
       'Sa+jEpzFlT1qoSTunBbrYzugPTajIJDTg6R1IRsF/J+mmakn0POVPvi4jCo9wqavB324Bx0Wipnc\n' +
       'EU5WO0oBHo5l4x6dTpU=',
         // Private key for decryption, encoded in Base64.
         key:
        'MIICXgIBAAKBgQCx414QSP3RsYWYzf9mkBMiBAXo6S7Lpva1fKlcuVxjoFC1iMnz\n' +
        'D4mC0uiL4k5MNi43J64c7dbqi3qAJjdAtuwQ6NZJ+Enz0RzmVFh/4yk6lmqRzuEF\n' +
        'QqhQqSZzaLq6sq2N2G0Sv2Xl3sLvqAfe2HNm2oBwjBpApTJ3TeneOo6Z5QIDAQAB\n' +
        'AoGBAKPNtoRQcklxqo+2wQP0j2m3Qqnib1DggjVEgb/8f/LNYQSI3U2QdROemryU\n' +
        'u3y6N3xacZ359PktTrRKfH5+8ohmHGhIuPAnefp6bLvAFUcl4t1xm74Cow62Kyw3\n' +
        'aSbmuTG98dxPA1sXD0jiprdtsq2wQ9CoKNyY7/d/pKoqxNuBAkEA4GytZ60NCTj9\n' +
        'w24jACFeko5YqCFY/TTLoc4SQvWtFMnimRPclLZhtUIK0P8dib71UFedx+AxklgL\n' +
        'A5gjcfo+2QJBAMrqiwyCh3OQ5DhyRPDwt87x1/jg5fy4hhete2ufSf2FoQCVqO+w\n' +
        'PKoljdXmJeS6rGgzGibstuHLrP3tcIho4+0CQD3ZFWzF/xq0jxKlrpWhnJuNCRfE\n' +
        'oO6e9yNvVA8J/5oEDSOcmqSNIp4+RhbUx8InUxnCG6Ryv5aSFu71pYcKrPkCQQCL\n' +
        'RUGcm3ZGTnslduB0knNF+V2ndwzDUQ7P74UXT+PjurTPhujFYiuxCEd6ORVnEOzG\n' +
        'M9TORIgdH8MjIbWsGnndAkEAw9yURDaorE8IYPLF2IEn09g1uzvWPs3phDb6smVx\n' +
        '8GfqIdUNf+aCG5TZK/kXBF1sqcsi7jXMAf4jBlejVbSVZg==',
         success: function(data) {
           console.info(`handling success:${data.text}`);
         },
         fail: function(data, code) {
           console.error(`### cipher.rsa decrypt fail ### ${code}:${data}`);
         },
         complete: function() {
           console.info(`operation complete!`);
         }
       });
   }
}
```


## cipher.aes

aes(options: CipherAesOptions): void

Encrypts or decrypts data using AES.

**System capability**: SystemCapability.Security.Cipher

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| options | [CipherAesOptions](#cipheraesoptions) | Yes| Parameters set for AES encryption or decryption.|

**Example**

```js
export default {
  aes() {
    cipher.aes({
      // Encrypt.
      action: 'encrypt',
      // Text content to be encrypted.
      text: 'hello',
      // Key encoded in Base64.
      key: 'NDM5Qjk2UjAzMEE0NzVCRjlFMkQwQkVGOFc1NkM1QkQ=',
      transformation: 'AES/CBC/PKCS5Padding',
      ivOffset: '0',
      ivLen: '16',
      success: function(data) {
        console.info(`handling success:${data.text}`);
        },
      fail: function(data, code) {
        console.error(`### cipher.aes encrypt fail ### ${code}:${data}`);
        },
      complete: function() {
        console.info(`operation complete!`);
      }
    });
    cipher.aes({
      // Decrypt:
      action: 'decrypt',
      // Content to be decrypted, which is a binary value encoded in Base64.
      text: '1o0kf2HXwLxHkSh5W5NhzA==',
       // Key encoded in Base64.
       key: 'NDM5Qjk2UjAzMEE0NzVCRjlFMkQwQkVGOFc1NkM1QkQ=',
       transformation: 'AES/CBC/PKCS5Padding',
       ivOffset: '0',
       ivLen: '16',
       success: function(data) {
         console.info(`handling success:${data.text}`);
        },
       fail: function(data, code) {
         console.error(`### cipher.aes decrypt fail ### ${code}:${data}`);
       },
       complete: function() {
         console.info(`operation complete!`);
        }
     });
  }
}

```

