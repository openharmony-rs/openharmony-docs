# crypto_asym_cipher.h

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=76caeef80126e754bb89b8cf8b2b7380f3d3d3a7 translatedAt=2026-08-20T12:24:50.886Z pushedAt=2026-08-23T06:51:51.163Z -->

## Overview

Defines APIs for asymmetric encryption and decryption.

**Header file**: <CryptoArchitectureKit/crypto_asym_cipher.h>

**Library**: libohcrypto.so

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 20

**Related module**: [CryptoAsymCipherApi](capi-cryptoasymcipherapi.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_CryptoAsymCipher](capi-cryptoasymcipherapi-oh-cryptoasymcipher.md) | OH_CryptoAsymCipher | Defines an asymmetric cipher struct, indicating the asymmetric cipher context. |
| [OH_CryptoSm2CiphertextSpec](capi-cryptoasymcipherapi-oh-cryptosm2ciphertextspec.md) | OH_CryptoSm2CiphertextSpec | Defines a struct for SM2 ciphertext specifications. |

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [CryptoSm2CiphertextSpec_item](#cryptosm2ciphertextspec_item) | CryptoSm2CiphertextSpec_item | Defines the type of SM2 ciphertext specification items.|

### Functions

| Name| Description|
| -- | -- |
| [OH_Crypto_ErrCode OH_CryptoAsymCipher_Create(const char *algoName, OH_CryptoAsymCipher **ctx)](#oh_cryptoasymcipher_create) | Creates an asymmetric cipher context based on the given algorithm name.<br> Note: The created resource must be destroyed by calling [OH_CryptoAsymCipher_Destroy](capi-crypto-asym-cipher-h.md#oh_cryptoasymcipher_destroy). |
| [OH_Crypto_ErrCode OH_CryptoAsymCipher_Init(OH_CryptoAsymCipher *ctx, Crypto_CipherMode mode, OH_CryptoKeyPair *key)](#oh_cryptoasymcipher_init) | Initializes the asymmetric cipher context using the given cipher mode and key. |
| [OH_Crypto_ErrCode OH_CryptoAsymCipher_Final(OH_CryptoAsymCipher *ctx, const Crypto_DataBlob *in, Crypto_DataBlob *out)](#oh_cryptoasymcipher_final) | Finalizes the cipher operation.<br> Note: After this method is used, the memory for storing the **out** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob). |
| [void OH_CryptoAsymCipher_Destroy(OH_CryptoAsymCipher *ctx)](#oh_cryptoasymcipher_destroy) | Destroys the asymmetric cipher context. |
| [OH_Crypto_ErrCode OH_CryptoSm2CiphertextSpec_Create(Crypto_DataBlob *sm2Ciphertext, OH_CryptoSm2CiphertextSpec **spec)](#oh_cryptosm2ciphertextspec_create) | Creates SM2 ciphertext specifications.<br> Note: The created resource must be destroyed by calling [OH_CryptoSm2CiphertextSpec_Destroy](capi-crypto-asym-cipher-h.md#oh_cryptosm2ciphertextspec_destroy).|
| [OH_Crypto_ErrCode OH_CryptoSm2CiphertextSpec_GetItem(OH_CryptoSm2CiphertextSpec *spec, CryptoSm2CiphertextSpec_item item, Crypto_DataBlob *out)](#oh_cryptosm2ciphertextspec_getitem) | Obtains a specified item in SM2 ciphertext specifications.<br> Note: After this method is used, the memory for storing the **out** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob). |
| [OH_Crypto_ErrCode OH_CryptoSm2CiphertextSpec_SetItem(OH_CryptoSm2CiphertextSpec *spec, CryptoSm2CiphertextSpec_item item, Crypto_DataBlob *in)](#oh_cryptosm2ciphertextspec_setitem) | Sets a specified item in SM2 ciphertext specifications. |
| [OH_Crypto_ErrCode OH_CryptoSm2CiphertextSpec_Encode(OH_CryptoSm2CiphertextSpec *spec, Crypto_DataBlob *out)](#oh_cryptosm2ciphertextspec_encode) | Encodes SM2 ciphertext specifications into DER ciphertext.<br> Note: After this method is used, the memory for storing the **out** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob).|
| [void OH_CryptoSm2CiphertextSpec_Destroy(OH_CryptoSm2CiphertextSpec *spec)](#oh_cryptosm2ciphertextspec_destroy) | Destroys SM2 ciphertext specifications.|

## Enum Description

### CryptoSm2CiphertextSpec_item

```c
enum CryptoSm2CiphertextSpec_item
```

**Description**

Defines the type of SM2 ciphertext specification items.

**Since**: 20

| Enum Item| Description|
| -- | -- |
| CRYPTO_SM2_CIPHERTEXT_C1_X = 0 | Public key x, also called C1x.|
| CRYPTO_SM2_CIPHERTEXT_C1_Y = 1 | Public key y, also called C1y.|
| CRYPTO_SM2_CIPHERTEXT_C2 = 2 | Hash value, also called C2.|
| CRYPTO_SM2_CIPHERTEXT_C3 = 3 | Ciphertext data, also called C3.|

## Function Description

### OH_CryptoAsymCipher_Create()

```c
OH_Crypto_ErrCode OH_CryptoAsymCipher_Create(const char *algoName, OH_CryptoAsymCipher **ctx)
```

**Description**

Creates an asymmetric cipher context based on the given algorithm name.

Note: The created resource must be destroyed by calling [OH_CryptoAsymCipher_Destroy](capi-crypto-asym-cipher-h.md#oh_cryptoasymcipher_destroy).

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| const char *algoName | Input parameter, indicating the name of the asymmetric encryption/decryption algorithm, which cannot be null. The options are as follows:<br>- RSA with PKCS1 padding: The value is **RSA\|PKCS1**.<br>- RSA with OAEP padding: The value is in the format of **RSA\|PKCS1_OAEP\|MD\|MGF1 MD**, for example, **RSA\|PKCS1_OAEP\|SHA256\|MGF1_SHA256**. The MD can be set to **MD5**, **SHA1**, **SHA224**, **SHA256**, **SHA384**, or **SHA512**. The MGF1 MD can be set to **MGF1_SHA1**, **MGF1_SHA224**, **MGF1_SHA256**, **MGF1_SHA384**, or **MGF1_SHA512**.<br>- RSA with no padding: The value is **RSA\|NoPadding**.<br>- SM2: The value is in the format of **SM2\|MD**, for example, **SM2\|SM3**. The MD can be set to **MD5**, **SHA1**, **SHA224**, **SHA256**, **SHA384**, **SHA512**, or **SM3**. |
| [OH_CryptoAsymCipher](capi-cryptoasymcipherapi-oh-cryptoasymcipher.md) **ctx | Output parameter, indicating a pointer to the asymmetric cipher context. The value of **ctx** cannot be null, but the value of ***ctx** must be null. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: **algoName** or **ctx** is null.<br>**CRYPTO_NOT_SUPPORTED**: The algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation fails.<br>**CRYPTO_OPERTION_ERROR**: The cipher operation fails. |

**Reference**

[OH_CryptoAsymCipher_Init](capi-crypto-asym-cipher-h.md#oh_cryptoasymcipher_init) for initializing the asymmetric cipher context.

### OH_CryptoAsymCipher_Init()

```c
OH_Crypto_ErrCode OH_CryptoAsymCipher_Init(OH_CryptoAsymCipher *ctx, Crypto_CipherMode mode, OH_CryptoKeyPair *key)
```

**Description**

Initializes the asymmetric cipher context using the given cipher mode and key.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoAsymCipher](capi-cryptoasymcipherapi-oh-cryptoasymcipher.md) *ctx | Input parameter, indicating the asymmetric cipher context. The value cannot be null. |
| [Crypto_CipherMode](capi-crypto-common-h.md#crypto_ciphermode) mode | Input parameter, indicating the cipher mode, which can be encryption or decryption. |
| [OH_CryptoKeyPair](capi-cryptoasymkeyapi-oh-cryptokeypair.md) *key | Input parameter, indicating an asymmetric key. The value cannot be null. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: **ctx** or **key** is null.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory operation fails.<br>**CRYPTO_OPERTION_ERROR**: The cipher operation initialization fails. |

**Reference**

[OH_CryptoAsymCipher_Final](capi-crypto-asym-cipher-h.md#oh_cryptoasymcipher_final) for finalizing the cipher operation.

### OH_CryptoAsymCipher_Final()

```c
OH_Crypto_ErrCode OH_CryptoAsymCipher_Final(OH_CryptoAsymCipher *ctx, const Crypto_DataBlob *in, Crypto_DataBlob *out)
```

**Description**

Finalizes the cipher operation.

Note: After this method is used, the memory for storing the **out** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob).

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoAsymCipher](capi-cryptoasymcipherapi-oh-cryptoasymcipher.md) *ctx | Input parameter, indicating the asymmetric cipher context. The value cannot be null. |
| [const Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *in | Input parameter, indicating the data to be encrypted or decrypted. The value cannot be null. |
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *out | Output parameter, indicating a pointer to the **Crypto_DataBlob** struct used to store the encryption or decryption result. The value cannot be null. Before calling this method, initialize **out** to 0. Do not set the **data** field of **out**. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: **ctx**, **in**, or **out** is null.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation fails.<br>**CRYPTO_OPERTION_ERROR**: The cipher operation fails. The possible causes are as follows:<br>During encryption using RSA, the length of the plaintext exceeds the maximum length allowed by the key length and padding mode.<br>During decryption using RSA, the key is incorrect or the ciphertext is damaged.<br>During decryption using SM2, the key is incorrect or the ciphertext is damaged.<br>The ASN.1 structure of the SM2 ciphertext is invalid. |

### OH_CryptoAsymCipher_Destroy()

```c
void OH_CryptoAsymCipher_Destroy(OH_CryptoAsymCipher *ctx)
```

**Description**

Destroys the asymmetric cipher context.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoAsymCipher](capi-cryptoasymcipherapi-oh-cryptoasymcipher.md) *ctx | Input parameter, indicating the asymmetric cipher context. |

### OH_CryptoSm2CiphertextSpec_Create()

```c
OH_Crypto_ErrCode OH_CryptoSm2CiphertextSpec_Create(Crypto_DataBlob *sm2Ciphertext, OH_CryptoSm2CiphertextSpec **spec)
```

**Description**

Creates SM2 ciphertext specifications.

Note: The created resource must be destroyed by calling [OH_CryptoSm2CiphertextSpec_Destroy](capi-crypto-asym-cipher-h.md#oh_cryptosm2ciphertextspec_destroy).

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *sm2Ciphertext | Input parameter, indicating the SM2 ciphertext in DER format. If the value is null, an empty SM2 ciphertext specification is created. |
| [OH_CryptoSm2CiphertextSpec](capi-cryptoasymcipherapi-oh-cryptosm2ciphertextspec.md) **spec | Output parameter, indicating a pointer to the SM2 ciphertext specification. The value of **spec** cannot be null, but the value of ***spec** must be null. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: **spec** is null.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation fails.<br>**CRYPTO_OPERTION_ERROR**: The SM2 ciphertext fails to be parsed. A possible cause is that the input data is not valid SM2 ciphertext encoded in DER format. |

**Reference**

[OH_CryptoSm2CiphertextSpec_GetItem](capi-crypto-asym-cipher-h.md#oh_cryptosm2ciphertextspec_getitem) for obtaining a specified item in SM2 ciphertext specifications.

[OH_CryptoSm2CiphertextSpec_SetItem](capi-crypto-asym-cipher-h.md#oh_cryptosm2ciphertextspec_setitem) for setting a specified item in SM2 ciphertext specifications.

### OH_CryptoSm2CiphertextSpec_GetItem()

```c
OH_Crypto_ErrCode OH_CryptoSm2CiphertextSpec_GetItem(OH_CryptoSm2CiphertextSpec *spec, CryptoSm2CiphertextSpec_item item, Crypto_DataBlob *out)
```

**Description**

Obtains a specified item in SM2 ciphertext specifications.

Note: After this method is used, the memory for storing the **out** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob).

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoSm2CiphertextSpec](capi-cryptoasymcipherapi-oh-cryptosm2ciphertextspec.md) *spec | Input parameter, indicating a pointer to the SM2 ciphertext specifications. The value cannot be null. |
| [CryptoSm2CiphertextSpec_item](capi-crypto-asym-cipher-h.md#cryptosm2ciphertextspec_item) item | Input parameter, indicating an item in the SM2 ciphertext specifications. |
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *out | Output parameter, indicating a pointer to the **Crypto_DataBlob** struct used to store the output data. The value cannot be null. Before calling this method, initialize **out** to 0. Do not set the **data** field of **out**. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: **spec** or **out** is null.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation fails.<br>**CRYPTO_OPERTION_ERROR**: The cipher operation fails. |

### OH_CryptoSm2CiphertextSpec_SetItem()

```c
OH_Crypto_ErrCode OH_CryptoSm2CiphertextSpec_SetItem(OH_CryptoSm2CiphertextSpec *spec, CryptoSm2CiphertextSpec_item item, Crypto_DataBlob *in)
```

**Description**

Sets a specified item in the SM2 ciphertext specifications.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoSm2CiphertextSpec](capi-cryptoasymcipherapi-oh-cryptosm2ciphertextspec.md) *spec | Input parameter, indicating a pointer to the SM2 ciphertext specifications. The value cannot be null. |
| [CryptoSm2CiphertextSpec_item](capi-crypto-asym-cipher-h.md#cryptosm2ciphertextspec_item) item | Input parameter, indicating an item in the SM2 ciphertext specifications. |
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *in | Input parameter, indicating the input data. The value cannot be null. This API performs deep copy of the input data. The caller can immediately release the input data after the API returns a result. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: **spec** or **in** is null, **data** of **in** is null, or **len** of **in** is **0**.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation for deep copy fails.<br>**CRYPTO_OPERTION_ERROR**: The cipher operation fails. |

**Reference**

[OH_CryptoSm2CiphertextSpec_Encode](capi-crypto-asym-cipher-h.md#oh_cryptosm2ciphertextspec_encode) for encoding SM2 ciphertext specifications into DER ciphertext.

### OH_CryptoSm2CiphertextSpec_Encode()

```c
OH_Crypto_ErrCode OH_CryptoSm2CiphertextSpec_Encode(OH_CryptoSm2CiphertextSpec *spec, Crypto_DataBlob *out)
```

**Description**

Encodes the SM2 ciphertext specifications into DER-format ciphertext.

Note: After this method is used, the memory for storing the **out** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob).

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoSm2CiphertextSpec](capi-cryptoasymcipherapi-oh-cryptosm2ciphertextspec.md) *spec | Input parameter, indicating a pointer to the SM2 ciphertext specifications. The value cannot be null. |
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *out | Output parameter, indicating a pointer to the **Crypto_DataBlob** struct used to store the encoded data. The value cannot be null. Before calling this method, initialize **out** to 0. Do not set the **data** field of **out**. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: **spec** or **out** is null, the SM2 ciphertext fields (C1X, C1Y, C2, and C3) are not set, or the length of C3 (**hashData**) is not 32 bytes.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: The memory operation fails.<br>**CRYPTO_OPERTION_ERROR**: Encoding fails. |

### OH_CryptoSm2CiphertextSpec_Destroy()

```c
void OH_CryptoSm2CiphertextSpec_Destroy(OH_CryptoSm2CiphertextSpec *spec)
```

**Description**

Destroys SM2 ciphertext specifications.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoSm2CiphertextSpec](capi-cryptoasymcipherapi-oh-cryptosm2ciphertextspec.md) *spec | Input parameter, indicating a pointer to the SM2 ciphertext specifications. |