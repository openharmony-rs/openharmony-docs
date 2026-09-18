# HuksTag

Enumerates the tags used to invoke parameters.

**Since:** 8

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_TAG_INVALID

```TypeScript
HUKS_TAG_INVALID = HuksTagType.HUKS_TAG_TYPE_INVALID | 0
```

Invalid tag.

Note: This parameter is supported since API version 8 and deprecated since API version 9.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_TAG_ALGORITHM

```TypeScript
HUKS_TAG_ALGORITHM = HuksTagType.HUKS_TAG_TYPE_UINT | 1
```

Algorithm.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_TAG_PURPOSE

```TypeScript
HUKS_TAG_PURPOSE = HuksTagType.HUKS_TAG_TYPE_UINT | 2
```

Purpose of the key.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_TAG_KEY_SIZE

```TypeScript
HUKS_TAG_KEY_SIZE = HuksTagType.HUKS_TAG_TYPE_UINT | 3
```

Key size, in bits.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_TAG_DIGEST

```TypeScript
HUKS_TAG_DIGEST = HuksTagType.HUKS_TAG_TYPE_UINT | 4
```

Digest algorithm.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.Huks.Core
- API versions 8 to 11: SystemCapability.Security.Huks.Extension

## HUKS_TAG_PADDING

```TypeScript
HUKS_TAG_PADDING = HuksTagType.HUKS_TAG_TYPE_UINT | 5
```

Padding mode.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_TAG_BLOCK_MODE

```TypeScript
HUKS_TAG_BLOCK_MODE = HuksTagType.HUKS_TAG_TYPE_UINT | 6
```

Cipher mode.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_TAG_KEY_TYPE

```TypeScript
HUKS_TAG_KEY_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT | 7
```

Key type.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_TAG_ASSOCIATED_DATA

```TypeScript
HUKS_TAG_ASSOCIATED_DATA = HuksTagType.HUKS_TAG_TYPE_BYTES | 8
```

Associated authentication data.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_TAG_NONCE

```TypeScript
HUKS_TAG_NONCE = HuksTagType.HUKS_TAG_TYPE_BYTES | 9
```

Nonce for key encryption and decryption.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_TAG_IV

```TypeScript
HUKS_TAG_IV = HuksTagType.HUKS_TAG_TYPE_BYTES | 10
```

IV.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_TAG_INFO

```TypeScript
HUKS_TAG_INFO = HuksTagType.HUKS_TAG_TYPE_BYTES | 11
```

Information generated during key derivation.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_TAG_SALT

```TypeScript
HUKS_TAG_SALT = HuksTagType.HUKS_TAG_TYPE_BYTES | 12
```

Salt value used for key derivation.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.Huks.Core
- API versions 8 to 11: SystemCapability.Security.Huks.Extension

## HUKS_TAG_PWD

```TypeScript
HUKS_TAG_PWD = HuksTagType.HUKS_TAG_TYPE_BYTES | 13
```

OS patch level.

Note: This parameter is supported since API version 8 and deprecated since API version 9.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_TAG_ITERATION

```TypeScript
HUKS_TAG_ITERATION = HuksTagType.HUKS_TAG_TYPE_UINT | 14
```

Number of iterations for key derivation.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.Huks.Core
- API versions 8 to 11: SystemCapability.Security.Huks.Extension

## HUKS_TAG_KEY_GENERATE_TYPE

```TypeScript
HUKS_TAG_KEY_GENERATE_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT | 15
```

Key generation type.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_TAG_DERIVE_MAIN_KEY

```TypeScript
HUKS_TAG_DERIVE_MAIN_KEY = HuksTagType.HUKS_TAG_TYPE_BYTES | 16
```

Reserved field.

Note: This API is deprecated since API version 9. No substitute API is provided.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_TAG_DERIVE_FACTOR

```TypeScript
HUKS_TAG_DERIVE_FACTOR = HuksTagType.HUKS_TAG_TYPE_BYTES | 17
```

Reserved field.

Note: This API is deprecated since API version 9. No substitute API is provided.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_TAG_DERIVE_ALG

```TypeScript
HUKS_TAG_DERIVE_ALG = HuksTagType.HUKS_TAG_TYPE_UINT | 18
```

Reserved field.

Note: This API is deprecated since API version 9. No substitute API is provided.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_TAG_AGREE_ALG

```TypeScript
HUKS_TAG_AGREE_ALG = HuksTagType.HUKS_TAG_TYPE_UINT | 19
```

Type of the algorithm used for key agreement.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.Huks.Core
- API versions 8 to 11: SystemCapability.Security.Huks.Extension

## HUKS_TAG_AGREE_PUBLIC_KEY_IS_KEY_ALIAS

```TypeScript
HUKS_TAG_AGREE_PUBLIC_KEY_IS_KEY_ALIAS = HuksTagType.HUKS_TAG_TYPE_BOOL | 20
```

Public key alias used in key agreement.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.Huks.Core
- API versions 8 to 11: SystemCapability.Security.Huks.Extension

## HUKS_TAG_AGREE_PRIVATE_KEY_ALIAS

```TypeScript
HUKS_TAG_AGREE_PRIVATE_KEY_ALIAS = HuksTagType.HUKS_TAG_TYPE_BYTES | 21
```

Private key alias used in key agreement.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.Huks.Core
- API versions 8 to 11: SystemCapability.Security.Huks.Extension

## HUKS_TAG_AGREE_PUBLIC_KEY

```TypeScript
HUKS_TAG_AGREE_PUBLIC_KEY = HuksTagType.HUKS_TAG_TYPE_BYTES | 22
```

Public key used in key agreement.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.Huks.Core
- API versions 8 to 11: SystemCapability.Security.Huks.Extension

## HUKS_TAG_KEY_ALIAS

```TypeScript
HUKS_TAG_KEY_ALIAS = HuksTagType.HUKS_TAG_TYPE_BYTES | 23
```

Key alias.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_TAG_DERIVE_KEY_SIZE

```TypeScript
HUKS_TAG_DERIVE_KEY_SIZE = HuksTagType.HUKS_TAG_TYPE_UINT | 24
```

Size of the derived key, in bytes.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.Huks.Core
- API versions 8 to 11: SystemCapability.Security.Huks.Extension

## HUKS_TAG_IMPORT_KEY_TYPE

```TypeScript
HUKS_TAG_IMPORT_KEY_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT | 25
```

Type of the imported key.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.Huks.Core
- API versions 9 to 11: SystemCapability.Security.Huks.Extension

## HUKS_TAG_UNWRAP_ALGORITHM_SUITE

```TypeScript
HUKS_TAG_UNWRAP_ALGORITHM_SUITE = HuksTagType.HUKS_TAG_TYPE_UINT | 26
```

Suite for securely importing a key.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.Huks.Core
- API versions 9 to 11: SystemCapability.Security.Huks.Extension

## HUKS_TAG_DERIVED_AGREED_KEY_STORAGE_FLAG

```TypeScript
HUKS_TAG_DERIVED_AGREED_KEY_STORAGE_FLAG = HuksTagType.HUKS_TAG_TYPE_UINT | 29
```

Storage type of the derived key or agreed key.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.Huks.Core
- API versions 10 to 11: SystemCapability.Security.Huks.Extension

## HUKS_TAG_RSA_PSS_SALT_LEN_TYPE

```TypeScript
HUKS_TAG_RSA_PSS_SALT_LEN_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT | 30
```

Type of the **rsa_pss_salt_length**.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.Huks.Core
- API versions 10 to 11: SystemCapability.Security.Huks.Extension

## HUKS_TAG_ACTIVE_DATETIME

```TypeScript
HUKS_TAG_ACTIVE_DATETIME = HuksTagType.HUKS_TAG_TYPE_ULONG | 201
```

Parameter originally reserved for certificate management. It is deprecated because certificate management is no longer implemented in this module.

Note: This API is deprecated since API version 9. No substitute API is provided.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ORIGINATION_EXPIRE_DATETIME

```TypeScript
HUKS_TAG_ORIGINATION_EXPIRE_DATETIME = HuksTagType.HUKS_TAG_TYPE_ULONG | 202
```

Parameter originally reserved for certificate management. It is deprecated because certificate management is no longer implemented in this module.

Note: This API is deprecated since API version 9. No substitute API is provided.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_TAG_USAGE_EXPIRE_DATETIME

```TypeScript
HUKS_TAG_USAGE_EXPIRE_DATETIME = HuksTagType.HUKS_TAG_TYPE_ULONG | 203
```

Parameter originally reserved for certificate management. It is deprecated because certificate management is no longer implemented in this module.

Note: This API is deprecated since API version 9. No substitute API is provided.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_TAG_CREATION_DATETIME

```TypeScript
HUKS_TAG_CREATION_DATETIME = HuksTagType.HUKS_TAG_TYPE_ULONG | 204
```

Parameter originally reserved for certificate management. It is deprecated because certificate management is no longer implemented in this module.

Note: This API is deprecated since API version 9. No substitute API is provided.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_TAG_ALL_USERS

```TypeScript
HUKS_TAG_ALL_USERS = HuksTagType.HUKS_TAG_TYPE_BOOL | 301
```

Reserved.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.Huks.Core
- API versions 8 to 11: SystemCapability.Security.Huks.Extension

## HUKS_TAG_USER_ID

```TypeScript
HUKS_TAG_USER_ID = HuksTagType.HUKS_TAG_TYPE_UINT | 302
```

ID of the user to which the key belongs.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.Huks.Core
- API versions 8 to 11: SystemCapability.Security.Huks.Extension

## HUKS_TAG_NO_AUTH_REQUIRED

```TypeScript
HUKS_TAG_NO_AUTH_REQUIRED = HuksTagType.HUKS_TAG_TYPE_BOOL | 303
```

Reserved.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.Huks.Core
- API versions 8 to 11: SystemCapability.Security.Huks.Extension

## HUKS_TAG_USER_AUTH_TYPE

```TypeScript
HUKS_TAG_USER_AUTH_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT | 304
```

User authentication type. For details, see [HuksUserAuthType](arkts-universalkeystore-huks-huksuserauthtype-e.md). This parameter must be set together with [HuksAuthAccessType](arkts-universalkeystore-huks-huksauthaccesstype-e.md). You can set a maximum of two user authentication types at a time. For example, if **HuksAuthAccessType** is **HUKS_AUTH_ACCESS_INVALID_NEW_BIO_ENROLL**, you can set two of **HUKS_USER_AUTH_TYPE_FACE**, **HUKS_USER_AUTH_TYPE_FINGERPRINT**, and **HUKS_USER_AUTH_TYPE_FACE | HUKS_USER_AUTH_TYPE_FINGERPRINT**.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_TAG_AUTH_TIMEOUT

```TypeScript
HUKS_TAG_AUTH_TIMEOUT = HuksTagType.HUKS_TAG_TYPE_UINT | 305
```

One-time validity period of the authentication token, in seconds.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_TAG_AUTH_TOKEN

```TypeScript
HUKS_TAG_AUTH_TOKEN = HuksTagType.HUKS_TAG_TYPE_BYTES | 306
```

Authentication token.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_TAG_KEY_AUTH_ACCESS_TYPE

```TypeScript
HUKS_TAG_KEY_AUTH_ACCESS_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT | 307
```

Access control type. For details, see [HuksAuthAccessType](arkts-universalkeystore-huks-huksauthaccesstype-e.md). This parameter must be set together with [HuksUserAuthType](arkts-universalkeystore-huks-huksuserauthtype-e.md).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_TAG_KEY_SECURE_SIGN_TYPE

```TypeScript
HUKS_TAG_KEY_SECURE_SIGN_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT | 308
```

Signature type of the key generated or imported.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_TAG_CHALLENGE_TYPE

```TypeScript
HUKS_TAG_CHALLENGE_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT | 309
```

Type of the challenge generated for a key. For details, see [HuksChallengeType](arkts-universalkeystore-huks-hukschallengetype-e.md).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_TAG_CHALLENGE_POS

```TypeScript
HUKS_TAG_CHALLENGE_POS = HuksTagType.HUKS_TAG_TYPE_UINT | 310
```

Position of the 8-byte valid value in a custom challenge. For details, see [HuksChallengePosition](arkts-universalkeystore-huks-hukschallengeposition-e.md).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_TAG_KEY_AUTH_PURPOSE

```TypeScript
HUKS_TAG_KEY_AUTH_PURPOSE = HuksTagType.HUKS_TAG_TYPE_UINT | 311
```

Key authentication purpose.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_TAG_AUTH_STORAGE_LEVEL

```TypeScript
HUKS_TAG_AUTH_STORAGE_LEVEL = HuksTagType.HUKS_TAG_TYPE_UINT | 316
```

Key storage security level, which is a value of [HuksAuthStorageLevel](arkts-universalkeystore-huks-huksauthstoragelevel-e.md).

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_TAG_USER_AUTH_MODE

```TypeScript
HUKS_TAG_USER_AUTH_MODE = HuksTagType.HUKS_TAG_TYPE_UINT | 319
```

User authentication mode. It is a value of [HuksUserAuthMode](arkts-universalkeystore-huks-huksuserauthmode-e.md).

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_CHALLENGE

```TypeScript
HUKS_TAG_ATTESTATION_CHALLENGE = HuksTagType.HUKS_TAG_TYPE_BYTES | 501
```

Challenge value used in the attestation.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_APPLICATION_ID

```TypeScript
HUKS_TAG_ATTESTATION_APPLICATION_ID = HuksTagType.HUKS_TAG_TYPE_BYTES | 502
```

Application ID used in the attestation.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_ID_BRAND

```TypeScript
HUKS_TAG_ATTESTATION_ID_BRAND = HuksTagType.HUKS_TAG_TYPE_BYTES | 503
```

Reserved field.

Note: This API is deprecated since API version 9. No substitute API is provided.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_ID_DEVICE

```TypeScript
HUKS_TAG_ATTESTATION_ID_DEVICE = HuksTagType.HUKS_TAG_TYPE_BYTES | 504
```

Reserved field.

Note: This API is deprecated since API version 9. No substitute API is provided.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_ID_PRODUCT

```TypeScript
HUKS_TAG_ATTESTATION_ID_PRODUCT = HuksTagType.HUKS_TAG_TYPE_BYTES | 505
```

Reserved field.

Note: This API is deprecated since API version 9. No substitute API is provided.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_ID_SERIAL

```TypeScript
HUKS_TAG_ATTESTATION_ID_SERIAL = HuksTagType.HUKS_TAG_TYPE_BYTES | 506
```

Reserved field.

Note: This API is deprecated since API version 9. No substitute API is provided.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_ID_IMEI

```TypeScript
HUKS_TAG_ATTESTATION_ID_IMEI = HuksTagType.HUKS_TAG_TYPE_BYTES | 507
```

Reserved field.

Note: This API is deprecated since API version 9. No substitute API is provided.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_ID_MEID

```TypeScript
HUKS_TAG_ATTESTATION_ID_MEID = HuksTagType.HUKS_TAG_TYPE_BYTES | 508
```

Reserved field.

Note: This API is deprecated since API version 9. No substitute API is provided.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_ID_MANUFACTURER

```TypeScript
HUKS_TAG_ATTESTATION_ID_MANUFACTURER = HuksTagType.HUKS_TAG_TYPE_BYTES | 509
```

Reserved field.

Note: This API is deprecated since API version 9. No substitute API is provided.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_ID_MODEL

```TypeScript
HUKS_TAG_ATTESTATION_ID_MODEL = HuksTagType.HUKS_TAG_TYPE_BYTES | 510
```

Reserved field.

Note: This API is deprecated since API version 9. No substitute API is provided.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_ID_ALIAS

```TypeScript
HUKS_TAG_ATTESTATION_ID_ALIAS = HuksTagType.HUKS_TAG_TYPE_BYTES | 511
```

Key alias used in the attestation.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_ID_SOCID

```TypeScript
HUKS_TAG_ATTESTATION_ID_SOCID = HuksTagType.HUKS_TAG_TYPE_BYTES | 512
```

Reserved field.

Note: This API is deprecated since API version 9. No substitute API is provided.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_ID_UDID

```TypeScript
HUKS_TAG_ATTESTATION_ID_UDID = HuksTagType.HUKS_TAG_TYPE_BYTES | 513
```

Reserved field.

Note: This API is deprecated since API version 9. No substitute API is provided.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_ID_SEC_LEVEL_INFO

```TypeScript
HUKS_TAG_ATTESTATION_ID_SEC_LEVEL_INFO = HuksTagType.HUKS_TAG_TYPE_BYTES | 514
```

Security level used in the attestation.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ATTESTATION_ID_VERSION_INFO

```TypeScript
HUKS_TAG_ATTESTATION_ID_VERSION_INFO = HuksTagType.HUKS_TAG_TYPE_BYTES | 515
```

Version information used in the attestation.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_TAG_KEY_OVERRIDE

```TypeScript
HUKS_TAG_KEY_OVERRIDE = HuksTagType.HUKS_TAG_TYPE_BOOL | 520
```

Whether to overwrite the key with the same name.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_TAG_AE_TAG_LEN

```TypeScript
HUKS_TAG_AE_TAG_LEN = HuksTagType.HUKS_TAG_TYPE_UINT | 521
```

Length of the specified AEAD tag, in bytes.

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_TAG_KEY_CLASS

```TypeScript
HUKS_TAG_KEY_CLASS = HuksTagType.HUKS_TAG_TYPE_UINT | 522
```

Key source.

**Since:** 22

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_TAG_KEY_ACCESS_GROUP

```TypeScript
HUKS_TAG_KEY_ACCESS_GROUP = HuksTagType.HUKS_TAG_TYPE_BYTES | 523
```

Information about the specified group.

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_TAG_KEY_SECURITY_LEVEL

```TypeScript
HUKS_TAG_KEY_SECURITY_LEVEL = HuksTagType.HUKS_TAG_TYPE_UINT | 526
```

Security level of the key.

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_TAG_AAD

```TypeScript
HUKS_TAG_AAD = HuksTagType.HUKS_TAG_TYPE_BYTES | 527
```

Additional verification data indicating the GCM or CCM mode.

**Since:** 24

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_TAG_CONTEXT

```TypeScript
HUKS_TAG_CONTEXT = HuksTagType.HUKS_TAG_TYPE_BYTES | 528
```

The tag indicates the context for crypto operations, such as ML-DSA, etc.

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_TAG_IS_KEY_ALIAS

```TypeScript
HUKS_TAG_IS_KEY_ALIAS = HuksTagType.HUKS_TAG_TYPE_BOOL | 1001
```

Whether to use the alias passed in during key generation.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_TAG_KEY_STORAGE_FLAG

```TypeScript
HUKS_TAG_KEY_STORAGE_FLAG = HuksTagType.HUKS_TAG_TYPE_UINT | 1002
```

Key storage mode.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_TAG_IS_ALLOWED_WRAP

```TypeScript
HUKS_TAG_IS_ALLOWED_WRAP = HuksTagType.HUKS_TAG_TYPE_BOOL | 1003
```

Reserved.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.Huks.Core
- API versions 8 to 11: SystemCapability.Security.Huks.Extension

## HUKS_TAG_KEY_WRAP_TYPE

```TypeScript
HUKS_TAG_KEY_WRAP_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT | 1004
```

Reserved.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.Huks.Core
- API versions 8 to 11: SystemCapability.Security.Huks.Extension

## HUKS_TAG_KEY_AUTH_ID

```TypeScript
HUKS_TAG_KEY_AUTH_ID = HuksTagType.HUKS_TAG_TYPE_BYTES | 1005
```

Reserved.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_TAG_KEY_ROLE

```TypeScript
HUKS_TAG_KEY_ROLE = HuksTagType.HUKS_TAG_TYPE_UINT | 1006
```

Reserved.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.Huks.Core
- API versions 8 to 11: SystemCapability.Security.Huks.Extension

## HUKS_TAG_KEY_FLAG

```TypeScript
HUKS_TAG_KEY_FLAG = HuksTagType.HUKS_TAG_TYPE_UINT | 1007
```

Flag of the key.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_TAG_IS_ASYNCHRONIZED

```TypeScript
HUKS_TAG_IS_ASYNCHRONIZED = HuksTagType.HUKS_TAG_TYPE_UINT | 1008
```

Reserved.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.Huks.Core
- API versions 8 to 11: SystemCapability.Security.Huks.Extension

## HUKS_TAG_SECURE_KEY_ALIAS

```TypeScript
HUKS_TAG_SECURE_KEY_ALIAS = HuksTagType.HUKS_TAG_TYPE_BOOL | 1009
```

OS patch level.

Note: This parameter is supported since API version 8 and deprecated since API version 9.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_TAG_SECURE_KEY_UUID

```TypeScript
HUKS_TAG_SECURE_KEY_UUID = HuksTagType.HUKS_TAG_TYPE_BYTES | 1010
```

Reserved field.

Note: This API is deprecated since API version 9. No substitute API is provided.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_TAG_KEY_DOMAIN

```TypeScript
HUKS_TAG_KEY_DOMAIN = HuksTagType.HUKS_TAG_TYPE_UINT | 1011
```

Reserved.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_TAG_IS_DEVICE_PASSWORD_SET

```TypeScript
HUKS_TAG_IS_DEVICE_PASSWORD_SET = HuksTagType.HUKS_TAG_TYPE_BOOL | 1012
```

Whether the key is accessible only when the user sets a lock screen password.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_TAG_PROCESS_NAME

```TypeScript
HUKS_TAG_PROCESS_NAME = HuksTagType.HUKS_TAG_TYPE_BYTES | 10001
```

OS patch level.

Note: This parameter is supported since API version 8 and deprecated since API version 9.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_TAG_PACKAGE_NAME

```TypeScript
HUKS_TAG_PACKAGE_NAME = HuksTagType.HUKS_TAG_TYPE_BYTES | 10002
```

Reserved field.

Note: This API is deprecated since API version 9. No substitute API is provided.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_TAG_ACCESS_TIME

```TypeScript
HUKS_TAG_ACCESS_TIME = HuksTagType.HUKS_TAG_TYPE_UINT | 10003
```

Reserved field.

Note: This API is deprecated since API version 9. No substitute API is provided.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_TAG_USES_TIME

```TypeScript
HUKS_TAG_USES_TIME = HuksTagType.HUKS_TAG_TYPE_UINT | 10004
```

Reserved field.

Note: This API is deprecated since API version 9. No substitute API is provided.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_TAG_CRYPTO_CTX

```TypeScript
HUKS_TAG_CRYPTO_CTX = HuksTagType.HUKS_TAG_TYPE_ULONG | 10005
```

Reserved field.

Note: This API is deprecated since API version 9. No substitute API is provided.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_TAG_KEY

```TypeScript
HUKS_TAG_KEY = HuksTagType.HUKS_TAG_TYPE_BYTES | 10006
```

Reserved.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_TAG_KEY_VERSION

```TypeScript
HUKS_TAG_KEY_VERSION = HuksTagType.HUKS_TAG_TYPE_UINT | 10007
```

Reserved field.

Note: This API is deprecated since API version 9. No substitute API is provided.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_TAG_PAYLOAD_LEN

```TypeScript
HUKS_TAG_PAYLOAD_LEN = HuksTagType.HUKS_TAG_TYPE_UINT | 10008
```

Reserved field.

Note: This API is deprecated since API version 9. No substitute API is provided.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Security.Huks.Extension

## HUKS_TAG_AE_TAG

```TypeScript
HUKS_TAG_AE_TAG = HuksTagType.HUKS_TAG_TYPE_BYTES | 10009
```

Used to pass in the AEAD in GCM mode.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_TAG_IS_KEY_HANDLE

```TypeScript
HUKS_TAG_IS_KEY_HANDLE = HuksTagType.HUKS_TAG_TYPE_ULONG | 10010
```

OS patch level.

Note: This parameter is supported since API version 8 and deprecated since API version 9.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_TAG_OS_VERSION

```TypeScript
HUKS_TAG_OS_VERSION = HuksTagType.HUKS_TAG_TYPE_UINT | 10101
```

OS version.

Note: This parameter is supported since API version 8 and deprecated since API version 9.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_TAG_OS_PATCHLEVEL

```TypeScript
HUKS_TAG_OS_PATCHLEVEL = HuksTagType.HUKS_TAG_TYPE_UINT | 10102
```

OS patch level.

Note: This parameter is supported since API version 8 and deprecated since API version 9.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_TAG_SYMMETRIC_KEY_DATA

```TypeScript
HUKS_TAG_SYMMETRIC_KEY_DATA = HuksTagType.HUKS_TAG_TYPE_BYTES | 20001
```

Reserved.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Huks.Core

## HUKS_TAG_ASYMMETRIC_PUBLIC_KEY_DATA

```TypeScript
HUKS_TAG_ASYMMETRIC_PUBLIC_KEY_DATA = HuksTagType.HUKS_TAG_TYPE_BYTES | 20002
```

Reserved.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.Huks.Core
- API versions 8 to 11: SystemCapability.Security.Huks.Extension

## HUKS_TAG_ASYMMETRIC_PRIVATE_KEY_DATA

```TypeScript
HUKS_TAG_ASYMMETRIC_PRIVATE_KEY_DATA = HuksTagType.HUKS_TAG_TYPE_BYTES | 20003
```

Reserved.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.Huks.Core
- API versions 8 to 11: SystemCapability.Security.Huks.Extension
