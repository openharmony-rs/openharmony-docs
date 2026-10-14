# crypto_mac.h

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=76caeef80126e754bb89b8cf8b2b7380f3d3d3a7 translatedAt=2026-09-02T07:18:27.758Z pushedAt=2026-09-04T06:09:55.530Z -->

## Overview

Defines the message authentication code (MAC) APIs.

**Header file**: <CryptoArchitectureKit/crypto_mac.h>

**Library**: libohcrypto.so

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 20

**Related module**: [CryptoMacApi](capi-cryptomacapi.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_CryptoMac](capi-cryptomacapi-oh-cryptomac.md) | OH_CryptoMac | Defines a struct for a MAC, which indicates the MAC context. |

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [CryptoMac_ParamType](#cryptomac_paramtype) | CryptoMac_ParamType | Defines the parameter type for the MAC algorithm.|

### Functions

| Name| Description|
| -- | -- |
| [OH_Crypto_ErrCode OH_CryptoMac_Create(const char *algoName, OH_CryptoMac **ctx)](#oh_cryptomac_create) | Creates a MAC context based on the given algorithm name.<br> Note: The created resource must be destroyed by calling [OH_CryptoMac_Destroy](capi-crypto-mac-h.md#oh_cryptomac_destroy). |
| [OH_Crypto_ErrCode OH_CryptoMac_SetParam(OH_CryptoMac *ctx, CryptoMac_ParamType type, const Crypto_DataBlob *value)](#oh_cryptomac_setparam) | Sets parameters of a MAC context. |
| [OH_Crypto_ErrCode OH_CryptoMac_Init(OH_CryptoMac *ctx, const OH_CryptoSymKey *key)](#oh_cryptomac_init) | Initializes the MAC context using a symmetric key. |
| [OH_Crypto_ErrCode OH_CryptoMac_Update(OH_CryptoMac *ctx, const Crypto_DataBlob *in)](#oh_cryptomac_update) | Updates the MAC data. |
| [OH_Crypto_ErrCode OH_CryptoMac_Final(OH_CryptoMac *ctx, Crypto_DataBlob *out)](#oh_cryptomac_final) | Finalizes the MAC operation.<br> Note: After the use is complete, the memory for storing the out parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob). |
| [OH_Crypto_ErrCode OH_CryptoMac_GetLength(OH_CryptoMac *ctx, uint32_t *length)](#oh_cryptomac_getlength) | Obtains the length of the MAC result. |
| [void OH_CryptoMac_Destroy(OH_CryptoMac *ctx)](#oh_cryptomac_destroy) | Destroys the MAC context. |

## Enum Description

### CryptoMac_ParamType

```c
enum CryptoMac_ParamType
```

**Description**

Defines the parameter type for the MAC algorithm.

**Since**: 20

| Enum Item| Description|
| -- | -- |
| CRYPTO_MAC_DIGEST_NAME_STR = 0 | Name of the HMAC message digest algorithm, which is set using [OH_CryptoMac_SetParam](capi-crypto-mac-h.md#oh_cryptomac_setparam). The options include **SHA1**, **SHA224**, **SHA256**, **SHA384**, **SHA512**, **SM3**, and **MD5**. Since API version 26.0.0, **SHA3-256**, **SHA3-384**, and **SHA3-512** are supported.<br>**Since:** 20 |
| CRYPTO_MAC_CIPHER_NAME_STR = 1 | Name of the CMAC symmetric encryption algorithm, which is set using [OH_CryptoMac_SetParam](capi-crypto-mac-h.md#oh_cryptomac_setparam). The options include **AES128** and **AES256**.<br>**Since:** 20 |


## Function Description

### OH_CryptoMac_Create()

```c
OH_Crypto_ErrCode OH_CryptoMac_Create(const char *algoName, OH_CryptoMac **ctx)
```

**Description**

Creates a MAC context based on the given algorithm name.

Note: The created resource must be destroyed by calling [OH_CryptoMac_Destroy](capi-crypto-mac-h.md#oh_cryptomac_destroy).

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| const char *algoName | Input parameter, indicating the MAC algorithm name, which cannot be null. The options include **HMAC** and **CMAC**. |
| [OH_CryptoMac](capi-cryptomacapi-oh-cryptomac.md) **ctx | Output parameter, indicating a pointer to the MAC context. The value of **ctx** cannot be null, but the value of ***ctx** must be null. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) |**CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: **algoName** or **ctx** is null, or **algoName** is not **HMAC** or **CMAC**.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: The memory operation fails.<br>**CRYPTO_OPERTION_ERROR**: The cryptographic operation fails. |

**Reference**

[OH_CryptoMac_SetParam](capi-crypto-mac-h.md#oh_cryptomac_setparam) for setting parameters of a MAC context.


### OH_CryptoMac_SetParam()

```c
OH_Crypto_ErrCode OH_CryptoMac_SetParam(OH_CryptoMac *ctx, CryptoMac_ParamType type, const Crypto_DataBlob *value)
```

**Description**

Sets parameters of a MAC context.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoMac](capi-cryptomacapi-oh-cryptomac.md) *ctx | Input parameter, indicating the MAC context. The value cannot be null. |
| [CryptoMac_ParamType](capi-crypto-mac-h.md#cryptomac_paramtype) type | Input parameter, indicating the MAC parameter type. |
| [const Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *value | Input parameter, indicating the parameter value. This API performs deep copy of the data in **value**. The caller can immediately release **value** after the API returns a result. The value cannot be null. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: **ctx**, **value**, or **data** in **value** is null; **type** is invalid for the current MAC algorithm; or the digest/encryption algorithm name is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation for the parameter copy fails.<br>**CRYPTO_MEMORY_ERROR**: Failed to allocate memory for parameter copying.<br>**CRYPTO_OPERTION_ERROR**: The cryptographic operation fails. |

**Reference**

[OH_CryptoMac_Init](capi-crypto-mac-h.md#oh_cryptomac_init) for initializing the MAC context using a symmetric key.


### OH_CryptoMac_Init()

```c
OH_Crypto_ErrCode OH_CryptoMac_Init(OH_CryptoMac *ctx, const OH_CryptoSymKey *key)
```

**Description**

Initializes the MAC context using a symmetric key.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoMac](capi-cryptomacapi-oh-cryptomac.md) *ctx | Input parameter, indicating the MAC context. The value cannot be null. |
| [const OH_CryptoSymKey](capi-cryptosymkeyapi-oh-cryptosymkey.md) *key | Input parameter, indicating a symmetric key. The value cannot be null. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: **ctx** or **key** is null.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: The memory operation fails.<br>**CRYPTO_OPERTION_ERROR**: MAC initialization fails. Possible causes: The key length does not meet the algorithm requirement. For example, AES-128 used by CMAC requires a 16-byte key.|

**Reference**

[OH_CryptoMac_Update](capi-crypto-mac-h.md#oh_cryptomac_update) for updating the MAC data.


### OH_CryptoMac_Update()

```c
OH_Crypto_ErrCode OH_CryptoMac_Update(OH_CryptoMac *ctx, const Crypto_DataBlob *in)
```

**Description**

Updates the MAC data.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoMac](capi-cryptomacapi-oh-cryptomac.md) *ctx | Input parameter, indicating the MAC context. The value cannot be null. |
| [const Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *in | Input parameter, indicating the data to be updated. The value cannot be null. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: **ctx** or **in** is null.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: The memory operation fails.<br>**CRYPTO_OPERTION_ERROR**: The MAC update fails. |

**Reference**

[OH_CryptoMac_Final](capi-crypto-mac-h.md#oh_cryptomac_final) for finalizing the MAC operation.


### OH_CryptoMac_Final()

```c
OH_Crypto_ErrCode OH_CryptoMac_Final(OH_CryptoMac *ctx, Crypto_DataBlob *out)
```

**Description**

Finalizes the MAC operation.

Note: After the method is used, the memory for storing the **out** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob).

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoMac](capi-cryptomacapi-oh-cryptomac.md) *ctx | Input parameter, indicating the MAC context. The value cannot be null. |
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *out | Output parameter, indicating a pointer to the **Crypto_DataBlob** struct used to store the MAC result. The value cannot be null. Before calling this method, initialize **out** to 0. Do not set the **data** field of **out**. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: **ctx** or **out** is null.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: The memory operation fails.<br>**CRYPTO_OPERTION_ERROR**: The MAC finalization operation fails. |

### OH_CryptoMac_GetLength()

```c
OH_Crypto_ErrCode OH_CryptoMac_GetLength(OH_CryptoMac *ctx, uint32_t *length)
```

**Description**

Obtains the length of the MAC result.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoMac](capi-cryptomacapi-oh-cryptomac.md) *ctx | Input parameter, indicating the MAC context. The value cannot be null. |
| uint32_t *length | Output parameter, indicating the length of the MAC result, in bytes. The value cannot be null. The caller allocates the memory. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: **ctx** or **length** is null.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: The memory operation fails.<br>**CRYPTO_OPERTION_ERROR**: The cryptographic operation fails. |

### OH_CryptoMac_Destroy()

```c
void OH_CryptoMac_Destroy(OH_CryptoMac *ctx)
```

**Description**

Destroys the MAC context.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoMac](capi-cryptomacapi-oh-cryptomac.md) *ctx | Input parameter, indicating the MAC context. |


