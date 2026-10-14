# crypto_rand.h

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=76caeef80126e754bb89b8cf8b2b7380f3d3d3a7 translatedAt=2026-09-02T07:18:07.712Z pushedAt=2026-09-04T06:31:19.394Z -->

## Overview

Defines APIs for a random number generator.

**Header file**: <CryptoArchitectureKit/crypto_rand.h>

**Library**: libohcrypto.so

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 20

**Related module**: [CryptoRandApi](capi-cryptorandapi.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_CryptoRand](capi-cryptorandapi-oh-cryptorand.md) | OH_CryptoRand | Defines a struct for a random number generator, which indicates the context of the random number generator. |

### Functions

| Name| Description|
| -- | -- |
| [OH_Crypto_ErrCode OH_CryptoRand_Create(OH_CryptoRand **ctx)](#oh_cryptorand_create) | Creates a random number generator context.<br> Note: The created resource must be destroyed by calling [OH_CryptoRand_Destroy](capi-crypto-rand-h.md#oh_cryptorand_destroy). |
| [OH_Crypto_ErrCode OH_CryptoRand_GenerateRandom(OH_CryptoRand *ctx, int len, Crypto_DataBlob *out)](#oh_cryptorand_generaterandom) | Generates random numbers.<br> Note: After the use is complete, the memory for storing the **out** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob).|
| [const char *OH_CryptoRand_GetAlgoName(OH_CryptoRand *ctx)](#oh_cryptorand_getalgoname) | Obtains the algorithm name of the random number generator. |
| [OH_Crypto_ErrCode OH_CryptoRand_SetSeed(OH_CryptoRand *ctx, Crypto_DataBlob *seed)](#oh_cryptorand_setseed) | Sets the seed of a random number generator.|
| [OH_Crypto_ErrCode OH_CryptoRand_EnableHardwareEntropy(OH_CryptoRand *ctx)](#oh_cryptorand_enablehardwareentropy) | Enables the hardware entropy source.|
| [void OH_CryptoRand_Destroy(OH_CryptoRand *ctx)](#oh_cryptorand_destroy) | Destroys the random number generator context. |

## Function Description

### OH_CryptoRand_Create()

```c
OH_Crypto_ErrCode OH_CryptoRand_Create(OH_CryptoRand **ctx)
```

**Description**

Creates a random number generator context.

Note: The created resource must be destroyed by calling [OH_CryptoRand_Destroy](capi-crypto-rand-h.md#oh_cryptorand_destroy).

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoRand](capi-cryptorandapi-oh-cryptorand.md) **ctx | Output parameter, indicating a pointer to the random number generator context. The value of **ctx** cannot be null, but the value of ***ctx** must be null. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: **ctx** is null.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: The memory operation fails.<br>**CRYPTO_OPERTION_ERROR**: The cryptographic operation fails. |

### OH_CryptoRand_GenerateRandom()

```c
OH_Crypto_ErrCode OH_CryptoRand_GenerateRandom(OH_CryptoRand *ctx, int len, Crypto_DataBlob *out)
```

**Description**

Generates random numbers.

Note: After the method is used, the memory for storing the **out** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob).

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoRand](capi-cryptorandapi-oh-cryptorand.md) *ctx | Input parameter, indicating the random number generator context. The value cannot be null. |
| int len | Input parameter, indicating the length of the random number, in bytes. |
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *out | Output parameter, indicating a pointer to the **Crypto_DataBlob** struct used to store the random number. The value cannot be null. Before calling this method, initialize **out** to 0. Do not set the **data** field of **out**. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: **ctx** or **out** is null, or **len** is less than or equal to 0.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: The memory operation fails.<br>**CRYPTO_OPERTION_ERROR**: The cryptographic operation fails. |

### OH_CryptoRand_GetAlgoName()

```c
const char *OH_CryptoRand_GetAlgoName(OH_CryptoRand *ctx)
```

**Description**

Obtains the algorithm name of the random number generator.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoRand](capi-cryptorandapi-oh-cryptorand.md) *ctx | Input parameter, indicating the random number generator context. The value cannot be null.
 |

**Returns**

| Type| Description|
| -- | -- |
| const char * | Name of the random number generator algorithm, which does not need to be released by the caller. This value cannot be used after the context is destroyed. |

### OH_CryptoRand_SetSeed()

```c
OH_Crypto_ErrCode OH_CryptoRand_SetSeed(OH_CryptoRand *ctx, Crypto_DataBlob *seed)
```

**Description**

Sets the seed of a random number generator.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoRand](capi-cryptorandapi-oh-cryptorand.md) *ctx | Input parameter, indicating the random number generator context. The value cannot be null. |
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *seed | Input parameter, indicating the seed data. This API performs deep copy of the data in **seed**. The caller can immediately release **seed** after the API returns a result. The value cannot be null. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: **ctx** is null, or **seed** is invalid. For example, **seed** is null, **data** in **seed** is null, **len** in **seed** is **0**, or **len** in ***seed** exceeds the value of **INT_MAX**.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: The memory operation fails.<br>**CRYPTO_OPERTION_ERROR**: The cryptographic operation fails. |

### OH_CryptoRand_EnableHardwareEntropy()

```c
OH_Crypto_ErrCode OH_CryptoRand_EnableHardwareEntropy(OH_CryptoRand *ctx)
```

**Description**

Enables the hardware entropy source.

**Since**: 21

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoRand](capi-cryptorandapi-oh-cryptorand.md) *ctx | Input parameter, indicating the random number generator context. The value cannot be null. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: **ctx** is null.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: The memory operation fails.<br>**CRYPTO_OPERTION_ERROR**: The cryptographic operation fails. |

### OH_CryptoRand_Destroy()

```c
void OH_CryptoRand_Destroy(OH_CryptoRand *ctx)
```

**Description**

Destroys the random number generator context.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoRand](capi-cryptorandapi-oh-cryptorand.md) *ctx | Input parameter, indicating the random number generator context. |


