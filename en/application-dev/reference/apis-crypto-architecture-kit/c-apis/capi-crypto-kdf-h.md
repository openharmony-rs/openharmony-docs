# crypto_kdf.h

## Overview

Defines the key derivation interfaces.

**Include**: <CryptoArchitectureKit/crypto_kdf.h>

**Library**: libohcrypto.so

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 20

**Related module**: [CryptoKdfApi](capi-cryptokdfapi.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_CryptoKdf](capi-cryptokdfapi-oh-cryptokdf.md) | OH_CryptoKdf | KDF structure, representing a KDF context. |
| [OH_CryptoKdfParams](capi-cryptokdfapi-oh-cryptokdfparams.md) | OH_CryptoKdfParams | KDF parameters structure, representing KDF parameters. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [CryptoKdf_ParamType](#cryptokdf_paramtype) | CryptoKdf_ParamType | Defines KDF parameter types. |

### Function

| Name | Description |
| -- | -- |
| [OH_Crypto_ErrCode OH_CryptoKdfParams_Create(const char *algoName, OH_CryptoKdfParams **params)](#oh_cryptokdfparams_create) | Creates KDF parameters. |
| [OH_Crypto_ErrCode OH_CryptoKdfParams_SetParam(OH_CryptoKdfParams *params, CryptoKdf_ParamType type, Crypto_DataBlob *value)](#oh_cryptokdfparams_setparam) | Sets KDF parameters. |
| [void OH_CryptoKdfParams_Destroy(OH_CryptoKdfParams *params)](#oh_cryptokdfparams_destroy) | Destroys KDF parameters. |
| [OH_Crypto_ErrCode OH_CryptoKdf_Create(const char *algoName, OH_CryptoKdf **ctx)](#oh_cryptokdf_create) | Creates a KDF context based on the given algorithm name. |
| [OH_Crypto_ErrCode OH_CryptoKdf_Derive(OH_CryptoKdf *ctx, const OH_CryptoKdfParams *params, int keyLen, Crypto_DataBlob *key)](#oh_cryptokdf_derive) | Derives a key. |
| [void OH_CryptoKdf_Destroy(OH_CryptoKdf *ctx)](#oh_cryptokdf_destroy) | Destroys the KDF context. |

## Enum type description

### CryptoKdf_ParamType

```c
enum CryptoKdf_ParamType
```

**Description**

Defines KDF parameter types.

**Since**: 20

| Enum item | Description |
| -- | -- |
| CRYPTO_KDF_KEY_DATABLOB = 0 | Key or password for KDF.<br>**Since**: 20 |
| CRYPTO_KDF_SALT_DATABLOB = 1 | Salt value for KDF.<br>**Since**: 20 |
| CRYPTO_KDF_INFO_DATABLOB = 2 | Info for KDF.<br>**Since**: 20 |
| CRYPTO_KDF_ITER_COUNT_INT = 3 | Iteration count for PBKDF2.<br>**Since**: 20 |
| CRYPTO_KDF_SCRYPT_N_UINT64 = 4 | n parameter for SCRYPT KDF.<br>**Since**: 20 |
| CRYPTO_KDF_SCRYPT_R_UINT64 = 5 | r parameter for SCRYPT KDF.<br>**Since**: 20 |
| CRYPTO_KDF_SCRYPT_P_UINT64 = 6 | p parameter for SCRYPT KDF.<br>**Since**: 20 |
| CRYPTO_KDF_SCRYPT_MAX_MEM_UINT64 = 7 | Maximum memory parameter for SCRYPT KDF.<br>**Since**: 20 |


## Function description

### OH_CryptoKdfParams_Create()

```c
OH_Crypto_ErrCode OH_CryptoKdfParams_Create(const char *algoName, OH_CryptoKdfParams **params)
```

**Description**

Creates KDF parameters.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *algoName | [in] KDF parameter algorithm name. Cannot be NULL. Values: - "HKDF", "PBKDF2", "SCRYPT" supported since API version 20. - "X963KDF" supported since API version 22. |
| [OH_CryptoKdfParams](capi-cryptokdfapi-oh-cryptokdfparams.md) **params | [out] Pointer to the KDF parameters pointer. params cannot be NULL, *params must be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_PARAMETER_CHECK_FAILED} if algoName or params is NULL,<br>            algoName is not a supported KDF type.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if unsupported operation or algorithm.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory allocation fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if crypto operation fails.</li>          </ul> |

**Reference**:

[OH_CryptoKdfParams_SetParam](capi-crypto-kdf-h.md#oh_cryptokdfparams_setparam) Sets KDF parameters


### OH_CryptoKdfParams_SetParam()

```c
OH_Crypto_ErrCode OH_CryptoKdfParams_SetParam(OH_CryptoKdfParams *params, CryptoKdf_ParamType type, Crypto_DataBlob *value)
```

**Description**

Sets KDF parameters.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoKdfParams](capi-cryptokdfapi-oh-cryptokdfparams.md) *params | [in] KDF parameters. Cannot be NULL. |
| [CryptoKdf_ParamType](capi-crypto-kdf-h.md#cryptokdf_paramtype) type | [in] KDF parameter type. |
| Crypto_DataBlob *value | [in] KDF parameter value. This function performs a deep copy of the data in value. The caller can release value immediately after the function returns. Cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_PARAMETER_CHECK_FAILED} if params or value is NULL,<br>           value->data is NULL, or type is not valid for the KDF algorithm.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if unsupported operation or algorithm.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory allocation for param copy fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if crypto operation fails.</li>          </ul> |

### OH_CryptoKdfParams_Destroy()

```c
void OH_CryptoKdfParams_Destroy(OH_CryptoKdfParams *params)
```

**Description**

Destroys KDF parameters.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoKdfParams](capi-cryptokdfapi-oh-cryptokdfparams.md) *params | [in] KDF parameters. |

### OH_CryptoKdf_Create()

```c
OH_Crypto_ErrCode OH_CryptoKdf_Create(const char *algoName, OH_CryptoKdf **ctx)
```

**Description**

Creates a KDF context based on the given algorithm name.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *algoName | [in] KDF algorithm name. Cannot be NULL. Format: "KDFType\|DigestAlgorithm". Values: - "PBKDF2\|SHA1", "PBKDF2\|SHA224", "PBKDF2\|SHA256", "PBKDF2\|SHA384", "PBKDF2\|SHA512", "PBKDF2\|SM3" supported since API version 20. "PBKDF2\|SHA3-256", "PBKDF2\|SHA3-384", "PBKDF2\|SHA3-512" supported since API version 26.0.0. - "HKDF\|SHA1", "HKDF\|SHA224", "HKDF\|SHA256", "HKDF\|SHA384", "HKDF\|SHA512", "HKDF\|SM3" supported since API version 20. HKDF supports an optional third parameter to specify the mode: "EXTRACT_AND_EXPAND" (default), "EXTRACT_ONLY", "EXPAND_ONLY", e.g. "HKDF\|SHA256\|EXTRACT_ONLY". "HKDF\|SHA3-256", "HKDF\|SHA3-384", "HKDF\|SHA3-512" supported since API version 26.0.0. - "SCRYPT" supported since API version 20. - "X963KDF\|SHA1", "X963KDF\|SHA224", "X963KDF\|SHA256", "X963KDF\|SHA384", "X963KDF\|SHA512" supported since API version 22. "X963KDF\|SHA3-256", "X963KDF\|SHA3-384", "X963KDF\|SHA3-512" supported since API version 26.0.0. |
| [OH_CryptoKdf](capi-cryptokdfapi-oh-cryptokdf.md) **ctx | [out] Pointer to the KDF context pointer. ctx cannot be NULL, *ctx must be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_PARAMETER_CHECK_FAILED} if algoName or ctx is NULL.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if the algorithm is not supported.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory allocation fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if crypto operation fails.</li>          </ul> |

**Reference**:

[OH_CryptoKdf_Derive](capi-crypto-kdf-h.md#oh_cryptokdf_derive) Derives a key


### OH_CryptoKdf_Derive()

```c
OH_Crypto_ErrCode OH_CryptoKdf_Derive(OH_CryptoKdf *ctx, const OH_CryptoKdfParams *params, int keyLen, Crypto_DataBlob *key)
```

**Description**

Derives a key.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoKdf](capi-cryptokdfapi-oh-cryptokdf.md) *ctx | [in] KDF context. Cannot be NULL. |
| [const OH_CryptoKdfParams](capi-cryptokdfapi-oh-cryptokdfparams.md) *params | [in] KDF parameters. Cannot be NULL. |
| int keyLen | [in] Byte length of the derived key. |
| Crypto_DataBlob *key | [out] Pointer to the Crypto_DataBlob structure for storing the derived key. Cannot be NULL. Initialize key to {0} before calling. Do not pre-allocate key->data. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_PARAMETER_CHECK_FAILED} if ctx, params, or key is NULL,<br>           or keyLen is less than or equal to 0, or required<br>           parameters are missing (e.g. HKDF key, Scrypt password or salt).</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if the algorithm is not supported.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory allocation fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if the key derivation fails.</li>          </ul> |

### OH_CryptoKdf_Destroy()

```c
void OH_CryptoKdf_Destroy(OH_CryptoKdf *ctx)
```

**Description**

Destroys the KDF context.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoKdf](capi-cryptokdfapi-oh-cryptokdf.md) *ctx | [in] KDF context. |


