# crypto_asym_cipher.h

## Overview

Defines the asymmetric cipher interfaces.

**Include**: <CryptoArchitectureKit/crypto_asym_cipher.h>

**Library**: libohcrypto.so

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 20

**Related module**: [CryptoAsymCipherApi](capi-cryptoasymcipherapi.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_CryptoAsymCipher](capi-cryptoasymcipherapi-oh-cryptoasymcipher.md) | OH_CryptoAsymCipher | Asymmetric cipher structure, representing an asymmetric cipher context. |
| [OH_CryptoSm2CiphertextSpec](capi-cryptoasymcipherapi-oh-cryptosm2ciphertextspec.md) | OH_CryptoSm2CiphertextSpec | SM2 ciphertext specification structure, representing an SM2 ciphertext specification. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [CryptoSm2CiphertextSpec_item](#cryptosm2ciphertextspec_item) | CryptoSm2CiphertextSpec_item | Defines SM2 ciphertext specification item types. |

### Function

| Name | Description |
| -- | -- |
| [OH_Crypto_ErrCode OH_CryptoAsymCipher_Create(const char *algoName, OH_CryptoAsymCipher **ctx)](#oh_cryptoasymcipher_create) | Creates an asymmetric cipher context based on the given algorithm name. |
| [OH_Crypto_ErrCode OH_CryptoAsymCipher_Init(OH_CryptoAsymCipher *ctx, Crypto_CipherMode mode, OH_CryptoKeyPair *key)](#oh_cryptoasymcipher_init) | Initializes the asymmetric cipher context with the given cipher mode and key. |
| [OH_Crypto_ErrCode OH_CryptoAsymCipher_Final(OH_CryptoAsymCipher *ctx, const Crypto_DataBlob *in, Crypto_DataBlob *out)](#oh_cryptoasymcipher_final) | Finishes the cipher operation. |
| [void OH_CryptoAsymCipher_Destroy(OH_CryptoAsymCipher *ctx)](#oh_cryptoasymcipher_destroy) | Destroys the asymmetric cipher context. |
| [OH_Crypto_ErrCode OH_CryptoSm2CiphertextSpec_Create(Crypto_DataBlob *sm2Ciphertext, OH_CryptoSm2CiphertextSpec **spec)](#oh_cryptosm2ciphertextspec_create) | Creates an SM2 ciphertext specification. |
| [OH_Crypto_ErrCode OH_CryptoSm2CiphertextSpec_GetItem(OH_CryptoSm2CiphertextSpec *spec, CryptoSm2CiphertextSpec_item item, Crypto_DataBlob *out)](#oh_cryptosm2ciphertextspec_getitem) | Obtains the specified item of the SM2 ciphertext. |
| [OH_Crypto_ErrCode OH_CryptoSm2CiphertextSpec_SetItem(OH_CryptoSm2CiphertextSpec *spec, CryptoSm2CiphertextSpec_item item, Crypto_DataBlob *in)](#oh_cryptosm2ciphertextspec_setitem) | Sets the specified item of the SM2 ciphertext specification. |
| [OH_Crypto_ErrCode OH_CryptoSm2CiphertextSpec_Encode(OH_CryptoSm2CiphertextSpec *spec, Crypto_DataBlob *out)](#oh_cryptosm2ciphertextspec_encode) | Encodes the SM2 ciphertext specification to DER format ciphertext. |
| [void OH_CryptoSm2CiphertextSpec_Destroy(OH_CryptoSm2CiphertextSpec *spec)](#oh_cryptosm2ciphertextspec_destroy) | Destroys the SM2 ciphertext specification. |

## Enum type description

### CryptoSm2CiphertextSpec_item

```c
enum CryptoSm2CiphertextSpec_item
```

**Description**

Defines SM2 ciphertext specification item types.

**Since**: 20

| Enum item | Description |
| -- | -- |
| CRYPTO_SM2_CIPHERTEXT_C1_X = 0 | Public key x, also known as C1x.<br>**Since**: 20 |
| CRYPTO_SM2_CIPHERTEXT_C1_Y = 1 | Public key y, also known as C1y.<br>**Since**: 20 |
| CRYPTO_SM2_CIPHERTEXT_C2 = 2 | Ciphertext data, also known as C2.<br>**Since**: 20 |
| CRYPTO_SM2_CIPHERTEXT_C3 = 3 | Message digest (hash value), also known as C3.<br>**Since**: 20 |


## Function description

### OH_CryptoAsymCipher_Create()

```c
OH_Crypto_ErrCode OH_CryptoAsymCipher_Create(const char *algoName, OH_CryptoAsymCipher **ctx)
```

**Description**

Creates an asymmetric cipher context based on the given algorithm name.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *algoName | [in] Asymmetric cipher algorithm name. Cannot be NULL. Values: - RSA algorithm PKCS1 padding mode: "RSA\|PKCS1". - RSA algorithm OAEP padding mode: Format "RSA\|PKCS1_OAEP\|Digest\|MGF1Digest", e.g. "RSA\|PKCS1_OAEP\|SHA256\|MGF1_SHA256". Digest supports "MD5", "SHA1", "SHA224", "SHA256", "SHA384", "SHA512". MGF1 digest supports "MGF1_SHA1", "MGF1_SHA224", "MGF1_SHA256", "MGF1_SHA384", "MGF1_SHA512". - RSA algorithm NoPadding padding mode: "RSA\|NoPadding". - SM2 algorithm: Format "SM2\|Digest", e.g. "SM2\|SM3". Digest supports "MD5", "SHA1", "SHA224", "SHA256", "SHA384", "SHA512", "SM3". |
| [OH_CryptoAsymCipher](capi-cryptoasymcipherapi-oh-cryptoasymcipher.md) **ctx | [out] Pointer to the asymmetric cipher context pointer. ctx cannot be NULL, *ctx must be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_PARAMETER_CHECK_FAILED} if algoName or ctx is NULL.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if the algorithm is not supported.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory allocation fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if crypto operation fails.</li>          </ul> |

**Reference**:

[OH_CryptoAsymCipher_Init](capi-crypto-asym-cipher-h.md#oh_cryptoasymcipher_init) Initializes the asymmetric cipher context


### OH_CryptoAsymCipher_Init()

```c
OH_Crypto_ErrCode OH_CryptoAsymCipher_Init(OH_CryptoAsymCipher *ctx, Crypto_CipherMode mode, OH_CryptoKeyPair *key)
```

**Description**

Initializes the asymmetric cipher context with the given cipher mode and key.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoAsymCipher](capi-cryptoasymcipherapi-oh-cryptoasymcipher.md) *ctx | [in] Asymmetric cipher context. Cannot be NULL. |
| Crypto_CipherMode mode | [in] Cipher mode, encryption or decryption. |
| OH_CryptoKeyPair *key | [in] Asymmetric key. Cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_PARAMETER_CHECK_FAILED} if ctx or key is NULL.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if unsupported operation or algorithm.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory operation fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if cipher init fails.</li>          </ul> |

**Reference**:

[OH_CryptoAsymCipher_Final](capi-crypto-asym-cipher-h.md#oh_cryptoasymcipher_final) Finishes the cipher operation


### OH_CryptoAsymCipher_Final()

```c
OH_Crypto_ErrCode OH_CryptoAsymCipher_Final(OH_CryptoAsymCipher *ctx, const Crypto_DataBlob *in, Crypto_DataBlob *out)
```

**Description**

Finishes the cipher operation.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoAsymCipher](capi-cryptoasymcipherapi-oh-cryptoasymcipher.md) *ctx | [in] Asymmetric cipher context. Cannot be NULL. |
| const Crypto_DataBlob *in | [in] Data to be encrypted or decrypted. Cannot be NULL. |
| Crypto_DataBlob *out | [out] Pointer to the Crypto_DataBlob structure for storing the encrypted or decrypted result. Cannot be NULL. Initialize out to {0} before calling. Do not pre-allocate out->data. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_PARAMETER_CHECK_FAILED} if ctx, in, or out is NULL.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if unsupported operation or algorithm.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory allocation fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if cipher final fails. Possible causes:             RSA encryption where plaintext exceeds the maximum length allowed by the key size and             padding mode; RSA decryption with incorrect key or corrupted ciphertext; SM2 decryption             with incorrect key or corrupted ciphertext; SM2 ciphertext with invalid ASN.1 structure.</li>          </ul> |

### OH_CryptoAsymCipher_Destroy()

```c
void OH_CryptoAsymCipher_Destroy(OH_CryptoAsymCipher *ctx)
```

**Description**

Destroys the asymmetric cipher context.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoAsymCipher](capi-cryptoasymcipherapi-oh-cryptoasymcipher.md) *ctx | [in] Asymmetric cipher context. |

### OH_CryptoSm2CiphertextSpec_Create()

```c
OH_Crypto_ErrCode OH_CryptoSm2CiphertextSpec_Create(Crypto_DataBlob *sm2Ciphertext, OH_CryptoSm2CiphertextSpec **spec)
```

**Description**

Creates an SM2 ciphertext specification.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| Crypto_DataBlob *sm2Ciphertext | [in] SM2 ciphertext in DER format. If NULL, an empty SM2 ciphertext specification is created. |
| [OH_CryptoSm2CiphertextSpec](capi-cryptoasymcipherapi-oh-cryptosm2ciphertextspec.md) **spec | [out] Pointer to the SM2 ciphertext specification pointer. spec cannot be NULL, *spec must be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_PARAMETER_CHECK_FAILED} if spec is NULL.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if unsupported operation or algorithm.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory allocation fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if parsing SM2 ciphertext fails. Possible causes:             the input data is not valid DER-encoded SM2 ciphertext.</li>          </ul> |

**Reference**:

[OH_CryptoSm2CiphertextSpec_GetItem](capi-crypto-asym-cipher-h.md#oh_cryptosm2ciphertextspec_getitem) Obtains the specified item of the SM2 ciphertext
[OH_CryptoSm2CiphertextSpec_SetItem](capi-crypto-asym-cipher-h.md#oh_cryptosm2ciphertextspec_setitem) Sets the specified item of the SM2 ciphertext


### OH_CryptoSm2CiphertextSpec_GetItem()

```c
OH_Crypto_ErrCode OH_CryptoSm2CiphertextSpec_GetItem(OH_CryptoSm2CiphertextSpec *spec, CryptoSm2CiphertextSpec_item item, Crypto_DataBlob *out)
```

**Description**

Obtains the specified item of the SM2 ciphertext.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoSm2CiphertextSpec](capi-cryptoasymcipherapi-oh-cryptosm2ciphertextspec.md) *spec | [in] SM2 ciphertext specification. Cannot be NULL. |
| [CryptoSm2CiphertextSpec_item](capi-crypto-asym-cipher-h.md#cryptosm2ciphertextspec_item) item | [in] SM2 ciphertext specification item. |
| Crypto_DataBlob *out | [out] Pointer to the Crypto_DataBlob structure for storing the output data. Cannot be NULL. Initialize out to {0} before calling. Do not pre-allocate out->data. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_PARAMETER_CHECK_FAILED} if spec or out is NULL.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if unsupported operation or algorithm.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory allocation fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if crypto operation fails.</li>          </ul> |

### OH_CryptoSm2CiphertextSpec_SetItem()

```c
OH_Crypto_ErrCode OH_CryptoSm2CiphertextSpec_SetItem(OH_CryptoSm2CiphertextSpec *spec, CryptoSm2CiphertextSpec_item item, Crypto_DataBlob *in)
```

**Description**

Sets the specified item of the SM2 ciphertext specification.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoSm2CiphertextSpec](capi-cryptoasymcipherapi-oh-cryptosm2ciphertextspec.md) *spec | [in] SM2 ciphertext specification. Cannot be NULL. |
| [CryptoSm2CiphertextSpec_item](capi-crypto-asym-cipher-h.md#cryptosm2ciphertextspec_item) item | [in] SM2 ciphertext specification item. |
| Crypto_DataBlob *in | [in] Input data. Cannot be NULL. This function performs a deep copy of the input data. The caller can release in immediately after the function returns. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_PARAMETER_CHECK_FAILED} if spec or in is NULL,<br>           in->data is NULL, or in->len is 0.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if unsupported operation or algorithm.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory allocation for deep copy fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if crypto operation fails.</li>          </ul> |

**Reference**:

[OH_CryptoSm2CiphertextSpec_Encode](capi-crypto-asym-cipher-h.md#oh_cryptosm2ciphertextspec_encode) Encodes the SM2 ciphertext specification to DER format


### OH_CryptoSm2CiphertextSpec_Encode()

```c
OH_Crypto_ErrCode OH_CryptoSm2CiphertextSpec_Encode(OH_CryptoSm2CiphertextSpec *spec, Crypto_DataBlob *out)
```

**Description**

Encodes the SM2 ciphertext specification to DER format ciphertext.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoSm2CiphertextSpec](capi-cryptoasymcipherapi-oh-cryptosm2ciphertextspec.md) *spec | [in] SM2 ciphertext specification. Cannot be NULL. |
| Crypto_DataBlob *out | [out] Pointer to the Crypto_DataBlob structure for storing the encoded data. Cannot be NULL. Initialize out to {0} before calling. Do not pre-allocate out->data. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_PARAMETER_CHECK_FAILED} if spec or out is NULL,<br>           or SM2 ciphertext fields (C1X, C1Y, C2, C3) have not been set, or C3 (hashData)<br>           length is not 32 bytes.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if unsupported operation or algorithm.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory operation fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if encoding fails.</li>          </ul> |

### OH_CryptoSm2CiphertextSpec_Destroy()

```c
void OH_CryptoSm2CiphertextSpec_Destroy(OH_CryptoSm2CiphertextSpec *spec)
```

**Description**

Destroys the SM2 ciphertext specification.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoSm2CiphertextSpec](capi-cryptoasymcipherapi-oh-cryptosm2ciphertextspec.md) *spec | [in] SM2 ciphertext specification. |


