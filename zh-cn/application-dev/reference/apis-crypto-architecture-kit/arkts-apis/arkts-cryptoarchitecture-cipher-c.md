# Cipher

提供加解密接口。

**起始版本：** 3

**废弃版本：** 9

**替代接口：** Cipher

**系统能力：** SystemCapability.Security.Cipher

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
| options | CipherAesOptions | 是 | AES 加解密参数。 |

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
| options | CipherRsaOptions | 是 | RSA 加解密参数。 |

