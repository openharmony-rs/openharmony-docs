# crypto_sym_cipher.h

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

## Overview

Defines APIs for symmetric encryption and decryption.

**Header file**: <CryptoArchitectureKit/crypto_sym_cipher.h>

**Library**: libohcrypto.so

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 12

**Related module**: [CryptoSymCipherApi](capi-cryptosymcipherapi.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_CryptoSymCipher](capi-cryptosymcipherapi-oh-cryptosymcipher.md) | OH_CryptoSymCipher | Defines a symmetric cipher struct, indicating the symmetric cipher context.|
| [OH_CryptoSymCipherParams](capi-cryptosymcipherapi-oh-cryptosymcipherparams.md) | OH_CryptoSymCipherParams | Defines a symmetric cipher parameter struct, indicating the symmetric cipher parameters.|

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [CryptoSymCipher_ParamsType](#cryptosymcipher_paramstype) | CryptoSymCipher_ParamsType | Enumerates the types of cipher parameters.|

### Functions

| Name| Description|
| -- | -- |
| [OH_Crypto_ErrCode OH_CryptoSymCipherParams_Create(OH_CryptoSymCipherParams **params)](#oh_cryptosymcipherparams_create) | Creates symmetric cipher parameters.<br> Note: The created resource must be destroyed by calling [OH_CryptoSymCipherParams_Destroy](capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_destroy). |
| [OH_Crypto_ErrCode OH_CryptoSymCipherParams_SetParam(OH_CryptoSymCipherParams *params, CryptoSymCipher_ParamsType paramsType, Crypto_DataBlob *value)](#oh_cryptosymcipherparams_setparam) | Sets cipher parameters.|
| [void OH_CryptoSymCipherParams_Destroy(OH_CryptoSymCipherParams *params)](#oh_cryptosymcipherparams_destroy) | Destroys cipher parameters.|
| [OH_Crypto_ErrCode OH_CryptoSymCipher_Create(const char *algoName, OH_CryptoSymCipher **ctx)](#oh_cryptosymcipher_create) | Creates a symmetric key cipher context based on the given algorithm name.<br> Note: The created resource must be destroyed by calling [OH_CryptoSymCipher_Destroy](capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_destroy). |
| [OH_Crypto_ErrCode OH_CryptoSymCipher_Init(OH_CryptoSymCipher *ctx, Crypto_CipherMode mod, OH_CryptoSymKey *key, OH_CryptoSymCipherParams *params)](#oh_cryptosymcipher_init) | Initializes the encryption or decryption operation using the given cipher mode, key, and parameters.|
| [OH_Crypto_ErrCode OH_CryptoSymCipher_Update(OH_CryptoSymCipher *ctx, Crypto_DataBlob *in, Crypto_DataBlob *out)](#oh_cryptosymcipher_update) | Updates the encryption or decryption data and outputs the encrypted or decrypted data.<br> Note: After the use is complete, the memory for storing the **out** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob). |
| [OH_Crypto_ErrCode OH_CryptoSymCipher_Final(OH_CryptoSymCipher *ctx, Crypto_DataBlob *in, Crypto_DataBlob *out)](#oh_cryptosymcipher_final) | Finalizes the cipher operation and output the final result. <br> Note: After the use is complete, the memory for storing the **out** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob).|
| [const char *OH_CryptoSymCipher_GetAlgoName(OH_CryptoSymCipher *ctx)](#oh_cryptosymcipher_getalgoname) | Obtains the symmetric encryption/decryption algorithm.|
| [void OH_CryptoSymCipher_Destroy(OH_CryptoSymCipher *ctx)](#oh_cryptosymcipher_destroy) | Destroys the symmetric cipher context.|

## Enum Description

### CryptoSymCipher_ParamsType

```c
enum CryptoSymCipher_ParamsType
```

**Description**

Enumerates the types of cipher parameters.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| CRYPTO_IV_DATABLOB = 100 | Initialization vector (IV) parameter.|
| CRYPTO_AAD_DATABLOB = 101 | Additional authentication data (AAD) in AEAD mode, such as GCM and CCM.|
| CRYPTO_TAG_DATABLOB = 102 | Authentication tag in AEAD mode, such as GCM and CCM, used for data integrity check.|


## Function Description

### OH_CryptoSymCipherParams_Create()

```c
OH_Crypto_ErrCode OH_CryptoSymCipherParams_Create(OH_CryptoSymCipherParams **params)
```

**Description**

Creates symmetric cipher parameters.

Note: The created resource must be destroyed by calling [OH_CryptoSymCipherParams_Destroy](capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_destroy).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoSymCipherParams](capi-cryptosymcipherapi-oh-cryptosymcipherparams.md) **params | Output parameter, indicating a pointer to the ciphering parameter. The value of **params** cannot be null, but the value of ***params** must be null.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_INVALID_PARAMS**: **params** is null.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: The memory operation fails.<br>**CRYPTO_OPERTION_ERROR**: The cipher operation fails.|

**Reference**

[OH_CryptoSymCipherParams_SetParam](capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_setparam) for setting cipher parameters.


### OH_CryptoSymCipherParams_SetParam()

```c
OH_Crypto_ErrCode OH_CryptoSymCipherParams_SetParam(OH_CryptoSymCipherParams *params, CryptoSymCipher_ParamsType paramsType, Crypto_DataBlob *value)
```

**Description**

Sets cipher parameters.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoSymCipherParams](capi-cryptosymcipherapi-oh-cryptosymcipherparams.md) *params | Input parameter, indicating cipher parameters. The value cannot be null.|
| [CryptoSymCipher_ParamsType](capi-crypto-sym-cipher-h.md#cryptosymcipher_paramstype) paramsType | Input parameter, indicating the type of the cipher parameter to be set.|
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *value | Input parameter, indicating the parameter value. This API performs shallow copy and does not copy the data in **value**. The caller must ensure that the memory to which **value** points remains valid before the [OH_CryptoSymCipher_Init](capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_init) call is complete. The value cannot be null.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_INVALID_PARAMS**: **params** or **value** is null, or **paramsType** cannot be identified.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: The memory operation fails.<br>**CRYPTO_OPERTION_ERROR**: The cipher operation fails.|

### OH_CryptoSymCipherParams_Destroy()

```c
void OH_CryptoSymCipherParams_Destroy(OH_CryptoSymCipherParams *params)
```

**Description**

Destroys cipher parameters.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoSymCipherParams](capi-cryptosymcipherapi-oh-cryptosymcipherparams.md) *params | Input parameter, indicating cipher parameters.|

### OH_CryptoSymCipher_Create()

```c
OH_Crypto_ErrCode OH_CryptoSymCipher_Create(const char *algoName, OH_CryptoSymCipher **ctx)
```

**Description**

Creates a symmetric key cipher context based on the given algorithm name.

Note: The created resource must be destroyed by calling [OH_CryptoSymCipher_Destroy](capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_destroy).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const char *algoName | Input parameter, indicating the name of the symmetric encryption/decryption algorithm, which cannot be **NULL**. The value is in the format of **Algorithm\|Mode\|Padding**. Different parts are separated by vertical bars (\|). The algorithms can be set to **AES128**, **AES192**, **AES256**, **SM4_128**, **3DES192**, **DES64**, **ChaCha20**, **RC2, Blowfish**, or **CAST**. The modes can be set to **ECB**, **CBC**, **CTR**, **OFB**, **CFB**, **CFB1**, **CFB8**, **CFB64**, **CFB128**, **GCM**, **CCM**, **XTS**, or **Poly1305**. The padding can be set to **NoPadding**, **PKCS5**, or **PKCS7**. The following algorithms are supported:<br>- Since API version 12, the **AES128**, **AES192**, and **AES256** algorithms are supported. The modes can be set to **ECB**, **CBC**, **CTR**, **OFB**, **CFB**, **GCM**, or **CCM**. The padding can be set to **NoPadding** or **PKCS7**. Example: **AES128\|GCM** or **AES256\|CBC\|PKCS7**.<br>- Since API version 12, the **3DES192** algorithm is supported. The mode can be set to **ECB**, **CBC**, **OFB**, or **CFB**. The padding can be set to **NoPadding**, **PKCS5**, or **PKCS7**. Example: **3DES192\|CBC\|PKCS5**.<br>- Since API version 12, the **SM4_128** algorithm is supported. The mode can be set to **ECB**, **CBC**, **CTR**, **OFB**, **CFB**, **CFB128**, or **GCM**. The padding can be set to **NoPadding** or **PKCS7**. Example: **SM4_128\|CBC\|PKCS7** or **SM4_128\|GCM\|NoPadding**.<br>- Since API version 20, the **DES64** algorithm is supported. The mode can be set to **ECB**, **CBC**, **OFB**, or **CFB**. The padding can be set to **NoPadding**, **PKCS5**, or **PKCS7**. Example: **DES64\|CBC\|PKCS5**.<br>- Since API version 22, the **AES128_WRAP**, **AES192_WRAP**, and **AES256_WRAP** algorithms are supported. Example: **AES128_WRAP**, **AES192_WRAP**, or **AES256_WRAP**.<br>- Since API version 22, **ChaCha20** and **ChaCha20\|Poly1305** are supported. Example: **ChaCha20\|Poly1305** or **ChaCha20**.<br>- Since API version 26.0.0, the AES algorithm in XTS mode is supported. Example: **AES128\|XTS** or **AES256\|XTS**. Note that **AES192** is not supported.<br>- Since API version 26.0.0, the **RC2** algorithm is supported. The mode can be set to **ECB**, **CBC**, **OFB**, or **CFB**. The padding can be set to **NoPadding**, **PKCS5**, or **PKCS7**. Example: **RC2\|CBC\|PKCS5**.<br>- Since API version 26.0.0, **RC4** is supported. Example: **RC4**.<br>- Since API version 26.0.0, the **Blowfish** algorithm is supported. The mode can be set to **ECB**, **CBC**, **OFB**, or **CFB**. The padding can be set to **NoPadding**, **PKCS5**, or **PKCS7**. Example: **Blowfish\|CBC\|PKCS5**.<br>- Since API version 26.0.0, the **CAST** algorithm is supported. The mode can be set to **ECB**, **CBC**, **OFB**, or **CFB**. The padding can be set to **NoPadding**, **PKCS5**, or **PKCS7**. Example: **CAST\|CBC\|PKCS5**. Padding description:<br>- The **ECB** and **CBC** modes involve padding. If the plaintext length is not an integer multiple of the algorithm block size, **PKCS5** or **PKCS7** padding must be used. If **NoPadding** is used, the input data length must be an integer multiple of the algorithm block size (16 bytes for **AES** and **SM4**, and 8 bytes for **DES**, **3DES**, **RC2**, **Blowfish**, and **CAST**).<br>- The **CTR**, **OFB**, **CFB**, **CFB1**, **CFB8**, **CFB64**, **CFB128**, **GCM**, and **CCM** modes convert block ciphers into stream ciphers and do not require padding. Any padding specified is treated as **NoPadding**.<br>- The **XTS** mode does not involve padding. Therefore, you do not need to specify a padding field. Any padding specified is treated as **NoPadding**.<br>- **ChaCha20** is a stream cryptographic algorithm and does not require a padding field. Any padding specified is treated as **NoPadding**.|
| [OH_CryptoSymCipher](capi-cryptosymcipherapi-oh-cryptosymcipher.md) **ctx | Output parameter, indicating a pointer to the symmetric cipher context. The value of **ctx** cannot be null, but the value of ***ctx** must be null.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_INVALID_PARAMS**: The value of **ctx** or **algoName** is null.<br>**CRYPTO_NOT_SUPPORTED**: The algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation fails.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: The parameter is invalid. Applicable versions: 20+<br>**CRYPTO_OPERTION_ERROR**: The cipher operation fails.|

**Reference**

[OH_CryptoSymCipher_Init](capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_init) for initializing the encryption or decryption operation using the given cipher mode, key, and parameters.


### OH_CryptoSymCipher_Init()

```c
OH_Crypto_ErrCode OH_CryptoSymCipher_Init(OH_CryptoSymCipher *ctx, Crypto_CipherMode mod, OH_CryptoSymKey *key, OH_CryptoSymCipherParams *params)
```

**Description**

Initializes the encryption or decryption operation using the given cipher mode, key, and parameters.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoSymCipher](capi-cryptosymcipherapi-oh-cryptosymcipher.md) *ctx | Input parameter, indicating the symmetric cipher context. The value cannot be null.|
| [Crypto_CipherMode](capi-crypto-common-h.md#crypto_ciphermode) mod | Input parameter, indicating the cipher mode, which can be encryption or decryption.|
| [OH_CryptoSymKey](capi-cryptosymkeyapi-oh-cryptosymkey.md) *key | Input parameter, indicating a symmetric key. The value cannot be null.|
| [OH_CryptoSymCipherParams](capi-cryptosymcipherapi-oh-cryptosymcipherparams.md) *params | Input parameter, indicating an algorithm parameter, for example, **IV**. In ECB mode, the value must be null. In other modes, the value cannot be null.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_INVALID_PARAMS**: **ctx** or **key** is null, or the IV is missing or has an incorrect length in non-ECB mode.<br>**CRYPTO_NOT_SUPPORTED**: The operation is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation fails.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: The parameter is invalid. Applicable versions: 20+<br>**CRYPTO_OPERTION_ERROR**: The cipher operation initialization fails. Possible causes: The key length does not match the algorithm.|

**Reference**

[OH_CryptoSymCipher_Update](capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_update) for updating the encryption or decryption data and outputting the encrypted or decrypted data.

[OH_CryptoSymCipher_Final](capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_final) finalizing the cipher operation and outputting the final result. 


### OH_CryptoSymCipher_Update()

```c
OH_Crypto_ErrCode OH_CryptoSymCipher_Update(OH_CryptoSymCipher *ctx, Crypto_DataBlob *in, Crypto_DataBlob *out)
```

**Description**

Updates the encryption or decryption data and outputs the encrypted or decrypted data.

Note: After the use is complete, the memory for storing the **out** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoSymCipher](capi-cryptosymcipherapi-oh-cryptosymcipher.md) *ctx | Input parameter, indicating the symmetric cipher context. The value cannot be null.|
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *in | Input parameter, indicating the data to be encrypted or decrypted. The value cannot be null.|
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *out | Output parameter, indicating a pointer to the **Crypto_DataBlob** struct used to store the updated data. The value cannot be null. Before calling this method, initialize **out** to 0. Do not set the **data** field of **out**.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_INVALID_PARAMS**: **ctx**, **in**, or **out** is null.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: The memory operation fails.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: The parameter is invalid. Applicable versions: 20+<br>**CRYPTO_OPERTION_ERROR**: The cipher operation update fails.|

**Reference**

[OH_CryptoSymCipher_Final](capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_final) finalizing the cipher operation and outputting the final result. 


### OH_CryptoSymCipher_Final()

```c
OH_Crypto_ErrCode OH_CryptoSymCipher_Final(OH_CryptoSymCipher *ctx, Crypto_DataBlob *in, Crypto_DataBlob *out)
```

**Description**

Finalizes the cipher operation and output the final result. 

Note: After the use is complete, the memory for storing the **out** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoSymCipher](capi-cryptosymcipherapi-oh-cryptosymcipher.md) *ctx | Input parameter, indicating the symmetric cipher context. The value cannot be null.|
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *in | Input parameter, indicating the data to be encrypted or decrypted. If all data has been updated by calling [OH_CryptoSymCipher_Update](capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_update), this parameter can be null.|
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *out | Output parameter, indicating a pointer to the **Crypto_DataBlob** struct used to store the final result. The value cannot be null. Before calling this method, initialize **out** to 0. Do not set the **data** field of **out**.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_INVALID_PARAMS**: The value of **ctx** or **out** is null.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: The memory operation fails.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: The parameter is invalid. Applicable versions: 20+<br>**CRYPTO_OPERTION_ERROR**: The cipher finally fails. The possible causes are as follows:<br>The IV or key is incorrect during decryption. The AEAD (GCM/CCM) authentication tag fails to be verified (the tag, AAD, ciphertext, or key is incorrect).<br>The length of the ciphertext is not an integer multiple of the block size during the decryption of a block cipher (such as AES-CBC/ECB).<br>The length of the plaintext is not an integer multiple of the block size when the block cipher uses NoPadding for encryption.|

### OH_CryptoSymCipher_GetAlgoName()

```c
const char *OH_CryptoSymCipher_GetAlgoName(OH_CryptoSymCipher *ctx)
```

**Description**

Obtains the symmetric encryption/decryption algorithm.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoSymCipher](capi-cryptosymcipherapi-oh-cryptosymcipher.md) *ctx | Input parameter, indicating the symmetric cipher context. The value cannot be null.|

**Returns**

| Type| Description|
| -- | -- |
| const char * | Name of the symmetric cipher encryption/decryption algorithm, which does not need to be released by the caller. This value cannot be used after the context is destroyed.|

### OH_CryptoSymCipher_Destroy()

```c
void OH_CryptoSymCipher_Destroy(OH_CryptoSymCipher *ctx)
```

**Description**

Destroys the symmetric cipher context.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoSymCipher](capi-cryptosymcipherapi-oh-cryptosymcipher.md) *ctx | Input parameter, indicating the symmetric cipher context.|
