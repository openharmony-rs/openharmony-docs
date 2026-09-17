# crypto_sym_key.h

## Overview

Defines the symmetric key interfaces.

**Include**: <CryptoArchitectureKit/crypto_sym_key.h>

**Library**: libohcrypto.so

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 12

**Related module**: [CryptoSymKeyApi](capi-cryptosymkeyapi.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_CryptoSymKey](capi-cryptosymkeyapi-oh-cryptosymkey.md) | OH_CryptoSymKey | Symmetric key structure, representing a symmetric key. |
| [OH_CryptoSymKeyGenerator](capi-cryptosymkeyapi-oh-cryptosymkeygenerator.md) | OH_CryptoSymKeyGenerator | Symmetric key generator structure, representing a symmetric key generator. |

### Function

| Name | Description |
| -- | -- |
| [OH_Crypto_ErrCode OH_CryptoSymKeyGenerator_Create(const char *algoName, OH_CryptoSymKeyGenerator **ctx)](#oh_cryptosymkeygenerator_create) | Creates a symmetric key generator based on the given algorithm name, e.g. AES256. |
| [OH_Crypto_ErrCode OH_CryptoSymKeyGenerator_Generate(OH_CryptoSymKeyGenerator *ctx, OH_CryptoSymKey **keyCtx)](#oh_cryptosymkeygenerator_generate) | Generates a symmetric key randomly. |
| [OH_Crypto_ErrCode OH_CryptoSymKeyGenerator_Convert(OH_CryptoSymKeyGenerator *ctx, const Crypto_DataBlob *keyData, OH_CryptoSymKey **keyCtx)](#oh_cryptosymkeygenerator_convert) | Converts symmetric key data to a symmetric key. |
| [const char *OH_CryptoSymKeyGenerator_GetAlgoName(OH_CryptoSymKeyGenerator *ctx)](#oh_cryptosymkeygenerator_getalgoname) | Obtains the algorithm name of the symmetric key generator. |
| [void OH_CryptoSymKeyGenerator_Destroy(OH_CryptoSymKeyGenerator *ctx)](#oh_cryptosymkeygenerator_destroy) | Destroys the symmetric key generator. |
| [const char *OH_CryptoSymKey_GetAlgoName(OH_CryptoSymKey *keyCtx)](#oh_cryptosymkey_getalgoname) | Obtains the symmetric key algorithm name from the symmetric key. |
| [OH_Crypto_ErrCode OH_CryptoSymKey_GetKeyData(OH_CryptoSymKey *keyCtx, Crypto_DataBlob *out)](#oh_cryptosymkey_getkeydata) | Obtains the symmetric key data from the symmetric key. |
| [void OH_CryptoSymKey_Destroy(OH_CryptoSymKey *keyCtx)](#oh_cryptosymkey_destroy) | Destroys the symmetric key. |

## Function description

### OH_CryptoSymKeyGenerator_Create()

```c
OH_Crypto_ErrCode OH_CryptoSymKeyGenerator_Create(const char *algoName, OH_CryptoSymKeyGenerator **ctx)
```

**Description**

Creates a symmetric key generator based on the given algorithm name, e.g. AES256.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *algoName | [in] Symmetric key algorithm name. Cannot be NULL. Values: - "AES128", "AES192", "AES256", "3DES192", "HMAC\|SHA1", "HMAC\|SHA224", "HMAC\|SHA256", "HMAC\|SHA384", "HMAC\|SHA512", "HMAC\|SM3", "HMAC\|MD5" supported since API version 12. "HMAC\|SHA3-256", "HMAC\|SHA3-384", "HMAC\|SHA3-512" supported since API version 26.0.0. - "SM4_128" supported since API version 12. - "DES64" supported since API version 20. - "ChaCha20" supported since API version 22. - "RC2", "RC4", "Blowfish", "CAST" supported since API version 26.0.0. Note: only key conversion is supported, random generation is not. |
| [OH_CryptoSymKeyGenerator](capi-cryptosymkeyapi-oh-cryptosymkeygenerator.md) **ctx | [out] Pointer to the symmetric key generator pointer. ctx cannot be NULL, *ctx must be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_INVALID_PARAMS} if ctx or algoName is NULL.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if the algorithm is not supported.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory allocation fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if crypto operation fails.</li>          </ul> |

**Reference**:

[OH_CryptoSymKeyGenerator_Generate](capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_generate) Generates a symmetric key randomly
[OH_CryptoSymKeyGenerator_Convert](capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_convert) Converts symmetric key data to a symmetric key


### OH_CryptoSymKeyGenerator_Generate()

```c
OH_Crypto_ErrCode OH_CryptoSymKeyGenerator_Generate(OH_CryptoSymKeyGenerator *ctx, OH_CryptoSymKey **keyCtx)
```

**Description**

Generates a symmetric key randomly.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoSymKeyGenerator](capi-cryptosymkeyapi-oh-cryptosymkeygenerator.md) *ctx | [in] Symmetric key generator. Cannot be NULL. |
| [OH_CryptoSymKey](capi-cryptosymkeyapi-oh-cryptosymkey.md) **keyCtx | [out] Pointer to the symmetric key pointer. keyCtx cannot be NULL, *keyCtx must be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_INVALID_PARAMS} if ctx or keyCtx is NULL.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if unsupported operation or algorithm.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory operation fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_INVALID_CALL} if the function call is invalid. Possible causes:<br>           the algorithm does not support random key generation (e.g. RC2, RC4, Blowfish, CAST),<br>           use OH_CryptoSymKeyGenerator_Convert interface instead.[since 26.0.0]</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if crypto operation fails.</li>          </ul> |

### OH_CryptoSymKeyGenerator_Convert()

```c
OH_Crypto_ErrCode OH_CryptoSymKeyGenerator_Convert(OH_CryptoSymKeyGenerator *ctx, const Crypto_DataBlob *keyData, OH_CryptoSymKey **keyCtx)
```

**Description**

Converts symmetric key data to a symmetric key.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoSymKeyGenerator](capi-cryptosymkeyapi-oh-cryptosymkeygenerator.md) *ctx | [in] Symmetric key generator. Cannot be NULL. |
| const Crypto_DataBlob *keyData | [in] Data used to generate the symmetric key. Cannot be NULL. |
| [OH_CryptoSymKey](capi-cryptosymkeyapi-oh-cryptosymkey.md) **keyCtx | [out] Pointer to the symmetric key pointer. keyCtx cannot be NULL, *keyCtx must be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_INVALID_PARAMS} if ctx, keyData, or keyCtx is NULL.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if unsupported operation or algorithm.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory allocation fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if crypto operation fails.</li>          </ul> |

### OH_CryptoSymKeyGenerator_GetAlgoName()

```c
const char *OH_CryptoSymKeyGenerator_GetAlgoName(OH_CryptoSymKeyGenerator *ctx)
```

**Description**

Obtains the algorithm name of the symmetric key generator.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoSymKeyGenerator](capi-cryptosymkeyapi-oh-cryptosymkeygenerator.md) *ctx | [in] Symmetric key generator. Cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| const char * | Returns the symmetric key algorithm name. No need to free by the caller. Invalid after      the generator is destroyed. |

### OH_CryptoSymKeyGenerator_Destroy()

```c
void OH_CryptoSymKeyGenerator_Destroy(OH_CryptoSymKeyGenerator *ctx)
```

**Description**

Destroys the symmetric key generator.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoSymKeyGenerator](capi-cryptosymkeyapi-oh-cryptosymkeygenerator.md) *ctx | [in] Symmetric key generator. |

### OH_CryptoSymKey_GetAlgoName()

```c
const char *OH_CryptoSymKey_GetAlgoName(OH_CryptoSymKey *keyCtx)
```

**Description**

Obtains the symmetric key algorithm name from the symmetric key.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoSymKey](capi-cryptosymkeyapi-oh-cryptosymkey.md) *keyCtx | [in] Symmetric key. Cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| const char * | Returns the algorithm name. No need to free by the caller. Invalid after the key is destroyed. |

### OH_CryptoSymKey_GetKeyData()

```c
OH_Crypto_ErrCode OH_CryptoSymKey_GetKeyData(OH_CryptoSymKey *keyCtx, Crypto_DataBlob *out)
```

**Description**

Obtains the symmetric key data from the symmetric key.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoSymKey](capi-cryptosymkeyapi-oh-cryptosymkey.md) *keyCtx | [in] Symmetric key. Cannot be NULL. |
| Crypto_DataBlob *out | [out] Pointer to the Crypto_DataBlob structure for storing the key data. Cannot be NULL. Initialize out to {0} before calling. Do not pre-allocate out->data. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_INVALID_PARAMS} if keyCtx or out is NULL.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if unsupported operation or algorithm.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory operation fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if crypto operation fails.</li>          </ul> |

### OH_CryptoSymKey_Destroy()

```c
void OH_CryptoSymKey_Destroy(OH_CryptoSymKey *keyCtx)
```

**Description**

Destroys the symmetric key.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoSymKey](capi-cryptosymkeyapi-oh-cryptosymkey.md) *keyCtx | [in] Symmetric key. |


