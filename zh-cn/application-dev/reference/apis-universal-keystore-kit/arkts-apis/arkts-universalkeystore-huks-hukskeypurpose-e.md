# HuksKeyPurpose

表示密钥用途。

一个密钥仅能用于单类用途，不能既用于加解密又用于签名验签。

**起始版本：** 8

<!--Device-huks-export enum HuksKeyPurpose--><!--Device-huks-export enum HuksKeyPurpose-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_KEY_PURPOSE_ENCRYPT

```TypeScript
HUKS_KEY_PURPOSE_ENCRYPT = 1
```

表示密钥用于对明文进行加密操作。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HuksKeyPurpose-HUKS_KEY_PURPOSE_ENCRYPT = 1--><!--Device-HuksKeyPurpose-HUKS_KEY_PURPOSE_ENCRYPT = 1-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_KEY_PURPOSE_DECRYPT

```TypeScript
HUKS_KEY_PURPOSE_DECRYPT = 2
```

表示密钥用于对密文进行解密操作。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HuksKeyPurpose-HUKS_KEY_PURPOSE_DECRYPT = 2--><!--Device-HuksKeyPurpose-HUKS_KEY_PURPOSE_DECRYPT = 2-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_KEY_PURPOSE_SIGN

```TypeScript
HUKS_KEY_PURPOSE_SIGN = 4
```

表示密钥用于对数据进行签名。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HuksKeyPurpose-HUKS_KEY_PURPOSE_SIGN = 4--><!--Device-HuksKeyPurpose-HUKS_KEY_PURPOSE_SIGN = 4-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.Huks.Core
- API版本8-11：SystemCapability.Security.Huks.Extension

## HUKS_KEY_PURPOSE_VERIFY

```TypeScript
HUKS_KEY_PURPOSE_VERIFY = 8
```

表示密钥用于验证签名后的数据。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HuksKeyPurpose-HUKS_KEY_PURPOSE_VERIFY = 8--><!--Device-HuksKeyPurpose-HUKS_KEY_PURPOSE_VERIFY = 8-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.Huks.Core
- API版本8-11：SystemCapability.Security.Huks.Extension

## HUKS_KEY_PURPOSE_DERIVE

```TypeScript
HUKS_KEY_PURPOSE_DERIVE = 16
```

表示密钥用于派生密钥。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HuksKeyPurpose-HUKS_KEY_PURPOSE_DERIVE = 16--><!--Device-HuksKeyPurpose-HUKS_KEY_PURPOSE_DERIVE = 16-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.Huks.Core
- API版本8-11：SystemCapability.Security.Huks.Extension

## HUKS_KEY_PURPOSE_WRAP

```TypeScript
HUKS_KEY_PURPOSE_WRAP = 32
```

表示密钥用于加密导出。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HuksKeyPurpose-HUKS_KEY_PURPOSE_WRAP = 32--><!--Device-HuksKeyPurpose-HUKS_KEY_PURPOSE_WRAP = 32-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.Huks.Core
- API版本8-11：SystemCapability.Security.Huks.Extension

## HUKS_KEY_PURPOSE_UNWRAP

```TypeScript
HUKS_KEY_PURPOSE_UNWRAP = 64
```

表示密钥用于安全导入。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HuksKeyPurpose-HUKS_KEY_PURPOSE_UNWRAP = 64--><!--Device-HuksKeyPurpose-HUKS_KEY_PURPOSE_UNWRAP = 64-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.Huks.Core
- API版本8-11：SystemCapability.Security.Huks.Extension

## HUKS_KEY_PURPOSE_MAC

```TypeScript
HUKS_KEY_PURPOSE_MAC = 128
```

表示密钥用于生成消息验证码。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HuksKeyPurpose-HUKS_KEY_PURPOSE_MAC = 128--><!--Device-HuksKeyPurpose-HUKS_KEY_PURPOSE_MAC = 128-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.Huks.Core
- API版本8-11：SystemCapability.Security.Huks.Extension

## HUKS_KEY_PURPOSE_AGREE

```TypeScript
HUKS_KEY_PURPOSE_AGREE = 256
```

表示密钥用于进行密钥协商。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HuksKeyPurpose-HUKS_KEY_PURPOSE_AGREE = 256--><!--Device-HuksKeyPurpose-HUKS_KEY_PURPOSE_AGREE = 256-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.Huks.Core
- API版本8-11：SystemCapability.Security.Huks.Extension

