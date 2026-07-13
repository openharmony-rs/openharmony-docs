# CipherSpecItem

表示加解密参数的枚举。这些参数支持通过[setCipherSpec](arkts-cryptoarchitecture-cipher-i.md#setcipherspec-1)接口设置，通过
[getCipherSpec](arkts-cryptoarchitecture-cipher-i.md#getcipherspec-1)接口获取。

当前只支持RSA算法和SM2算法，从API version 11开始，增加对SM2_MD_NAME_STR参数的支持，详细规格请参考
[加解密规格](../../../../security/CryptoArchitectureKit/crypto-asym-encrypt-decrypt-spec.md)。

API version 10-11 系统能力为 SystemCapability.Security.CryptoFramework；从 API version 12 开始为
SystemCapability.Security.CryptoFramework.Cipher

**起始版本：** 10

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本10-11：SystemCapability.Security.CryptoFramework

## OAEP_MD_NAME_STR

```TypeScript
OAEP_MD_NAME_STR = 100
```

表示RSA算法中，使用PKCS1_OAEP模式时，消息摘要功能的算法名。

**起始版本：** 10

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本10-11：SystemCapability.Security.CryptoFramework

## OAEP_MGF_NAME_STR

```TypeScript
OAEP_MGF_NAME_STR = 101
```

表示RSA算法中，使用PKCS1_OAEP模式时，掩码生成算法（目前仅支持MGF1）。

**起始版本：** 10

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本10-11：SystemCapability.Security.CryptoFramework

## OAEP_MGF1_MD_STR

```TypeScript
OAEP_MGF1_MD_STR = 102
```

表示RSA算法中，使用PKCS1_OAEP模式时，MGF1掩码生成功能的消息摘要算法。

**起始版本：** 10

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本10-11：SystemCapability.Security.CryptoFramework

## OAEP_MGF1_PSRC_UINT8ARR

```TypeScript
OAEP_MGF1_PSRC_UINT8ARR = 103
```

表示RSA算法中，使用PKCS1_OAEP模式时，pSource的字节流。

**起始版本：** 10

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本10-11：SystemCapability.Security.CryptoFramework

## SM2_MD_NAME_STR

```TypeScript
SM2_MD_NAME_STR = 104
```

表示SM2算法中，使用的摘要算法名。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本11：SystemCapability.Security.CryptoFramework

