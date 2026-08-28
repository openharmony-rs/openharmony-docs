# crypto_asym_key.h

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=76caeef80126e754bb89b8cf8b2b7380f3d3d3a7 translatedAt=2026-08-20T12:30:23.193Z pushedAt=2026-08-27T01:22:34.655Z -->

## Overview

Defines APIs for asymmetric key operations.

**Header file**: <CryptoArchitectureKit/crypto_asym_key.h>

**Library**: libohcrypto.so

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 12

**Related module**: [CryptoAsymKeyApi](capi-cryptoasymkeyapi.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_CryptoKeyPair](capi-cryptoasymkeyapi-oh-cryptokeypair.md) | OH_CryptoKeyPair | Defines a struct for an asymmetric key pair. |
| [OH_CryptoPubKey](capi-cryptoasymkeyapi-oh-cryptopubkey.md) | OH_CryptoPubKey | Defines a struct for a public key. |
| [OH_CryptoPrivKey](capi-cryptoasymkeyapi-oh-cryptoprivkey.md) | OH_CryptoPrivKey | Defines a struct for a private key. |
| [OH_CryptoAsymKeyGenerator](capi-cryptoasymkeyapi-oh-cryptoasymkeygenerator.md) | OH_CryptoAsymKeyGenerator | Defines a struct for an asymmetric key generator. |
| [OH_CryptoPrivKeyEncodingParams](capi-cryptoasymkeyapi-oh-cryptoprivkeyencodingparams.md) | OH_CryptoPrivKeyEncodingParams | Defines a struct for private key encoding parameters. |
| [OH_CryptoAsymKeySpec](capi-cryptoasymkeyapi-oh-cryptoasymkeyspec.md) | OH_CryptoAsymKeySpec | Defines a struct for asymmetric key specifications. |
| [OH_CryptoAsymKeyGeneratorWithSpec](capi-cryptoasymkeyapi-oh-cryptoasymkeygeneratorwithspec.md) | OH_CryptoAsymKeyGeneratorWithSpec | Defines a struct for an asymmetric key generator with specifications. |
| [OH_CryptoEcPoint](capi-cryptoasymkeyapi-oh-cryptoecpoint.md) | OH_CryptoEcPoint | Defines a struct for an EC point. |

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [CryptoAsymKey_ParamType](#cryptoasymkey_paramtype) | CryptoAsymKey_ParamType | Enumerates the types of the asymmetric key parameters.|
| [Crypto_EncodingType](#crypto_encodingtype) | Crypto_EncodingType | Enumerates the encoding types. |
| [CryptoPrivKeyEncoding_ParamType](#cryptoprivkeyencoding_paramtype) | CryptoPrivKeyEncoding_ParamType | Defines the parameter type for private key encoding.|
| [CryptoAsymKeySpec_Type](#cryptoasymkeyspec_type) | CryptoAsymKeySpec_Type | Defines the specification type of an asymmetric key.|

### Functions

| Name| Description|
| -- | -- |
| [OH_Crypto_ErrCode OH_CryptoAsymKeyGenerator_Create(const char *algoName, OH_CryptoAsymKeyGenerator **ctx)](#oh_cryptoasymkeygenerator_create) | Creates an asymmetric key generator based on the given algorithm name.<br> Note: The created resource must be destroyed by calling [OH_CryptoAsymKeyGenerator_Destroy](capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_destroy).  |
| [OH_Crypto_ErrCode OH_CryptoAsymKeyGenerator_Generate(OH_CryptoAsymKeyGenerator *ctx, OH_CryptoKeyPair **keyCtx)](#oh_cryptoasymkeygenerator_generate) | Generates an asymmetric key pair. Note: After the method is used, the memory for storing the **keyCtx** parameter must be destroyed by calling [OH_CryptoKeyPair_Destroy](capi-crypto-asym-key-h.md#oh_cryptokeypair_destroy). |
| [OH_Crypto_ErrCode OH_CryptoAsymKeyGenerator_Convert(OH_CryptoAsymKeyGenerator *ctx, Crypto_EncodingType type, Crypto_DataBlob *pubKeyData, Crypto_DataBlob *priKeyData, OH_CryptoKeyPair **keyCtx)](#oh_cryptoasymkeygenerator_convert) | Converts asymmetric key data into a key pair.<br>Note: After the method is used, the memory for storing the **keyCtx** parameter must be destroyed by calling [OH_CryptoKeyPair_Destroy](capi-crypto-asym-key-h.md#oh_cryptokeypair_destroy). |
| [const char *OH_CryptoAsymKeyGenerator_GetAlgoName(OH_CryptoAsymKeyGenerator *ctx)](#oh_cryptoasymkeygenerator_getalgoname) | Obtains the algorithm of an asymmetric key generator instance. |
| [void OH_CryptoAsymKeyGenerator_Destroy(OH_CryptoAsymKeyGenerator *ctx)](#oh_cryptoasymkeygenerator_destroy) | Destroys the asymmetric key generator. |
| [void OH_CryptoKeyPair_Destroy(OH_CryptoKeyPair *keyCtx)](#oh_cryptokeypair_destroy) | Destroys the key pair. |
| [OH_CryptoPubKey *OH_CryptoKeyPair_GetPubKey(OH_CryptoKeyPair *keyCtx)](#oh_cryptokeypair_getpubkey) | Obtains the public key in the key pair. |
| [OH_CryptoPrivKey *OH_CryptoKeyPair_GetPrivKey(OH_CryptoKeyPair *keyCtx)](#oh_cryptokeypair_getprivkey) | Obtains the private key in the key pair. |
| [OH_Crypto_ErrCode OH_CryptoPubKey_Encode(OH_CryptoPubKey *key, Crypto_EncodingType type, const char *encodingStandard, Crypto_DataBlob *out)](#oh_cryptopubkey_encode) | Encodes a public key.<br>Note: After the method is used, the memory for storing the **out** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob). |
| [OH_Crypto_ErrCode OH_CryptoPubKey_GetParam(OH_CryptoPubKey *key, CryptoAsymKey_ParamType item, Crypto_DataBlob *value)](#oh_cryptopubkey_getparam) | Obtains the specified parameter of the public key.<br>Note: After the method is used, the memory for storing the **value** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob). |
| [OH_Crypto_ErrCode OH_CryptoAsymKeyGenerator_SetPassword(OH_CryptoAsymKeyGenerator *ctx, const unsigned char *password, uint32_t passwordLen)](#oh_cryptoasymkeygenerator_setpassword) | Sets the password of the asymmetric key generator. If you need to use [OH_CryptoAsymKeyGenerator_Convert](capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_convert) to convert the encrypted private key data into a key pair, call this method to set the password. |
| [OH_Crypto_ErrCode OH_CryptoPrivKeyEncodingParams_Create(OH_CryptoPrivKeyEncodingParams **ctx)](#oh_cryptoprivkeyencodingparams_create) | Creates private key encoding parameters.<br> Note: The created resource must be destroyed by calling [OH_CryptoPrivKeyEncodingParams_Destroy](capi-crypto-asym-key-h.md#oh_cryptoprivkeyencodingparams_destroy).|
| [OH_Crypto_ErrCode OH_CryptoPrivKeyEncodingParams_SetParam(OH_CryptoPrivKeyEncodingParams *ctx, CryptoPrivKeyEncoding_ParamType type, Crypto_DataBlob *value)](#oh_cryptoprivkeyencodingparams_setparam) | Sets a private key encoding parameter.|
| [void OH_CryptoPrivKeyEncodingParams_Destroy(OH_CryptoPrivKeyEncodingParams *ctx)](#oh_cryptoprivkeyencodingparams_destroy) | Destroys a private key encoding parameter.|
| [OH_Crypto_ErrCode OH_CryptoPrivKey_Encode(OH_CryptoPrivKey *key, Crypto_EncodingType type, const char *encodingStandard, OH_CryptoPrivKeyEncodingParams *params, Crypto_DataBlob *out)](#oh_cryptoprivkey_encode) | Encodes a private key.<br> Note: After the method is used, the memory for storing the **out** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob).  |
| [OH_Crypto_ErrCode OH_CryptoPrivKey_GetParam(OH_CryptoPrivKey *key, CryptoAsymKey_ParamType item, Crypto_DataBlob *value)](#oh_cryptoprivkey_getparam) | Obtains the specified parameter of a private key.<br> Note: After the method is used, the memory for storing the **value** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob). |
| [OH_Crypto_ErrCode OH_CryptoAsymKeySpec_GenEcCommonParamsSpec(const char *curveName, OH_CryptoAsymKeySpec **spec)](#oh_cryptoasymkeyspec_geneccommonparamsspec) | Generates EC common parameter specifications.<br> Note: After the method is used, the memory for storing the **spec** parameter must be destroyed by calling [OH_CryptoAsymKeySpec_Destroy](capi-crypto-asym-key-h.md#oh_cryptoasymkeyspec_destroy).|
| [OH_Crypto_ErrCode OH_CryptoAsymKeySpec_GenDhCommonParamsSpec(int pLen, int skLen, OH_CryptoAsymKeySpec **spec)](#oh_cryptoasymkeyspec_gendhcommonparamsspec) | Generates DH common parameter specifications.<br> Note: After the method is used, the memory for storing the **spec** parameter must be destroyed by calling [OH_CryptoAsymKeySpec_Destroy](capi-crypto-asym-key-h.md#oh_cryptoasymkeyspec_destroy).|
| [OH_Crypto_ErrCode OH_CryptoAsymKeySpec_Create(const char *algoName, CryptoAsymKeySpec_Type type, OH_CryptoAsymKeySpec **spec)](#oh_cryptoasymkeyspec_create) | Creates asymmetric key specifications based on the given algorithm name and specification type.<br> Note: The created resource must be destroyed by calling [OH_CryptoAsymKeySpec_Destroy](capi-crypto-asym-key-h.md#oh_cryptoasymkeyspec_destroy).|
| [OH_Crypto_ErrCode OH_CryptoAsymKeySpec_SetParam(OH_CryptoAsymKeySpec *spec, CryptoAsymKey_ParamType type, Crypto_DataBlob *value)](#oh_cryptoasymkeyspec_setparam) | Sets the specified parameters for asymmetric key specifications.|
| [OH_Crypto_ErrCode OH_CryptoAsymKeySpec_SetCommonParamsSpec(OH_CryptoAsymKeySpec *spec, OH_CryptoAsymKeySpec *commonParamsSpec)](#oh_cryptoasymkeyspec_setcommonparamsspec) | Sets the common parameters specification into the asymmetric key specification. |
| [OH_Crypto_ErrCode OH_CryptoAsymKeySpec_GetParam(OH_CryptoAsymKeySpec *spec, CryptoAsymKey_ParamType type, Crypto_DataBlob *value)](#oh_cryptoasymkeyspec_getparam) | Obtains the specified parameters for asymmetric key specifications.<br> Note: After the method is used, the memory for storing the **value** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob).|
| [void OH_CryptoAsymKeySpec_Destroy(OH_CryptoAsymKeySpec *spec)](#oh_cryptoasymkeyspec_destroy) | Destroys asymmetric key specifications.|
| [OH_Crypto_ErrCode OH_CryptoAsymKeyGeneratorWithSpec_Create(OH_CryptoAsymKeySpec *keySpec, OH_CryptoAsymKeyGeneratorWithSpec **generator)](#oh_cryptoasymkeygeneratorwithspec_create) | Creates a key generator instance based on asymmetric key specifications.<br> Note: The created resource must be destroyed by calling [OH_CryptoAsymKeyGeneratorWithSpec_Destroy](capi-crypto-asym-key-h.md#oh_cryptoasymkeygeneratorwithspec_destroy).  |
| [OH_Crypto_ErrCode OH_CryptoAsymKeyGeneratorWithSpec_GenKeyPair(OH_CryptoAsymKeyGeneratorWithSpec *generator, OH_CryptoKeyPair **keyPair)](#oh_cryptoasymkeygeneratorwithspec_genkeypair) | Generates a key pair based on asymmetric key specifications.<br> Note: After the method is used, the memory for storing the **keyPair** parameter must be released by calling [OH_CryptoKeyPair_Destroy](capi-crypto-asym-key-h.md#oh_cryptokeypair_destroy).|
| [void OH_CryptoAsymKeyGeneratorWithSpec_Destroy(OH_CryptoAsymKeyGeneratorWithSpec *generator)](#oh_cryptoasymkeygeneratorwithspec_destroy) | Destroys the asymmetric key generator instance created based on specifications. |
| [OH_Crypto_ErrCode OH_CryptoEcPoint_Create(const char *curveName, Crypto_DataBlob *ecKeyData, OH_CryptoEcPoint **point)](#oh_cryptoecpoint_create) | Creates an elliptic curve point.<br> Note: The created resource must be destroyed by calling [OH_CryptoEcPoint_Destroy](capi-crypto-asym-key-h.md#oh_cryptoecpoint_destroy). |
| [OH_Crypto_ErrCode OH_CryptoEcPoint_GetCoordinate(OH_CryptoEcPoint *point, Crypto_DataBlob *x, Crypto_DataBlob *y)](#oh_cryptoecpoint_getcoordinate) | Obtains the X and Y coordinates of an elliptic curve point.<br> Note: After the method is used, the memory for storing the **x** and **y** parameters must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob). |
| [OH_Crypto_ErrCode OH_CryptoEcPoint_SetCoordinate(OH_CryptoEcPoint *point, Crypto_DataBlob *x, Crypto_DataBlob *y)](#oh_cryptoecpoint_setcoordinate) | Sets the X and Y coordinates of an elliptic curve point. |
| [OH_Crypto_ErrCode OH_CryptoEcPoint_Encode(OH_CryptoEcPoint *point, const char *format, Crypto_DataBlob *out)](#oh_cryptoecpoint_encode) | Encodes an elliptic curve point in a specified format.<br> Note: After the method is used, the memory for storing the **out** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob).  |
| [void OH_CryptoEcPoint_Destroy(OH_CryptoEcPoint *point)](#oh_cryptoecpoint_destroy) | Destroys an elliptic curve point. |

## Enum Description

### CryptoAsymKey_ParamType

```c
enum CryptoAsymKey_ParamType
```

**Description**

Enumerates the types of the asymmetric key parameters.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| CRYPTO_DSA_P_DATABLOB = 101 | Prime modulus **p** in the DSA algorithm. |
| CRYPTO_DSA_Q_DATABLOB = 102 | Sub-prime modulus **q** in the DSA algorithm. |
| CRYPTO_DSA_G_DATABLOB = 103 | Base **g** in the DSA algorithm. |
| CRYPTO_DSA_SK_DATABLOB = 104 | Private key in the DSA algorithm. |
| CRYPTO_DSA_PK_DATABLOB = 105 | Public key in the DSA algorithm. |
| CRYPTO_ECC_FP_P_DATABLOB = 201 | Prime modulus **p** in the prime field of an elliptic curve (EC). |
| CRYPTO_ECC_A_DATABLOB = 202 | First coefficient **a** of the elliptic curve. |
| CRYPTO_ECC_B_DATABLOB = 203 | Second coefficient **b** of the elliptic curve. |
| CRYPTO_ECC_G_X_DATABLOB = 204 | Affine x-coordinate of the base point **g**. |
| CRYPTO_ECC_G_Y_DATABLOB = 205 | Affine y-coordinate of the base point  **g**. |
| CRYPTO_ECC_N_DATABLOB = 206 | Order of the base point **g**. |
| CRYPTO_ECC_H_INT = 207 | Cofactor of the elliptic curve. |
| CRYPTO_ECC_SK_DATABLOB = 208 | Private key value in ECC. |
| CRYPTO_ECC_PK_X_DATABLOB = 209 | Affine x-coordinate of the public key point in the ECC public key. |
| CRYPTO_ECC_PK_Y_DATABLOB = 210 | Affine y-coordinate of the public key point in the ECC public key. |
| CRYPTO_ECC_FIELD_TYPE_STR = 211 | Finite field type of an elliptic curve. |
| CRYPTO_ECC_FIELD_SIZE_INT = 212 | Length of the finite field, in bits. |
| CRYPTO_ECC_CURVE_NAME_STR = 213 | SECG curve name. |
| CRYPTO_RSA_N_DATABLOB = 301 | Modulus **n** in the RSA algorithm. |
| CRYPTO_RSA_D_DATABLOB = 302 | Private key exponent **d** in the RSA algorithm. |
| CRYPTO_RSA_E_DATABLOB = 303 | Public key exponent **e** in the RSA algorithm. |
| CRYPTO_DH_P_DATABLOB = 401 | Prime modulus **p** in the DH algorithm. |
| CRYPTO_DH_G_DATABLOB = 402 | Generator **g** in the DH algorithm. |
| CRYPTO_DH_L_INT = 403 | Length of the private key in the DH algorithm, in bits. |
| CRYPTO_DH_SK_DATABLOB = 404 | Private key value in DH. |
| CRYPTO_DH_PK_DATABLOB = 405 | Public key value in DH. |
| CRYPTO_ED25519_SK_DATABLOB = 501 | Private key value in ED25519. |
| CRYPTO_ED25519_PK_DATABLOB = 502 | Public key value in ED25519. |
| CRYPTO_X25519_SK_DATABLOB = 601 | Private key value in X25519. |
| CRYPTO_X25519_PK_DATABLOB = 602 | Public key value in X25519. |

### Crypto_EncodingType

```c
enum Crypto_EncodingType
```

**Description**

Defines the encoding types.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| CRYPTO_PEM = 0 | PEM. |
| CRYPTO_DER = 1 | DER. |

### CryptoPrivKeyEncoding_ParamType

```c
enum CryptoPrivKeyEncoding_ParamType
```

**Description**

Defines the parameter type for private key encoding.

**Since**: 20

| Enum Item| Description|
| -- | -- |
| CRYPTO_PRIVATE_KEY_ENCODING_PASSWORD_STR = 0 | Password string.|
| CRYPTO_PRIVATE_KEY_ENCODING_SYMMETRIC_CIPHER_STR = 1 | Name of the symmetric encryption algorithm, which is set using [OH_CryptoPrivKeyEncodingParams_SetParam](capi-crypto-asym-key-h.md#oh_cryptoprivkeyencodingparams_setparam). The options include **DES-EDE3-CBC**, **AES-128-CBC**, **AES-192-CBC**, or **AES-256-CBC**. |

### CryptoAsymKeySpec_Type

```c
enum CryptoAsymKeySpec_Type
```

**Description**

Defines the specification type of an asymmetric key.

**Since**: 20

| Enum Item| Description|
| -- | -- |
| CRYPTO_ASYM_KEY_COMMON_PARAMS_SPEC = 0 | Common parameter specifications.|
| CRYPTO_ASYM_KEY_PRIVATE_KEY_SPEC = 1 | Private key specifications.|
| CRYPTO_ASYM_KEY_PUBLIC_KEY_SPEC = 2 | Public key specifications.|
| CRYPTO_ASYM_KEY_KEY_PAIR_SPEC = 3 | Key pair specifications.|

## Function Description

### OH_CryptoAsymKeyGenerator_Create()

```c
OH_Crypto_ErrCode OH_CryptoAsymKeyGenerator_Create(const char *algoName, OH_CryptoAsymKeyGenerator **ctx)
```

**Description**

Creates an asymmetric key generator based on the given algorithm name.

Note: The created resource must be destroyed by calling [OH_CryptoAsymKeyGenerator_Destroy](capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_destroy).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const char *algoName | Input parameter, indicating the name of the asymmetric key algorithm, which cannot be null. The options are as follows:<br>- RSA algorithms supported since API version 12: **RSA512**, **RSA768**, **RSA1024**, **RSA2048**, **RSA3072**, **RSA4096**, and **RSA8192**. Multi-prime RSA algorithms are supported, for example, **RSA1024\|PRIMES_3**, **RSA4096\|PRIMES_4**, and **RSA8192\|PRIMES_5**.<br>- ECC algorithms supported since API version 12: **ECC224**, **ECC256**, **ECC384**, and **ECC521**.<br>- ECC BrainPool algorithms supported since API version 12: **ECC_BrainPoolP160r1**, **ECC_BrainPoolP160t1**, **ECC_BrainPoolP192r1**, **ECC_BrainPoolP192t1**, **ECC_BrainPoolP224r1**, **ECC_BrainPoolP224t1**, **ECC_BrainPoolP256r1**, **ECC_BrainPoolP256t1**, **ECC_BrainPoolP320r1**, **ECC_BrainPoolP320t1**, **ECC_BrainPoolP384r1**, **ECC_BrainPoolP384t1**, **ECC_BrainPoolP512r1**, and **ECC_BrainPoolP512t1**.<br>- **SM2_256**, **Ed25519**, and **X25519** are supported since API version 12.<br>- DSA series algorithms supported since API version 12: **DSA1024**, **DSA2048**, and **DSA3072**.<br>- DH algorithms supported since API version 12: **DH_modp1536**, **DH_modp2048**, **DH_modp3072**, **DH_modp4096**, **DH_modp6144**, **DH_modp8192**, **DH_ffdhe2048**, **DH_ffdhe3072**, **DH_ffdhe4096**, **DH_ffdhe6144**, and **DH_ffdhe8192**.<br>- **ECC_Secp256k1** supported since API version 14.<br>- **ECC192** supported since API version 26.0.0. |
| [OH_CryptoAsymKeyGenerator](capi-cryptoasymkeyapi-oh-cryptoasymkeygenerator.md) **ctx | Output parameter, indicating a pointer to the asymmetric key generator instance. The value of **ctx** cannot be null, but the value of ***ctx** must be null. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_INVALID_PARAMS**: The value of **ctx** or **algoName** is null.<br>**CRYPTO_NOT_SUPPORTED**: The algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation fails.<br>**CRYPTO_OPERATION_ERROR**: The cryptographic operation fails. |

**Reference**

[OH_CryptoAsymKeyGenerator_Generate](capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_generate) for generating an asymmetric key pair.

[OH_CryptoAsymKeyGenerator_Convert](capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_convert) for converting asymmetric key data into a key pair.

### OH_CryptoAsymKeyGenerator_Generate()

```c
OH_Crypto_ErrCode OH_CryptoAsymKeyGenerator_Generate(OH_CryptoAsymKeyGenerator *ctx, OH_CryptoKeyPair **keyCtx)
```

**Description**

Generates an asymmetric key pair.

Note: After the method is used, the memory for storing the **keyCtx** parameter must be destroyed by calling [OH_CryptoKeyPair_Destroy](capi-crypto-asym-key-h.md#oh_cryptokeypair_destroy).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoAsymKeyGenerator](capi-cryptoasymkeyapi-oh-cryptoasymkeygenerator.md) *ctx | Input parameter, indicating a pointer to an asymmetric key generator instance. The value cannot be null. |
| [OH_CryptoKeyPair](capi-cryptoasymkeyapi-oh-cryptokeypair.md) **keyCtx | Output parameter, indicating a pointer to the key pair. The value of **keyCtx** cannot be null, but the value of ***keyCtx** must be null. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_INVALID_PARAMS**: The value of **ctx** or **keyCtx** is null.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: The memory operation fails.<br>**CRYPTO_OPERATION_ERROR**: The cryptographic operation fails. |

### OH_CryptoAsymKeyGenerator_Convert()

```c
OH_Crypto_ErrCode OH_CryptoAsymKeyGenerator_Convert(OH_CryptoAsymKeyGenerator *ctx, Crypto_EncodingType type, Crypto_DataBlob *pubKeyData, Crypto_DataBlob *priKeyData, OH_CryptoKeyPair **keyCtx)
```

**Description**

Converts asymmetric key data into a key pair.

Note: After the method is used, the memory for storing the **keyCtx** parameter must be destroyed by calling [OH_CryptoKeyPair_Destroy](capi-crypto-asym-key-h.md#oh_cryptokeypair_destroy).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoAsymKeyGenerator](capi-cryptoasymkeyapi-oh-cryptoasymkeygenerator.md) *ctx | Input parameter, indicating a pointer to an asymmetric key generator instance. The value cannot be null. |
| [Crypto_EncodingType](capi-crypto-asym-key-h.md#crypto_encodingtype) type | Input parameter, indicating the encoding type. |
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *pubKeyData | Input parameter, indicating the public key data. This parameter and **priKeyData** cannot be null at the same time. |
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *priKeyData | Input parameter, indicating the private key data. This parameter and **pubKeyData** cannot be null at the same time. |
| [OH_CryptoKeyPair](capi-cryptoasymkeyapi-oh-cryptokeypair.md) **keyCtx | Output parameter, indicating a pointer to the key pair. The value of **keyCtx** cannot be null, but the value of ***keyCtx** must be null. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_INVALID_PARAMS**: The value of **ctx** is null, both **pubKeyData** and **priKeyData** are null, **keyCtx** is null, or **type** is not a valid **Crypto_EncodingType**.<br>**CRYPTO_NOT_SUPPORTED**: The key format is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation fails.<br>**CRYPTO_OPERATION_ERROR**: The key conversion fails. The possible causes are as follows:<br>The key data is damaged or is not in valid PEM/DER format, the key data does not match the algorithm, or the password for encrypting the private key is incorrect. |

### OH_CryptoAsymKeyGenerator_GetAlgoName()

```c
const char *OH_CryptoAsymKeyGenerator_GetAlgoName(OH_CryptoAsymKeyGenerator *ctx)
```

**Description**

Obtains the algorithm of an asymmetric key generator instance.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoAsymKeyGenerator](capi-cryptoasymkeyapi-oh-cryptoasymkeygenerator.md) *ctx | Input parameter, indicating a pointer to an asymmetric key generator instance. The value cannot be null. |

**Returns**

| Type| Description|
| -- | -- |
| const char * | Name of the asymmetric key algorithm, which does not need to be released by the caller. This value cannot be used after the generator instance is destroyed.<br>If **ctx** is null, the return value is null. |

### OH_CryptoAsymKeyGenerator_Destroy()

```c
void OH_CryptoAsymKeyGenerator_Destroy(OH_CryptoAsymKeyGenerator *ctx)
```

**Description**

Destroys the asymmetric key generator instance.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoAsymKeyGenerator](capi-cryptoasymkeyapi-oh-cryptoasymkeygenerator.md) *ctx | Input parameter, indicating a pointer to an asymmetric key generator instance. |

### OH_CryptoKeyPair_Destroy()

```c
void OH_CryptoKeyPair_Destroy(OH_CryptoKeyPair *keyCtx)
```

**Description**

Destroys a key pair.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoKeyPair](capi-cryptoasymkeyapi-oh-cryptokeypair.md) *keyCtx | Input parameter, indicating a key pair. |

### OH_CryptoKeyPair_GetPubKey()

```c
OH_CryptoPubKey *OH_CryptoKeyPair_GetPubKey(OH_CryptoKeyPair *keyCtx)
```

**Description**

Obtains the public key in the key pair.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoKeyPair](capi-cryptoasymkeyapi-oh-cryptokeypair.md) *keyCtx | Input parameter, indicating a key pair. The value cannot be null. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_CryptoPubKey *](capi-cryptoasymkeyapi-oh-cryptopubkey.md) | Public key in the key pair. It is used for internal reference and does not need to be destroyed separately. It cannot be used after the key pair is destroyed.<br>If **keyCtx** is null or the public key does not exist, the return value is null. |

### OH_CryptoKeyPair_GetPrivKey()

```c
OH_CryptoPrivKey *OH_CryptoKeyPair_GetPrivKey(OH_CryptoKeyPair *keyCtx)
```

**Description**

Obtains the private key in the key pair.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoKeyPair](capi-cryptoasymkeyapi-oh-cryptokeypair.md) *keyCtx | Input parameter, indicating a key pair. The value cannot be null. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_CryptoPrivKey *](capi-cryptoasymkeyapi-oh-cryptoprivkey.md) | Private key in the key pair. It is used for internal reference and does not need to be destroyed separately. It cannot be used after the key pair is destroyed.<br>If **keyCtx** is null or the private key does not exist, the return value is null. |

### OH_CryptoPubKey_Encode()

```c
OH_Crypto_ErrCode OH_CryptoPubKey_Encode(OH_CryptoPubKey *key, Crypto_EncodingType type, const char *encodingStandard, Crypto_DataBlob *out)
```

**Description**

Encodes a public key.

Note: After the method is used, the memory for storing the **out** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoPubKey](capi-cryptoasymkeyapi-oh-cryptopubkey.md) *key | Input parameter, indicating a public key. The value cannot be null. |
| [Crypto_EncodingType](capi-crypto-asym-key-h.md#crypto_encodingtype) type | Input parameter, indicating the encoding type. |
| const char *encodingStandard | Input parameter, indicating the encoding standard. The value can be **X509**. The value cannot be null. |
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *out | Output parameter, indicating a pointer to the **Crypto_DataBlob** struct used to store the encoding result. The value cannot be null. Before calling this method, initialize **out** to 0. Do not set the **data** field of **out**. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_INVALID_PARAMS**: The value of **key**, **out**, or **encodingStandard** is null, **type** is not a valid **Crypto_EncodingType**, or the encoding standard is incompatible with the key type.<br>**CRYPTO_NOT_SUPPORTED**: The encoding format is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation fails.<br>**CRYPTO_OPERATION_ERROR**: Encoding fails. |

### OH_CryptoPubKey_GetParam()

```c
OH_Crypto_ErrCode OH_CryptoPubKey_GetParam(OH_CryptoPubKey *key, CryptoAsymKey_ParamType item, Crypto_DataBlob *value)
```

**Description**

Obtains the specified parameters of the public key.

Note: After the method is used, the memory for storing the **value** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoPubKey](capi-cryptoasymkeyapi-oh-cryptopubkey.md) *key | Input parameter, indicating a public key. The value cannot be null. |
| [CryptoAsymKey_ParamType](capi-crypto-asym-key-h.md#cryptoasymkey_paramtype) item | Input parameter, indicating the type of the asymmetric key parameter. |
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *value | Output parameter, indicating a pointer to the **Crypto_DataBlob** struct used to store the output data. The value cannot be null. Before calling this method, initialize **value** to 0. Do not set the **data** field of **value**. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_INVALID_PARAMS**: The value of **key** or **value** is null, or the parameter type is not supported by the key algorithm.<br>**CRYPTO_NOT_SUPPORTED**: The parameter type is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation fails.<br>**CRYPTO_OPERATION_ERROR**: The parameter fails to be obtained. |

### OH_CryptoAsymKeyGenerator_SetPassword()

```c
OH_Crypto_ErrCode OH_CryptoAsymKeyGenerator_SetPassword(OH_CryptoAsymKeyGenerator *ctx, const unsigned char *password, uint32_t passwordLen)
```

**Description**

Sets the password of the asymmetric key generator. If you need to use [OH_CryptoAsymKeyGenerator_Convert](capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_convert) to convert the encrypted private key data into a key pair, call this method to set the password.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoAsymKeyGenerator](capi-cryptoasymkeyapi-oh-cryptoasymkeygenerator.md) *ctx | Input parameter, indicating a pointer to an asymmetric key generator instance. The value cannot be null. |
| const unsigned char *password | Input password, indicating the password. This API performs deep copy of the data in **password**. The caller can immediately release **password** after the API returns a result. |
| uint32_t passwordLen | Input parameter, indicating the length of the password, in bytes. The value must be greater than 0. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation fails.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: The value of **ctx** or **password** is null, or the value of **passwordLen** is **0**.<br>**CRYPTO_OPERATION_ERROR**: The cryptographic operation fails. |

### OH_CryptoPrivKeyEncodingParams_Create()

```c
OH_Crypto_ErrCode OH_CryptoPrivKeyEncodingParams_Create(OH_CryptoPrivKeyEncodingParams **ctx)
```

**Description**

Creates private key encoding parameters.

Note: The created resource must be destroyed by calling [OH_CryptoPrivKeyEncodingParams_Destroy](capi-crypto-asym-key-h.md#oh_cryptoprivkeyencodingparams_destroy).

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoPrivKeyEncodingParams](capi-cryptoasymkeyapi-oh-cryptoprivkeyencodingparams.md) **ctx | Output parameter, indicating a pointer to the private key encoding parameter. The value of **ctx** cannot be null, but the value of ***ctx** must be null. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: The value of **ctx** is null.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation fails.<br>**CRYPTO_OPERATION_ERROR**: The cryptographic operation fails. |

**Reference**

[OH_CryptoPrivKeyEncodingParams_SetParam](capi-crypto-asym-key-h.md#oh_cryptoprivkeyencodingparams_setparam) for setting a private key encoding parameter.

### OH_CryptoPrivKeyEncodingParams_SetParam()

```c
OH_Crypto_ErrCode OH_CryptoPrivKeyEncodingParams_SetParam(OH_CryptoPrivKeyEncodingParams *ctx, CryptoPrivKeyEncoding_ParamType type, Crypto_DataBlob *value)
```

**Description**

Sets a private key encoding parameter.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoPrivKeyEncodingParams](capi-cryptoasymkeyapi-oh-cryptoprivkeyencodingparams.md) *ctx | Input parameter, indicating a pointer to the private key encoding parameters. The value cannot be null. |
| [CryptoPrivKeyEncoding_ParamType](capi-crypto-asym-key-h.md#cryptoprivkeyencoding_paramtype) type | Input parameter, indicating the parameter type for private key encoding. |
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *value | Input parameter, indicating the value of a private key encoding parameter. This API performs deep copy of the data in **value**. The caller can immediately release **value** after the API returns a result. The value cannot be null. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: The value of **ctx** or **value** is null, **data** in **value** is null, **len** in **value** is **0**, or **type** cannot be identified.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation for deep copy fails.<br>**CRYPTO_OPERATION_ERROR**: The cryptographic operation fails. |

### OH_CryptoPrivKeyEncodingParams_Destroy()

```c
void OH_CryptoPrivKeyEncodingParams_Destroy(OH_CryptoPrivKeyEncodingParams *ctx)
```

**Description**

Destroys a private key encoding parameter.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoPrivKeyEncodingParams](capi-cryptoasymkeyapi-oh-cryptoprivkeyencodingparams.md) *ctx | Input parameter, indicating a pointer to the private key encoding parameters. |

### OH_CryptoPrivKey_Encode()

```c
OH_Crypto_ErrCode OH_CryptoPrivKey_Encode(OH_CryptoPrivKey *key, Crypto_EncodingType type, const char *encodingStandard, OH_CryptoPrivKeyEncodingParams *params, Crypto_DataBlob *out)
```

**Description**

Encodes a private key.

Note: After the method is used, the memory for storing the **out** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob).

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoPrivKey](capi-cryptoasymkeyapi-oh-cryptoprivkey.md) *key | Input parameter, indicating a private key. The value cannot be null. |
| [Crypto_EncodingType](capi-crypto-asym-key-h.md#crypto_encodingtype) type | Input parameter, indicating the encoding type. |
| const char *encodingStandard | Input parameter, indicating the encoding standard. The value can be **PKCS8** or **PKCS1**. **PKCS1** is only supported for RSA private keys. The value cannot be null. |
| [OH_CryptoPrivKeyEncodingParams](capi-cryptoasymkeyapi-oh-cryptoprivkeyencodingparams.md) *params | Input parameter, indicating a pointer to the private key encoding parameters, which can be null. Set this parameter if you need to encrypt a private key. |
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *out | Output parameter, indicating a pointer to the **Crypto_DataBlob** struct used to store the encoding result. The value cannot be null. Before calling this method, initialize **out** to 0. Do not set the **data** field of **out**. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: The value of **key**, **out**, or **encodingStandard** is null, **type** is not a valid **Crypto_EncodingType**, or the encoding standard is incompatible with the key type.<br>**CRYPTO_NOT_SUPPORTED**: The encoding format is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation fails.<br>**CRYPTO_OPERATION_ERROR**: Encoding fails. |

### OH_CryptoPrivKey_GetParam()

```c
OH_Crypto_ErrCode OH_CryptoPrivKey_GetParam(OH_CryptoPrivKey *key, CryptoAsymKey_ParamType item, Crypto_DataBlob *value)
```

**Description**

Obtains the specified parameter of a private key.

Note: After the method is used, the memory for storing the **value** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob).

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoPrivKey](capi-cryptoasymkeyapi-oh-cryptoprivkey.md) *key | Input parameter, indicating a private key. The value cannot be null. |
| [CryptoAsymKey_ParamType](capi-crypto-asym-key-h.md#cryptoasymkey_paramtype) item | Input parameter, indicating the type of the asymmetric key parameter. |
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *value | Output parameter, indicating a pointer to the **Crypto_DataBlob** struct used to store the output data. The value cannot be null. Before calling this method, initialize **value** to 0. Do not set the **data** field of **value**. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: The value of **key** or **value** is null, or the parameter type is not supported by the key algorithm.<br>**CRYPTO_NOT_SUPPORTED**: The parameter type is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation fails.<br>**CRYPTO_OPERATION_ERROR**: The parameter fails to be obtained. |

### OH_CryptoAsymKeySpec_GenEcCommonParamsSpec()

```c
OH_Crypto_ErrCode OH_CryptoAsymKeySpec_GenEcCommonParamsSpec(const char *curveName, OH_CryptoAsymKeySpec **spec)
```

**Description**

Generates EC common parameter specifications.

Note: After the method is used, the memory for storing the **spec** parameter must be destroyed by calling [OH_CryptoAsymKeySpec_Destroy](capi-crypto-asym-key-h.md#oh_cryptoasymkeyspec_destroy).

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| const char *curveName | Input parameter, indicating the NID of the ECC curve. The value cannot be null. The value can be **NID_X9_62_prime256v1**, **NID_secp384r1**, **NID_secp521r1**, or **NID_sm2**. |
| [OH_CryptoAsymKeySpec](capi-cryptoasymkeyapi-oh-cryptoasymkeyspec.md) **spec | Output parameter, indicating a pointer to the asymmetric key specification. The value of **spec** cannot be null, but the value of ***spec** must be null. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: The value of **curveName** or **spec** is null, or the curve name is not valid.<br>**CRYPTO_NOT_SUPPORTED**: The curve is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation fails.<br>**CRYPTO_OPERTION_ERROR**: The specification fails to be generated. |

### OH_CryptoAsymKeySpec_GenDhCommonParamsSpec()

```c
OH_Crypto_ErrCode OH_CryptoAsymKeySpec_GenDhCommonParamsSpec(int pLen, int skLen, OH_CryptoAsymKeySpec **spec)
```

**Description**

Generates DH common parameter specifications.

Note: After the method is used, the memory for storing the **spec** parameter must be destroyed by calling [OH_CryptoAsymKeySpec_Destroy](capi-crypto-asym-key-h.md#oh_cryptoasymkeyspec_destroy).

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| int pLen | Input parameter, indicating the length of the prime number **p**, in bytes. |
| int skLen | Input parameter, indicating the length of the private key, in bytes. |
| [OH_CryptoAsymKeySpec](capi-cryptoasymkeyapi-oh-cryptoasymkeyspec.md) **spec | Output parameter, indicating a pointer to the asymmetric key specification. The value of **spec** cannot be null, but the value of ***spec** must be null. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: **spec** is null, **pLen** is a negative number, **skLen** is a negative number, or **skLen** is greater than **pLen**.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation fails.<br>**CRYPTO_OPERATION_ERROR**: The cryptographic operation fails. |

### OH_CryptoAsymKeySpec_Create()

```c
OH_Crypto_ErrCode OH_CryptoAsymKeySpec_Create(const char *algoName, CryptoAsymKeySpec_Type type, OH_CryptoAsymKeySpec **spec)
```

**Description**

Creates asymmetric key specifications based on the given algorithm name and specification type.

Note: The created resource must be destroyed by calling [OH_CryptoAsymKeySpec_Destroy](capi-crypto-asym-key-h.md#oh_cryptoasymkeyspec_destroy).

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| const char *algoName | Input parameter, indicating the name of the asymmetric key specification algorithm, which cannot be null. The options are as follows:<br>- Since API version 20, **RSA**, **ECC**, **DSA**, **SM2**, **Ed25519**, **X25519**, and **DH** are supported. |
| [CryptoAsymKeySpec_Type](capi-crypto-asym-key-h.md#cryptoasymkeyspec_type) type | Input parameter, indicating the specification type of an asymmetric key. |
| [OH_CryptoAsymKeySpec](capi-cryptoasymkeyapi-oh-cryptoasymkeyspec.md) **spec | Output parameter, indicating a pointer to the asymmetric key specification. The value of **spec** cannot be null, but the value of ***spec** must be null. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: The value of **algoName** or **spec** is null, or **algoName** is not a supported algorithm name.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation fails.<br>**CRYPTO_OPERATION_ERROR**: The cryptographic operation fails. |

### OH_CryptoAsymKeySpec_SetParam()

```c
OH_Crypto_ErrCode OH_CryptoAsymKeySpec_SetParam(OH_CryptoAsymKeySpec *spec, CryptoAsymKey_ParamType type, Crypto_DataBlob *value)
```

**Description**

Sets the specified parameters for asymmetric key specifications.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoAsymKeySpec](capi-cryptoasymkeyapi-oh-cryptoasymkeyspec.md) *spec | Input parameter, indicating a pointer to the asymmetric key specifications. The value cannot be null. |
| [CryptoAsymKey_ParamType](capi-crypto-asym-key-h.md#cryptoasymkey_paramtype) type | Input parameter, indicating the type of the asymmetric key parameter. |
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *value | Input parameter, indicating the input data. This API performs deep copy of the data in **value**. The caller can immediately release **value** after the API returns a result. The value cannot be null. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: The value of **spec** or **value** is null, **data** in **value** is null, **len** in **value** is **0**, or the parameter type is not supported by the algorithm.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation for deep copy fails.<br>**CRYPTO_OPERATION_ERROR**: The cryptographic operation fails. |

### OH_CryptoAsymKeySpec_SetCommonParamsSpec()

```c
OH_Crypto_ErrCode OH_CryptoAsymKeySpec_SetCommonParamsSpec(OH_CryptoAsymKeySpec *spec, OH_CryptoAsymKeySpec *commonParamsSpec)
```

**Description**

Sets the common parameter specifications into the asymmetric key specifications.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoAsymKeySpec](capi-cryptoasymkeyapi-oh-cryptoasymkeyspec.md) *spec | Input parameter, indicating a pointer to the asymmetric key specifications. The value cannot be null. |
| [OH_CryptoAsymKeySpec](capi-cryptoasymkeyapi-oh-cryptoasymkeyspec.md) *commonParamsSpec | Input parameter, indicating common parameter specifications. This API performs deep copy of the data in **commonParamsSpec**. The caller can immediately release **commonParamsSpec** after the API returns a result. The value cannot be null. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: The value of **spec** or **commonParamsSpec** is null.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation fails.<br>**CRYPTO_OPERATION_ERROR**: The cryptographic operation fails. |

### OH_CryptoAsymKeySpec_GetParam()

```c
OH_Crypto_ErrCode OH_CryptoAsymKeySpec_GetParam(OH_CryptoAsymKeySpec *spec, CryptoAsymKey_ParamType type, Crypto_DataBlob *value)
```

**Description**

Obtains the specified parameters for asymmetric key specifications.

Note: After the method is used, the memory for storing the **value** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob).

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoAsymKeySpec](capi-cryptoasymkeyapi-oh-cryptoasymkeyspec.md) *spec | Input parameter, indicating a pointer to the asymmetric key specifications. The value cannot be null. |
| [CryptoAsymKey_ParamType](capi-crypto-asym-key-h.md#cryptoasymkey_paramtype) type | Input parameter, indicating the type of the asymmetric key parameter. |
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *value | Output parameter, indicating a pointer to the **Crypto_DataBlob** struct used to store the output data. The value cannot be null. Before calling this method, initialize **value** to 0. Do not set the **data** field of **value**. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: The value of **spec** or **value** is null, or the parameter type is not supported by the algorithm.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation fails.<br>**CRYPTO_OPERATION_ERROR**: The cryptographic operation fails. |

### OH_CryptoAsymKeySpec_Destroy()

```c
void OH_CryptoAsymKeySpec_Destroy(OH_CryptoAsymKeySpec *spec)
```

**Description**

Destroys asymmetric key specifications.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoAsymKeySpec](capi-cryptoasymkeyapi-oh-cryptoasymkeyspec.md) *spec | Input parameter, indicating a pointer to the asymmetric key specifications. |

### OH_CryptoAsymKeyGeneratorWithSpec_Create()

```c
OH_Crypto_ErrCode OH_CryptoAsymKeyGeneratorWithSpec_Create(OH_CryptoAsymKeySpec *keySpec, OH_CryptoAsymKeyGeneratorWithSpec **generator)
```

**Description**

Creates a key generator instance based on asymmetric key specifications.

Note: The created resource must be destroyed by calling [OH_CryptoAsymKeyGeneratorWithSpec_Destroy](capi-crypto-asym-key-h.md#oh_cryptoasymkeygeneratorwithspec_destroy).

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoAsymKeySpec](capi-cryptoasymkeyapi-oh-cryptoasymkeyspec.md) *keySpec | Input parameter, indicating a pointer to the asymmetric key specifications. The value cannot be null. |
| [OH_CryptoAsymKeyGeneratorWithSpec](capi-cryptoasymkeyapi-oh-cryptoasymkeygeneratorwithspec.md) **generator | Output parameter, indicating a pointer to the asymmetric key generator instance based on asymmetric key specifications. The value of **generator** cannot be null, but the value of ***generator** must be null. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: The value of **keySpec** or **generator** is null, or the key specification parameters are incomplete or invalid.<br>**CRYPTO_NOT_SUPPORTED**: The algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation fails.<br>**CRYPTO_OPERATION_ERROR**: The generator instance fails to be created. |

**Reference**

[OH_CryptoAsymKeyGeneratorWithSpec_GenKeyPair](capi-crypto-asym-key-h.md#oh_cryptoasymkeygeneratorwithspec_genkeypair) for generating a key pair based on asymmetric key specifications.

### OH_CryptoAsymKeyGeneratorWithSpec_GenKeyPair()

```c
OH_Crypto_ErrCode OH_CryptoAsymKeyGeneratorWithSpec_GenKeyPair(OH_CryptoAsymKeyGeneratorWithSpec *generator, OH_CryptoKeyPair **keyPair)
```

**Description**

Generates a key pair based on the asymmetric key specification.

Note: After the method is used, the memory for storing the **keyPair** parameter must be released by calling [OH_CryptoKeyPair_Destroy](capi-crypto-asym-key-h.md#oh_cryptokeypair_destroy).

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoAsymKeyGeneratorWithSpec](capi-cryptoasymkeyapi-oh-cryptoasymkeygeneratorwithspec.md) *generator | Input parameter, indicating a pointer to the asymmetric key generator instance based on the specifications. The value cannot be null. |
| [OH_CryptoKeyPair](capi-cryptoasymkeyapi-oh-cryptokeypair.md) **keyPair | Output parameter, indicating a pointer to the key pair. The value of **keyPair** cannot be null, but the value of ***keyPair** must be null. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: The value of **generator** or **keyPair** is null.<br>**CRYPTO_NOT_SUPPORTED**: The operation is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation fails.<br>**CRYPTO_OPERATION_ERROR**: The key pair fails to be generated. A possible cause is that the key specification parameters are incomplete or inconsistent. |

### OH_CryptoAsymKeyGeneratorWithSpec_Destroy()

```c
void OH_CryptoAsymKeyGeneratorWithSpec_Destroy(OH_CryptoAsymKeyGeneratorWithSpec *generator)
```

**Description**

Destroys the asymmetric key generator instance created based on specifications.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoAsymKeyGeneratorWithSpec](capi-cryptoasymkeyapi-oh-cryptoasymkeygeneratorwithspec.md) *generator | Input parameter, indicating a pointer to the asymmetric key generator instance based on the specifications. |

### OH_CryptoEcPoint_Create()

```c
OH_Crypto_ErrCode OH_CryptoEcPoint_Create(const char *curveName, Crypto_DataBlob *ecKeyData, OH_CryptoEcPoint **point)
```

**Description**

Creates an elliptic curve point.

Note: The created resource must be destroyed by calling [OH_CryptoEcPoint_Destroy](capi-crypto-asym-key-h.md#oh_cryptoecpoint_destroy).

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| const char *curveName | Input parameter, indicating the NID of the elliptic curve. The value cannot be null. The value can be **NID_X9_62_prime256v1**, **NID_secp384r1**, **NID_secp521r1**, or **NID_sm2**. |
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *ecKeyData | Input parameter, indicating the elliptic curve point data. The value can be in the format of **04 \|\| x \|\| y**, **02 \|\| x**, or **03 \|\| x**. The value can be null. If **ecKeyData** is null, an empty elliptic curve point specification is created. |
| [OH_CryptoEcPoint](capi-cryptoasymkeyapi-oh-cryptoecpoint.md) **point | Output parameter, indicating a pointer to the elliptic curve point. The value of **point** cannot be null, but the value of ***point** must be null. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: The value of **curveName** or **point** is null, or the curve name is invalid.<br>**CRYPTO_NOT_SUPPORTED**: The curve is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation fails.<br>**CRYPTO_OPERATION_ERROR**: The EC point fails to be created. A possible cause is that the point data format is incorrect. |

**Reference**

[OH_CryptoEcPoint_GetCoordinate](capi-crypto-asym-key-h.md#oh_cryptoecpoint_getcoordinate) for obtaining the X and Y coordinates of an elliptic curve point.

[OH_CryptoEcPoint_SetCoordinate](capi-crypto-asym-key-h.md#oh_cryptoecpoint_setcoordinate) for setting the X and Y coordinates of an elliptic curve point.

### OH_CryptoEcPoint_GetCoordinate()

```c
OH_Crypto_ErrCode OH_CryptoEcPoint_GetCoordinate(OH_CryptoEcPoint *point, Crypto_DataBlob *x, Crypto_DataBlob *y)
```

**Description**

Obtains the X and Y coordinates of an elliptic curve point.

Note: After the method is used, the memory for storing the **x** and **y** parameters must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob).

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoEcPoint](capi-cryptoasymkeyapi-oh-cryptoecpoint.md) *point | Input parameter, indicating an elliptic curve point. The value cannot be null. |
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *x | Output parameter, indicating a pointer to the **Crypto_DataBlob** struct used to store the X coordinate. The value cannot be null. Before calling this method, initialize **x** to 0. Do not set the **data** field of **x**. |
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *y | Output parameter, indicating a pointer to the **Crypto_DataBlob** struct used to store the Y coordinate. The value cannot be null. Before calling this method, initialize **y** to 0. Do not set the **data** field of **y**. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: The value of **point**, **x**, or **y** is null.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation fails.<br>**CRYPTO_OPERATION_ERROR**: The cryptographic operation fails. |

### OH_CryptoEcPoint_SetCoordinate()

```c
OH_Crypto_ErrCode OH_CryptoEcPoint_SetCoordinate(OH_CryptoEcPoint *point, Crypto_DataBlob *x, Crypto_DataBlob *y)
```

**Description**

Sets the X and Y coordinates of an elliptic curve point.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoEcPoint](capi-cryptoasymkeyapi-oh-cryptoecpoint.md) *point | Input parameter, indicating an elliptic curve point. The value cannot be null. |
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *x | Input parameter, indicating the X coordinate of the point on an elliptic curve. This API performs deep copy of the data in **x** and **y**. The caller can immediately release **x** and **y** after the API returns a result. The value cannot be null. |
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *y | Input parameter, indicating the Y coordinate of the point on an elliptic curve. The value cannot be null. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: The value of **point**, **x**, or **y** is null.<br>**CRYPTO_NOT_SUPPORTED**: The operation or algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation for deep copy fails.<br>**CRYPTO_OPERATION_ERROR**: The cryptographic operation fails. |

**Reference**

[OH_CryptoEcPoint_Encode](capi-crypto-asym-key-h.md#oh_cryptoecpoint_encode) for encoding an elliptic curve point in a specified format.

### OH_CryptoEcPoint_Encode()

```c
OH_Crypto_ErrCode OH_CryptoEcPoint_Encode(OH_CryptoEcPoint *point, const char *format, Crypto_DataBlob *out)
```

**Description**

Encodes an elliptic curve point in a specified format.

Note: After the method is used, the memory for storing the **out** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob).

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoEcPoint](capi-cryptoasymkeyapi-oh-cryptoecpoint.md) *point | Input parameter, indicating an elliptic curve point. The value cannot be null. |
| const char *format | Input parameter, indicating the encoding format. The value cannot be null. This parameter can be set to **UNCOMPRESSED** or **COMPRESSED** |
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *out | Output parameter, indicating a pointer to the **Crypto_DataBlob** struct used to store the encoded elliptic curve point data. The value cannot be null. Before calling this method, initialize **out** to 0. Do not set the **data** field of **out**. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: The value of **point**, **format**, or **out** is null, or the format string is not in a valid point format.<br>**CRYPTO_NOT_SUPPORTED**: The format is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation fails.<br>**CRYPTO_OPERATION_ERROR**: Encoding fails. A possible cause is that the point is not a valid curve point. |

### OH_CryptoEcPoint_Destroy()

```c
void OH_CryptoEcPoint_Destroy(OH_CryptoEcPoint *point)
```

**Description**

Destroys an elliptic curve point.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoEcPoint](capi-cryptoasymkeyapi-oh-cryptoecpoint.md) *point | Input parameter, indicating an elliptic curve point. |