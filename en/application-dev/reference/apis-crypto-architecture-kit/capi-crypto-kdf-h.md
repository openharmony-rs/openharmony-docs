# crypto_kdf.h

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=76caeef80126e754bb89b8cf8b2b7380f3d3d3a7 translatedAt=2026-09-02T07:18:26.478Z pushedAt=2026-09-04T03:47:56.840Z -->

## Overview

Defines key derivation function (KDF) APIs.

**Header file**: <CryptoArchitectureKit/crypto_kdf.h>

**Library**: libohcrypto.so

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 20

**Related module**: [CryptoKdfApi](capi-cryptokdfapi.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_CryptoKdf](capi-cryptokdfapi-oh-cryptokdf.md) | OH_CryptoKdf | Defines a KDF struct, which indicates the KDF context. |
| [OH_CryptoKdfParams](capi-cryptokdfapi-oh-cryptokdfparams.md) | OH_CryptoKdfParams | Defines a KDF parameter struct, which indicates the KDF parameters. |

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [CryptoKdf_ParamType](#cryptokdf_paramtype) | CryptoKdf_ParamType | Enumerates KDF parameter types. |

### Functions

| Name| Description|
| -- | -- |
| [OH_Crypto_ErrCode OH_CryptoKdfParams_Create(const char *algoName, OH_CryptoKdfParams **params)](#oh_cryptokdfparams_create) | Creates KDF parameters.<br> **Note:** The created resource must be destroyed by calling [OH_CryptoKdfParams_Destroy](capi-crypto-kdf-h.md#oh_cryptokdfparams_destroy).  |
| [OH_Crypto_ErrCode OH_CryptoKdfParams_SetParam(OH_CryptoKdfParams *params, CryptoKdf_ParamType type, Crypto_DataBlob *value)](#oh_cryptokdfparams_setparam) | Sets KDF parameters. |
| [void OH_CryptoKdfParams_Destroy(OH_CryptoKdfParams *params)](#oh_cryptokdfparams_destroy) | Destroys KDF parameters. |
| [OH_Crypto_ErrCode OH_CryptoKdf_Create(const char *algoName, OH_CryptoKdf **ctx)](#oh_cryptokdf_create) | Creates a KDF context based on the given algorithm name.<br> **Note:** The created resource must be destroyed by calling [OH_CryptoKdf_Destroy](capi-crypto-kdf-h.md#oh_cryptokdf_destroy).  |
| [OH_Crypto_ErrCode OH_CryptoKdf_Derive(OH_CryptoKdf *ctx, const OH_CryptoKdfParams *params, int keyLen, Crypto_DataBlob *key)](#oh_cryptokdf_derive) | Derives a key.<br> Note: After the use is complete, the memory for storing the **key** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob).|
| [void OH_CryptoKdf_Destroy(OH_CryptoKdf *ctx)](#oh_cryptokdf_destroy) | Destroys the KDF context. |

## Enum Description

### CryptoKdf_ParamType

```c
enum CryptoKdf_ParamType
```

**Description**

Enumerates KDF parameter types.

**Since**: 20

| Enum Item| Description|
| -- | -- |
| CRYPTO_KDF_KEY_DATABLOB = 0 | Key or password of the KDF.|
| CRYPTO_KDF_SALT_DATABLOB = 1 | Salt value of the KDF.|
| CRYPTO_KDF_INFO_DATABLOB = 2 | Information of the KDF. |
| CRYPTO_KDF_ITER_COUNT_INT = 3 | Iteration count of PBKDF2.|
| CRYPTO_KDF_SCRYPT_N_UINT64 = 4 | Parameter **n** of the SCRYPT KDF.|
| CRYPTO_KDF_SCRYPT_R_UINT64 = 5 | Parameter **r** of the SCRYPT KDF.|
| CRYPTO_KDF_SCRYPT_P_UINT64 = 6 | Parameter **p** of the SCRYPT KDF.|
| CRYPTO_KDF_SCRYPT_MAX_MEM_UINT64 = 7 | Maximum memory parameter of the SCRYPT KDF. |


## Function Description

### OH_CryptoKdfParams_Create()

```c
OH_Crypto_ErrCode OH_CryptoKdfParams_Create(const char *algoName, OH_CryptoKdfParams **params)
```

**Description**

Creates KDF parameters.

**Note:** The created resource must be destroyed by calling [OH_CryptoKdfParams_Destroy](capi-crypto-kdf-h.md#oh_cryptokdfparams_destroy).

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| const char *algoName | Input parameter, indicating the KDF algorithm name, which cannot be null. The options are as follows:<br>- Since API version 20, **HKDF**, **PBKDF2**, and **SCRYPT** are supported.<br>- Since API version 22, **X963KDF** is supported. |
| [OH_CryptoKdfParams](capi-cryptokdfapi-oh-cryptokdfparams.md) **params | Output parameter, indicating a pointer to the KDF parameter. The value of **params** cannot be null, but the value of ***params** must be null. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: The value of **algoName** or **params** is null, or **algoName** is not a supported KDF type.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation fails.<br>**CRYPTO_OPERTION_ERROR**: The cryptographic operation fails. |

**Reference**

[OH_CryptoKdfParams_SetParam](capi-crypto-kdf-h.md#oh_cryptokdfparams_setparam) sets KDF parameters.


### OH_CryptoKdfParams_SetParam()

```c
OH_Crypto_ErrCode OH_CryptoKdfParams_SetParam(OH_CryptoKdfParams *params, CryptoKdf_ParamType type, Crypto_DataBlob *value)
```

**Description**

Sets KDF parameters.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoKdfParams](capi-cryptokdfapi-oh-cryptokdfparams.md) *params | Input parameter, indicating KDF parameters. The value cannot be null. |
| [CryptoKdf_ParamType](capi-crypto-kdf-h.md#cryptokdf_paramtype) type | Input parameter, indicating the KDF parameter type. |
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *value | Input parameter, indicating the KDF parameter value. This API performs deep copy of the data in **value**. The caller can immediately release **value** after the API returns a result. The value cannot be null. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: The value of **params** or **value** is null, **data** in **value** is null, or **type** is invalid for the KDF algorithm.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation for the parameter copy fails.<br>**CRYPTO_OPERTION_ERROR**: The cryptographic operation fails. |

### OH_CryptoKdfParams_Destroy()

```c
void OH_CryptoKdfParams_Destroy(OH_CryptoKdfParams *params)
```

**Description**

Destroys KDF parameters.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoKdfParams](capi-cryptokdfapi-oh-cryptokdfparams.md) *params | Input parameter, indicating KDF parameters. |

### OH_CryptoKdf_Create()

```c
OH_Crypto_ErrCode OH_CryptoKdf_Create(const char *algoName, OH_CryptoKdf **ctx)
```

**Description**

Creates a KDF context based on the given algorithm name.

Note: The created resource must be destroyed by calling [OH_CryptoKdf_Destroy](capi-crypto-kdf-h.md#oh_cryptokdf_destroy).

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| const char *algoName | Input parameter, indicating the KDF algorithm name. The value cannot be null. The value is in the format of **KDF type\|digest algorithm**. The options are as follows:<br>- Since API version 20, **PBKDF2\|SHA1**, **PBKDF2\|SHA224**, **PBKDF2\|SHA256**, **PBKDF2\|SHA384**, **PBKDF2\|SHA512**, and **PBKDF2\|SM3** are supported.<br>- Since API version 26.0.0, **PBKDF2\|SHA3-256**, **PBKDF2\|SHA3-384**, and **PBKDF2\|SHA3-512** are supported.<br>- Since API version 20, **HKDF\|SHA1**, **HKDF\|SHA224**, **HKDF\|SHA256**, **HKDF\|SHA384**, **HKDF\|SHA512**, and **HKDF\|SM3** are supported. An optional third parameter can be used for HKDF to specify the mode: **EXTRACT_AND_EXPAND** (default), **EXTRACT_ONLY**, or **EXPAND_ONLY**. For example, **HKDF\|SHA256\|EXTRACT_ONLY**.<br>- Since API version 26.0.0, **HKDF\|SHA3-256**, **HKDF\|SHA3-384**, and **HKDF\|SHA3-512** are supported.<br>- Since API version 20, **SCRYPT** is supported.<br>- Since API version 22, **X963KDF\|SHA1**, **X963KDF\|SHA224**, **X963KDF\|SHA256**, **X963KDF\|SHA384**, and **X963KDF\|SHA512** are supported.<br> - Since API version 26.0.0, **X963KDF\|SHA3-256**, **X963KDF\|SHA3-384** and **X963KDF\|SHA3-512** are supported. |
| [OH_CryptoKdf](capi-cryptokdfapi-oh-cryptokdf.md) **ctx | Output parameter, indicating a pointer to the KDF context. The value of **ctx** cannot be null, but the value of ***ctx** must be null. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: The value of **algoName** or **ctx** is null.<br>**CRYPTO_NOT_SUPPORTED**: The algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation fails.<br>**CRYPTO_OPERTION_ERROR**: The cryptographic operation fails. |

**Reference**

[OH_CryptoKdf_Derive](capi-crypto-kdf-h.md#oh_cryptokdf_derive) for deriving a key.


### OH_CryptoKdf_Derive()

```c
OH_Crypto_ErrCode OH_CryptoKdf_Derive(OH_CryptoKdf *ctx, const OH_CryptoKdfParams *params, int keyLen, Crypto_DataBlob *key)
```

**Description**

Derives a key.

Note: After the method is used, the memory for storing the **key** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob).

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoKdf](capi-cryptokdfapi-oh-cryptokdf.md) *ctx | Input parameter, indicating the KDF context. The value cannot be null. |
| [const OH_CryptoKdfParams](capi-cryptokdfapi-oh-cryptokdfparams.md) *params | Input parameter, indicating KDF parameters. The value cannot be null. |
| int keyLen | Input parameter, indicating the length of the derived key, in bytes. |
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *key | Output parameter, indicating a pointer to the **Crypto_DataBlob** struct used to store the derived key. The value cannot be null. Before calling this method, initialize **key** to 0. Do not set the **data** field of **key**. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: **ctx**, **params**, or **key** is null, **keyLen** is less than or equal to 0, or a mandatory parameter (such as the HKDF key, Scrypt password, or salt value) is missing.<br>**CRYPTO_NOT_SUPPORTED**: The algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation fails.<br>**CRYPTO_OPERTION_ERROR**: Key derivation fails. |

### OH_CryptoKdf_Destroy()

```c
void OH_CryptoKdf_Destroy(OH_CryptoKdf *ctx)
```

**Description**

Destroys the KDF context.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoKdf](capi-cryptokdfapi-oh-cryptokdf.md) *ctx | Input parameter, indicating the KDF context. |


