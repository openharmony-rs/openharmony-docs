# crypto_signature.h

## Overview

Defines the signing and verification interfaces.

**Include**: <CryptoArchitectureKit/crypto_signature.h>

**Library**: libohcrypto.so

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 12

**Related module**: [CryptoSignatureApi](capi-cryptosignatureapi.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_CryptoVerify](capi-cryptosignatureapi-oh-cryptoverify.md) | OH_CryptoVerify | Verification structure, representing a verification context. |
| [OH_CryptoSign](capi-cryptosignatureapi-oh-cryptosign.md) | OH_CryptoSign | Signing structure, representing a signing context. |
| [OH_CryptoEccSignatureSpec](capi-cryptosignatureapi-oh-cryptoeccsignaturespec.md) | OH_CryptoEccSignatureSpec | ECC signature specification structure, representing an ECC signature specification. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [CryptoSignature_ParamType](#cryptosignature_paramtype) | CryptoSignature_ParamType | Defines signature parameter types. |

### Function

| Name | Description |
| -- | -- |
| [OH_Crypto_ErrCode OH_CryptoVerify_Create(const char *algoName, OH_CryptoVerify **verify)](#oh_cryptoverify_create) | Creates a verification context based on the given algorithm name. |
| [OH_Crypto_ErrCode OH_CryptoVerify_Init(OH_CryptoVerify *ctx, OH_CryptoPubKey *pubKey)](#oh_cryptoverify_init) | Initializes the verification context with the given public key. |
| [OH_Crypto_ErrCode OH_CryptoVerify_Update(OH_CryptoVerify *ctx, Crypto_DataBlob *in)](#oh_cryptoverify_update) | Appends message data to be verified. |
| [bool OH_CryptoVerify_Final(OH_CryptoVerify *ctx, Crypto_DataBlob *in, Crypto_DataBlob *signData)](#oh_cryptoverify_final) | Verifies message data. |
| [OH_Crypto_ErrCode OH_CryptoVerify_Recover(OH_CryptoVerify *ctx, Crypto_DataBlob *signData, Crypto_DataBlob *rawSignData)](#oh_cryptoverify_recover) | Recovers signature data. Only RSA algorithm is supported. |
| [const char *OH_CryptoVerify_GetAlgoName(OH_CryptoVerify *ctx)](#oh_cryptoverify_getalgoname) | Obtains the algorithm name of the verification context. |
| [OH_Crypto_ErrCode OH_CryptoVerify_SetParam(OH_CryptoVerify *ctx, CryptoSignature_ParamType type, Crypto_DataBlob *value)](#oh_cryptoverify_setparam) | Sets the specified parameter of the verification context. |
| [OH_Crypto_ErrCode OH_CryptoVerify_GetParam(OH_CryptoVerify *ctx, CryptoSignature_ParamType type, Crypto_DataBlob *value)](#oh_cryptoverify_getparam) | Obtains the specified parameter of the verification context. |
| [void OH_CryptoVerify_Destroy(OH_CryptoVerify *ctx)](#oh_cryptoverify_destroy) | Destroys the verification context. |
| [OH_Crypto_ErrCode OH_CryptoSign_Create(const char *algoName, OH_CryptoSign **sign)](#oh_cryptosign_create) | Creates a signing context based on the given algorithm name. |
| [OH_Crypto_ErrCode OH_CryptoSign_Init(OH_CryptoSign *ctx, OH_CryptoPrivKey *privKey)](#oh_cryptosign_init) | Initializes the signing context. |
| [OH_Crypto_ErrCode OH_CryptoSign_Update(OH_CryptoSign *ctx, const Crypto_DataBlob *in)](#oh_cryptosign_update) | Updates data to be signed. |
| [OH_Crypto_ErrCode OH_CryptoSign_Final(OH_CryptoSign *ctx, const Crypto_DataBlob *in, Crypto_DataBlob *out)](#oh_cryptosign_final) | Finishes the signing operation. |
| [const char *OH_CryptoSign_GetAlgoName(OH_CryptoSign *ctx)](#oh_cryptosign_getalgoname) | Obtains the algorithm name of the signing context. |
| [OH_Crypto_ErrCode OH_CryptoSign_SetParam(OH_CryptoSign *ctx, CryptoSignature_ParamType type, const Crypto_DataBlob *value)](#oh_cryptosign_setparam) | Sets the specified parameter for the signing context. |
| [OH_Crypto_ErrCode OH_CryptoSign_GetParam(OH_CryptoSign *ctx, CryptoSignature_ParamType type, Crypto_DataBlob *value)](#oh_cryptosign_getparam) | Obtains the specified parameter from the signing context. |
| [void OH_CryptoSign_Destroy(OH_CryptoSign *ctx)](#oh_cryptosign_destroy) | Destroys the signing context. |
| [OH_Crypto_ErrCode OH_CryptoEccSignatureSpec_Create(Crypto_DataBlob *eccSignature, OH_CryptoEccSignatureSpec **spec)](#oh_cryptoeccsignaturespec_create) | Creates an ECC signature specification. Also supports SM2 signatures. |
| [OH_Crypto_ErrCode OH_CryptoEccSignatureSpec_GetRAndS(OH_CryptoEccSignatureSpec *spec, Crypto_DataBlob *r, Crypto_DataBlob *s)](#oh_cryptoeccsignaturespec_getrands) | Gets the r and s values from the ECC signature specification. |
| [OH_Crypto_ErrCode OH_CryptoEccSignatureSpec_SetRAndS(OH_CryptoEccSignatureSpec *spec, Crypto_DataBlob *r, Crypto_DataBlob *s)](#oh_cryptoeccsignaturespec_setrands) | Sets the r and s values for the ECC signature specification. |
| [OH_Crypto_ErrCode OH_CryptoEccSignatureSpec_Encode(OH_CryptoEccSignatureSpec *spec, Crypto_DataBlob *out)](#oh_cryptoeccsignaturespec_encode) | Encodes the ECC signature specification into DER format signature data. |
| [void OH_CryptoEccSignatureSpec_Destroy(OH_CryptoEccSignatureSpec *spec)](#oh_cryptoeccsignaturespec_destroy) | Destroys the ECC signature specification. |

## Enum type description

### CryptoSignature_ParamType

```c
enum CryptoSignature_ParamType
```

**Description**

Defines signature parameter types.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 12

| Enum item | Description |
| -- | -- |
| CRYPTO_PSS_MD_NAME_STR = 100 | Algorithm name of the message digest function.<br>**Since**: 12 |
| CRYPTO_PSS_MGF_NAME_STR = 101 | Algorithm name of the mask generation function.<br>**Since**: 12 |
| CRYPTO_PSS_MGF1_NAME_STR = 102 | Message digest parameter of the MGF1 mask generation function.<br>**Since**: 12 |
| CRYPTO_PSS_SALT_LEN_INT = 103 | Byte length of the salt value.<br>**Since**: 12 |
| CRYPTO_PSS_TRAILER_FIELD_INT = 104 | Value of the trailer field.<br>**Since**: 12 |
| CRYPTO_SM2_USER_ID_DATABLOB = 105 | User ID value for the SM2 algorithm.<br>**Since**: 12 |


## Function description

### OH_CryptoVerify_Create()

```c
OH_Crypto_ErrCode OH_CryptoVerify_Create(const char *algoName, OH_CryptoVerify **verify)
```

**Description**

Creates a verification context based on the given algorithm name.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *algoName | [in] Verification algorithm name. Cannot be NULL. Values: - RSA PKCS1 mode: Format "RSA\|PKCS1\|Digest", e.g. "RSA\|PKCS1\|SHA256", "RSA\|PKCS1\|SHA512". Digest supports "MD5", "SHA1", "SHA224", "SHA256", "SHA384", "SHA512". - RSA PSS mode: Format "RSA\|PSS\|Digest\|MGF1Digest", e.g. "RSA\|PSS\|SHA256\|MGF1_SHA256". Digest supports "MD5", "SHA1", "SHA224", "SHA256", "SHA384", "SHA512". MGF1 digest supports "MGF1_MD5", "MGF1_SHA1", "MGF1_SHA224", "MGF1_SHA256", "MGF1_SHA384", "MGF1_SHA512". - RSA verify recovery: Format "RSA\|PKCS1\|Digest\|Recover", e.g. "RSA\|PKCS1\|SHA256\|Recover", "RSA\|PKCS1\|SHA512\|Recover". Digest supports "NoHash", "MD5", "SHA1", "SHA224", "SHA256", "SHA384", "SHA512". - ECDSA algorithm: Format "ECC\|Digest", e.g. "ECC\|SHA256", "ECC\|SHA384". Digest supports "SHA1", "SHA224", "SHA256", "SHA384", "SHA512". - DSA algorithm: Format "DSA\|Digest", e.g. "DSA\|SHA256", "DSA\|SHA384". Digest supports "NoHash", "SHA1", "SHA224", "SHA256", "SHA384", "SHA512". - SM2 algorithm: "SM2\|SM3". - Ed25519 algorithm: "Ed25519". |
| [OH_CryptoVerify](capi-cryptosignatureapi-oh-cryptoverify.md) **verify | [out] Pointer to the verification context pointer. verify cannot be NULL, *verify must be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>[CRYPTO_SUCCESS](capi-crypto-common-h.md#oh_crypto_errcode) if the operation succeeds.</li>          <li>[CRYPTO_INVALID_PARAMS](capi-crypto-common-h.md#oh_crypto_errcode) if verify or algoName is NULL.</li>          <li>[CRYPTO_NOT_SUPPORTED](capi-crypto-common-h.md#oh_crypto_errcode) if the algorithm is not supported.</li>          <li>[CRYPTO_MEMORY_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if memory allocation fails.</li>          <li>[CRYPTO_OPERTION_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if crypto operation fails.</li>          </ul> |

**Reference**:

[OH_CryptoVerify_Init](capi-crypto-signature-h.md#oh_cryptoverify_init) Initializes the verification context with the given public key


### OH_CryptoVerify_Init()

```c
OH_Crypto_ErrCode OH_CryptoVerify_Init(OH_CryptoVerify *ctx, OH_CryptoPubKey *pubKey)
```

**Description**

Initializes the verification context with the given public key.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoVerify](capi-cryptosignatureapi-oh-cryptoverify.md) *ctx | [in] Verification context. Cannot be NULL. |
| OH_CryptoPubKey *pubKey | [in] Public key. Cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>[CRYPTO_SUCCESS](capi-crypto-common-h.md#oh_crypto_errcode) if the operation succeeds.</li>          <li>[CRYPTO_INVALID_PARAMS](capi-crypto-common-h.md#oh_crypto_errcode) if ctx or pubKey is NULL, or the key             type does not match the signature algorithm.</li>          <li>[CRYPTO_NOT_SUPPORTED](capi-crypto-common-h.md#oh_crypto_errcode) if unsupported operation or algorithm.</li>          <li>[CRYPTO_MEMORY_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if memory operation fails.</li>          <li>[CRYPTO_OPERTION_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if verify init fails.</li>          </ul> |

**Reference**:

[OH_CryptoVerify_Update](capi-crypto-signature-h.md#oh_cryptoverify_update) Appends message data to be verified
[OH_CryptoVerify_Final](capi-crypto-signature-h.md#oh_cryptoverify_final) Verifies message data
[OH_CryptoVerify_Recover](capi-crypto-signature-h.md#oh_cryptoverify_recover) Recovers signature data


### OH_CryptoVerify_Update()

```c
OH_Crypto_ErrCode OH_CryptoVerify_Update(OH_CryptoVerify *ctx, Crypto_DataBlob *in)
```

**Description**

Appends message data to be verified.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoVerify](capi-cryptosignatureapi-oh-cryptoverify.md) *ctx | [in] Verification context. Cannot be NULL. |
| Crypto_DataBlob *in | [in] Data to be verified. Cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>[CRYPTO_SUCCESS](capi-crypto-common-h.md#oh_crypto_errcode) if the operation succeeds.</li>          <li>[CRYPTO_INVALID_PARAMS](capi-crypto-common-h.md#oh_crypto_errcode) if ctx or in is NULL.</li>          <li>[CRYPTO_NOT_SUPPORTED](capi-crypto-common-h.md#oh_crypto_errcode) if unsupported operation or algorithm.</li>          <li>[CRYPTO_MEMORY_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if memory operation fails.</li>          <li>[CRYPTO_INVALID_CALL](capi-crypto-common-h.md#oh_crypto_errcode) if the function call is invalid. [since 26.0.0]</li>          <li>[CRYPTO_OPERTION_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if verify update fails.</li>          </ul> |

**Reference**:

[OH_CryptoVerify_Final](capi-crypto-signature-h.md#oh_cryptoverify_final) Verifies message data


### OH_CryptoVerify_Final()

```c
bool OH_CryptoVerify_Final(OH_CryptoVerify *ctx, Crypto_DataBlob *in, Crypto_DataBlob *signData)
```

**Description**

Verifies message data.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoVerify](capi-cryptosignatureapi-oh-cryptoverify.md) *ctx | [in] Verification context. Cannot be NULL. |
| Crypto_DataBlob *in | [in] Data to be verified. Can be NULL if all data has been updated via [OH_CryptoVerify_Update](capi-crypto-signature-h.md#oh_cryptoverify_update). |
| Crypto_DataBlob *signData | [in] Signature data. Cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns the boolean verification result. Returns true if verification succeeds, false if verification fails.      Possible causes: incorrect public key, corrupted signature data, mismatched hash algorithm,      mismatched padding mode, or the data does not match the original signed data. |

### OH_CryptoVerify_Recover()

```c
OH_Crypto_ErrCode OH_CryptoVerify_Recover(OH_CryptoVerify *ctx, Crypto_DataBlob *signData, Crypto_DataBlob *rawSignData)
```

**Description**

Recovers signature data. Only RSA algorithm is supported.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoVerify](capi-cryptosignatureapi-oh-cryptoverify.md) *ctx | [in] Verification context. Cannot be NULL. |
| Crypto_DataBlob *signData | [in] Signature data. Cannot be NULL. |
| Crypto_DataBlob *rawSignData | [out] Pointer to the Crypto_DataBlob structure for storing the raw signature data. Cannot be NULL. Initialize rawSignData to {0} before calling. Do not pre-allocate rawSignData->data. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>[CRYPTO_SUCCESS](capi-crypto-common-h.md#oh_crypto_errcode) if the operation succeeds.</li>          <li>[CRYPTO_INVALID_PARAMS](capi-crypto-common-h.md#oh_crypto_errcode) if ctx, signData, or rawSignData is NULL.</li>          <li>[CRYPTO_NOT_SUPPORTED](capi-crypto-common-h.md#oh_crypto_errcode) if unsupported operation or algorithm.</li>          <li>[CRYPTO_MEMORY_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if memory operation fails.</li>          <li>[CRYPTO_INVALID_CALL](capi-crypto-common-h.md#oh_crypto_errcode) if the function call is invalid. [since 26.0.0]</li>          <li>[CRYPTO_OPERTION_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if recover fails. Possible causes:             signature data length does not match the RSA key modulus size.</li>          </ul> |

### OH_CryptoVerify_GetAlgoName()

```c
const char *OH_CryptoVerify_GetAlgoName(OH_CryptoVerify *ctx)
```

**Description**

Obtains the algorithm name of the verification context.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoVerify](capi-cryptosignatureapi-oh-cryptoverify.md) *ctx | [in] Verification context. Cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| const char * | Returns the verification algorithm name. No need to free by the caller. Invalid after the context is      destroyed. |

### OH_CryptoVerify_SetParam()

```c
OH_Crypto_ErrCode OH_CryptoVerify_SetParam(OH_CryptoVerify *ctx, CryptoSignature_ParamType type, Crypto_DataBlob *value)
```

**Description**

Sets the specified parameter of the verification context.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoVerify](capi-cryptosignatureapi-oh-cryptoverify.md) *ctx | [in] Verification context. Cannot be NULL. |
| [CryptoSignature_ParamType](capi-crypto-signature-h.md#cryptosignature_paramtype) type | [in] Signature parameter type. |
| Crypto_DataBlob *value | [in] Input data. This function performs a deep copy of the data in value. The caller can release value immediately after the function returns. Cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>[CRYPTO_SUCCESS](capi-crypto-common-h.md#oh_crypto_errcode) if the operation succeeds.</li>          <li>[CRYPTO_INVALID_PARAMS](capi-crypto-common-h.md#oh_crypto_errcode) if ctx or value is NULL,             value->data is NULL, value->len does not match the expected size for the             type, or type is not a valid CryptoSignature_ParamType.</li>          <li>[CRYPTO_NOT_SUPPORTED](capi-crypto-common-h.md#oh_crypto_errcode) if unsupported operation or algorithm.</li>          <li>[CRYPTO_MEMORY_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if memory operation fails.</li>          <li>[CRYPTO_OPERTION_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if setting parameter fails.</li>          </ul> |

### OH_CryptoVerify_GetParam()

```c
OH_Crypto_ErrCode OH_CryptoVerify_GetParam(OH_CryptoVerify *ctx, CryptoSignature_ParamType type, Crypto_DataBlob *value)
```

**Description**

Obtains the specified parameter of the verification context.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoVerify](capi-cryptosignatureapi-oh-cryptoverify.md) *ctx | [in] Verification context. Cannot be NULL. |
| [CryptoSignature_ParamType](capi-crypto-signature-h.md#cryptosignature_paramtype) type | [in] Signature parameter type. |
| Crypto_DataBlob *value | [out] Pointer to the Crypto_DataBlob structure for storing the output data. Cannot be NULL. Initialize value to {0} before calling. Do not pre-allocate value->data. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>[CRYPTO_SUCCESS](capi-crypto-common-h.md#oh_crypto_errcode) if the operation succeeds.</li>          <li>[CRYPTO_INVALID_PARAMS](capi-crypto-common-h.md#oh_crypto_errcode) if ctx or value is NULL, or type is             not a valid CryptoSignature_ParamType.</li>          <li>[CRYPTO_NOT_SUPPORTED](capi-crypto-common-h.md#oh_crypto_errcode) if unsupported operation or algorithm.</li>          <li>[CRYPTO_MEMORY_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if memory allocation for the output fails.</li>          <li>[CRYPTO_OPERTION_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if getting parameter fails.</li>          </ul> |

### OH_CryptoVerify_Destroy()

```c
void OH_CryptoVerify_Destroy(OH_CryptoVerify *ctx)
```

**Description**

Destroys the verification context.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoVerify](capi-cryptosignatureapi-oh-cryptoverify.md) *ctx | [in] Verification context. |

### OH_CryptoSign_Create()

```c
OH_Crypto_ErrCode OH_CryptoSign_Create(const char *algoName, OH_CryptoSign **sign)
```

**Description**

Creates a signing context based on the given algorithm name.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *algoName | [in] Signing algorithm name. Cannot be NULL. Values: - RSA PKCS1 mode: Format "RSA\|PKCS1\|Digest", e.g. "RSA\|PKCS1\|SHA256", "RSA\|PKCS1\|SHA512". Digest supports "MD5", "SHA1", "SHA224", "SHA256", "SHA384", "SHA512". - RSA PSS mode: Format "RSA\|PSS\|Digest\|MGF1Digest", e.g. "RSA\|PSS\|SHA256\|MGF1_SHA256". Digest supports "MD5", "SHA1", "SHA224", "SHA256", "SHA384", "SHA512". MGF1 digest supports "MGF1_MD5", "MGF1_SHA1", "MGF1_SHA224", "MGF1_SHA256", "MGF1_SHA384", "MGF1_SHA512". - RSA sign only: Format "RSA\|PKCS1\|Digest\|OnlySign", e.g. "RSA\|PKCS1\|SHA256\|OnlySign", "RSA\|PKCS1\|SHA512\|OnlySign". Digest supports "NoHash", "MD5", "SHA1", "SHA224", "SHA256", "SHA384", "SHA512". - ECDSA algorithm: Format "ECC\|Digest", e.g. "ECC\|SHA256", "ECC\|SHA384". Digest supports "SHA1", "SHA224", "SHA256", "SHA384", "SHA512". - DSA algorithm: Format "DSA\|Digest", e.g. "DSA\|SHA256", "DSA\|SHA384". Digest supports "NoHash", "SHA1", "SHA224", "SHA256", "SHA384", "SHA512". - SM2 algorithm: "SM2\|SM3". - Ed25519 algorithm: "Ed25519". |
| [OH_CryptoSign](capi-cryptosignatureapi-oh-cryptosign.md) **sign | [out] Pointer to the signing context pointer. sign cannot be NULL, *sign must be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>[CRYPTO_SUCCESS](capi-crypto-common-h.md#oh_crypto_errcode) if the operation succeeds.</li>          <li>[CRYPTO_PARAMETER_CHECK_FAILED](capi-crypto-common-h.md#oh_crypto_errcode) if sign or algoName is NULL.</li>          <li>[CRYPTO_NOT_SUPPORTED](capi-crypto-common-h.md#oh_crypto_errcode) if the algorithm is not supported.</li>          <li>[CRYPTO_MEMORY_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if memory allocation fails.</li>          <li>[CRYPTO_OPERTION_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if crypto operation fails.</li>          </ul> |

**Reference**:

[OH_CryptoSign_Init](capi-crypto-signature-h.md#oh_cryptosign_init) Initializes the signing context


### OH_CryptoSign_Init()

```c
OH_Crypto_ErrCode OH_CryptoSign_Init(OH_CryptoSign *ctx, OH_CryptoPrivKey *privKey)
```

**Description**

Initializes the signing context.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoSign](capi-cryptosignatureapi-oh-cryptosign.md) *ctx | [in] Signing context. Cannot be NULL. |
| OH_CryptoPrivKey *privKey | [in] Private key. Cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>[CRYPTO_SUCCESS](capi-crypto-common-h.md#oh_crypto_errcode) if the operation succeeds.</li>          <li>[CRYPTO_PARAMETER_CHECK_FAILED](capi-crypto-common-h.md#oh_crypto_errcode) if ctx or privKey is NULL.</li>          <li>[CRYPTO_NOT_SUPPORTED](capi-crypto-common-h.md#oh_crypto_errcode) if unsupported operation or algorithm.</li>          <li>[CRYPTO_MEMORY_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if memory operation fails.</li>          <li>[CRYPTO_OPERTION_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if sign init fails.</li>          </ul> |

**Reference**:

[OH_CryptoSign_Update](capi-crypto-signature-h.md#oh_cryptosign_update) Updates data to be signed
[OH_CryptoSign_Final](capi-crypto-signature-h.md#oh_cryptosign_final) Finishes the signing operation


### OH_CryptoSign_Update()

```c
OH_Crypto_ErrCode OH_CryptoSign_Update(OH_CryptoSign *ctx, const Crypto_DataBlob *in)
```

**Description**

Updates data to be signed.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoSign](capi-cryptosignatureapi-oh-cryptosign.md) *ctx | [in] Signing context. Cannot be NULL. |
| const Crypto_DataBlob *in | [in] Data to be signed. Cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>[CRYPTO_SUCCESS](capi-crypto-common-h.md#oh_crypto_errcode) if the operation succeeds.</li>          <li>[CRYPTO_PARAMETER_CHECK_FAILED](capi-crypto-common-h.md#oh_crypto_errcode) if ctx or in is NULL.</li>          <li>[CRYPTO_NOT_SUPPORTED](capi-crypto-common-h.md#oh_crypto_errcode) if unsupported operation or algorithm.</li>          <li>[CRYPTO_MEMORY_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if memory operation fails.</li>          <li>[CRYPTO_INVALID_CALL](capi-crypto-common-h.md#oh_crypto_errcode) if the function call is invalid. [since 26.0.0]</li>          <li>[CRYPTO_OPERTION_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if sign update fails.</li>          </ul> |

**Reference**:

[OH_CryptoSign_Final](capi-crypto-signature-h.md#oh_cryptosign_final) Finishes the signing operation


### OH_CryptoSign_Final()

```c
OH_Crypto_ErrCode OH_CryptoSign_Final(OH_CryptoSign *ctx, const Crypto_DataBlob *in, Crypto_DataBlob *out)
```

**Description**

Finishes the signing operation.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoSign](capi-cryptosignatureapi-oh-cryptosign.md) *ctx | [in] Signing context. Cannot be NULL. |
| const Crypto_DataBlob *in | [in] Data to be signed. Can be NULL if all data has been updated via [OH_CryptoSign_Update](capi-crypto-signature-h.md#oh_cryptosign_update). |
| Crypto_DataBlob *out | [out] Pointer to the Crypto_DataBlob structure for storing the signature result. Cannot be NULL. Initialize out to {0} before calling. Do not pre-allocate out->data. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>[CRYPTO_SUCCESS](capi-crypto-common-h.md#oh_crypto_errcode) if the operation succeeds.</li>          <li>[CRYPTO_PARAMETER_CHECK_FAILED](capi-crypto-common-h.md#oh_crypto_errcode) if ctx or out is NULL.</li>          <li>[CRYPTO_NOT_SUPPORTED](capi-crypto-common-h.md#oh_crypto_errcode) if unsupported operation or algorithm.</li>          <li>[CRYPTO_MEMORY_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if memory operation fails.</li>          <li>[CRYPTO_OPERTION_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if signing fails.</li>          </ul> |

### OH_CryptoSign_GetAlgoName()

```c
const char *OH_CryptoSign_GetAlgoName(OH_CryptoSign *ctx)
```

**Description**

Obtains the algorithm name of the signing context.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoSign](capi-cryptosignatureapi-oh-cryptosign.md) *ctx | [in] Signing context. Cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| const char * | Returns the signing algorithm name. No need to free by the caller. Invalid after the context is destroyed. |

### OH_CryptoSign_SetParam()

```c
OH_Crypto_ErrCode OH_CryptoSign_SetParam(OH_CryptoSign *ctx, CryptoSignature_ParamType type, const Crypto_DataBlob *value)
```

**Description**

Sets the specified parameter for the signing context.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoSign](capi-cryptosignatureapi-oh-cryptosign.md) *ctx | [in] Signing context. Cannot be NULL. |
| [CryptoSignature_ParamType](capi-crypto-signature-h.md#cryptosignature_paramtype) type | [in] Signing parameter type. |
| const Crypto_DataBlob *value | [in] Input data. This function performs a deep copy of the data in value. The caller can release value immediately after the function returns. Cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>[CRYPTO_SUCCESS](capi-crypto-common-h.md#oh_crypto_errcode) if the operation succeeds.</li>          <li>[CRYPTO_PARAMETER_CHECK_FAILED](capi-crypto-common-h.md#oh_crypto_errcode) if ctx or value is NULL.</li>          <li>[CRYPTO_NOT_SUPPORTED](capi-crypto-common-h.md#oh_crypto_errcode) if unsupported operation or algorithm.</li>          <li>[CRYPTO_MEMORY_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if memory operation fails.</li>          <li>[CRYPTO_OPERTION_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if crypto operation fails.</li>          </ul> |

### OH_CryptoSign_GetParam()

```c
OH_Crypto_ErrCode OH_CryptoSign_GetParam(OH_CryptoSign *ctx, CryptoSignature_ParamType type, Crypto_DataBlob *value)
```

**Description**

Obtains the specified parameter from the signing context.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoSign](capi-cryptosignatureapi-oh-cryptosign.md) *ctx | [in] Signing context. Cannot be NULL. |
| [CryptoSignature_ParamType](capi-crypto-signature-h.md#cryptosignature_paramtype) type | [in] Signing parameter type. |
| Crypto_DataBlob *value | [out] Pointer to the Crypto_DataBlob structure for storing the output data. Cannot be NULL. Initialize value to {0} before calling. Do not pre-allocate value->data. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>[CRYPTO_SUCCESS](capi-crypto-common-h.md#oh_crypto_errcode) if the operation succeeds.</li>          <li>[CRYPTO_PARAMETER_CHECK_FAILED](capi-crypto-common-h.md#oh_crypto_errcode) if ctx or value is NULL.</li>          <li>[CRYPTO_NOT_SUPPORTED](capi-crypto-common-h.md#oh_crypto_errcode) if unsupported operation or algorithm.</li>          <li>[CRYPTO_MEMORY_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if memory operation fails.</li>          <li>[CRYPTO_OPERTION_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if crypto operation fails.</li>          </ul> |

### OH_CryptoSign_Destroy()

```c
void OH_CryptoSign_Destroy(OH_CryptoSign *ctx)
```

**Description**

Destroys the signing context.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoSign](capi-cryptosignatureapi-oh-cryptosign.md) *ctx | [in] Signing context. |

### OH_CryptoEccSignatureSpec_Create()

```c
OH_Crypto_ErrCode OH_CryptoEccSignatureSpec_Create(Crypto_DataBlob *eccSignature, OH_CryptoEccSignatureSpec **spec)
```

**Description**

Creates an ECC signature specification. Also supports SM2 signatures.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| Crypto_DataBlob *eccSignature | [in] ECC signature data in DER format. If NULL, an empty signature specification is created. |
| [OH_CryptoEccSignatureSpec](capi-cryptosignatureapi-oh-cryptoeccsignaturespec.md) **spec | [out] Pointer to the ECC signature specification pointer. spec cannot be NULL, *spec must be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>[CRYPTO_SUCCESS](capi-crypto-common-h.md#oh_crypto_errcode) if the operation succeeds.</li>          <li>[CRYPTO_PARAMETER_CHECK_FAILED](capi-crypto-common-h.md#oh_crypto_errcode) if spec is NULL or spec is not NULL.</li>          <li>[CRYPTO_NOT_SUPPORTED](capi-crypto-common-h.md#oh_crypto_errcode) if unsupported operation or algorithm.</li>          <li>[CRYPTO_MEMORY_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if memory operation fails.</li>          <li>[CRYPTO_OPERTION_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if parsing eccSignature fails or             eccSignature contains an invalid DER-encoded ECDSA-Sig-Value.</li>          </ul> |

**Reference**:

[OH_CryptoEccSignatureSpec_GetRAndS](capi-crypto-signature-h.md#oh_cryptoeccsignaturespec_getrands) Gets the r and s values from the ECC signature specification
[OH_CryptoEccSignatureSpec_SetRAndS](capi-crypto-signature-h.md#oh_cryptoeccsignaturespec_setrands) Sets the r and s values for the ECC signature specification


### OH_CryptoEccSignatureSpec_GetRAndS()

```c
OH_Crypto_ErrCode OH_CryptoEccSignatureSpec_GetRAndS(OH_CryptoEccSignatureSpec *spec, Crypto_DataBlob *r, Crypto_DataBlob *s)
```

**Description**

Gets the r and s values from the ECC signature specification.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoEccSignatureSpec](capi-cryptosignatureapi-oh-cryptoeccsignaturespec.md) *spec | [in] ECC signature specification. Cannot be NULL. |
| Crypto_DataBlob *r | [out] Pointer to the Crypto_DataBlob structure for storing the r value. Cannot be NULL. Initialize r to {0} before calling. Do not pre-allocate r->data. |
| Crypto_DataBlob *s | [out] Pointer to the Crypto_DataBlob structure for storing the s value. Cannot be NULL. Initialize s to {0} before calling. Do not pre-allocate s->data. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>[CRYPTO_SUCCESS](capi-crypto-common-h.md#oh_crypto_errcode) if the operation succeeds.</li>          <li>[CRYPTO_PARAMETER_CHECK_FAILED](capi-crypto-common-h.md#oh_crypto_errcode) if spec, r, or s is NULL.</li>          <li>[CRYPTO_NOT_SUPPORTED](capi-crypto-common-h.md#oh_crypto_errcode) if unsupported operation or algorithm.</li>          <li>[CRYPTO_MEMORY_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if memory operation fails.</li>          <li>[CRYPTO_OPERTION_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if crypto operation fails.</li>          </ul> |

### OH_CryptoEccSignatureSpec_SetRAndS()

```c
OH_Crypto_ErrCode OH_CryptoEccSignatureSpec_SetRAndS(OH_CryptoEccSignatureSpec *spec, Crypto_DataBlob *r, Crypto_DataBlob *s)
```

**Description**

Sets the r and s values for the ECC signature specification.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoEccSignatureSpec](capi-cryptosignatureapi-oh-cryptoeccsignaturespec.md) *spec | [in] ECC signature specification. Cannot be NULL. |
| Crypto_DataBlob *r | [in] r value. This function performs a deep copy of the data in r and s. The caller can release r and s immediately after the function returns. Cannot be NULL. |
| Crypto_DataBlob *s | [in] s value. Cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>[CRYPTO_SUCCESS](capi-crypto-common-h.md#oh_crypto_errcode) if the operation succeeds.</li>          <li>[CRYPTO_PARAMETER_CHECK_FAILED](capi-crypto-common-h.md#oh_crypto_errcode) if spec, r, or s is NULL.</li>          <li>[CRYPTO_NOT_SUPPORTED](capi-crypto-common-h.md#oh_crypto_errcode) if unsupported operation or algorithm.</li>          <li>[CRYPTO_MEMORY_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if memory operation fails.</li>          <li>[CRYPTO_OPERTION_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if crypto operation fails.</li>          </ul> |

**Reference**:

[OH_CryptoEccSignatureSpec_Encode](capi-crypto-signature-h.md#oh_cryptoeccsignaturespec_encode) Encodes the ECC signature specification into DER format signature data


### OH_CryptoEccSignatureSpec_Encode()

```c
OH_Crypto_ErrCode OH_CryptoEccSignatureSpec_Encode(OH_CryptoEccSignatureSpec *spec, Crypto_DataBlob *out)
```

**Description**

Encodes the ECC signature specification into DER format signature data.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoEccSignatureSpec](capi-cryptosignatureapi-oh-cryptoeccsignaturespec.md) *spec | [in] ECC signature specification. Cannot be NULL. |
| Crypto_DataBlob *out | [out] Pointer to the Crypto_DataBlob structure for storing the encoded signature. Cannot be NULL. Initialize out to {0} before calling. Do not pre-allocate out->data. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>[CRYPTO_SUCCESS](capi-crypto-common-h.md#oh_crypto_errcode) if the operation succeeds.</li>          <li>[CRYPTO_PARAMETER_CHECK_FAILED](capi-crypto-common-h.md#oh_crypto_errcode) if spec or out is NULL, or             r and s values have not been set via [OH_CryptoEccSignatureSpec_SetRAndS](capi-crypto-signature-h.md#oh_cryptoeccsignaturespec_setrands).</li>          <li>[CRYPTO_NOT_SUPPORTED](capi-crypto-common-h.md#oh_crypto_errcode) if unsupported operation or algorithm.</li>          <li>[CRYPTO_MEMORY_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if memory allocation fails.</li>          <li>[CRYPTO_OPERTION_ERROR](capi-crypto-common-h.md#oh_crypto_errcode) if encoding fails.</li>          </ul> |

### OH_CryptoEccSignatureSpec_Destroy()

```c
void OH_CryptoEccSignatureSpec_Destroy(OH_CryptoEccSignatureSpec *spec)
```

**Description**

Destroys the ECC signature specification.

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoEccSignatureSpec](capi-cryptosignatureapi-oh-cryptoeccsignaturespec.md) *spec | [in] ECC signature specification. |


