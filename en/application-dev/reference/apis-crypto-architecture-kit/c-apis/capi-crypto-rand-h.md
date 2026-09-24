# crypto_rand.h

## Overview

Defines the random number generator interfaces.

**Include**: <CryptoArchitectureKit/crypto_rand.h>

**Library**: libohcrypto.so

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 20

**Related module**: [CryptoRandApi](capi-cryptorandapi.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_CryptoRand](capi-cryptorandapi-oh-cryptorand.md) | OH_CryptoRand | Random number generator structure, representing a random number generator context. |

### Function

| Name | Description |
| -- | -- |
| [OH_Crypto_ErrCode OH_CryptoRand_Create(OH_CryptoRand **ctx)](#oh_cryptorand_create) | Creates a random number generator context. |
| [OH_Crypto_ErrCode OH_CryptoRand_GenerateRandom(OH_CryptoRand *ctx, int len, Crypto_DataBlob *out)](#oh_cryptorand_generaterandom) | Generates random numbers. |
| [const char *OH_CryptoRand_GetAlgoName(OH_CryptoRand *ctx)](#oh_cryptorand_getalgoname) | Obtains the algorithm name of the random number generator. |
| [OH_Crypto_ErrCode OH_CryptoRand_SetSeed(OH_CryptoRand *ctx, Crypto_DataBlob *seed)](#oh_cryptorand_setseed) | Sets the seed for the random number generator. |
| [OH_Crypto_ErrCode OH_CryptoRand_EnableHardwareEntropy(OH_CryptoRand *ctx)](#oh_cryptorand_enablehardwareentropy) | Enables hardware entropy source. |
| [void OH_CryptoRand_Destroy(OH_CryptoRand *ctx)](#oh_cryptorand_destroy) | Destroys the random number generator context. |

## Function description

### OH_CryptoRand_Create()

```c
OH_Crypto_ErrCode OH_CryptoRand_Create(OH_CryptoRand **ctx)
```

**Description**

Creates a random number generator context.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoRand](capi-cryptorandapi-oh-cryptorand.md) **ctx | [out] Pointer to the random number generator context pointer. ctx cannot be NULL, *ctx must be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>[CRYPTO_SUCCESS](capi-crypto-common-h.md#oh_crypto_errcode) if the operation succeeds.</li>          <li>[CRYPTO_PARAMETER_CHECK_FAILED](capi-crypto-common-h.md#oh_crypto_errcode) if ctx is NULL.</li>          <li>[CRYPTO_NOT_SUPPORTED](capi-crypto-common-h.md#oh_crypto_errcode) if unsupported operation or algorithm.</li>          <li>[CRYPTO_MEMORY_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if memory operation fails.</li>          <li>[CRYPTO_OPERTION_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if crypto operation fails.</li>          </ul> |

### OH_CryptoRand_GenerateRandom()

```c
OH_Crypto_ErrCode OH_CryptoRand_GenerateRandom(OH_CryptoRand *ctx, int len, Crypto_DataBlob *out)
```

**Description**

Generates random numbers.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoRand](capi-cryptorandapi-oh-cryptorand.md) *ctx | [in] Random number generator context. Cannot be NULL. |
| int len | [in] Byte length of the random number. |
| Crypto_DataBlob *out | [out] Pointer to the Crypto_DataBlob structure for storing the random number. Cannot be NULL. Initialize out to {0} before calling. Do not pre-allocate out->data. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>[CRYPTO_SUCCESS](capi-crypto-common-h.md#oh_crypto_errcode) if the operation succeeds.</li>          <li>[CRYPTO_PARAMETER_CHECK_FAILED](capi-crypto-common-h.md#oh_crypto_errcode) if ctx or out is NULL, or len is less than             or equal to 0.</li>          <li>[CRYPTO_NOT_SUPPORTED](capi-crypto-common-h.md#oh_crypto_errcode) if unsupported operation or algorithm.</li>          <li>[CRYPTO_MEMORY_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if memory operation fails.</li>          <li>[CRYPTO_OPERTION_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if crypto operation fails.</li>          </ul> |

### OH_CryptoRand_GetAlgoName()

```c
const char *OH_CryptoRand_GetAlgoName(OH_CryptoRand *ctx)
```

**Description**

Obtains the algorithm name of the random number generator.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoRand](capi-cryptorandapi-oh-cryptorand.md) *ctx | [in] Random number generator context. Cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| const char * | Returns the random number generator algorithm name. No need to free by the caller. Invalid after the context      is destroyed. |

### OH_CryptoRand_SetSeed()

```c
OH_Crypto_ErrCode OH_CryptoRand_SetSeed(OH_CryptoRand *ctx, Crypto_DataBlob *seed)
```

**Description**

Sets the seed for the random number generator.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoRand](capi-cryptorandapi-oh-cryptorand.md) *ctx | [in] Random number generator context. Cannot be NULL. |
| Crypto_DataBlob *seed | [in] Seed data. This function performs a deep copy of the data in seed. The caller can release seed immediately after the function returns. Cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>[CRYPTO_SUCCESS](capi-crypto-common-h.md#oh_crypto_errcode) if the operation succeeds.</li>          <li>[CRYPTO_PARAMETER_CHECK_FAILED](capi-crypto-common-h.md#oh_crypto_errcode) if ctx is NULL, or seed is invalid             (seed is NULL, seed->data is NULL, seed->len is 0, or seed->len exceeds INT_MAX).</li>          <li>[CRYPTO_NOT_SUPPORTED](capi-crypto-common-h.md#oh_crypto_errcode) if unsupported operation or algorithm.</li>          <li>[CRYPTO_MEMORY_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if memory operation fails.</li>          <li>[CRYPTO_OPERTION_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if crypto operation fails.</li>          </ul> |

### OH_CryptoRand_EnableHardwareEntropy()

```c
OH_Crypto_ErrCode OH_CryptoRand_EnableHardwareEntropy(OH_CryptoRand *ctx)
```

**Description**

Enables hardware entropy source.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoRand](capi-cryptorandapi-oh-cryptorand.md) *ctx | [in] Random number generator context. Cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>[CRYPTO_SUCCESS](capi-crypto-common-h.md#oh_crypto_errcode) if the operation succeeds.</li>          <li>[CRYPTO_PARAMETER_CHECK_FAILED](capi-crypto-common-h.md#oh_crypto_errcode) if ctx is NULL.</li>          <li>[CRYPTO_NOT_SUPPORTED](capi-crypto-common-h.md#oh_crypto_errcode) if unsupported operation or algorithm.</li>          <li>[CRYPTO_MEMORY_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if memory operation fails.</li>          <li>[CRYPTO_OPERTION_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if crypto operation fails.</li>          </ul> |

### OH_CryptoRand_Destroy()

```c
void OH_CryptoRand_Destroy(OH_CryptoRand *ctx)
```

**Description**

Destroys the random number generator context.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoRand](capi-cryptorandapi-oh-cryptorand.md) *ctx | [in] Random number generator context. |


