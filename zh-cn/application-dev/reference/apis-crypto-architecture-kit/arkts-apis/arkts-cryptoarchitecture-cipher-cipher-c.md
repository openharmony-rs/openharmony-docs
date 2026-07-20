# Cipher

提供加解密接口。

**起始版本：** 3

**废弃版本：** 9

**替代接口：** Cipher

<!--Device-unnamed-export default class Cipher--><!--Device-unnamed-export default class Cipher-End-->

**系统能力：** SystemCapability.Security.Cipher

## 导入模块

```TypeScript
import { CipherAesOptions, CipherResponse, CipherRsaOptions } from '@kit.CryptoArchitectureKit';
```

<a id="aes"></a>
## aes

```TypeScript
static aes(options: CipherAesOptions): void
```

使用AES对数据进行加密或解密。

**起始版本：** 3

**废弃版本：** 9

**替代接口：** Cipher

<!--Device-Cipher-static aes(options: CipherAesOptions): void--><!--Device-Cipher-static aes(options: CipherAesOptions): void-End-->

**系统能力：** SystemCapability.Security.Cipher

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [CipherAesOptions](arkts-cryptoarchitecture-cipher-cipheraesoptions-i.md) | 是 | AES 加解密参数。 |

<a id="rsa"></a>
## rsa

```TypeScript
static rsa(options: CipherRsaOptions): void
```

使用RSA对数据进行加密或解密。

**起始版本：** 3

**废弃版本：** 9

**替代接口：** Cipher

<!--Device-Cipher-static rsa(options: CipherRsaOptions): void--><!--Device-Cipher-static rsa(options: CipherRsaOptions): void-End-->

**系统能力：** SystemCapability.Security.Cipher

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [CipherRsaOptions](arkts-cryptoarchitecture-cipher-cipherrsaoptions-i.md) | 是 | RSA 加解密参数。 |

