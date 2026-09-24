# crypto_mac.h

## Overview

Defines the message authentication code interfaces.

**Include**: <CryptoArchitectureKit/crypto_mac.h>

**Library**: libohcrypto.so

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 20

**Related module**: [CryptoMacApi](capi-cryptomacapi.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_CryptoMac](capi-cryptomacapi-oh-cryptomac.md) | OH_CryptoMac | MAC structure, representing a MAC context. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [CryptoMac_ParamType](#cryptomac_paramtype) | CryptoMac_ParamType | Defines MAC algorithm parameter types. |

### Function

| Name | Description |
| -- | -- |
| [OH_Crypto_ErrCode OH_CryptoMac_Create(const char *algoName, OH_CryptoMac **ctx)](#oh_cryptomac_create) | Creates a MAC context based on the given algorithm name. |
| [OH_Crypto_ErrCode OH_CryptoMac_SetParam(OH_CryptoMac *ctx, CryptoMac_ParamType type, const Crypto_DataBlob *value)](#oh_cryptomac_setparam) | Sets the specified parameter of the MAC context. |
| [OH_Crypto_ErrCode OH_CryptoMac_Init(OH_CryptoMac *ctx, const OH_CryptoSymKey *key)](#oh_cryptomac_init) | Initializes the MAC context with a symmetric key. |
| [OH_Crypto_ErrCode OH_CryptoMac_Update(OH_CryptoMac *ctx, const Crypto_DataBlob *in)](#oh_cryptomac_update) | Updates MAC data. |
| [OH_Crypto_ErrCode OH_CryptoMac_Final(OH_CryptoMac *ctx, Crypto_DataBlob *out)](#oh_cryptomac_final) | Finishes the MAC operation. |
| [OH_Crypto_ErrCode OH_CryptoMac_GetLength(OH_CryptoMac *ctx, uint32_t *length)](#oh_cryptomac_getlength) | Obtains the MAC result length. |
| [void OH_CryptoMac_Destroy(OH_CryptoMac *ctx)](#oh_cryptomac_destroy) | Destroys the MAC context. |

## Enum type description

### CryptoMac_ParamType

```c
enum CryptoMac_ParamType
```

**Description**

Defines MAC algorithm parameter types.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 20

| Enum item | Description |
| -- | -- |
| CRYPTO_MAC_DIGEST_NAME_STR = 0 | Algorithm name of the message digest function for HMAC, set via [OH_CryptoMac_SetParam](capi-crypto-mac-h.md#oh_cryptomac_setparam). Values: "SHA1", "SHA224", "SHA256", "SHA384", "SHA512", "SM3", "MD5". "SHA3-256", "SHA3-384", "SHA3-512" are supported since API version 26.0.0.<br>**Since**: 20 |
| CRYPTO_MAC_CIPHER_NAME_STR = 1 | Algorithm name of the symmetric cipher function for CMAC, set via [OH_CryptoMac_SetParam](capi-crypto-mac-h.md#oh_cryptomac_setparam). Values: "AES128", "AES256".<br>**Since**: 20 |


## Function description

### OH_CryptoMac_Create()

```c
OH_Crypto_ErrCode OH_CryptoMac_Create(const char *algoName, OH_CryptoMac **ctx)
```

**Description**

Creates a MAC context based on the given algorithm name.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *algoName | [in] MAC algorithm name. Cannot be NULL. Supports "HMAC" and "CMAC". |
| [OH_CryptoMac](capi-cryptomacapi-oh-cryptomac.md) **ctx | [out] Pointer to the MAC context pointer. ctx cannot be NULL, *ctx must be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>[CRYPTO_SUCCESS](capi-crypto-common-h.md#oh_crypto_errcode) if the operation succeeds.</li>          <li>[CRYPTO_PARAMETER_CHECK_FAILED](capi-crypto-common-h.md#oh_crypto_errcode) if algoName or ctx is NULL,              algoName is not "HMAC" or "CMAC".</li>          <li>[CRYPTO_NOT_SUPPORTED](capi-crypto-common-h.md#oh_crypto_errcode) if unsupported operation or algorithm.</li>          <li>[CRYPTO_MEMORY_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if memory operation fails.</li>          <li>[CRYPTO_OPERTION_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if crypto operation fails.</li>          </ul> |

**Reference**:

[OH_CryptoMac_SetParam](capi-crypto-mac-h.md#oh_cryptomac_setparam) Sets the specified parameter of the MAC context


### OH_CryptoMac_SetParam()

```c
OH_Crypto_ErrCode OH_CryptoMac_SetParam(OH_CryptoMac *ctx, CryptoMac_ParamType type, const Crypto_DataBlob *value)
```

**Description**

Sets the specified parameter of the MAC context.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoMac](capi-cryptomacapi-oh-cryptomac.md) *ctx | [in] MAC context. Cannot be NULL. |
| [CryptoMac_ParamType](capi-crypto-mac-h.md#cryptomac_paramtype) type | [in] MAC parameter type. |
| const Crypto_DataBlob *value | [in] Parameter value. This function performs a deep copy of the data in value. The caller can release value immediately after the function returns. Cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>[CRYPTO_SUCCESS](capi-crypto-common-h.md#oh_crypto_errcode) if the operation succeeds.</li>          <li>[CRYPTO_PARAMETER_CHECK_FAILED](capi-crypto-common-h.md#oh_crypto_errcode) if ctx, value, or             value->data is NULL, type is not valid for the MAC algorithm,             or the digest/cipher algorithm name is not supported.</li>          <li>[CRYPTO_NOT_SUPPORTED](capi-crypto-common-h.md#oh_crypto_errcode) if unsupported operation or algorithm.</li>          <li>[CRYPTO_MEMORY_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if memory allocation for param copy fails.</li>          <li>[CRYPTO_OPERTION_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if crypto operation fails.</li>          </ul> |

**Reference**:

[OH_CryptoMac_Init](capi-crypto-mac-h.md#oh_cryptomac_init) Initializes the MAC context with a symmetric key


### OH_CryptoMac_Init()

```c
OH_Crypto_ErrCode OH_CryptoMac_Init(OH_CryptoMac *ctx, const OH_CryptoSymKey *key)
```

**Description**

Initializes the MAC context with a symmetric key.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoMac](capi-cryptomacapi-oh-cryptomac.md) *ctx | [in] MAC context. Cannot be NULL. |
| const OH_CryptoSymKey *key | [in] Symmetric key. Cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>[CRYPTO_SUCCESS](capi-crypto-common-h.md#oh_crypto_errcode) if the operation succeeds.</li>          <li>[CRYPTO_PARAMETER_CHECK_FAILED](capi-crypto-common-h.md#oh_crypto_errcode) if ctx or key is NULL.</li>          <li>[CRYPTO_NOT_SUPPORTED](capi-crypto-common-h.md#oh_crypto_errcode) if unsupported operation or algorithm.</li>          <li>[CRYPTO_MEMORY_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if memory operation fails.</li>          <li>[CRYPTO_OPERTION_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if MAC init fails. Possible causes:             the key length does not match the algorithm (e.g. CMAC with AES-128 requires a 16-byte key).</li>          </ul> |

**Reference**:

[OH_CryptoMac_Update](capi-crypto-mac-h.md#oh_cryptomac_update) Updates MAC data


### OH_CryptoMac_Update()

```c
OH_Crypto_ErrCode OH_CryptoMac_Update(OH_CryptoMac *ctx, const Crypto_DataBlob *in)
```

**Description**

Updates MAC data.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoMac](capi-cryptomacapi-oh-cryptomac.md) *ctx | [in] MAC context. Cannot be NULL. |
| const Crypto_DataBlob *in | [in] Data to update. Cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>[CRYPTO_SUCCESS](capi-crypto-common-h.md#oh_crypto_errcode) if the operation succeeds.</li>          <li>[CRYPTO_PARAMETER_CHECK_FAILED](capi-crypto-common-h.md#oh_crypto_errcode) if ctx or in is NULL.</li>          <li>[CRYPTO_NOT_SUPPORTED](capi-crypto-common-h.md#oh_crypto_errcode) if unsupported operation or algorithm.</li>          <li>[CRYPTO_MEMORY_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if memory operation fails.</li>          <li>[CRYPTO_OPERTION_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if MAC update fails.</li>          </ul> |

**Reference**:

[OH_CryptoMac_Final](capi-crypto-mac-h.md#oh_cryptomac_final) Finishes the MAC operation


### OH_CryptoMac_Final()

```c
OH_Crypto_ErrCode OH_CryptoMac_Final(OH_CryptoMac *ctx, Crypto_DataBlob *out)
```

**Description**

Finishes the MAC operation.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoMac](capi-cryptomacapi-oh-cryptomac.md) *ctx | [in] MAC context. Cannot be NULL. |
| Crypto_DataBlob *out | [out] Pointer to the Crypto_DataBlob structure for storing the MAC result. Cannot be NULL. Initialize out to {0} before calling. Do not pre-allocate out->data. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>[CRYPTO_SUCCESS](capi-crypto-common-h.md#oh_crypto_errcode) if the operation succeeds.</li>          <li>[CRYPTO_PARAMETER_CHECK_FAILED](capi-crypto-common-h.md#oh_crypto_errcode) if ctx or out is NULL.</li>          <li>[CRYPTO_NOT_SUPPORTED](capi-crypto-common-h.md#oh_crypto_errcode) if unsupported operation or algorithm.</li>          <li>[CRYPTO_MEMORY_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if memory operation fails.</li>          <li>[CRYPTO_OPERTION_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if MAC final fails.</li>          </ul> |

### OH_CryptoMac_GetLength()

```c
OH_Crypto_ErrCode OH_CryptoMac_GetLength(OH_CryptoMac *ctx, uint32_t *length)
```

**Description**

Obtains the MAC result length.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoMac](capi-cryptomacapi-oh-cryptomac.md) *ctx | [in] MAC context. Cannot be NULL. |
| uint32_t *length | [out] MAC length in bytes. Cannot be NULL. Memory allocated by the caller. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>[CRYPTO_SUCCESS](capi-crypto-common-h.md#oh_crypto_errcode) if the operation succeeds.</li>          <li>[CRYPTO_PARAMETER_CHECK_FAILED](capi-crypto-common-h.md#oh_crypto_errcode) if ctx or length is NULL.</li>          <li>[CRYPTO_NOT_SUPPORTED](capi-crypto-common-h.md#oh_crypto_errcode) if unsupported operation or algorithm.</li>          <li>[CRYPTO_MEMORY_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if memory operation fails.</li>          <li>[CRYPTO_OPERTION_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if crypto operation fails.</li>          </ul> |

### OH_CryptoMac_Destroy()

```c
void OH_CryptoMac_Destroy(OH_CryptoMac *ctx)
```

**Description**

Destroys the MAC context.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoMac](capi-cryptomacapi-oh-cryptomac.md) *ctx | [in] MAC context. |


