# crypto_sym_cipher.h

## Overview

Defines the symmetric key cipher interfaces.

**Include**: <CryptoArchitectureKit/crypto_sym_cipher.h>

**Library**: libohcrypto.so

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 12

**Related module**: [CryptoSymCipherApi](capi-cryptosymcipherapi.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_CryptoSymCipher](capi-cryptosymcipherapi-oh-cryptosymcipher.md) | OH_CryptoSymCipher | Symmetric cipher structure, representing a symmetric cipher context. |
| [OH_CryptoSymCipherParams](capi-cryptosymcipherapi-oh-cryptosymcipherparams.md) | OH_CryptoSymCipherParams | Symmetric cipher parameters structure, representing symmetric cipher parameters. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [CryptoSymCipher_ParamsType](#cryptosymcipher_paramstype) | CryptoSymCipher_ParamsType | Defines the cipher parameter types. |

### Function

| Name | Description |
| -- | -- |
| [OH_Crypto_ErrCode OH_CryptoSymCipherParams_Create(OH_CryptoSymCipherParams **params)](#oh_cryptosymcipherparams_create) | Creates symmetric cipher parameters. |
| [OH_Crypto_ErrCode OH_CryptoSymCipherParams_SetParam(OH_CryptoSymCipherParams *params, CryptoSymCipher_ParamsType paramsType, Crypto_DataBlob *value)](#oh_cryptosymcipherparams_setparam) | Sets cipher parameters. |
| [void OH_CryptoSymCipherParams_Destroy(OH_CryptoSymCipherParams *params)](#oh_cryptosymcipherparams_destroy) | Destroys cipher parameters. |
| [OH_Crypto_ErrCode OH_CryptoSymCipher_Create(const char *algoName, OH_CryptoSymCipher **ctx)](#oh_cryptosymcipher_create) | Creates a symmetric cipher context based on the given algorithm name. |
| [OH_Crypto_ErrCode OH_CryptoSymCipher_Init(OH_CryptoSymCipher *ctx, Crypto_CipherMode mod, OH_CryptoSymKey *key, OH_CryptoSymCipherParams *params)](#oh_cryptosymcipher_init) | Initializes the cipher operation with the given mode, key, and parameters. |
| [OH_Crypto_ErrCode OH_CryptoSymCipher_Update(OH_CryptoSymCipher *ctx, Crypto_DataBlob *in, Crypto_DataBlob *out)](#oh_cryptosymcipher_update) | Updates cipher data, outputting encrypted or decrypted data. |
| [OH_Crypto_ErrCode OH_CryptoSymCipher_Final(OH_CryptoSymCipher *ctx, Crypto_DataBlob *in, Crypto_DataBlob *out)](#oh_cryptosymcipher_final) | Finishes the cipher operation, outputting the final result. |
| [const char *OH_CryptoSymCipher_GetAlgoName(OH_CryptoSymCipher *ctx)](#oh_cryptosymcipher_getalgoname) | Obtains the symmetric cipher algorithm name. |
| [void OH_CryptoSymCipher_Destroy(OH_CryptoSymCipher *ctx)](#oh_cryptosymcipher_destroy) | Destroys the symmetric cipher context. |

## Enum type description

### CryptoSymCipher_ParamsType

```c
enum CryptoSymCipher_ParamsType
```

**Description**

Defines the cipher parameter types.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 12

| Enum item | Description |
| -- | -- |
| CRYPTO_IV_DATABLOB = 100 | Initialization vector (IV) parameter.<br>**Since**: 12 |
| CRYPTO_AAD_DATABLOB = 101 | Additional authenticated data (AAD) for AEAD modes (e.g. GCM, CCM).<br>**Since**: 12 |
| CRYPTO_TAG_DATABLOB = 102 | Authentication tag for AEAD modes (e.g. GCM, CCM), used for data integrity verification.<br>**Since**: 12 |


## Function description

### OH_CryptoSymCipherParams_Create()

```c
OH_Crypto_ErrCode OH_CryptoSymCipherParams_Create(OH_CryptoSymCipherParams **params)
```

**Description**

Creates symmetric cipher parameters.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoSymCipherParams](capi-cryptosymcipherapi-oh-cryptosymcipherparams.md) **params | [out] Pointer to the cipher parameters pointer. params cannot be NULL, *params must be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>[CRYPTO_SUCCESS](capi-crypto-common-h.md#oh_crypto_errcode) if the operation succeeds.</li>          <li>[CRYPTO_INVALID_PARAMS](capi-crypto-common-h.md#oh_crypto_errcode) if params is NULL.</li>          <li>[CRYPTO_NOT_SUPPORTED](capi-crypto-common-h.md#oh_crypto_errcode) if unsupported operation or algorithm.</li>          <li>[CRYPTO_MEMORY_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if memory operation fails.</li>          <li>[CRYPTO_OPERTION_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if crypto operation fails.</li>          </ul> |

**Reference**:

[OH_CryptoSymCipherParams_SetParam](capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_setparam) Sets cipher parameters


### OH_CryptoSymCipherParams_SetParam()

```c
OH_Crypto_ErrCode OH_CryptoSymCipherParams_SetParam(OH_CryptoSymCipherParams *params, CryptoSymCipher_ParamsType paramsType, Crypto_DataBlob *value)
```

**Description**

Sets cipher parameters.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoSymCipherParams](capi-cryptosymcipherapi-oh-cryptosymcipherparams.md) *params | [in] Cipher parameters. Cannot be NULL. |
| [CryptoSymCipher_ParamsType](capi-crypto-sym-cipher-h.md#cryptosymcipher_paramstype) paramsType | [in] Cipher parameter type to set. |
| Crypto_DataBlob *value | [in] Parameter value. This function performs a shallow copy and does not copy the data in value. The caller must ensure that the memory pointed to by value remains valid until [OH_CryptoSymCipher_Init](capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_init) completes. Cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>[CRYPTO_SUCCESS](capi-crypto-common-h.md#oh_crypto_errcode) if the operation succeeds.</li>          <li>[CRYPTO_INVALID_PARAMS](capi-crypto-common-h.md#oh_crypto_errcode) if params or value is NULL, or             paramsType is unrecognized.</li>          <li>[CRYPTO_NOT_SUPPORTED](capi-crypto-common-h.md#oh_crypto_errcode) if unsupported operation or algorithm.</li>          <li>[CRYPTO_MEMORY_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if memory operation fails.</li>          <li>[CRYPTO_OPERTION_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if crypto operation fails.</li>          </ul> |

### OH_CryptoSymCipherParams_Destroy()

```c
void OH_CryptoSymCipherParams_Destroy(OH_CryptoSymCipherParams *params)
```

**Description**

Destroys cipher parameters.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoSymCipherParams](capi-cryptosymcipherapi-oh-cryptosymcipherparams.md) *params | [in] Cipher parameters. |

### OH_CryptoSymCipher_Create()

```c
OH_Crypto_ErrCode OH_CryptoSymCipher_Create(const char *algoName, OH_CryptoSymCipher **ctx)
```

**Description**

Creates a symmetric cipher context based on the given algorithm name.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *algoName | [in] Symmetric cipher algorithm name. Cannot be NULL. Format: "Algorithm\|Mode\|Padding", separated by "\|". Algorithms: AES128, AES192, AES256, SM4_128, 3DES192, DES64, ChaCha20, RC2, Blowfish, CAST. Modes: ECB, CBC, CTR, OFB, CFB, CFB1, CFB8, CFB64, CFB128, GCM, CCM, XTS, Poly1305. Padding: NoPadding, PKCS5, PKCS7. Supported combinations: - AES series since API version 12: AES128, AES192, AES256 algorithms, ECB, CBC, CTR, OFB, CFB, GCM, CCM modes, NoPadding or PKCS7. Examples: "AES128\|GCM", "AES256\|CBC\|PKCS7". - 3DES series since API version 12: 3DES192 algorithm, ECB, CBC, OFB, CFB modes, NoPadding, PKCS5, or PKCS7. Example: "3DES192\|CBC\|PKCS5". - SM4 series since API version 12: SM4_128 algorithm, ECB, CBC, CTR, OFB, CFB, CFB128, GCM modes, NoPadding or PKCS7. Examples: "SM4_128\|CBC\|PKCS7", "SM4_128\|GCM\|NoPadding". - DES series since API version 20: DES64 algorithm, ECB, CBC, OFB, CFB modes, NoPadding, PKCS5, or PKCS7. Example: "DES64\|CBC\|PKCS5". - AES WRAP algorithms since API version 22: AES128_WRAP, AES192_WRAP, AES256_WRAP. Examples: "AES128_WRAP", "AES192_WRAP", "AES256_WRAP". - ChaCha20 since API version 22: "ChaCha20", "ChaCha20\|Poly1305". Examples: "ChaCha20\|Poly1305", "ChaCha20". - AES XTS mode since API version 26.0.0: "AES128\|XTS", "AES256\|XTS". AES192 is not supported. - RC2 since API version 26.0.0: ECB, CBC, OFB, CFB modes, NoPadding, PKCS5, or PKCS7. Example: "RC2\|CBC\|PKCS5". - RC4 since API version 26.0.0: "RC4". Example: "RC4". - Blowfish since API version 26.0.0: ECB, CBC, OFB, CFB modes, NoPadding, PKCS5, or PKCS7. Example: "Blowfish\|CBC\|PKCS5". - CAST since API version 26.0.0: ECB, CBC, OFB, CFB modes, NoPadding, PKCS5, or PKCS7. Example: "CAST\|CBC\|PKCS5". Padding notes: - ECB and CBC modes require padding: when plaintext length is not a multiple of the algorithm block size, PKCS5 or PKCS7 must be used; with NoPadding, input length must be a multiple of the block size (16 bytes for AES/SM4, 8 bytes for DES/3DES/RC2/Blowfish/CAST). - CTR, OFB, CFB, CFB1, CFB8, CFB64, CFB128, GCM, CCM modes convert block ciphers to stream mode and do not need padding. Any specified padding is treated as NoPadding. - XTS mode does not involve padding and does not require a padding field. Any specified padding is treated as NoPadding. - ChaCha20 is a stream cipher algorithm and does not require a padding field. Any specified padding is treated as NoPadding. |
| [OH_CryptoSymCipher](capi-cryptosymcipherapi-oh-cryptosymcipher.md) **ctx | [out] Pointer to the symmetric cipher context pointer. ctx cannot be NULL, *ctx must be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>[CRYPTO_SUCCESS](capi-crypto-common-h.md#oh_crypto_errcode) if the operation succeeds.</li>          <li>[CRYPTO_INVALID_PARAMS](capi-crypto-common-h.md#oh_crypto_errcode) if ctx or algoName is NULL.</li>          <li>[CRYPTO_NOT_SUPPORTED](capi-crypto-common-h.md#oh_crypto_errcode) if the algorithm is not supported.</li>          <li>[CRYPTO_MEMORY_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if memory allocation fails.</li>          <li>[CRYPTO_PARAMETER_CHECK_FAILED](capi-crypto-common-h.md#oh_crypto_errcode) if parameters are invalid. [since 20]</li>          <li>[CRYPTO_OPERTION_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if crypto operation fails.</li>          </ul> |

**Reference**:

[OH_CryptoSymCipher_Init](capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_init) Initializes the cipher operation with the given mode, key, and parameters


### OH_CryptoSymCipher_Init()

```c
OH_Crypto_ErrCode OH_CryptoSymCipher_Init(OH_CryptoSymCipher *ctx, Crypto_CipherMode mod, OH_CryptoSymKey *key, OH_CryptoSymCipherParams *params)
```

**Description**

Initializes the cipher operation with the given mode, key, and parameters.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoSymCipher](capi-cryptosymcipherapi-oh-cryptosymcipher.md) *ctx | [in] Symmetric cipher context. Cannot be NULL. |
| Crypto_CipherMode mod | [in] Cipher mode, encryption or decryption. |
| OH_CryptoSymKey *key | [in] Symmetric key. Cannot be NULL. |
| [OH_CryptoSymCipherParams](capi-cryptosymcipherapi-oh-cryptosymcipherparams.md) *params | [in] Algorithm parameters, e.g. IV. Must be NULL for ECB mode; cannot be NULL for other modes. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>[CRYPTO_SUCCESS](capi-crypto-common-h.md#oh_crypto_errcode) if the operation succeeds.</li>          <li>[CRYPTO_INVALID_PARAMS](capi-crypto-common-h.md#oh_crypto_errcode) if ctx or key is NULL,             or IV is missing or has wrong length for non-ECB modes.</li>          <li>[CRYPTO_NOT_SUPPORTED](capi-crypto-common-h.md#oh_crypto_errcode) if the operation is not supported.</li>          <li>[CRYPTO_MEMORY_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if memory allocation fails.</li>          <li>[CRYPTO_PARAMETER_CHECK_FAILED](capi-crypto-common-h.md#oh_crypto_errcode) if parameters are invalid. [since 20]</li>          <li>[CRYPTO_OPERTION_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if cipher init fails. Possible causes:             key length does not match the algorithm.</li>          </ul> |

**Reference**:

[OH_CryptoSymCipher_Update](capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_update) Updates cipher data, outputting encrypted or decrypted data
[OH_CryptoSymCipher_Final](capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_final) Finishes the cipher operation, outputting the final result


### OH_CryptoSymCipher_Update()

```c
OH_Crypto_ErrCode OH_CryptoSymCipher_Update(OH_CryptoSymCipher *ctx, Crypto_DataBlob *in, Crypto_DataBlob *out)
```

**Description**

Updates cipher data, outputting encrypted or decrypted data.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoSymCipher](capi-cryptosymcipherapi-oh-cryptosymcipher.md) *ctx | [in] Symmetric cipher context. Cannot be NULL. |
| Crypto_DataBlob *in | [in] Data to be encrypted or decrypted. Cannot be NULL. |
| Crypto_DataBlob *out | [out] Pointer to the Crypto_DataBlob structure for storing the updated data. Cannot be NULL. Initialize out to {0} before calling. Do not pre-allocate out->data. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>[CRYPTO_SUCCESS](capi-crypto-common-h.md#oh_crypto_errcode) if the operation succeeds.</li>          <li>[CRYPTO_INVALID_PARAMS](capi-crypto-common-h.md#oh_crypto_errcode) if ctx, in, or out is NULL.</li>          <li>[CRYPTO_NOT_SUPPORTED](capi-crypto-common-h.md#oh_crypto_errcode) if unsupported operation or algorithm.</li>          <li>[CRYPTO_MEMORY_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if memory operation fails.</li>          <li>[CRYPTO_PARAMETER_CHECK_FAILED](capi-crypto-common-h.md#oh_crypto_errcode) if parameters are invalid. [since 20]</li>          <li>[CRYPTO_OPERTION_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if cipher update fails.</li>          </ul> |

**Reference**:

[OH_CryptoSymCipher_Final](capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_final) Finishes the cipher operation, outputting the final result


### OH_CryptoSymCipher_Final()

```c
OH_Crypto_ErrCode OH_CryptoSymCipher_Final(OH_CryptoSymCipher *ctx, Crypto_DataBlob *in, Crypto_DataBlob *out)
```

**Description**

Finishes the cipher operation, outputting the final result.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoSymCipher](capi-cryptosymcipherapi-oh-cryptosymcipher.md) *ctx | [in] Symmetric cipher context. Cannot be NULL. |
| Crypto_DataBlob *in | [in] Data to be encrypted or decrypted. Can be NULL if all data has been updated via [OH_CryptoSymCipher_Update](capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_update). |
| Crypto_DataBlob *out | [out] Pointer to the Crypto_DataBlob structure for storing the final result. Cannot be NULL. Initialize out to {0} before calling. Do not pre-allocate out->data. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>[CRYPTO_SUCCESS](capi-crypto-common-h.md#oh_crypto_errcode) if the operation succeeds.</li>          <li>[CRYPTO_INVALID_PARAMS](capi-crypto-common-h.md#oh_crypto_errcode) if ctx or out is NULL.</li>          <li>[CRYPTO_NOT_SUPPORTED](capi-crypto-common-h.md#oh_crypto_errcode) if unsupported operation or algorithm.</li>          <li>[CRYPTO_MEMORY_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if memory operation fails.</li>          <li>[CRYPTO_PARAMETER_CHECK_FAILED](capi-crypto-common-h.md#oh_crypto_errcode) if parameters are invalid. [since 20]</li>          <li>[CRYPTO_OPERTION_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if cipher final fails. Possible causes:             incorrect IV or key during decryption; AEAD (GCM/CCM) authentication tag verification             failure due to incorrect TAG, AAD, ciphertext, or key; block cipher (e.g. AES-CBC/ECB)             decryption where ciphertext length is not a multiple of the block size; block cipher             encryption with NoPadding where plaintext length is not a multiple of the block size.</li>          </ul> |

### OH_CryptoSymCipher_GetAlgoName()

```c
const char *OH_CryptoSymCipher_GetAlgoName(OH_CryptoSymCipher *ctx)
```

**Description**

Obtains the symmetric cipher algorithm name.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoSymCipher](capi-cryptosymcipherapi-oh-cryptosymcipher.md) *ctx | [in] Symmetric cipher context. Cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| const char * | Returns the symmetric cipher algorithm name. No need to free by the caller. Invalid after      the context is destroyed. |

### OH_CryptoSymCipher_Destroy()

```c
void OH_CryptoSymCipher_Destroy(OH_CryptoSymCipher *ctx)
```

**Description**

Destroys the symmetric cipher context.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoSymCipher](capi-cryptosymcipherapi-oh-cryptosymcipher.md) *ctx | [in] Symmetric cipher context. |


