# crypto_sym_key.h

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

## Overview

Provides APIs for symmetric keys.

**Header file**: <CryptoArchitectureKit/crypto_sym_key.h>

**Library**: libohcrypto.so

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 12

**Related module**: [CryptoSymKeyApi](capi-cryptosymkeyapi.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_CryptoSymKey](capi-cryptosymkeyapi-oh-cryptosymkey.md) | OH_CryptoSymKey | Defines a symmetric key struct.|
| [OH_CryptoSymKeyGenerator](capi-cryptosymkeyapi-oh-cryptosymkeygenerator.md) | OH_CryptoSymKeyGenerator | Defines a struct for a symmetric key generator.|

### Functions

| Name| Description|
| -- | -- |
| [OH_Crypto_ErrCode OH_CryptoSymKeyGenerator_Create(const char *algoName, OH_CryptoSymKeyGenerator **ctx)](#oh_cryptosymkeygenerator_create) | Creates a symmetric key generator instance based on the given algorithm name. For example, **AES256**.<br> Note: The created resource must be destroyed by calling [OH_CryptoSymKeyGenerator_Destroy](capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_destroy).|
| [OH_Crypto_ErrCode OH_CryptoSymKeyGenerator_Generate(OH_CryptoSymKeyGenerator *ctx, OH_CryptoSymKey **keyCtx)](#oh_cryptosymkeygenerator_generate) | Randomly generates a symmetric key.<br> Note: After the use is complete, the memory for storing the **keyCtx** parameter must be destroyed by calling [OH_CryptoSymKey_Destroy](capi-crypto-sym-key-h.md#oh_cryptosymkey_destroy).|
| [OH_Crypto_ErrCode OH_CryptoSymKeyGenerator_Convert(OH_CryptoSymKeyGenerator *ctx, const Crypto_DataBlob *keyData, OH_CryptoSymKey **keyCtx)](#oh_cryptosymkeygenerator_convert) | Converts binary data into a symmetric key.<br> Note: After the use is complete, the memory for storing the **keyCtx** parameter must be destroyed by calling [OH_CryptoSymKey_Destroy](capi-crypto-sym-key-h.md#oh_cryptosymkey_destroy).|
| [const char *OH_CryptoSymKeyGenerator_GetAlgoName(OH_CryptoSymKeyGenerator *ctx)](#oh_cryptosymkeygenerator_getalgoname) | Obtains the algorithm of a symmetric key generator instance.|
| [void OH_CryptoSymKeyGenerator_Destroy(OH_CryptoSymKeyGenerator *ctx)](#oh_cryptosymkeygenerator_destroy) | Destroys a symmetric key generator instance.|
| [const char *OH_CryptoSymKey_GetAlgoName(OH_CryptoSymKey *keyCtx)](#oh_cryptosymkey_getalgoname) | Obtains the algorithm of a symmetric key.|
| [OH_Crypto_ErrCode OH_CryptoSymKey_GetKeyData(OH_CryptoSymKey *keyCtx, Crypto_DataBlob *out)](#oh_cryptosymkey_getkeydata) | Obtains the data of a symmetric key.<br> Note: After the use is complete, the memory for storing the **out** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob).|
| [void OH_CryptoSymKey_Destroy(OH_CryptoSymKey *keyCtx)](#oh_cryptosymkey_destroy) | Destroys a symmetric key instance.|

## Function Description

### OH_CryptoSymKeyGenerator_Create()

```c
OH_Crypto_ErrCode OH_CryptoSymKeyGenerator_Create(const char *algoName, OH_CryptoSymKeyGenerator **ctx)
```

**Description**

Creates a symmetric key generator instance based on the given algorithm name. For example, **AES256**.

Note: The created resource must be destroyed by calling [OH_CryptoSymKeyGenerator_Destroy](capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_destroy).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const char *algoName | Input parameter, indicating the name of the symmetric key algorithm, which cannot be null. The options are as follows:<br>- Since API version 12, **AES128**, **AES192**, **AES256**, **3DES192**, **HMAC\|SHA1**, **HMAC\|SHA224**, **HMAC\|SHA256**, **HMAC\|SHA384**, **HMAC\|SHA512**, **HMAC\|SM3** and **HMAC\|MD5** are supported. Since API version 26.0.0, **HMAC\|SHA3-256**, **HMAC\|SHA3-384**, and **HMAC\|SHA3-512** are supported.<br>- Since API version 12, **SM4_128** is supported.<br>- Since API version 20, **DES64** is supported.<br>- Since API version 22, **ChaCha20** is supported.<br>- Since API version 26.0.0, **RC2**, **RC4**, **Blowfish**, and **CAST** are supported. Note that only symmetric key data can be converted into a symmetric key. Random generation is not supported.|
| [OH_CryptoSymKeyGenerator](capi-cryptosymkeyapi-oh-cryptosymkeygenerator.md) **ctx | Output parameter, indicating a pointer to the symmetric key generator instance. The value of **ctx** cannot be null, but the value of ***ctx** must be null.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_INVALID_PARAMS**: The value of **ctx** or **algoName** is null.<br>**CRYPTO_NOT_SUPPORTED**: The algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation fails.<br>**CRYPTO_OPERTION_ERROR**: The cryptographic operation fails.|

**Reference**

[OH_CryptoSymKeyGenerator_Generate](capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_generate) for randomly generating a symmetric key.

[OH_CryptoSymKeyGenerator_Convert](capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_convert) for converting binary data into a symmetric key.


### OH_CryptoSymKeyGenerator_Generate()

```c
OH_Crypto_ErrCode OH_CryptoSymKeyGenerator_Generate(OH_CryptoSymKeyGenerator *ctx, OH_CryptoSymKey **keyCtx)
```

**Description**

Randomly generates a symmetric key.

Note: After the use is complete, the memory for storing the **keyCtx** parameter must be destroyed by calling [OH_CryptoSymKey_Destroy](capi-crypto-sym-key-h.md#oh_cryptosymkey_destroy).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoSymKeyGenerator](capi-cryptosymkeyapi-oh-cryptosymkeygenerator.md) *ctx | Input parameter, indicating a pointer to the symmetric key generator instance. The value cannot be null.|
| [OH_CryptoSymKey](capi-cryptosymkeyapi-oh-cryptosymkey.md) **keyCtx | Output parameter, indicating a pointer to the symmetric key. The value of **keyCtx** cannot be null, but the value of ***keyCtx** must be null.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_INVALID_PARAMS**: The value of **ctx** or **keyCtx** is null.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: The memory operation fails.<br>**CRYPTO_INVALID_CALL**: The function call is invalid. Possible causes: The algorithm does not support generating keys randomly (such as **RC2**, **RC4**, **Blowfish**, and **CAST**). Use the **OH_CryptoSymKeyGenerator_Convert** API. Applicable versions: 26.0.0+<br>**CRYPTO_OPERTION_ERROR**: The cryptographic operation fails.|

### OH_CryptoSymKeyGenerator_Convert()

```c
OH_Crypto_ErrCode OH_CryptoSymKeyGenerator_Convert(OH_CryptoSymKeyGenerator *ctx, const Crypto_DataBlob *keyData, OH_CryptoSymKey **keyCtx)
```

**Description**

Converts binary data into a symmetric key.

Note: After the use is complete, the memory for storing the **keyCtx** parameter must be destroyed by calling [OH_CryptoSymKey_Destroy](capi-crypto-sym-key-h.md#oh_cryptosymkey_destroy).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoSymKeyGenerator](capi-cryptosymkeyapi-oh-cryptosymkeygenerator.md) *ctx | Input parameter, indicating a pointer to the symmetric key generator instance. The value cannot be null.|
| [const Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *keyData | Input parameter, indicating the data used to generate a symmetric key. The value cannot be null.|
| [OH_CryptoSymKey](capi-cryptosymkeyapi-oh-cryptosymkey.md) **keyCtx | Output parameter, indicating a pointer to the symmetric key. The value of **keyCtx** cannot be null, but the value of ***keyCtx** must be null.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_INVALID_PARAMS**: **ctx**, **keyData**, or **keyCtx** is null.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation fails.<br>**CRYPTO_OPERTION_ERROR**: The cryptographic operation fails.|

### OH_CryptoSymKeyGenerator_GetAlgoName()

```c
const char *OH_CryptoSymKeyGenerator_GetAlgoName(OH_CryptoSymKeyGenerator *ctx)
```

**Description**

Obtains the algorithm of a symmetric key generator instance.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoSymKeyGenerator](capi-cryptosymkeyapi-oh-cryptosymkeygenerator.md) *ctx | Input parameter, indicating a pointer to the symmetric key generator instance. The value cannot be null.|

**Returns**

| Type| Description|
| -- | -- |
| const char * | Name of the symmetric key algorithm, which does not need to be released by the caller. This value cannot be used after the generator instance is destroyed.|

### OH_CryptoSymKeyGenerator_Destroy()

```c
void OH_CryptoSymKeyGenerator_Destroy(OH_CryptoSymKeyGenerator *ctx)
```

**Description**

Destroys a symmetric key generator instance.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoSymKeyGenerator](capi-cryptosymkeyapi-oh-cryptosymkeygenerator.md) *ctx | Input parameter, indicating a pointer to the symmetric key generator instance.|

### OH_CryptoSymKey_GetAlgoName()

```c
const char *OH_CryptoSymKey_GetAlgoName(OH_CryptoSymKey *keyCtx)
```

**Description**

Obtains the algorithm of a symmetric key.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoSymKey](capi-cryptosymkeyapi-oh-cryptosymkey.md) *keyCtx | Input parameter, indicating a symmetric key. The value cannot be null.|

**Returns**

| Type| Description|
| -- | -- |
| const char * | Algorithm name, which does not need to be released by the caller and cannot be used after the key is destroyed.|

### OH_CryptoSymKey_GetKeyData()

```c
OH_Crypto_ErrCode OH_CryptoSymKey_GetKeyData(OH_CryptoSymKey *keyCtx, Crypto_DataBlob *out)
```

**Description**

Obtains the data of a symmetric key.

Note: After the use is complete, the memory for storing the **out** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoSymKey](capi-cryptosymkeyapi-oh-cryptosymkey.md) *keyCtx | Input parameter, indicating a symmetric key. The value cannot be null.|
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *out | Output parameter, indicating a pointer to the **Crypto_DataBlob** struct used to store key data. The value cannot be null. Before calling this method, initialize **out** to 0. Do not set the **data** field of **out**.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>CRYPTO_INVALID_PARAMS: **keyCtx** or **out** is null.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: The memory operation fails.<br>**CRYPTO_OPERTION_ERROR**: The cryptographic operation fails.|

### OH_CryptoSymKey_Destroy()

```c
void OH_CryptoSymKey_Destroy(OH_CryptoSymKey *keyCtx)
```

**Description**

Destroys a symmetric key instance.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoSymKey](capi-cryptosymkeyapi-oh-cryptosymkey.md) *keyCtx | Input parameter, indicating a symmetric key.|
