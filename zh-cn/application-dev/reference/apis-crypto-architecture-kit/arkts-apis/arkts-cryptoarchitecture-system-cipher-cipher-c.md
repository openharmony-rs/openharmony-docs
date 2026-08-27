# Cipher

提供加解密接口。

**起始版本：** 3

**废弃版本：** 9

**替代接口：** Cipher

**系统能力：** SystemCapability.Security.Cipher

## 导入模块

```TypeScript
import { Cipher, CipherAesOptions, CipherResponse, CipherRsaOptions } from '@kit.CryptoArchitectureKit';
```

## aes

```TypeScript
static aes(options: CipherAesOptions): void
```

使用AES对数据进行加密或解密。

**起始版本：** 3

**废弃版本：** 9

**替代接口：** Cipher

**系统能力：** SystemCapability.Security.Cipher

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [CipherAesOptions](arkts-cryptoarchitecture-system-cipher-cipheraesoptions-i.md) | 是 | AES 加解密参数。 |

**示例**

```TypeScript
export default {
  aes() {
    cipher.aes({
      // 加密。
      action: 'encrypt',
      // 待加密的文本内容。
      text: 'hello',
      // base64编码后的密钥。
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
      // 解密：
      action: 'decrypt',
      // 待解密的内容，是base64编码后的一段二进制值。
      text: '1o0kf2HXwLxHkSh5W5NhzA==',
       // base64编码后的密钥。
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

## rsa

```TypeScript
static rsa(options: CipherRsaOptions): void
```

使用RSA对数据进行加密或解密。

**起始版本：** 3

**废弃版本：** 9

**替代接口：** Cipher

**系统能力：** SystemCapability.Security.Cipher

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [CipherRsaOptions](arkts-cryptoarchitecture-system-cipher-cipherrsaoptions-i.md) | 是 | RSA 加解密参数。 |

**示例**

```TypeScript
export default {
  rsa() {
    cipher.rsa({
      // 加密。
      action: 'encrypt',
      // 待加密的文本内容。
      text: 'hello',
      // base64编码后的加密公钥。
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
        // 解密：
        action: 'decrypt',
        // 待解密的内容，是base64编码后的一段二进制值，解密后是文本内容“hello”。
        text:
       'EPeCFPib6ayKbA0M6oSywARvFZ8dFYfjQv3nY8ikZGtS9UHq2sLPvAfpeIzggSiCxqbWeCftP1XQ\n' +
       'Sa+jEpzFlT1qoSTunBbrYzugPTajIJDTg6R1IRsF/J+mmakn0POVPvi4jCo9wqavB324Bx0Wipnc\n' +
       'EU5WO0oBHo5l4x6dTpU=',
         // base64编码后的解密私钥。
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
