# HuksTag

表示调用参数的Tag。

**起始版本：** 8

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_INVALID

```TypeScript
HUKS_TAG_INVALID = HuksTagType.HUKS_TAG_TYPE_INVALID | 0
```

表示非法的Tag。

**说明：** 从API version 8开始使用，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_ALGORITHM

```TypeScript
HUKS_TAG_ALGORITHM = HuksTagType.HUKS_TAG_TYPE_UINT | 1
```

表示算法的Tag。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_PURPOSE

```TypeScript
HUKS_TAG_PURPOSE = HuksTagType.HUKS_TAG_TYPE_UINT | 2
```

表示密钥用途的Tag。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_KEY_SIZE

```TypeScript
HUKS_TAG_KEY_SIZE = HuksTagType.HUKS_TAG_TYPE_UINT | 3
```

表示密钥长度的Tag，单位：bit。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_DIGEST

```TypeScript
HUKS_TAG_DIGEST = HuksTagType.HUKS_TAG_TYPE_UINT | 4
```

表示摘要算法的Tag。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.Huks.Core
- API版本8-11：SystemCapability.Security.Huks.Extension

## HUKS_TAG_PADDING

```TypeScript
HUKS_TAG_PADDING = HuksTagType.HUKS_TAG_TYPE_UINT | 5
```

表示填充模式的Tag。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_BLOCK_MODE

```TypeScript
HUKS_TAG_BLOCK_MODE = HuksTagType.HUKS_TAG_TYPE_UINT | 6
```

表示加密模式的Tag。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_KEY_TYPE

```TypeScript
HUKS_TAG_KEY_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT | 7
```

表示密钥类型的Tag。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_ASSOCIATED_DATA

```TypeScript
HUKS_TAG_ASSOCIATED_DATA = HuksTagType.HUKS_TAG_TYPE_BYTES | 8
```

表示附加身份验证数据的Tag。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_NONCE

```TypeScript
HUKS_TAG_NONCE = HuksTagType.HUKS_TAG_TYPE_BYTES | 9
```

表示密钥加解密的NONCE字段。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_IV

```TypeScript
HUKS_TAG_IV = HuksTagType.HUKS_TAG_TYPE_BYTES | 10
```

表示密钥初始化的向量。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_INFO

```TypeScript
HUKS_TAG_INFO = HuksTagType.HUKS_TAG_TYPE_BYTES | 11
```

表示密钥派生时的info。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_SALT

```TypeScript
HUKS_TAG_SALT = HuksTagType.HUKS_TAG_TYPE_BYTES | 12
```

表示密钥派生时的盐值。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.Huks.Core
- API版本8-11：SystemCapability.Security.Huks.Extension

## HUKS_TAG_PWD

```TypeScript
HUKS_TAG_PWD = HuksTagType.HUKS_TAG_TYPE_BYTES | 13
```

表示操作系统补丁级别的Tag。

**说明：** 从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_ITERATION

```TypeScript
HUKS_TAG_ITERATION = HuksTagType.HUKS_TAG_TYPE_UINT | 14
```

表示密钥派生时的迭代次数。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.Huks.Core
- API版本8-11：SystemCapability.Security.Huks.Extension

## HUKS_TAG_KEY_GENERATE_TYPE

```TypeScript
HUKS_TAG_KEY_GENERATE_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT | 15
```

表示生成密钥类型的Tag。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_DERIVE_MAIN_KEY

```TypeScript
HUKS_TAG_DERIVE_MAIN_KEY = HuksTagType.HUKS_TAG_TYPE_BYTES | 16
```

原为预留字段。

**说明：** 从API version 9开始废弃，无替代接口。

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_DERIVE_FACTOR

```TypeScript
HUKS_TAG_DERIVE_FACTOR = HuksTagType.HUKS_TAG_TYPE_BYTES | 17
```

原为预留字段。

**说明：** 从API version 9开始废弃，无替代接口。

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_DERIVE_ALG

```TypeScript
HUKS_TAG_DERIVE_ALG = HuksTagType.HUKS_TAG_TYPE_UINT | 18
```

原为预留字段。

**说明：** 从API version 9开始废弃，无替代接口。

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_AGREE_ALG

```TypeScript
HUKS_TAG_AGREE_ALG = HuksTagType.HUKS_TAG_TYPE_UINT | 19
```

表示密钥协商时的算法类型。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.Huks.Core
- API版本8-11：SystemCapability.Security.Huks.Extension

## HUKS_TAG_AGREE_PUBLIC_KEY_IS_KEY_ALIAS

```TypeScript
HUKS_TAG_AGREE_PUBLIC_KEY_IS_KEY_ALIAS = HuksTagType.HUKS_TAG_TYPE_BOOL | 20
```

表示密钥协商时的公钥别名。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.Huks.Core
- API版本8-11：SystemCapability.Security.Huks.Extension

## HUKS_TAG_AGREE_PRIVATE_KEY_ALIAS

```TypeScript
HUKS_TAG_AGREE_PRIVATE_KEY_ALIAS = HuksTagType.HUKS_TAG_TYPE_BYTES | 21
```

表示密钥协商时的私钥别名。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.Huks.Core
- API版本8-11：SystemCapability.Security.Huks.Extension

## HUKS_TAG_AGREE_PUBLIC_KEY

```TypeScript
HUKS_TAG_AGREE_PUBLIC_KEY = HuksTagType.HUKS_TAG_TYPE_BYTES | 22
```

表示密钥协商时的公钥。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.Huks.Core
- API版本8-11：SystemCapability.Security.Huks.Extension

## HUKS_TAG_KEY_ALIAS

```TypeScript
HUKS_TAG_KEY_ALIAS = HuksTagType.HUKS_TAG_TYPE_BYTES | 23
```

表示密钥别名。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_DERIVE_KEY_SIZE

```TypeScript
HUKS_TAG_DERIVE_KEY_SIZE = HuksTagType.HUKS_TAG_TYPE_UINT | 24
```

表示派生密钥的大小，单位：byte。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.Huks.Core
- API版本8-11：SystemCapability.Security.Huks.Extension

## HUKS_TAG_IMPORT_KEY_TYPE

```TypeScript
HUKS_TAG_IMPORT_KEY_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT | 25
```

表示导入的密钥类型。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.Huks.Core
- API版本9-11：SystemCapability.Security.Huks.Extension

## HUKS_TAG_UNWRAP_ALGORITHM_SUITE

```TypeScript
HUKS_TAG_UNWRAP_ALGORITHM_SUITE = HuksTagType.HUKS_TAG_TYPE_UINT | 26
```

表示安全导入密钥的套件。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.Huks.Core
- API版本9-11：SystemCapability.Security.Huks.Extension

## HUKS_TAG_DERIVED_AGREED_KEY_STORAGE_FLAG

```TypeScript
HUKS_TAG_DERIVED_AGREED_KEY_STORAGE_FLAG = HuksTagType.HUKS_TAG_TYPE_UINT | 29
```

表示派生密钥/协商密钥的存储类型。

**起始版本：** 10

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.Huks.Core
- API版本10-11：SystemCapability.Security.Huks.Extension

## HUKS_TAG_RSA_PSS_SALT_LEN_TYPE

```TypeScript
HUKS_TAG_RSA_PSS_SALT_LEN_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT | 30
```

表示rsa_pss_salt_length的类型。

**起始版本：** 10

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.Huks.Core
- API版本10-11：SystemCapability.Security.Huks.Extension

## HUKS_TAG_ACTIVE_DATETIME

```TypeScript
HUKS_TAG_ACTIVE_DATETIME = HuksTagType.HUKS_TAG_TYPE_ULONG | 201
```

原为证书业务预留字段，当前证书管理已独立，此字段废弃，不再预留。

**说明：** 从API version 9开始废弃，无替代接口。

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ORIGINATION_EXPIRE_DATETIME

```TypeScript
HUKS_TAG_ORIGINATION_EXPIRE_DATETIME = HuksTagType.HUKS_TAG_TYPE_ULONG | 202
```

原为证书业务预留字段，当前证书管理已独立，此字段废弃，不再预留。

**说明：** 从API version 9开始废弃，无替代接口。

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_USAGE_EXPIRE_DATETIME

```TypeScript
HUKS_TAG_USAGE_EXPIRE_DATETIME = HuksTagType.HUKS_TAG_TYPE_ULONG | 203
```

原为证书业务预留字段，当前证书管理已独立，此字段废弃，不再预留。

**说明：** 从API version 9开始废弃，无替代接口。

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_CREATION_DATETIME

```TypeScript
HUKS_TAG_CREATION_DATETIME = HuksTagType.HUKS_TAG_TYPE_ULONG | 204
```

原为证书业务预留字段，当前证书管理已独立，此字段废弃，不再预留。

**说明：** 从API version 9开始废弃，无替代接口。

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_ALL_USERS

```TypeScript
HUKS_TAG_ALL_USERS = HuksTagType.HUKS_TAG_TYPE_BOOL | 301
```

预留。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.Huks.Core
- API版本8-11：SystemCapability.Security.Huks.Extension

## HUKS_TAG_USER_ID

```TypeScript
HUKS_TAG_USER_ID = HuksTagType.HUKS_TAG_TYPE_UINT | 302
```

表示当前密钥属于哪个userID。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.Huks.Core
- API版本8-11：SystemCapability.Security.Huks.Extension

## HUKS_TAG_NO_AUTH_REQUIRED

```TypeScript
HUKS_TAG_NO_AUTH_REQUIRED = HuksTagType.HUKS_TAG_TYPE_BOOL | 303
```

预留。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.Huks.Core
- API版本8-11：SystemCapability.Security.Huks.Extension

## HUKS_TAG_USER_AUTH_TYPE

```TypeScript
HUKS_TAG_USER_AUTH_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT | 304
```

表示用户认证类型。从[HuksUserAuthType](arkts-universalkeystore-huksuserauthtype-e.md)中选择，需要与安全访问控制类型同时设置。支持同时指定两种用户认证类型，如：安全访问控制类型指定为
HUKS_AUTH_ACCESS_INVALID_NEW_BIO_ENROLL时，密钥访问认证类型可以指定以下三种： HUKS_USER_AUTH_TYPE_FACE 、
HUKS_USER_AUTH_TYPE_FINGERPRINT、HUKS_USER_AUTH_TYPE_FACE | HUKS_USER_AUTH_TYPE_FINGERPRINT

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_AUTH_TIMEOUT

```TypeScript
HUKS_TAG_AUTH_TIMEOUT = HuksTagType.HUKS_TAG_TYPE_UINT | 305
```

表示auth token单次有效期，单位：秒。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_AUTH_TOKEN

```TypeScript
HUKS_TAG_AUTH_TOKEN = HuksTagType.HUKS_TAG_TYPE_BYTES | 306
```

用于传入authToken的字段。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_KEY_AUTH_ACCESS_TYPE

```TypeScript
HUKS_TAG_KEY_AUTH_ACCESS_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT | 307
```

表示安全访问控制类型。从[HuksAuthAccessType](arkts-universalkeystore-huksauthaccesstype-e.md)中选择，需要和用户认证类型同时设置。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_KEY_SECURE_SIGN_TYPE

```TypeScript
HUKS_TAG_KEY_SECURE_SIGN_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT | 308
```

表示生成或导入密钥时，指定该密钥的签名类型。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_CHALLENGE_TYPE

```TypeScript
HUKS_TAG_CHALLENGE_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT | 309
```

表示密钥使用时生成的challenge类型。从[HuksChallengeType](arkts-universalkeystore-hukschallengetype-e.md)中选择。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_CHALLENGE_POS

```TypeScript
HUKS_TAG_CHALLENGE_POS = HuksTagType.HUKS_TAG_TYPE_UINT | 310
```

表示challenge类型为用户自定义类型时，huks产生的challenge有效长度仅为8字节连续的数据。从[HuksChallengePosition](arkts-universalkeystore-hukschallengeposition-e.md)中
选择。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_KEY_AUTH_PURPOSE

```TypeScript
HUKS_TAG_KEY_AUTH_PURPOSE = HuksTagType.HUKS_TAG_TYPE_UINT | 311
```

表示密钥认证用途的tag。

**起始版本：** 10

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_AUTH_STORAGE_LEVEL

```TypeScript
HUKS_TAG_AUTH_STORAGE_LEVEL = HuksTagType.HUKS_TAG_TYPE_UINT | 316
```

表示密钥存储安全等级的tag。从[HuksAuthStorageLevel](arkts-universalkeystore-huksauthstoragelevel-e.md)中选择。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_USER_AUTH_MODE

```TypeScript
HUKS_TAG_USER_AUTH_MODE = HuksTagType.HUKS_TAG_TYPE_UINT | 319
```

表示用户认证模式。从[HuksUserAuthMode](arkts-universalkeystore-huksuserauthmode-e.md)中选择。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_CHALLENGE

```TypeScript
HUKS_TAG_ATTESTATION_CHALLENGE = HuksTagType.HUKS_TAG_TYPE_BYTES | 501
```

表示attestation时的挑战值。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_APPLICATION_ID

```TypeScript
HUKS_TAG_ATTESTATION_APPLICATION_ID = HuksTagType.HUKS_TAG_TYPE_BYTES | 502
```

表示attestation时拥有该密钥的application的Id。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_ID_BRAND

```TypeScript
HUKS_TAG_ATTESTATION_ID_BRAND = HuksTagType.HUKS_TAG_TYPE_BYTES | 503
```

原为预留字段。

**说明：** 从API version 9开始废弃，无替代接口。

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_ID_DEVICE

```TypeScript
HUKS_TAG_ATTESTATION_ID_DEVICE = HuksTagType.HUKS_TAG_TYPE_BYTES | 504
```

原为预留字段。

**说明：** 从API version 9开始废弃，无替代接口。

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_ID_PRODUCT

```TypeScript
HUKS_TAG_ATTESTATION_ID_PRODUCT = HuksTagType.HUKS_TAG_TYPE_BYTES | 505
```

原为预留字段。

**说明：** 从API version 9开始废弃，无替代接口。

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_ID_SERIAL

```TypeScript
HUKS_TAG_ATTESTATION_ID_SERIAL = HuksTagType.HUKS_TAG_TYPE_BYTES | 506
```

原为预留字段。

**说明：** 从API version 9开始废弃，无替代接口。

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_ID_IMEI

```TypeScript
HUKS_TAG_ATTESTATION_ID_IMEI = HuksTagType.HUKS_TAG_TYPE_BYTES | 507
```

原为预留字段。

**说明：** 从API version 9开始废弃，无替代接口。

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_ID_MEID

```TypeScript
HUKS_TAG_ATTESTATION_ID_MEID = HuksTagType.HUKS_TAG_TYPE_BYTES | 508
```

原为预留字段。

**说明：** 从API version 9开始废弃，无替代接口。

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_ID_MANUFACTURER

```TypeScript
HUKS_TAG_ATTESTATION_ID_MANUFACTURER = HuksTagType.HUKS_TAG_TYPE_BYTES | 509
```

原为预留字段。

**说明：** 从API version 9开始废弃，无替代接口。

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_ID_MODEL

```TypeScript
HUKS_TAG_ATTESTATION_ID_MODEL = HuksTagType.HUKS_TAG_TYPE_BYTES | 510
```

原为预留字段。

**说明：** 从API version 9开始废弃，无替代接口。

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_ID_ALIAS

```TypeScript
HUKS_TAG_ATTESTATION_ID_ALIAS = HuksTagType.HUKS_TAG_TYPE_BYTES | 511
```

表示attestation时的密钥别名。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_ID_SOCID

```TypeScript
HUKS_TAG_ATTESTATION_ID_SOCID = HuksTagType.HUKS_TAG_TYPE_BYTES | 512
```

原为预留字段。

**说明：** 从API version 9开始废弃，无替代接口。

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_ID_UDID

```TypeScript
HUKS_TAG_ATTESTATION_ID_UDID = HuksTagType.HUKS_TAG_TYPE_BYTES | 513
```

原为预留字段。

**说明：** 从API version 9开始废弃，无替代接口。

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_ID_SEC_LEVEL_INFO

```TypeScript
HUKS_TAG_ATTESTATION_ID_SEC_LEVEL_INFO = HuksTagType.HUKS_TAG_TYPE_BYTES | 514
```

表示attestation时的安全凭据。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_ID_VERSION_INFO

```TypeScript
HUKS_TAG_ATTESTATION_ID_VERSION_INFO = HuksTagType.HUKS_TAG_TYPE_BYTES | 515
```

表示attestation时的版本号。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_KEY_OVERRIDE

```TypeScript
HUKS_TAG_KEY_OVERRIDE = HuksTagType.HUKS_TAG_TYPE_BOOL | 520
```

表示是否覆写同名密钥。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_AE_TAG_LEN

```TypeScript
HUKS_TAG_AE_TAG_LEN = HuksTagType.HUKS_TAG_TYPE_UINT | 521
```

表示指定的AEAD标签长度，单位：byte。

**起始版本：** 22

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_KEY_CLASS

```TypeScript
HUKS_TAG_KEY_CLASS = HuksTagType.HUKS_TAG_TYPE_UINT | 522
```

表示密钥来源。

**起始版本：** 22

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_KEY_ACCESS_GROUP

```TypeScript
HUKS_TAG_KEY_ACCESS_GROUP = HuksTagType.HUKS_TAG_TYPE_BYTES | 523
```

表示指定的分组信息。

**起始版本：** 23

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_KEY_SECURITY_LEVEL

```TypeScript
HUKS_TAG_KEY_SECURITY_LEVEL = HuksTagType.HUKS_TAG_TYPE_UINT | 526
```

表示密钥安全级别。

26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**起始版本：** 26.0.0

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_AAD

```TypeScript
HUKS_TAG_AAD = HuksTagType.HUKS_TAG_TYPE_BYTES | 527
```

标记指示GCM或CCM模式的附加验证数据。

**模型约束：** 此接口仅可在Stage模型下使用。

**起始版本：** 24

**元服务API：** 从API版本24开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_CONTEXT

```TypeScript
HUKS_TAG_CONTEXT = HuksTagType.HUKS_TAG_TYPE_BYTES | 528
```

标记指示加密操作的上下文，例如ML-DSA等。

**起始版本：** 26.0.0

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_IS_KEY_ALIAS

```TypeScript
HUKS_TAG_IS_KEY_ALIAS = HuksTagType.HUKS_TAG_TYPE_BOOL | 1001
```

表示是否使用生成key时传入的别名的Tag。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_KEY_STORAGE_FLAG

```TypeScript
HUKS_TAG_KEY_STORAGE_FLAG = HuksTagType.HUKS_TAG_TYPE_UINT | 1002
```

表示密钥存储方式的Tag。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_IS_ALLOWED_WRAP

```TypeScript
HUKS_TAG_IS_ALLOWED_WRAP = HuksTagType.HUKS_TAG_TYPE_BOOL | 1003
```

预留。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.Huks.Core
- API版本8-11：SystemCapability.Security.Huks.Extension

## HUKS_TAG_KEY_WRAP_TYPE

```TypeScript
HUKS_TAG_KEY_WRAP_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT | 1004
```

预留。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.Huks.Core
- API版本8-11：SystemCapability.Security.Huks.Extension

## HUKS_TAG_KEY_AUTH_ID

```TypeScript
HUKS_TAG_KEY_AUTH_ID = HuksTagType.HUKS_TAG_TYPE_BYTES | 1005
```

预留。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_KEY_ROLE

```TypeScript
HUKS_TAG_KEY_ROLE = HuksTagType.HUKS_TAG_TYPE_UINT | 1006
```

预留。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.Huks.Core
- API版本8-11：SystemCapability.Security.Huks.Extension

## HUKS_TAG_KEY_FLAG

```TypeScript
HUKS_TAG_KEY_FLAG = HuksTagType.HUKS_TAG_TYPE_UINT | 1007
```

表示密钥标志的Tag。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_IS_ASYNCHRONIZED

```TypeScript
HUKS_TAG_IS_ASYNCHRONIZED = HuksTagType.HUKS_TAG_TYPE_UINT | 1008
```

预留。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.Huks.Core
- API版本8-11：SystemCapability.Security.Huks.Extension

## HUKS_TAG_SECURE_KEY_ALIAS

```TypeScript
HUKS_TAG_SECURE_KEY_ALIAS = HuksTagType.HUKS_TAG_TYPE_BOOL | 1009
```

表示操作系统补丁级别的Tag。

**说明：** 从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_SECURE_KEY_UUID

```TypeScript
HUKS_TAG_SECURE_KEY_UUID = HuksTagType.HUKS_TAG_TYPE_BYTES | 1010
```

原为预留字段。

**说明：** 从API version 9开始废弃，无替代接口。

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_KEY_DOMAIN

```TypeScript
HUKS_TAG_KEY_DOMAIN = HuksTagType.HUKS_TAG_TYPE_UINT | 1011
```

预留。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_IS_DEVICE_PASSWORD_SET

```TypeScript
HUKS_TAG_IS_DEVICE_PASSWORD_SET = HuksTagType.HUKS_TAG_TYPE_BOOL | 1012
```

表示密钥锁屏密码访问控制字段，可限制密钥只有在用户设置了锁屏密码时可用。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_PROCESS_NAME

```TypeScript
HUKS_TAG_PROCESS_NAME = HuksTagType.HUKS_TAG_TYPE_BYTES | 10001
```

表示操作系统补丁级别的Tag。

**说明：** 从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_PACKAGE_NAME

```TypeScript
HUKS_TAG_PACKAGE_NAME = HuksTagType.HUKS_TAG_TYPE_BYTES | 10002
```

原为预留字段。

**说明：** 从API version 9开始废弃，无替代接口。

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ACCESS_TIME

```TypeScript
HUKS_TAG_ACCESS_TIME = HuksTagType.HUKS_TAG_TYPE_UINT | 10003
```

原为预留字段。

**说明：** 从API version 9开始废弃，无替代接口。

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_USES_TIME

```TypeScript
HUKS_TAG_USES_TIME = HuksTagType.HUKS_TAG_TYPE_UINT | 10004
```

原为预留字段。

**说明：** 从API version 9开始废弃，无替代接口。

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_CRYPTO_CTX

```TypeScript
HUKS_TAG_CRYPTO_CTX = HuksTagType.HUKS_TAG_TYPE_ULONG | 10005
```

原为预留字段。

**说明：** 从API version 9开始废弃，无替代接口。

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_KEY

```TypeScript
HUKS_TAG_KEY = HuksTagType.HUKS_TAG_TYPE_BYTES | 10006
```

预留。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_KEY_VERSION

```TypeScript
HUKS_TAG_KEY_VERSION = HuksTagType.HUKS_TAG_TYPE_UINT | 10007
```

原为预留字段。

**说明：** 从API version 9开始废弃，无替代接口。

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_PAYLOAD_LEN

```TypeScript
HUKS_TAG_PAYLOAD_LEN = HuksTagType.HUKS_TAG_TYPE_UINT | 10008
```

原为预留字段。

**说明：** 从API version 9开始废弃，无替代接口。

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_AE_TAG

```TypeScript
HUKS_TAG_AE_TAG = HuksTagType.HUKS_TAG_TYPE_BYTES | 10009
```

用于传入GCM模式中的AEAD数据的字段。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_IS_KEY_HANDLE

```TypeScript
HUKS_TAG_IS_KEY_HANDLE = HuksTagType.HUKS_TAG_TYPE_ULONG | 10010
```

表示操作系统补丁级别的Tag。

**说明：** 从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_OS_VERSION

```TypeScript
HUKS_TAG_OS_VERSION = HuksTagType.HUKS_TAG_TYPE_UINT | 10101
```

表示操作系统版本的Tag。

**说明：** 从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_OS_PATCHLEVEL

```TypeScript
HUKS_TAG_OS_PATCHLEVEL = HuksTagType.HUKS_TAG_TYPE_UINT | 10102
```

表示操作系统补丁级别的Tag。

**说明：** 从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_SYMMETRIC_KEY_DATA

```TypeScript
HUKS_TAG_SYMMETRIC_KEY_DATA = HuksTagType.HUKS_TAG_TYPE_BYTES | 20001
```

预留。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_ASYMMETRIC_PUBLIC_KEY_DATA

```TypeScript
HUKS_TAG_ASYMMETRIC_PUBLIC_KEY_DATA = HuksTagType.HUKS_TAG_TYPE_BYTES | 20002
```

预留。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.Huks.Core
- API版本8-11：SystemCapability.Security.Huks.Extension

## HUKS_TAG_ASYMMETRIC_PRIVATE_KEY_DATA

```TypeScript
HUKS_TAG_ASYMMETRIC_PRIVATE_KEY_DATA = HuksTagType.HUKS_TAG_TYPE_BYTES | 20003
```

预留。

**起始版本：** 8

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.Huks.Core
- API版本8-11：SystemCapability.Security.Huks.Extension

