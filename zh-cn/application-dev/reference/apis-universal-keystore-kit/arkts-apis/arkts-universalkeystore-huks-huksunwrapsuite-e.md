# HuksUnwrapSuite

表示安全导入密钥的算法套件。

**起始版本：** 9

<!--Device-huks-export enum HuksUnwrapSuite--><!--Device-huks-export enum HuksUnwrapSuite-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.Huks.Core
- API版本9-11：SystemCapability.Security.Huks.Extension

## HUKS_UNWRAP_SUITE_X25519_AES_256_GCM_NOPADDING

```TypeScript
HUKS_UNWRAP_SUITE_X25519_AES_256_GCM_NOPADDING = 1
```

安全导入密钥时，X25519密钥协商后使用AES-256 GCM解密。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HuksUnwrapSuite-HUKS_UNWRAP_SUITE_X25519_AES_256_GCM_NOPADDING = 1--><!--Device-HuksUnwrapSuite-HUKS_UNWRAP_SUITE_X25519_AES_256_GCM_NOPADDING = 1-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.Huks.Core
- API版本9-11：SystemCapability.Security.Huks.Extension

## HUKS_UNWRAP_SUITE_ECDH_AES_256_GCM_NOPADDING

```TypeScript
HUKS_UNWRAP_SUITE_ECDH_AES_256_GCM_NOPADDING = 2
```

安全导入密钥时，ECDH密钥协商后使用AES-256 GCM解密。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HuksUnwrapSuite-HUKS_UNWRAP_SUITE_ECDH_AES_256_GCM_NOPADDING = 2--><!--Device-HuksUnwrapSuite-HUKS_UNWRAP_SUITE_ECDH_AES_256_GCM_NOPADDING = 2-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.Huks.Core
- API版本9-11：SystemCapability.Security.Huks.Extension

## HUKS_UNWRAP_SUITE_SM2_SM4_ECB_NOPADDING

```TypeScript
HUKS_UNWRAP_SUITE_SM2_SM4_ECB_NOPADDING = 5
```

安全导入密钥时，使用临时SM4密钥加密导入密钥，使用已导入HUKS的SM2密钥加密SM4密钥。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-HuksUnwrapSuite-HUKS_UNWRAP_SUITE_SM2_SM4_ECB_NOPADDING = 5--><!--Device-HuksUnwrapSuite-HUKS_UNWRAP_SUITE_SM2_SM4_ECB_NOPADDING = 5-End-->

**系统能力：** SystemCapability.Security.Huks.Core

