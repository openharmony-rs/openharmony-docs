# crypto_digest.h

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=76caeef80126e754bb89b8cf8b2b7380f3d3d3a7 translatedAt=2026-08-20T12:23:07.583Z pushedAt=2026-08-24T02:33:11.261Z -->

## Overview

Defines APIs for MD algorithms.

**Header file**: <CryptoArchitectureKit/crypto_digest.h>

**Library**: libohcrypto.so

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 12

**Related module**: [CryptoDigestApi](capi-cryptodigestapi.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_CryptoDigest](capi-cryptodigestapi-oh-cryptodigest.md) | OH_CryptoDigest | Defines a digest struct. |

### Functions

| Name| Description|
| -- | -- |
| [OH_Crypto_ErrCode OH_CryptoDigest_Create(const char *algoName, OH_CryptoDigest **ctx)](#oh_cryptodigest_create) | Creates a digest context based on the given algorithm name.<br> Note: The created resource must be destroyed by calling [OH_DigestCrypto_Destroy](capi-crypto-digest-h.md#oh_digestcrypto_destroy). |
| [OH_Crypto_ErrCode OH_CryptoDigest_Update(OH_CryptoDigest *ctx, Crypto_DataBlob *in)](#oh_cryptodigest_update) | Updates MD data.|
| [OH_Crypto_ErrCode OH_CryptoDigest_Final(OH_CryptoDigest *ctx, Crypto_DataBlob *out)](#oh_cryptodigest_final) | Finalizes the digest operation and outputs the digest result.<br> Note: After the method is used, the memory for storing the **out** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob). |
| [uint32_t OH_CryptoDigest_GetLength(OH_CryptoDigest *ctx)](#oh_cryptodigest_getlength) | Obtains the length of the digest result. |
| [const char *OH_CryptoDigest_GetAlgoName(OH_CryptoDigest *ctx)](#oh_cryptodigest_getalgoname) | Obtains the name of the algorithm used for generating the digest context. |
| [void OH_DigestCrypto_Destroy(OH_CryptoDigest *ctx)](#oh_digestcrypto_destroy) | Destroys the digest context. |

## Function Description

### OH_CryptoDigest_Create()

```c
OH_Crypto_ErrCode OH_CryptoDigest_Create(const char *algoName, OH_CryptoDigest **ctx)
```

**Description**

Creates a digest context based on the given algorithm name.

Note: The created resource must be destroyed by calling [OH_DigestCrypto_Destroy](capi-crypto-digest-h.md#oh_digestcrypto_destroy).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const char *algoName | Input parameter, indicating the digest algorithm name, which cannot be null. The options are as follows:<br>- Since API version 12, **SHA1**, **SHA224**, **SHA256**, **SHA384**, **SHA512**, **MD5**, and **SM3** are supported.<br>- Since API version 22, **SHA3-256**, **SHA3-384**, and **SHA3-512** are supported. |
| [OH_CryptoDigest](capi-cryptodigestapi-oh-cryptodigest.md) **ctx | Output parameter, indicating a pointer to the digest context. The value of **ctx** cannot be null, but the value of ***ctx** must be null. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_INVALID_PARAMS**: The value of **ctx** or **algoName** is null, or **algoName** is not a valid digest algorithm name.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation fails.<br>**CRYPTO_OPERTION_ERROR**: The digest operation fails. |

**Reference**

[OH_CryptoDigest_Update](capi-crypto-digest-h.md#oh_cryptodigest_update) for updating MD data.

### OH_CryptoDigest_Update()

```c
OH_Crypto_ErrCode OH_CryptoDigest_Update(OH_CryptoDigest *ctx, Crypto_DataBlob *in)
```

**Description**

Updates MD data.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoDigest](capi-cryptodigestapi-oh-cryptodigest.md) *ctx | Input parameter, indicating the digest context. The value cannot be null. |
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *in | Input parameter, indicating the data whose digest is to be calculated. The value cannot be null. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_INVALID_PARAMS**: The value of **ctx** or **in** is null.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: The memory operation fails.<br>**CRYPTO_OPERTION_ERROR**: The digest update fails. |

**Reference**

[OH_CryptoDigest_Final](capi-crypto-digest-h.md#oh_cryptodigest_final) for finalizing the digest operation and outputting the digest result.

### OH_CryptoDigest_Final()

```c
OH_Crypto_ErrCode OH_CryptoDigest_Final(OH_CryptoDigest *ctx, Crypto_DataBlob *out)
```

**Description**

Finalizes the digest operation and outputs the digest result.

Note: After the method is used, the memory for storing the **out** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoDigest](capi-cryptodigestapi-oh-cryptodigest.md) *ctx | Input parameter, indicating the digest context. The value cannot be null. |
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *out | Output parameter, indicating a pointer to the **Crypto_DataBlob** struct used to store the digest result. The value cannot be null. Before calling this method, initialize **out** to 0. Do not set the **data** field of **out**. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_INVALID_PARAMS**: The value of **ctx** or **out** is null.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: The memory operation fails.<br>**CRYPTO_OPERTION_ERROR**: The digest finalization fails. |

### OH_CryptoDigest_GetLength()

```c
uint32_t OH_CryptoDigest_GetLength(OH_CryptoDigest *ctx)
```

**Description**

Obtains the length of the digest result.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoDigest](capi-cryptodigestapi-oh-cryptodigest.md) *ctx | Input parameter, indicating the digest context. The value cannot be null. |

**Returns**

| Type| Description|
| -- | -- |
| uint32_t | Length of the digest result, in bytes. Note: If the input parameter **ctx** is null, **401** is returned. In other failure scenarios, **0** is returned. |

### OH_CryptoDigest_GetAlgoName()

```c
const char *OH_CryptoDigest_GetAlgoName(OH_CryptoDigest *ctx)
```

**Description**

Obtains the name of the algorithm used for generating the digest context.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoDigest](capi-cryptodigestapi-oh-cryptodigest.md) *ctx | Input parameter, indicating the digest context. The value cannot be null. |

**Returns**

| Type| Description|
| -- | -- |
| const char * | Name of the digest algorithm, which does not need to be released by the caller. This value cannot be used after the context is destroyed. |

### OH_DigestCrypto_Destroy()

```c
void OH_DigestCrypto_Destroy(OH_CryptoDigest *ctx)
```

**Description**

Destroys the digest context.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoDigest](capi-cryptodigestapi-oh-cryptodigest.md) *ctx | Input parameter, indicating the digest context. |