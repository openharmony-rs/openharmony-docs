# crypto_signature.h

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

## Overview

Defines APIs for signature verification.

**Header file**: <CryptoArchitectureKit/crypto_signature.h>

**Library**: libohcrypto.so

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 12

**Related module**: [CryptoSignatureApi](capi-cryptosignatureapi.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_CryptoVerify](capi-cryptosignatureapi-oh-cryptoverify.md) | OH_CryptoVerify | Defines a struct for signature verification, which indicates the signature verification context.|
| [OH_CryptoSign](capi-cryptosignatureapi-oh-cryptosign.md) | OH_CryptoSign | Defines a struct for signing, which indicates the signing context.|
| [OH_CryptoEccSignatureSpec](capi-cryptosignatureapi-oh-cryptoeccsignaturespec.md) | OH_CryptoEccSignatureSpec | Defines a struct for ECC signing specifications.|

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [CryptoSignature_ParamType](#cryptosignature_paramtype) | CryptoSignature_ParamType | Enumerates the types of signing parameters.|

### Functions

| Name| Description|
| -- | -- |
| [OH_Crypto_ErrCode OH_CryptoVerify_Create(const char *algoName, OH_CryptoVerify **verify)](#oh_cryptoverify_create) | Creates a signature verification context based on the given algorithm name.<br> Note: The created resource must be destroyed by calling [OH_CryptoVerify_Destroy](capi-crypto-signature-h.md#oh_cryptoverify_destroy). |
| [OH_Crypto_ErrCode OH_CryptoVerify_Init(OH_CryptoVerify *ctx, OH_CryptoPubKey *pubKey)](#oh_cryptoverify_init) | Initializes the signature verification context using the given public key.|
| [OH_Crypto_ErrCode OH_CryptoVerify_Update(OH_CryptoVerify *ctx, Crypto_DataBlob *in)](#oh_cryptoverify_update) | Updates the message data to be verified.|
| [bool OH_CryptoVerify_Final(OH_CryptoVerify *ctx, Crypto_DataBlob *in, Crypto_DataBlob *signData)](#oh_cryptoverify_final) | Defines the signature verification message data.|
| [OH_Crypto_ErrCode OH_CryptoVerify_Recover(OH_CryptoVerify *ctx, Crypto_DataBlob *signData, Crypto_DataBlob *rawSignData)](#oh_cryptoverify_recover) | Restores the signing data. Only the RSA algorithm is supported.<br> Note: After the use is complete, the memory for storing the **rawSignData** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob).|
| [const char *OH_CryptoVerify_GetAlgoName(OH_CryptoVerify *ctx)](#oh_cryptoverify_getalgoname) | Obtains the name of the algorithm used for generating the signature verification context.|
| [OH_Crypto_ErrCode OH_CryptoVerify_SetParam(OH_CryptoVerify *ctx, CryptoSignature_ParamType type, Crypto_DataBlob *value)](#oh_cryptoverify_setparam) | Sets parameters of a signature verification context.|
| [OH_Crypto_ErrCode OH_CryptoVerify_GetParam(OH_CryptoVerify *ctx, CryptoSignature_ParamType type, Crypto_DataBlob *value)](#oh_cryptoverify_getparam) | Obtains parameters of a signature verification context.<br> Note: After the use is complete, the memory for storing the **value** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob). |
| [void OH_CryptoVerify_Destroy(OH_CryptoVerify *ctx)](#oh_cryptoverify_destroy) | Destroys the signature verification context.|
| [OH_Crypto_ErrCode OH_CryptoSign_Create(const char *algoName, OH_CryptoSign **sign)](#oh_cryptosign_create) | Creates a signing context based on the given algorithm name.<br> Note: The created resource must be destroyed by calling [OH_CryptoSign_Destroy](capi-crypto-signature-h.md#oh_cryptosign_destroy). |
| [OH_Crypto_ErrCode OH_CryptoSign_Init(OH_CryptoSign *ctx, OH_CryptoPrivKey *privKey)](#oh_cryptosign_init) | Initializes the signing context.|
| [OH_Crypto_ErrCode OH_CryptoSign_Update(OH_CryptoSign *ctx, const Crypto_DataBlob *in)](#oh_cryptosign_update) | Updates the data to be signed.|
| [OH_Crypto_ErrCode OH_CryptoSign_Final(OH_CryptoSign *ctx, const Crypto_DataBlob *in, Crypto_DataBlob *out)](#oh_cryptosign_final) | Finalizes the signing operation.<br> Note: After the use is complete, the memory for storing the **out** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob).|
| [const char *OH_CryptoSign_GetAlgoName(OH_CryptoSign *ctx)](#oh_cryptosign_getalgoname) | Obtains the name of the algorithm used for generating the signing context.|
| [OH_Crypto_ErrCode OH_CryptoSign_SetParam(OH_CryptoSign *ctx, CryptoSignature_ParamType type, const Crypto_DataBlob *value)](#oh_cryptosign_setparam) | Sets parameters of a signing context.|
| [OH_Crypto_ErrCode OH_CryptoSign_GetParam(OH_CryptoSign *ctx, CryptoSignature_ParamType type, Crypto_DataBlob *value)](#oh_cryptosign_getparam) | Obtains parameters of a signing context.<br> Note: After the use is complete, the memory for storing the **value** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob). |
| [void OH_CryptoSign_Destroy(OH_CryptoSign *ctx)](#oh_cryptosign_destroy) | Destroys the signing context.|
| [OH_Crypto_ErrCode OH_CryptoEccSignatureSpec_Create(Crypto_DataBlob *eccSignature, OH_CryptoEccSignatureSpec **spec)](#oh_cryptoeccsignaturespec_create) | Creates ECC signing specifications. The specifications also support SM2 signing.<br> Note: The created resource must be destroyed by calling [OH_CryptoEccSignatureSpec_Destroy](capi-crypto-signature-h.md#oh_cryptoeccsignaturespec_destroy). |
| [OH_Crypto_ErrCode OH_CryptoEccSignatureSpec_GetRAndS(OH_CryptoEccSignatureSpec *spec, Crypto_DataBlob *r, Crypto_DataBlob *s)](#oh_cryptoeccsignaturespec_getrands) | Obtains the **r** and **s** values in ECC signing specifications.<br> Note: After the use is complete, the memory for storing the **r** and **s** parameters must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob).|
| [OH_Crypto_ErrCode OH_CryptoEccSignatureSpec_SetRAndS(OH_CryptoEccSignatureSpec *spec, Crypto_DataBlob *r, Crypto_DataBlob *s)](#oh_cryptoeccsignaturespec_setrands) | Sets the **r** and **s** values in ECC signing specifications.|
| [OH_Crypto_ErrCode OH_CryptoEccSignatureSpec_Encode(OH_CryptoEccSignatureSpec *spec, Crypto_DataBlob *out)](#oh_cryptoeccsignaturespec_encode) | Encodes ECC signing specifications into signing data in DER format.<br> Note: After the use is complete, the memory for storing the **out** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob).|
| [void OH_CryptoEccSignatureSpec_Destroy(OH_CryptoEccSignatureSpec *spec)](#oh_cryptoeccsignaturespec_destroy) | Destroys ECC signing specifications.|

## Enum Description

### CryptoSignature_ParamType

```c
enum CryptoSignature_ParamType
```

**Description**

Enumerates the types of signing parameters.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| CRYPTO_PSS_MD_NAME_STR = 100 | Name of the algorithm used by the message digest function.|
| CRYPTO_PSS_MGF_NAME_STR = 101 | Name of the algorithm used by the mask generation function.|
| CRYPTO_PSS_MGF1_NAME_STR = 102 | Message digest parameter of the MGF1 mask generation function.|
| CRYPTO_PSS_SALT_LEN_INT = 103 | Salt length, in bytes.|
| CRYPTO_PSS_TRAILER_FIELD_INT = 104 | Value of the tail field.|
| CRYPTO_SM2_USER_ID_DATABLOB = 105 | User ID of the SM2 algorithm.|


## Function Description

### OH_CryptoVerify_Create()

```c
OH_Crypto_ErrCode OH_CryptoVerify_Create(const char *algoName, OH_CryptoVerify **verify)
```

**Description**

Creates a signature verification context based on the given algorithm name.

Note: The created resource must be destroyed by calling [OH_CryptoVerify_Destroy](capi-crypto-signature-h.md#oh_cryptoverify_destroy).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const char *algoName | Input parameter, indicating the signature verification algorithm name, which cannot be null. The options are as follows:<br>- RSA PKCS1 mode: The value is in the format of **RSA\|PKCS1\|Digest**, for example, **RSA\|PKCS1\|SHA256** or **RSA\|PKCS1\|SHA512**. The MD can be set to **MD5**, **SHA1**, **SHA224**, **SHA256**, **SHA384**, or **SHA512**.<br>- RSA PSS mode: The value is in the format of **RSA\|PSS\|Digest\|MGF1 Digest**, for example, **RSA\|PSS\|SHA256\|MGF1_SHA256**. The MD can be set to **MD5**, **SHA1**, **SHA224**, **SHA256**, **SHA384**, or **SHA512**. The MGF1 MD can be set to **MGF1_MD5**, **MGF1_SHA1**, **MGF1_SHA224**, **MGF1_SHA256**, **MGF1_SHA384**, or **MGF1_SHA512**.<br>- RSA signature verification recovery: The value is in the format of **RSA\|PKCS1\|Digest\|Recover**, for example, **RSA\|PKCS1\|SHA256\|Recover** or **RSA\|PKCS1\|SHA512\|Recover**. The MD can be set to **NoHash**, **MD5**, **SHA1**, **SHA224**, **SHA256**, **SHA384**, or **SHA512**.<br>- ECDSA algorithm: The value is in the format of **ECC\|Digest**, for example, **ECC\|SHA256** or **ECC\|SHA384**. The MD can be set to **SHA1**, **SHA224**, **SHA256**, **SHA384**, or **SHA512**.<br>- DSA algorithm: The value is in the format of **DSA\|Digest**, for example, **DSA\|SHA256** or **DSA\|SHA384**. The MD can be set to **NoHash**, **SHA1**, **SHA224**, **SHA256**, **SHA384**, or **SHA512**.<br>- SM2 algorithm: The value is **SM2\|SM3**.<br>- Ed25519 algorithm: The value is **Ed25519**.|
| [OH_CryptoVerify](capi-cryptosignatureapi-oh-cryptoverify.md) **verify | Output parameter, indicating a pointer to the signature verification context. The value of **verify** cannot be null, but the value of ***verify** must be null.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_INVALID_PARAMS**: **verify** or **algoName** is null.<br>**CRYPTO_NOT_SUPPORTED**: The algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation fails.<br>**CRYPTO_OPERTION_ERROR**: The cryptographic operation fails.|

**Reference**

[OH_CryptoVerify_Init](capi-crypto-signature-h.md#oh_cryptoverify_init) for initializing the signature verification context using the given public key.


### OH_CryptoVerify_Init()

```c
OH_Crypto_ErrCode OH_CryptoVerify_Init(OH_CryptoVerify *ctx, OH_CryptoPubKey *pubKey)
```

**Description**

Initializes the signature verification context using the given public key.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoVerify](capi-cryptosignatureapi-oh-cryptoverify.md) *ctx | Input parameter, indicating the signature verification context. The value cannot be null.|
| [OH_CryptoPubKey](capi-cryptoasymkeyapi-oh-cryptopubkey.md) *pubKey | Input parameter, indicating a public key. The value cannot be null.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_INVALID_PARAMS**: **ctx** or **pubKey** is null, or the key type does not match the signing algorithm.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: The memory operation fails.<br>**CRYPTO_OPERTION_ERROR**: The signature verification initialization fails.|

**Reference**

[OH_CryptoVerify_Update](capi-crypto-signature-h.md#oh_cryptoverify_update) for updating the message data to be verified.

[OH_CryptoVerify_Final](capi-crypto-signature-h.md#oh_cryptoverify_final) for defining signature verification message data.

[OH_CryptoVerify_Recover](capi-crypto-signature-h.md#oh_cryptoverify_recover) for restoring the signing data.


### OH_CryptoVerify_Update()

```c
OH_Crypto_ErrCode OH_CryptoVerify_Update(OH_CryptoVerify *ctx, Crypto_DataBlob *in)
```

**Description**

Updates the message data to be verified.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoVerify](capi-cryptosignatureapi-oh-cryptoverify.md) *ctx | Input parameter, indicating the signature verification context. The value cannot be null.|
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *in | Input parameter, indicating a pointer to the data with the signature to be verified. The value cannot be null.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_INVALID_PARAMS**: The value of **ctx** or **in** is null.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: The memory operation fails.<br>**CRYPTO_INVALID_CALL**: The function call is invalid. Applicable versions: 26.0.0+<br>**CRYPTO_OPERTION_ERROR**: The signature verification update fails.|

**Reference**

[OH_CryptoVerify_Final](capi-crypto-signature-h.md#oh_cryptoverify_final) for defining signature verification message data.


### OH_CryptoVerify_Final()

```c
bool OH_CryptoVerify_Final(OH_CryptoVerify *ctx, Crypto_DataBlob *in, Crypto_DataBlob *signData)
```

**Description**

Defines the signature verification message data.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoVerify](capi-cryptosignatureapi-oh-cryptoverify.md) *ctx | Input parameter, indicating the signature verification context. The value cannot be null.|
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *in | Input parameter, indicating a pointer to the data with the signature to be verified. If all data has been updated by calling [OH_CryptoVerify_Update](capi-crypto-signature-h.md#oh_cryptoverify_update), this parameter can be null.|
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *signData | Input parameter, indicating a pointer to the data to sign. The value cannot be null.|

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns a boolean value, indicating the signature verification result. The value **true** indicates that the signature verification is successful, and **false** indicates the opposite. Possible causes: The public key is incorrect, the signature data is damaged, the digest algorithm does not match,<br>     The padding mode does not match, or the data does not match the original signing data.|

### OH_CryptoVerify_Recover()

```c
OH_Crypto_ErrCode OH_CryptoVerify_Recover(OH_CryptoVerify *ctx, Crypto_DataBlob *signData, Crypto_DataBlob *rawSignData)
```

**Description**

Restores the signing data. Only the RSA algorithm is supported.

Note: After the use is complete, the memory for storing the **rawSignData** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoVerify](capi-cryptosignatureapi-oh-cryptoverify.md) *ctx | Input parameter, indicating the signature verification context. The value cannot be null.|
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *signData | Input parameter, indicating a pointer to the data to sign. The value cannot be null.|
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *rawSignData | Output parameter, indicating a pointer to the **Crypto_DataBlob** struct used to store the raw signature data. The value cannot be null. Before calling this method, initialize **rawSignData** to 0. Do not set the **data** field of **rawSignData**.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_INVALID_PARAMS**: **ctx**, **signData**, or **rawSignData** is null.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: The memory operation fails.<br>**CRYPTO_INVALID_CALL**: The function call is invalid. Applicable versions: 26.0.0+<br>**CRYPTO_OPERTION_ERROR**: The restoration fails. Possible cause: The length of the signature data does not match the modulus size of the RSA key.|

### OH_CryptoVerify_GetAlgoName()

```c
const char *OH_CryptoVerify_GetAlgoName(OH_CryptoVerify *ctx)
```

**Description**

Obtains the name of the algorithm used for generating the signature verification context.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoVerify](capi-cryptosignatureapi-oh-cryptoverify.md) *ctx | Input parameter, indicating the signature verification context. The value cannot be null.|

**Returns**

| Type| Description|
| -- | -- |
| const char * | Name of the signature verification algorithm, which does not need to be released by the caller. This value cannot be used after the context is destroyed.|

### OH_CryptoVerify_SetParam()

```c
OH_Crypto_ErrCode OH_CryptoVerify_SetParam(OH_CryptoVerify *ctx, CryptoSignature_ParamType type, Crypto_DataBlob *value)
```

**Description**

Sets parameters of a signature verification context.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoVerify](capi-cryptosignatureapi-oh-cryptoverify.md) *ctx | Input parameter, indicating the signature verification context. The value cannot be null.|
| [CryptoSignature_ParamType](capi-crypto-signature-h.md#cryptosignature_paramtype) type | Input parameter, indicating a pointer to the signature parameter type.|
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *value | Input parameter, indicating the input data. This API performs deep copy of the data in **value**. The caller can immediately release **value** after the API returns a result. The value cannot be null.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_INVALID_PARAMS**: **ctx** or **value** is null, or **data** in **value** is null.<br>            The value of **len** in **value** does not match the expected value of **type**, or **type** is not a valid **CryptoSignature_ParamType**.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: The memory operation fails.<br>**CRYPTO_OPERTION_ERROR**: The parameter fails to be set.|

### OH_CryptoVerify_GetParam()

```c
OH_Crypto_ErrCode OH_CryptoVerify_GetParam(OH_CryptoVerify *ctx, CryptoSignature_ParamType type, Crypto_DataBlob *value)
```

**Description**

Obtains parameters of a signature verification context.

Note: After the use is complete, the memory for storing the **value** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoVerify](capi-cryptosignatureapi-oh-cryptoverify.md) *ctx | Input parameter, indicating the signature verification context. The value cannot be null.|
| [CryptoSignature_ParamType](capi-crypto-signature-h.md#cryptosignature_paramtype) type | Input parameter, indicating a pointer to the signature parameter type.|
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *value | Output parameter, indicating a pointer to the **Crypto_DataBlob** struct used to store the output data. The value cannot be null. Before calling this method, initialize **value** to 0. Do not set the **data** field of **value**.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_INVALID_PARAMS**: The value of **ctx** or **value** is null, or **type** is not a valid **CryptoSignature_ParamType**.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation for the output data fails.<br>**CRYPTO_OPERTION_ERROR**: The parameter fails to be obtained.|

### OH_CryptoVerify_Destroy()

```c
void OH_CryptoVerify_Destroy(OH_CryptoVerify *ctx)
```

**Description**

Destroys the signature verification context.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoVerify](capi-cryptosignatureapi-oh-cryptoverify.md) *ctx | Input parameter, indicating the signature verification context.|

### OH_CryptoSign_Create()

```c
OH_Crypto_ErrCode OH_CryptoSign_Create(const char *algoName, OH_CryptoSign **sign)
```

**Description**

Creates a signing context based on the given algorithm name.

Note: The created resource must be destroyed by calling [OH_CryptoSign_Destroy](capi-crypto-signature-h.md#oh_cryptosign_destroy).

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| const char *algoName | Input parameter, indicating the signing algorithm name, which cannot be null. The options are as follows:<br>- RSA PKCS1 mode: The value is in the format of **RSA\|PKCS1\|Digest**, for example, **RSA\|PKCS1\|SHA256** or **RSA\|PKCS1\|SHA512**. The MD can be set to **MD5**, **SHA1**, **SHA224**, **SHA256**, **SHA384**, or **SHA512**.<br>- RSA PSS mode: The value is in the format of **RSA\|PSS\|Digest\|MGF1 Digest**, for example, **RSA\|PSS\|SHA256\|MGF1_SHA256**. The MD can be set to **MD5**, **SHA1**, **SHA224**, **SHA256**, **SHA384**, or **SHA512**. The MGF1 MD can be set to **MGF1_MD5**, **MGF1_SHA1**, **MGF1_SHA224**, **MGF1_SHA256**, **MGF1_SHA384**, or **MGF1_SHA512**.<br>- RSA signing only: The value is in the format of **RSA\|PKCS1\|Digest\|OnlySign**, for example, **RSA\|PKCS1\|SHA256\|OnlySign** or **RSA\|PKCS1\|SHA512\|OnlySign**. The MD can be set to **NoHash**, **MD5**, **SHA1**, **SHA224**, **SHA256**, **SHA384**, or **SHA512**.<br>- ECDSA algorithm: The value is in the format of **ECC\|Digest**, for example, **ECC\|SHA256** or **ECC\|SHA384**. The MD can be set to **SHA1**, **SHA224**, **SHA256**, **SHA384**, or **SHA512**.<br>- DSA algorithm: The value is in the format of **DSA\|Digest**, for example, **DSA\|SHA256** or **DSA\|SHA384**. The MD can be set to **NoHash**, **SHA1**, **SHA224**, **SHA256**, **SHA384**, or **SHA512**.<br>- SM2 algorithm: The value is **SM2\|SM3**.<br>- Ed25519 algorithm: The value is **Ed25519**.|
| [OH_CryptoSign](capi-cryptosignatureapi-oh-cryptosign.md) **sign | Output parameter, indicating a pointer to the signing context. The value of **sign** cannot be null, but the value of ***sign** must be null.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: **sign** or **algoName** is null.<br>**CRYPTO_NOT_SUPPORTED**: The algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation fails.<br>**CRYPTO_OPERTION_ERROR**: The cryptographic operation fails.|

**Reference**

[OH_CryptoSign_Init](capi-crypto-signature-h.md#oh_cryptosign_init) for initializing the signing context.


### OH_CryptoSign_Init()

```c
OH_Crypto_ErrCode OH_CryptoSign_Init(OH_CryptoSign *ctx, OH_CryptoPrivKey *privKey)
```

**Description**

Initializes the signing context.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoSign](capi-cryptosignatureapi-oh-cryptosign.md) *ctx | Input parameter, indicating the signing context. The value cannot be null.|
| [OH_CryptoPrivKey](capi-cryptoasymkeyapi-oh-cryptoprivkey.md) *privKey | Input parameter, indicating a private key. The value cannot be null.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: The value of **ctx** or **privKey** is null.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: The memory operation fails.<br>**CRYPTO_OPERTION_ERROR**: The signature initialization fails.|

**Reference**

[OH_CryptoSign_Update](capi-crypto-signature-h.md#oh_cryptosign_update) for updating the data to be signed.

[OH_CryptoSign_Final](capi-crypto-signature-h.md#oh_cryptosign_final) for finalizing the signing operation.


### OH_CryptoSign_Update()

```c
OH_Crypto_ErrCode OH_CryptoSign_Update(OH_CryptoSign *ctx, const Crypto_DataBlob *in)
```

**Description**

Updates the data to be signed.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoSign](capi-cryptosignatureapi-oh-cryptosign.md) *ctx | Input parameter, indicating the signing context. The value cannot be null.|
| [const Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *in | Input parameter, indicating the data to be signed. The value cannot be null.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: The value of **ctx** or **in** is null.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: The memory operation fails.<br>**CRYPTO_INVALID_CALL**: The function call is invalid. Applicable versions: 26.0.0+<br>**CRYPTO_OPERTION_ERROR**: The signature update fails.|

**Reference**

[OH_CryptoSign_Final](capi-crypto-signature-h.md#oh_cryptosign_final) for finalizing the signing operation.


### OH_CryptoSign_Final()

```c
OH_Crypto_ErrCode OH_CryptoSign_Final(OH_CryptoSign *ctx, const Crypto_DataBlob *in, Crypto_DataBlob *out)
```

**Description**

Finalizes the signing operation.

Note: After the use is complete, the memory for storing the **out** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob).

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoSign](capi-cryptosignatureapi-oh-cryptosign.md) *ctx | Input parameter, indicating the signing context. The value cannot be null.|
| [const Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *in | Input parameter, indicating the data to be signed. If all data has been updated by calling [OH_CryptoSign_Update](capi-crypto-signature-h.md#oh_cryptosign_update), this parameter can be null.|
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *out | Output parameter, indicating a pointer to the **Crypto_DataBlob** struct used to store the signature result. The value cannot be null. Before calling this method, initialize **out** to 0. Do not set the **data** field of **out**.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: The value of **ctx** or **out** is null.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: The memory operation fails.<br>**CRYPTO_OPERTION_ERROR**: Signing fails.|

### OH_CryptoSign_GetAlgoName()

```c
const char *OH_CryptoSign_GetAlgoName(OH_CryptoSign *ctx)
```

**Description**

Obtains the name of the algorithm used for generating the signing context.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoSign](capi-cryptosignatureapi-oh-cryptosign.md) *ctx | Input parameter, indicating the signing context. The value cannot be null.|

**Returns**

| Type| Description|
| -- | -- |
| const char * | Name of the signing algorithm, which does not need to be released by the caller. This value cannot be used after the context is destroyed.|

### OH_CryptoSign_SetParam()

```c
OH_Crypto_ErrCode OH_CryptoSign_SetParam(OH_CryptoSign *ctx, CryptoSignature_ParamType type, const Crypto_DataBlob *value)
```

**Description**

Sets parameters of a signing context.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoSign](capi-cryptosignatureapi-oh-cryptosign.md) *ctx | Input parameter, indicating the signing context. The value cannot be null.|
| [CryptoSignature_ParamType](capi-crypto-signature-h.md#cryptosignature_paramtype) type | Input parameter, indicating a pointer to the signature parameter type.|
| [const Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *value | Input parameter, indicating the input data. This API performs deep copy of the data in **value**. The caller can immediately release **value** after the API returns a result. The value cannot be null.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: **ctx** or **value** is null.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: The memory operation fails.<br>**CRYPTO_OPERTION_ERROR**: The cryptographic operation fails.|

### OH_CryptoSign_GetParam()

```c
OH_Crypto_ErrCode OH_CryptoSign_GetParam(OH_CryptoSign *ctx, CryptoSignature_ParamType type, Crypto_DataBlob *value)
```

**Description**

Obtains parameters of a signing context.

Note: After the use is complete, the memory for storing the **value** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob).

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoSign](capi-cryptosignatureapi-oh-cryptosign.md) *ctx | Input parameter, indicating the signing context. The value cannot be null.|
| [CryptoSignature_ParamType](capi-crypto-signature-h.md#cryptosignature_paramtype) type | Input parameter, indicating a pointer to the signature parameter type.|
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *value | Output parameter, indicating a pointer to the **Crypto_DataBlob** struct used to store the output data. The value cannot be null. Before calling this method, initialize **value** to 0. Do not set the **data** field of **value**.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: **ctx** or **value** is null.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: The memory operation fails.<br>**CRYPTO_OPERTION_ERROR**: The cryptographic operation fails.|

### OH_CryptoSign_Destroy()

```c
void OH_CryptoSign_Destroy(OH_CryptoSign *ctx)
```

**Description**

Destroys the signing context.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoSign](capi-cryptosignatureapi-oh-cryptosign.md) *ctx | Input parameter, indicating the signing context.|

### OH_CryptoEccSignatureSpec_Create()

```c
OH_Crypto_ErrCode OH_CryptoEccSignatureSpec_Create(Crypto_DataBlob *eccSignature, OH_CryptoEccSignatureSpec **spec)
```

**Description**

Creates ECC signing specifications. The specifications also support SM2 signing.

Note: The created resource must be destroyed by calling [OH_CryptoEccSignatureSpec_Destroy](capi-crypto-signature-h.md#oh_cryptoeccsignaturespec_destroy).

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *eccSignature | Input parameter, indicating the ECC signing data in DER format. If the value is null, an empty signing specification is created.|
| [OH_CryptoEccSignatureSpec](capi-cryptosignatureapi-oh-cryptoeccsignaturespec.md) **spec | Output parameter, indicating a pointer to the ECC signing specification. The value of **spec** cannot be null, but the value of ***spec** must be null.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: **spec** is null or ***spec** is not null.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: The memory operation fails.<br>**CRYPTO_OPERTION_ERROR**: **eccSignature** fails to be parsed, or **eccSignature** contains an invalid **ECDSA-Sig-Value** encoded in DER format.|

**Reference**

[OH_CryptoEccSignatureSpec_GetRAndS](capi-crypto-signature-h.md#oh_cryptoeccsignaturespec_getrands) for obtaining the **r** and **s** values in ECC signing specifications.

[OH_CryptoEccSignatureSpec_SetRAndS](capi-crypto-signature-h.md#oh_cryptoeccsignaturespec_setrands) for setting the **r** and **s** values in ECC signing specifications.


### OH_CryptoEccSignatureSpec_GetRAndS()

```c
OH_Crypto_ErrCode OH_CryptoEccSignatureSpec_GetRAndS(OH_CryptoEccSignatureSpec *spec, Crypto_DataBlob *r, Crypto_DataBlob *s)
```

**Description**

Obtains the **r** and **s** values in ECC signing specifications.

Note: After the use is complete, the memory for storing the **r** and **s** parameters must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob).

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoEccSignatureSpec](capi-cryptosignatureapi-oh-cryptoeccsignaturespec.md) *spec | Input parameter, indicating a pointer to the ECC signing specifications. The value cannot be null.|
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *r | Output parameter, indicating a pointer to the **Crypto_DataBlob** struct used to store the **r** value. The value cannot be null. Before calling this method, initialize **r** to 0. Do not set the **data** field of **r**.|
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *s | Output parameter, indicating a pointer to the **Crypto_DataBlob** struct used to store the **s** value. The value cannot be null. Before calling this method, initialize **s** to 0. Do not set the **data** field of **s**.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: **spec**, **r**, or **s** is null.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: The memory operation fails.<br>**CRYPTO_OPERTION_ERROR**: The cryptographic operation fails.|

### OH_CryptoEccSignatureSpec_SetRAndS()

```c
OH_Crypto_ErrCode OH_CryptoEccSignatureSpec_SetRAndS(OH_CryptoEccSignatureSpec *spec, Crypto_DataBlob *r, Crypto_DataBlob *s)
```

**Description**

Sets the **r** and **s** values in ECC signing specifications.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoEccSignatureSpec](capi-cryptosignatureapi-oh-cryptoeccsignaturespec.md) *spec | Input parameter, indicating a pointer to the ECC signing specifications. The value cannot be null.|
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *r | Input parameter, indicating a pointer to the **r** value. This API performs deep copy of the data in **r** and **s**. The caller can immediately release **r** and **s** after the API returns a result. The value cannot be null.|
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *s | Input parameter, indicating a pointer to the **s** value. The value cannot be null.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: **spec**, **r**, or **s** is null.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: The memory operation fails.<br>**CRYPTO_OPERTION_ERROR**: The cryptographic operation fails.|

**Reference**

[OH_CryptoEccSignatureSpec_Encode](capi-crypto-signature-h.md#oh_cryptoeccsignaturespec_encode) for encoding ECC signing specifications into signing data in DER format.


### OH_CryptoEccSignatureSpec_Encode()

```c
OH_Crypto_ErrCode OH_CryptoEccSignatureSpec_Encode(OH_CryptoEccSignatureSpec *spec, Crypto_DataBlob *out)
```

**Description**

Encodes ECC signing specifications into signing data in DER format.

Note: After the use is complete, the memory for storing the **out** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob).

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoEccSignatureSpec](capi-cryptosignatureapi-oh-cryptoeccsignaturespec.md) *spec | Input parameter, indicating a pointer to the ECC signing specifications. The value cannot be null.|
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *out | Output parameter, indicating a pointer to the **Crypto_DataBlob** struct used to store the encoded signature data. The value cannot be null. Before calling this method, initialize **out** to 0. Do not set the **data** field of **out**.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: **spec** or **out** is null, or the **r** and **s** values have not been set using [OH_CryptoEccSignatureSpec_SetRAndS](capi-crypto-signature-h.md#oh_cryptoeccsignaturespec_setrands).<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation fails.<br>**CRYPTO_OPERTION_ERROR**: Encoding fails.|

### OH_CryptoEccSignatureSpec_Destroy()

```c
void OH_CryptoEccSignatureSpec_Destroy(OH_CryptoEccSignatureSpec *spec)
```

**Description**

Destroys ECC signing specifications.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoEccSignatureSpec](capi-cryptosignatureapi-oh-cryptoeccsignaturespec.md) *spec | Input parameter, indicating a pointer to the ECC signing specifications.|
