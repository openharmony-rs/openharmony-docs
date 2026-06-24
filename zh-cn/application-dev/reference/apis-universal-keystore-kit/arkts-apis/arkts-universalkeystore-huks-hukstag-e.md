# HuksTag

```TypeScript
export enum HuksTag
```

��ʾ���ò�����Tag��

**起始版本：** 8

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_INVALID

```TypeScript
HUKS_TAG_INVALID = HuksTagType.HUKS_TAG_TYPE_INVALID | 0
```

��ʾ�Ƿ���Tag��

**˵����** ��API version 8��ʼʹ�ã���API version 9��ʼ������

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_ALGORITHM

```TypeScript
HUKS_TAG_ALGORITHM = HuksTagType.HUKS_TAG_TYPE_UINT | 1
```

��ʾ�㷨��Tag��

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_PURPOSE

```TypeScript
HUKS_TAG_PURPOSE = HuksTagType.HUKS_TAG_TYPE_UINT | 2
```

��ʾ��Կ��;��Tag��

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_KEY_SIZE

```TypeScript
HUKS_TAG_KEY_SIZE = HuksTagType.HUKS_TAG_TYPE_UINT | 3
```

��ʾ��Կ���ȵ�Tag����λ��bit��

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_DIGEST

```TypeScript
HUKS_TAG_DIGEST = HuksTagType.HUKS_TAG_TYPE_UINT | 4
```

��ʾժҪ�㷨��Tag��

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_PADDING

```TypeScript
HUKS_TAG_PADDING = HuksTagType.HUKS_TAG_TYPE_UINT | 5
```

��ʾ���ģʽ��Tag��

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_BLOCK_MODE

```TypeScript
HUKS_TAG_BLOCK_MODE = HuksTagType.HUKS_TAG_TYPE_UINT | 6
```

��ʾ����ģʽ��Tag��

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_KEY_TYPE

```TypeScript
HUKS_TAG_KEY_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT | 7
```

��ʾ��Կ���͵�Tag��

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_ASSOCIATED_DATA

```TypeScript
HUKS_TAG_ASSOCIATED_DATA = HuksTagType.HUKS_TAG_TYPE_BYTES | 8
```

��ʾ����������֤���ݵ�Tag��

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_NONCE

```TypeScript
HUKS_TAG_NONCE = HuksTagType.HUKS_TAG_TYPE_BYTES | 9
```

��ʾ��Կ�ӽ��ܵ�NONCE�ֶΡ�

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_IV

```TypeScript
HUKS_TAG_IV = HuksTagType.HUKS_TAG_TYPE_BYTES | 10
```

��ʾ��Կ��ʼ����������

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_INFO

```TypeScript
HUKS_TAG_INFO = HuksTagType.HUKS_TAG_TYPE_BYTES | 11
```

��ʾ��Կ����ʱ��info��

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_SALT

```TypeScript
HUKS_TAG_SALT = HuksTagType.HUKS_TAG_TYPE_BYTES | 12
```

��ʾ��Կ����ʱ����ֵ��

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_PWD

```TypeScript
HUKS_TAG_PWD = HuksTagType.HUKS_TAG_TYPE_BYTES | 13
```

��ʾ����ϵͳ���������Tag��

**˵����** ��API version 8��ʼ֧�֣���API version 9��ʼ������

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_ITERATION

```TypeScript
HUKS_TAG_ITERATION = HuksTagType.HUKS_TAG_TYPE_UINT | 14
```

��ʾ��Կ����ʱ�ĵ���������

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_KEY_GENERATE_TYPE

```TypeScript
HUKS_TAG_KEY_GENERATE_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT | 15
```

��ʾ������Կ���͵�Tag��

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_DERIVE_MAIN_KEY

```TypeScript
HUKS_TAG_DERIVE_MAIN_KEY = HuksTagType.HUKS_TAG_TYPE_BYTES | 16
```

ԭΪԤ���ֶΡ�

**˵����** ��API version 9��ʼ������������ӿڡ�

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_DERIVE_FACTOR

```TypeScript
HUKS_TAG_DERIVE_FACTOR = HuksTagType.HUKS_TAG_TYPE_BYTES | 17
```

ԭΪԤ���ֶΡ�

**˵����** ��API version 9��ʼ������������ӿڡ�

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_DERIVE_ALG

```TypeScript
HUKS_TAG_DERIVE_ALG = HuksTagType.HUKS_TAG_TYPE_UINT | 18
```

ԭΪԤ���ֶΡ�

**˵����** ��API version 9��ʼ������������ӿڡ�

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_AGREE_ALG

```TypeScript
HUKS_TAG_AGREE_ALG = HuksTagType.HUKS_TAG_TYPE_UINT | 19
```

��ʾ��ԿЭ��ʱ���㷨���͡�

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_AGREE_PUBLIC_KEY_IS_KEY_ALIAS

```TypeScript
HUKS_TAG_AGREE_PUBLIC_KEY_IS_KEY_ALIAS = HuksTagType.HUKS_TAG_TYPE_BOOL | 20
```

��ʾ��ԿЭ��ʱ�Ĺ�Կ������

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_AGREE_PRIVATE_KEY_ALIAS

```TypeScript
HUKS_TAG_AGREE_PRIVATE_KEY_ALIAS = HuksTagType.HUKS_TAG_TYPE_BYTES | 21
```

��ʾ��ԿЭ��ʱ��˽Կ������

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_AGREE_PUBLIC_KEY

```TypeScript
HUKS_TAG_AGREE_PUBLIC_KEY = HuksTagType.HUKS_TAG_TYPE_BYTES | 22
```

��ʾ��ԿЭ��ʱ�Ĺ�Կ��

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_KEY_ALIAS

```TypeScript
HUKS_TAG_KEY_ALIAS = HuksTagType.HUKS_TAG_TYPE_BYTES | 23
```

��ʾ��Կ������

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_DERIVE_KEY_SIZE

```TypeScript
HUKS_TAG_DERIVE_KEY_SIZE = HuksTagType.HUKS_TAG_TYPE_UINT | 24
```

��ʾ������Կ�Ĵ�С����λ��byte��

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_IMPORT_KEY_TYPE

```TypeScript
HUKS_TAG_IMPORT_KEY_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT | 25
```

��ʾ�������Կ���͡�

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_UNWRAP_ALGORITHM_SUITE

```TypeScript
HUKS_TAG_UNWRAP_ALGORITHM_SUITE = HuksTagType.HUKS_TAG_TYPE_UINT | 26
```

��ʾ��ȫ������Կ���׼���

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_DERIVED_AGREED_KEY_STORAGE_FLAG

```TypeScript
HUKS_TAG_DERIVED_AGREED_KEY_STORAGE_FLAG = HuksTagType.HUKS_TAG_TYPE_UINT | 29
```

��ʾ������Կ/Э����Կ�Ĵ洢���͡�

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_RSA_PSS_SALT_LEN_TYPE

```TypeScript
HUKS_TAG_RSA_PSS_SALT_LEN_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT | 30
```

��ʾrsa_pss_salt_length�����͡�

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_ACTIVE_DATETIME

```TypeScript
HUKS_TAG_ACTIVE_DATETIME = HuksTagType.HUKS_TAG_TYPE_ULONG | 201
```

ԭΪ֤��ҵ��Ԥ���ֶΣ���ǰ֤������Ѷ��������ֶη���������Ԥ����

**˵����** ��API version 9��ʼ������������ӿڡ�

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ORIGINATION_EXPIRE_DATETIME

```TypeScript
HUKS_TAG_ORIGINATION_EXPIRE_DATETIME = HuksTagType.HUKS_TAG_TYPE_ULONG | 202
```

ԭΪ֤��ҵ��Ԥ���ֶΣ���ǰ֤������Ѷ��������ֶη���������Ԥ����

**˵����** ��API version 9��ʼ������������ӿڡ�

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_USAGE_EXPIRE_DATETIME

```TypeScript
HUKS_TAG_USAGE_EXPIRE_DATETIME = HuksTagType.HUKS_TAG_TYPE_ULONG | 203
```

ԭΪ֤��ҵ��Ԥ���ֶΣ���ǰ֤������Ѷ��������ֶη���������Ԥ����

**˵����** ��API version 9��ʼ������������ӿڡ�

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_CREATION_DATETIME

```TypeScript
HUKS_TAG_CREATION_DATETIME = HuksTagType.HUKS_TAG_TYPE_ULONG | 204
```

ԭΪ֤��ҵ��Ԥ���ֶΣ���ǰ֤������Ѷ��������ֶη���������Ԥ����

**˵����** ��API version 9��ʼ������������ӿڡ�

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_ALL_USERS

```TypeScript
HUKS_TAG_ALL_USERS = HuksTagType.HUKS_TAG_TYPE_BOOL | 301
```

Ԥ����

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_USER_ID

```TypeScript
HUKS_TAG_USER_ID = HuksTagType.HUKS_TAG_TYPE_UINT | 302
```

��ʾ��ǰ��Կ�����ĸ�userID��

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_NO_AUTH_REQUIRED

```TypeScript
HUKS_TAG_NO_AUTH_REQUIRED = HuksTagType.HUKS_TAG_TYPE_BOOL | 303
```

Ԥ����

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_USER_AUTH_TYPE

```TypeScript
HUKS_TAG_USER_AUTH_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT | 304
```

��ʾ�û���֤���͡���[HuksUserAuthType](arkts-universalkeystore-huks-huksuserauthtype-e.md#HuksUserAuthType)��ѡ����Ҫ�밲ȫ���ʿ�������ͬʱ���á�֧��ͬʱָ�������û���֤���ͣ��磺��ȫ���ʿ�������ָ��Ϊ
HUKS_AUTH_ACCESS_INVALID_NEW_BIO_ENROLLʱ����Կ������֤���Ϳ���ָ���������֣� HUKS_USER_AUTH_TYPE_FACE ��
HUKS_USER_AUTH_TYPE_FINGERPRINT��HUKS_USER_AUTH_TYPE_FACE | HUKS_USER_AUTH_TYPE_FINGERPRINT

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_AUTH_TIMEOUT

```TypeScript
HUKS_TAG_AUTH_TIMEOUT = HuksTagType.HUKS_TAG_TYPE_UINT | 305
```

��ʾauth token������Ч�ڣ���λ���롣

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_AUTH_TOKEN

```TypeScript
HUKS_TAG_AUTH_TOKEN = HuksTagType.HUKS_TAG_TYPE_BYTES | 306
```

���ڴ���authToken���ֶΡ�

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_KEY_AUTH_ACCESS_TYPE

```TypeScript
HUKS_TAG_KEY_AUTH_ACCESS_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT | 307
```

��ʾ��ȫ���ʿ������͡���[HuksAuthAccessType](arkts-universalkeystore-huks-huksauthaccesstype-e.md#HuksAuthAccessType)��ѡ����Ҫ���û���֤����ͬʱ���á�

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_KEY_SECURE_SIGN_TYPE

```TypeScript
HUKS_TAG_KEY_SECURE_SIGN_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT | 308
```

��ʾ���ɻ�����Կʱ��ָ������Կ��ǩ�����͡�

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_CHALLENGE_TYPE

```TypeScript
HUKS_TAG_CHALLENGE_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT | 309
```

��ʾ��Կʹ��ʱ���ɵ�challenge���͡���[HuksChallengeType](arkts-universalkeystore-huks-hukschallengetype-e.md#HuksChallengeType)��ѡ��

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_CHALLENGE_POS

```TypeScript
HUKS_TAG_CHALLENGE_POS = HuksTagType.HUKS_TAG_TYPE_UINT | 310
```

��ʾchallenge����Ϊ�û��Զ�������ʱ��huks������challenge��Ч���Ƚ�Ϊ8�ֽ����������ݡ���[HuksChallengePosition](arkts-universalkeystore-huks-hukschallengeposition-e.md#HuksChallengePosition)��
ѡ��

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_KEY_AUTH_PURPOSE

```TypeScript
HUKS_TAG_KEY_AUTH_PURPOSE = HuksTagType.HUKS_TAG_TYPE_UINT | 311
```

��ʾ��Կ��֤��;��tag��

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_AUTH_STORAGE_LEVEL

```TypeScript
HUKS_TAG_AUTH_STORAGE_LEVEL = HuksTagType.HUKS_TAG_TYPE_UINT | 316
```

��ʾ��Կ�洢��ȫ�ȼ���tag����[HuksAuthStorageLevel](arkts-universalkeystore-huks-huksauthstoragelevel-e.md#HuksAuthStorageLevel)��ѡ��

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_USER_AUTH_MODE

```TypeScript
HUKS_TAG_USER_AUTH_MODE = HuksTagType.HUKS_TAG_TYPE_UINT | 319
```

��ʾ�û���֤ģʽ����[HuksUserAuthMode](arkts-universalkeystore-huks-huksuserauthmode-e.md#HuksUserAuthMode)��ѡ��

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_CHALLENGE

```TypeScript
HUKS_TAG_ATTESTATION_CHALLENGE = HuksTagType.HUKS_TAG_TYPE_BYTES | 501
```

��ʾattestationʱ����սֵ��

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_APPLICATION_ID

```TypeScript
HUKS_TAG_ATTESTATION_APPLICATION_ID = HuksTagType.HUKS_TAG_TYPE_BYTES | 502
```

��ʾattestationʱӵ�и���Կ��application��Id��

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_ID_BRAND

```TypeScript
HUKS_TAG_ATTESTATION_ID_BRAND = HuksTagType.HUKS_TAG_TYPE_BYTES | 503
```

ԭΪԤ���ֶΡ�

**˵����** ��API version 9��ʼ������������ӿڡ�

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_ID_DEVICE

```TypeScript
HUKS_TAG_ATTESTATION_ID_DEVICE = HuksTagType.HUKS_TAG_TYPE_BYTES | 504
```

ԭΪԤ���ֶΡ�

**˵����** ��API version 9��ʼ������������ӿڡ�

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_ID_PRODUCT

```TypeScript
HUKS_TAG_ATTESTATION_ID_PRODUCT = HuksTagType.HUKS_TAG_TYPE_BYTES | 505
```

ԭΪԤ���ֶΡ�

**˵����** ��API version 9��ʼ������������ӿڡ�

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_ID_SERIAL

```TypeScript
HUKS_TAG_ATTESTATION_ID_SERIAL = HuksTagType.HUKS_TAG_TYPE_BYTES | 506
```

ԭΪԤ���ֶΡ�

**˵����** ��API version 9��ʼ������������ӿڡ�

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_ID_IMEI

```TypeScript
HUKS_TAG_ATTESTATION_ID_IMEI = HuksTagType.HUKS_TAG_TYPE_BYTES | 507
```

ԭΪԤ���ֶΡ�

**˵����** ��API version 9��ʼ������������ӿڡ�

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_ID_MEID

```TypeScript
HUKS_TAG_ATTESTATION_ID_MEID = HuksTagType.HUKS_TAG_TYPE_BYTES | 508
```

ԭΪԤ���ֶΡ�

**˵����** ��API version 9��ʼ������������ӿڡ�

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_ID_MANUFACTURER

```TypeScript
HUKS_TAG_ATTESTATION_ID_MANUFACTURER = HuksTagType.HUKS_TAG_TYPE_BYTES | 509
```

ԭΪԤ���ֶΡ�

**˵����** ��API version 9��ʼ������������ӿڡ�

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_ID_MODEL

```TypeScript
HUKS_TAG_ATTESTATION_ID_MODEL = HuksTagType.HUKS_TAG_TYPE_BYTES | 510
```

ԭΪԤ���ֶΡ�

**˵����** ��API version 9��ʼ������������ӿڡ�

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_ID_ALIAS

```TypeScript
HUKS_TAG_ATTESTATION_ID_ALIAS = HuksTagType.HUKS_TAG_TYPE_BYTES | 511
```

��ʾattestationʱ����Կ������

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_ID_SOCID

```TypeScript
HUKS_TAG_ATTESTATION_ID_SOCID = HuksTagType.HUKS_TAG_TYPE_BYTES | 512
```

ԭΪԤ���ֶΡ�

**˵����** ��API version 9��ʼ������������ӿڡ�

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_ID_UDID

```TypeScript
HUKS_TAG_ATTESTATION_ID_UDID = HuksTagType.HUKS_TAG_TYPE_BYTES | 513
```

ԭΪԤ���ֶΡ�

**˵����** ��API version 9��ʼ������������ӿڡ�

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_ID_SEC_LEVEL_INFO

```TypeScript
HUKS_TAG_ATTESTATION_ID_SEC_LEVEL_INFO = HuksTagType.HUKS_TAG_TYPE_BYTES | 514
```

��ʾattestationʱ�İ�ȫƾ�ݡ�

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_ID_VERSION_INFO

```TypeScript
HUKS_TAG_ATTESTATION_ID_VERSION_INFO = HuksTagType.HUKS_TAG_TYPE_BYTES | 515
```

��ʾattestationʱ�İ汾�š�

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_KEY_OVERRIDE

```TypeScript
HUKS_TAG_KEY_OVERRIDE = HuksTagType.HUKS_TAG_TYPE_BOOL | 520
```

��ʾ�Ƿ�дͬ����Կ��

**起始版本：** 20

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_AE_TAG_LEN

```TypeScript
HUKS_TAG_AE_TAG_LEN = HuksTagType.HUKS_TAG_TYPE_UINT | 521
```

��ʾָ����AEAD��ǩ���ȣ���λ��byte��

**起始版本：** 22

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_KEY_CLASS

```TypeScript
HUKS_TAG_KEY_CLASS = HuksTagType.HUKS_TAG_TYPE_UINT | 522
```

��ʾ��Կ��Դ��

**起始版本：** 22

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_KEY_ACCESS_GROUP

```TypeScript
HUKS_TAG_KEY_ACCESS_GROUP = HuksTagType.HUKS_TAG_TYPE_BYTES | 523
```

��ʾָ���ķ�����Ϣ��

**起始版本：** 23

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_KEY_SECURITY_LEVEL

```TypeScript
HUKS_TAG_KEY_SECURITY_LEVEL = HuksTagType.HUKS_TAG_TYPE_UINT | 526
```

��ʾ��Կ��ȫ����

26.0.0

**ģ��Լ����** �˽ӿڽ�����Stageģ����ʹ�á�

**ԭ�ӻ�����API��** ��API�汾26.0.0��ʼ���ýӿ�֧����ԭ�ӻ�������ʹ�á�

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_AAD

```TypeScript
HUKS_TAG_AAD = HuksTagType.HUKS_TAG_TYPE_BYTES | 527
```

���ָʾGCM��CCMģʽ�ĸ�����֤���ݡ�

**ģ��Լ����** �˽ӿڽ�����Stageģ����ʹ�á�

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_CONTEXT

```TypeScript
HUKS_TAG_CONTEXT = HuksTagType.HUKS_TAG_TYPE_BYTES | 528
```

���ָʾ���ܲ����������ģ�����ML-DSA�ȡ�

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_IS_KEY_ALIAS

```TypeScript
HUKS_TAG_IS_KEY_ALIAS = HuksTagType.HUKS_TAG_TYPE_BOOL | 1001
```

��ʾ�Ƿ�ʹ������keyʱ����ı�����Tag��

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_KEY_STORAGE_FLAG

```TypeScript
HUKS_TAG_KEY_STORAGE_FLAG = HuksTagType.HUKS_TAG_TYPE_UINT | 1002
```

��ʾ��Կ�洢��ʽ��Tag��

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_IS_ALLOWED_WRAP

```TypeScript
HUKS_TAG_IS_ALLOWED_WRAP = HuksTagType.HUKS_TAG_TYPE_BOOL | 1003
```

Ԥ����

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_KEY_WRAP_TYPE

```TypeScript
HUKS_TAG_KEY_WRAP_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT | 1004
```

Ԥ����

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_KEY_AUTH_ID

```TypeScript
HUKS_TAG_KEY_AUTH_ID = HuksTagType.HUKS_TAG_TYPE_BYTES | 1005
```

Ԥ����

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_KEY_ROLE

```TypeScript
HUKS_TAG_KEY_ROLE = HuksTagType.HUKS_TAG_TYPE_UINT | 1006
```

Ԥ����

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_KEY_FLAG

```TypeScript
HUKS_TAG_KEY_FLAG = HuksTagType.HUKS_TAG_TYPE_UINT | 1007
```

��ʾ��Կ��־��Tag��

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_IS_ASYNCHRONIZED

```TypeScript
HUKS_TAG_IS_ASYNCHRONIZED = HuksTagType.HUKS_TAG_TYPE_UINT | 1008
```

Ԥ����

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_SECURE_KEY_ALIAS

```TypeScript
HUKS_TAG_SECURE_KEY_ALIAS = HuksTagType.HUKS_TAG_TYPE_BOOL | 1009
```

��ʾ����ϵͳ���������Tag��

**˵����** ��API version 8��ʼ֧�֣���API version 9��ʼ������

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_SECURE_KEY_UUID

```TypeScript
HUKS_TAG_SECURE_KEY_UUID = HuksTagType.HUKS_TAG_TYPE_BYTES | 1010
```

ԭΪԤ���ֶΡ�

**˵����** ��API version 9��ʼ������������ӿڡ�

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_KEY_DOMAIN

```TypeScript
HUKS_TAG_KEY_DOMAIN = HuksTagType.HUKS_TAG_TYPE_UINT | 1011
```

Ԥ����

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_IS_DEVICE_PASSWORD_SET

```TypeScript
HUKS_TAG_IS_DEVICE_PASSWORD_SET = HuksTagType.HUKS_TAG_TYPE_BOOL | 1012
```

��ʾ��Կ����������ʿ����ֶΣ���������Կֻ�����û���������������ʱ���á�

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_PROCESS_NAME

```TypeScript
HUKS_TAG_PROCESS_NAME = HuksTagType.HUKS_TAG_TYPE_BYTES | 10001
```

��ʾ����ϵͳ���������Tag��

**˵����** ��API version 8��ʼ֧�֣���API version 9��ʼ������

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_PACKAGE_NAME

```TypeScript
HUKS_TAG_PACKAGE_NAME = HuksTagType.HUKS_TAG_TYPE_BYTES | 10002
```

ԭΪԤ���ֶΡ�

**˵����** ��API version 9��ʼ������������ӿڡ�

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ACCESS_TIME

```TypeScript
HUKS_TAG_ACCESS_TIME = HuksTagType.HUKS_TAG_TYPE_UINT | 10003
```

ԭΪԤ���ֶΡ�

**˵����** ��API version 9��ʼ������������ӿڡ�

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_USES_TIME

```TypeScript
HUKS_TAG_USES_TIME = HuksTagType.HUKS_TAG_TYPE_UINT | 10004
```

ԭΪԤ���ֶΡ�

**˵����** ��API version 9��ʼ������������ӿڡ�

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_CRYPTO_CTX

```TypeScript
HUKS_TAG_CRYPTO_CTX = HuksTagType.HUKS_TAG_TYPE_ULONG | 10005
```

ԭΪԤ���ֶΡ�

**˵����** ��API version 9��ʼ������������ӿڡ�

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_KEY

```TypeScript
HUKS_TAG_KEY = HuksTagType.HUKS_TAG_TYPE_BYTES | 10006
```

Ԥ����

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_KEY_VERSION

```TypeScript
HUKS_TAG_KEY_VERSION = HuksTagType.HUKS_TAG_TYPE_UINT | 10007
```

ԭΪԤ���ֶΡ�

**˵����** ��API version 9��ʼ������������ӿڡ�

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_PAYLOAD_LEN

```TypeScript
HUKS_TAG_PAYLOAD_LEN = HuksTagType.HUKS_TAG_TYPE_UINT | 10008
```

ԭΪԤ���ֶΡ�

**˵����** ��API version 9��ʼ������������ӿڡ�

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_TAG_AE_TAG

```TypeScript
HUKS_TAG_AE_TAG = HuksTagType.HUKS_TAG_TYPE_BYTES | 10009
```

���ڴ���GCMģʽ�е�AEAD���ݵ��ֶΡ�

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_IS_KEY_HANDLE

```TypeScript
HUKS_TAG_IS_KEY_HANDLE = HuksTagType.HUKS_TAG_TYPE_ULONG | 10010
```

��ʾ����ϵͳ���������Tag��

**˵����** ��API version 8��ʼ֧�֣���API version 9��ʼ������

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_OS_VERSION

```TypeScript
HUKS_TAG_OS_VERSION = HuksTagType.HUKS_TAG_TYPE_UINT | 10101
```

��ʾ����ϵͳ�汾��Tag��

**˵����** ��API version 8��ʼ֧�֣���API version 9��ʼ������

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_OS_PATCHLEVEL

```TypeScript
HUKS_TAG_OS_PATCHLEVEL = HuksTagType.HUKS_TAG_TYPE_UINT | 10102
```

��ʾ����ϵͳ���������Tag��

**˵����** ��API version 8��ʼ֧�֣���API version 9��ʼ������

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_SYMMETRIC_KEY_DATA

```TypeScript
HUKS_TAG_SYMMETRIC_KEY_DATA = HuksTagType.HUKS_TAG_TYPE_BYTES | 20001
```

Ԥ����

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_ASYMMETRIC_PUBLIC_KEY_DATA

```TypeScript
HUKS_TAG_ASYMMETRIC_PUBLIC_KEY_DATA = HuksTagType.HUKS_TAG_TYPE_BYTES | 20002
```

Ԥ����

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_TAG_ASYMMETRIC_PRIVATE_KEY_DATA

```TypeScript
HUKS_TAG_ASYMMETRIC_PRIVATE_KEY_DATA = HuksTagType.HUKS_TAG_TYPE_BYTES | 20003
```

Ԥ����

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

