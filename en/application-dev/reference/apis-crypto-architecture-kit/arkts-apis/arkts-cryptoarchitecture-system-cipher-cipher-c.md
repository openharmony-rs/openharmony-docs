# Cipher

```TypeScript
export default class Cipher
```

Defines the cipher functions.

**Since:** 3

**Deprecated since:** 9

**Substitutes:** [Cipher](arkts-cryptoarchitecture-cryptoframework-cipher-i.md)

<!--Device-unnamed-export default class Cipher--><!--Device-unnamed-export default class Cipher-End-->

**System capability:** SystemCapability.Security.Cipher

## Modules to Import

```TypeScript
import { Cipher, CipherAesOptions, CipherResponse, CipherRsaOptions } from '@kit.CryptoArchitectureKit';
```

## aes

```TypeScript
static aes(options: CipherAesOptions): void
```

Encrypts or decrypts data using AES.

**Since:** 3

**Deprecated since:** 9

**Substitutes:** [Cipher](arkts-cryptoarchitecture-cryptoframework-cipher-i.md)

<!--Device-Cipher-static aes(options: CipherAesOptions): void--><!--Device-Cipher-static aes(options: CipherAesOptions): void-End-->

**System capability:** SystemCapability.Security.Cipher

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [CipherAesOptions](arkts-cryptoarchitecture-system-cipher-cipheraesoptions-i.md) | Yes | AES options. |

**Examples**

```TypeScript
export default {
  aes() {
    cipher.aes({
      // Encrypt data.
      action: 'encrypt',
      // Text to be encrypted.
      text: 'hello',
      // Base64-encoded key.
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
      // Decrypt data.
      action: 'decrypt',
      // Text to be decrypted, which is binary text encoded in Base64.
      text: '1o0kf2HXwLxHkSh5W5NhzA==',
       // Base64-encoded key.
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

Encrypts or decrypts data using RSA.

**Since:** 3

**Deprecated since:** 9

**Substitutes:** [Cipher](arkts-cryptoarchitecture-cryptoframework-cipher-i.md)

<!--Device-Cipher-static rsa(options: CipherRsaOptions): void--><!--Device-Cipher-static rsa(options: CipherRsaOptions): void-End-->

**System capability:** SystemCapability.Security.Cipher

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [CipherRsaOptions](arkts-cryptoarchitecture-system-cipher-cipherrsaoptions-i.md) | Yes | RSA options. |

**Examples**

```TypeScript
export default {
  rsa() {
    cipher.rsa({
      // Encrypt data.
      action: 'encrypt',
      // Text to be encrypted.
      text: 'hello',
      // Base64-encoded public key used for encryption.
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
        // Decrypt data.
        action: 'decrypt',
        // Text to be decrypted, which is binary text encoded in Base64. The decrypted text is "hello".
        text:
       'EPeCFPib6ayKbA0M6oSywARvFZ8dFYfjQv3nY8ikZGtS9UHq2sLPvAfpeIzggSiCxqbWeCftP1XQ\n' +
       'Sa+jEpzFlT1qoSTunBbrYzugPTajIJDTg6R1IRsF/J+mmakn0POVPvi4jCo9wqavB324Bx0Wipnc\n' +
       'EU5WO0oBHo5l4x6dTpU=',
         // Base64-encoded private key used for decryption.
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
