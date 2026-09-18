# crypto_digest.h

## Overview

Defines the digest algorithm interfaces.

**Include**: <CryptoArchitectureKit/crypto_digest.h>

**Library**: libohcrypto.so

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 12

**Related module**: [CryptoDigestApi](capi-cryptodigestapi.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_CryptoDigest](capi-cryptodigestapi-oh-cryptodigest.md) | OH_CryptoDigest | Digest structure, representing a digest context. |

### Function

| Name | Description |
| -- | -- |
| [OH_Crypto_ErrCode OH_CryptoDigest_Create(const char *algoName, OH_CryptoDigest **ctx)](#oh_cryptodigest_create) | Creates a digest context based on the given algorithm name. |
| [OH_Crypto_ErrCode OH_CryptoDigest_Update(OH_CryptoDigest *ctx, Crypto_DataBlob *in)](#oh_cryptodigest_update) | Updates digest data. |
| [OH_Crypto_ErrCode OH_CryptoDigest_Final(OH_CryptoDigest *ctx, Crypto_DataBlob *out)](#oh_cryptodigest_final) | Finishes the digest operation and outputs the result. |
| [uint32_t OH_CryptoDigest_GetLength(OH_CryptoDigest *ctx)](#oh_cryptodigest_getlength) | Obtains the length of the digest result. |
| [const char *OH_CryptoDigest_GetAlgoName(OH_CryptoDigest *ctx)](#oh_cryptodigest_getalgoname) | Obtains the algorithm name of the digest context. |
| [void OH_DigestCrypto_Destroy(OH_CryptoDigest *ctx)](#oh_digestcrypto_destroy) | Destroys the digest context. |

## Function description

### OH_CryptoDigest_Create()

```c
OH_Crypto_ErrCode OH_CryptoDigest_Create(const char *algoName, OH_CryptoDigest **ctx)
```

**Description**

Creates a digest context based on the given algorithm name.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *algoName | [in] Digest algorithm name. Cannot be NULL. Values: - "SHA1", "SHA224", "SHA256", "SHA384", "SHA512", "MD5", "SM3" supported since API version 12. - "SHA3-256", "SHA3-384", "SHA3-512" supported since API version 22. |
| [OH_CryptoDigest](capi-cryptodigestapi-oh-cryptodigest.md) **ctx | [out] Pointer to the digest context pointer. ctx cannot be NULL, *ctx must be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_INVALID_PARAMS} if ctx is NULL, algoName is NULL,<br>            algoName is not a supported digest algorithm name.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if unsupported operation or algorithm.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory allocation fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if the digest operation fails.</li>          </ul> |

**Reference**:

[OH_CryptoDigest_Update](capi-crypto-digest-h.md#oh_cryptodigest_update) Updates digest data


### OH_CryptoDigest_Update()

```c
OH_Crypto_ErrCode OH_CryptoDigest_Update(OH_CryptoDigest *ctx, Crypto_DataBlob *in)
```

**Description**

Updates digest data.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoDigest](capi-cryptodigestapi-oh-cryptodigest.md) *ctx | [in] Digest context. Cannot be NULL. |
| Crypto_DataBlob *in | [in] Data to be digested. Cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_INVALID_PARAMS} if ctx or in is NULL.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if unsupported operation or algorithm.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory operation fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if the digest update fails.</li>          </ul> |

**Reference**:

[OH_CryptoDigest_Final](capi-crypto-digest-h.md#oh_cryptodigest_final) Finishes the digest operation and outputs the result


### OH_CryptoDigest_Final()

```c
OH_Crypto_ErrCode OH_CryptoDigest_Final(OH_CryptoDigest *ctx, Crypto_DataBlob *out)
```

**Description**

Finishes the digest operation and outputs the result.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoDigest](capi-cryptodigestapi-oh-cryptodigest.md) *ctx | [in] Digest context. Cannot be NULL. |
| Crypto_DataBlob *out | [out] Pointer to the Crypto_DataBlob structure for storing the digest result. Cannot be NULL. Initialize out to {0} before calling. Do not pre-allocate out->data. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_INVALID_PARAMS} if ctx or out is NULL.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if unsupported operation or algorithm.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory operation fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if the digest final operation fails.</li>          </ul> |

### OH_CryptoDigest_GetLength()

```c
uint32_t OH_CryptoDigest_GetLength(OH_CryptoDigest *ctx)
```

**Description**

Obtains the length of the digest result.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoDigest](capi-cryptodigestapi-oh-cryptodigest.md) *ctx | [in] Digest context. Cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| uint32_t | Returns the byte length of the digest result. Note: If ctx is NULL, returns 401; for other failure cases,      returns 0. |

### OH_CryptoDigest_GetAlgoName()

```c
const char *OH_CryptoDigest_GetAlgoName(OH_CryptoDigest *ctx)
```

**Description**

Obtains the algorithm name of the digest context.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoDigest](capi-cryptodigestapi-oh-cryptodigest.md) *ctx | [in] Digest context. Cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| const char * | Returns the digest algorithm name. No need to free by the caller. Invalid after the context is destroyed. |

### OH_DigestCrypto_Destroy()

```c
void OH_DigestCrypto_Destroy(OH_CryptoDigest *ctx)
```

**Description**

Destroys the digest context.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoDigest](capi-cryptodigestapi-oh-cryptodigest.md) *ctx | [in] Digest context. |


