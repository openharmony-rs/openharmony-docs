# crypto_asym_key.h

## Overview

Defines the asymmetric key interfaces.

**Include**: <CryptoArchitectureKit/crypto_asym_key.h>

**Library**: libohcrypto.so

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 12

**Related module**: [CryptoAsymKeyApi](capi-cryptoasymkeyapi.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_CryptoKeyPair](capi-cryptoasymkeyapi-oh-cryptokeypair.md) | OH_CryptoKeyPair | Key pair structure, representing a key pair. |
| [OH_CryptoPubKey](capi-cryptoasymkeyapi-oh-cryptopubkey.md) | OH_CryptoPubKey | Public key structure, representing a public key. |
| [OH_CryptoPrivKey](capi-cryptoasymkeyapi-oh-cryptoprivkey.md) | OH_CryptoPrivKey | Private key structure, representing a private key. |
| [OH_CryptoAsymKeyGenerator](capi-cryptoasymkeyapi-oh-cryptoasymkeygenerator.md) | OH_CryptoAsymKeyGenerator | Asymmetric key generator structure, representing an asymmetric key generator. |
| [OH_CryptoPrivKeyEncodingParams](capi-cryptoasymkeyapi-oh-cryptoprivkeyencodingparams.md) | OH_CryptoPrivKeyEncodingParams | Private key encoding parameters structure, representing private key encoding parameters. |
| [OH_CryptoAsymKeySpec](capi-cryptoasymkeyapi-oh-cryptoasymkeyspec.md) | OH_CryptoAsymKeySpec | Asymmetric key specification structure, representing an asymmetric key specification. |
| [OH_CryptoAsymKeyGeneratorWithSpec](capi-cryptoasymkeyapi-oh-cryptoasymkeygeneratorwithspec.md) | OH_CryptoAsymKeyGeneratorWithSpec | Specification-based asymmetric key generator structure, representing a specification-based asymmetric key generator. |
| [OH_CryptoEcPoint](capi-cryptoasymkeyapi-oh-cryptoecpoint.md) | OH_CryptoEcPoint | Elliptic curve point structure, representing a point on the elliptic curve. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [CryptoAsymKey_ParamType](#cryptoasymkey_paramtype) | CryptoAsymKey_ParamType | Defines asymmetric key parameter types. |
| [Crypto_EncodingType](#crypto_encodingtype) | Crypto_EncodingType | Defines the encoding type. |
| [CryptoPrivKeyEncoding_ParamType](#cryptoprivkeyencoding_paramtype) | CryptoPrivKeyEncoding_ParamType | Defines private key encoding parameter types. |
| [CryptoAsymKeySpec_Type](#cryptoasymkeyspec_type) | CryptoAsymKeySpec_Type | Defines asymmetric key specification types. |

### Function

| Name | Description |
| -- | -- |
| [OH_Crypto_ErrCode OH_CryptoAsymKeyGenerator_Create(const char *algoName, OH_CryptoAsymKeyGenerator **ctx)](#oh_cryptoasymkeygenerator_create) | Creates an asymmetric key generator based on the given algorithm name. |
| [OH_Crypto_ErrCode OH_CryptoAsymKeyGenerator_Generate(OH_CryptoAsymKeyGenerator *ctx, OH_CryptoKeyPair **keyCtx)](#oh_cryptoasymkeygenerator_generate) | Generates an asymmetric key pair. |
| [OH_Crypto_ErrCode OH_CryptoAsymKeyGenerator_Convert(OH_CryptoAsymKeyGenerator *ctx, Crypto_EncodingType type, Crypto_DataBlob *pubKeyData, Crypto_DataBlob *priKeyData, OH_CryptoKeyPair **keyCtx)](#oh_cryptoasymkeygenerator_convert) | Converts asymmetric key data to a key pair. |
| [const char *OH_CryptoAsymKeyGenerator_GetAlgoName(OH_CryptoAsymKeyGenerator *ctx)](#oh_cryptoasymkeygenerator_getalgoname) | Obtains the algorithm name of the asymmetric key generator. |
| [void OH_CryptoAsymKeyGenerator_Destroy(OH_CryptoAsymKeyGenerator *ctx)](#oh_cryptoasymkeygenerator_destroy) | Destroys the asymmetric key generator. |
| [void OH_CryptoKeyPair_Destroy(OH_CryptoKeyPair *keyCtx)](#oh_cryptokeypair_destroy) | Destroys the key pair. |
| [OH_CryptoPubKey *OH_CryptoKeyPair_GetPubKey(OH_CryptoKeyPair *keyCtx)](#oh_cryptokeypair_getpubkey) | Obtains the public key from the key pair. |
| [OH_CryptoPrivKey *OH_CryptoKeyPair_GetPrivKey(OH_CryptoKeyPair *keyCtx)](#oh_cryptokeypair_getprivkey) | Obtains the private key from the key pair. |
| [OH_Crypto_ErrCode OH_CryptoPubKey_Encode(OH_CryptoPubKey *key, Crypto_EncodingType type, const char *encodingStandard, Crypto_DataBlob *out)](#oh_cryptopubkey_encode) | Encodes the public key. |
| [OH_Crypto_ErrCode OH_CryptoPubKey_GetParam(OH_CryptoPubKey *key, CryptoAsymKey_ParamType item, Crypto_DataBlob *value)](#oh_cryptopubkey_getparam) | Obtains the specified parameter of the public key. |
| [OH_Crypto_ErrCode OH_CryptoAsymKeyGenerator_SetPassword(OH_CryptoAsymKeyGenerator *ctx, const unsigned char *password, uint32_t passwordLen)](#oh_cryptoasymkeygenerator_setpassword) | Sets the password for the asymmetric key generator. Call this method to set the password if you need to use [OH_CryptoAsymKeyGenerator_Convert](capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_convert) to convert encrypted private key data to a key pair. |
| [OH_Crypto_ErrCode OH_CryptoPrivKeyEncodingParams_Create(OH_CryptoPrivKeyEncodingParams **ctx)](#oh_cryptoprivkeyencodingparams_create) | Creates private key encoding parameters. |
| [OH_Crypto_ErrCode OH_CryptoPrivKeyEncodingParams_SetParam(OH_CryptoPrivKeyEncodingParams *ctx, CryptoPrivKeyEncoding_ParamType type, Crypto_DataBlob *value)](#oh_cryptoprivkeyencodingparams_setparam) | Sets private key encoding parameters. |
| [void OH_CryptoPrivKeyEncodingParams_Destroy(OH_CryptoPrivKeyEncodingParams *ctx)](#oh_cryptoprivkeyencodingparams_destroy) | Destroys private key encoding parameters. |
| [OH_Crypto_ErrCode OH_CryptoPrivKey_Encode(OH_CryptoPrivKey *key, Crypto_EncodingType type, const char *encodingStandard, OH_CryptoPrivKeyEncodingParams *params, Crypto_DataBlob *out)](#oh_cryptoprivkey_encode) | Encodes the private key. |
| [OH_Crypto_ErrCode OH_CryptoPrivKey_GetParam(OH_CryptoPrivKey *key, CryptoAsymKey_ParamType item, Crypto_DataBlob *value)](#oh_cryptoprivkey_getparam) | Obtains the specified parameter of the private key. |
| [OH_Crypto_ErrCode OH_CryptoAsymKeySpec_GenEcCommonParamsSpec(const char *curveName, OH_CryptoAsymKeySpec **spec)](#oh_cryptoasymkeyspec_geneccommonparamsspec) | Generates EC common parameter specification. |
| [OH_Crypto_ErrCode OH_CryptoAsymKeySpec_GenDhCommonParamsSpec(int pLen, int skLen, OH_CryptoAsymKeySpec **spec)](#oh_cryptoasymkeyspec_gendhcommonparamsspec) | Generates DH common parameter specification. |
| [OH_Crypto_ErrCode OH_CryptoAsymKeySpec_Create(const char *algoName, CryptoAsymKeySpec_Type type, OH_CryptoAsymKeySpec **spec)](#oh_cryptoasymkeyspec_create) | Creates an asymmetric key specification based on the given algorithm name and specification type. |
| [OH_Crypto_ErrCode OH_CryptoAsymKeySpec_SetParam(OH_CryptoAsymKeySpec *spec, CryptoAsymKey_ParamType type, Crypto_DataBlob *value)](#oh_cryptoasymkeyspec_setparam) | Sets the specified parameter of the asymmetric key specification. |
| [OH_Crypto_ErrCode OH_CryptoAsymKeySpec_SetCommonParamsSpec(OH_CryptoAsymKeySpec *spec, OH_CryptoAsymKeySpec *commonParamsSpec)](#oh_cryptoasymkeyspec_setcommonparamsspec) | Sets the common parameter specification into the asymmetric key specification. |
| [OH_Crypto_ErrCode OH_CryptoAsymKeySpec_GetParam(OH_CryptoAsymKeySpec *spec, CryptoAsymKey_ParamType type, Crypto_DataBlob *value)](#oh_cryptoasymkeyspec_getparam) | Obtains the specified parameter of the asymmetric key specification. |
| [void OH_CryptoAsymKeySpec_Destroy(OH_CryptoAsymKeySpec *spec)](#oh_cryptoasymkeyspec_destroy) | Destroys the asymmetric key specification. |
| [OH_Crypto_ErrCode OH_CryptoAsymKeyGeneratorWithSpec_Create(OH_CryptoAsymKeySpec *keySpec, OH_CryptoAsymKeyGeneratorWithSpec **generator)](#oh_cryptoasymkeygeneratorwithspec_create) | Creates a key generator based on the asymmetric key specification. |
| [OH_Crypto_ErrCode OH_CryptoAsymKeyGeneratorWithSpec_GenKeyPair(OH_CryptoAsymKeyGeneratorWithSpec *generator, OH_CryptoKeyPair **keyPair)](#oh_cryptoasymkeygeneratorwithspec_genkeypair) | Generates a key pair based on the asymmetric key specification. |
| [void OH_CryptoAsymKeyGeneratorWithSpec_Destroy(OH_CryptoAsymKeyGeneratorWithSpec *generator)](#oh_cryptoasymkeygeneratorwithspec_destroy) | Destroys the specification-based asymmetric key generator. |
| [OH_Crypto_ErrCode OH_CryptoEcPoint_Create(const char *curveName, Crypto_DataBlob *ecKeyData, OH_CryptoEcPoint **point)](#oh_cryptoecpoint_create) | Creates an elliptic curve point. |
| [OH_Crypto_ErrCode OH_CryptoEcPoint_GetCoordinate(OH_CryptoEcPoint *point, Crypto_DataBlob *x, Crypto_DataBlob *y)](#oh_cryptoecpoint_getcoordinate) | Obtains the x and y coordinates of the elliptic curve point. |
| [OH_Crypto_ErrCode OH_CryptoEcPoint_SetCoordinate(OH_CryptoEcPoint *point, Crypto_DataBlob *x, Crypto_DataBlob *y)](#oh_cryptoecpoint_setcoordinate) | Sets the x and y coordinates of the elliptic curve point. |
| [OH_Crypto_ErrCode OH_CryptoEcPoint_Encode(OH_CryptoEcPoint *point, const char *format, Crypto_DataBlob *out)](#oh_cryptoecpoint_encode) | Encodes the elliptic curve point to the specified format. |
| [void OH_CryptoEcPoint_Destroy(OH_CryptoEcPoint *point)](#oh_cryptoecpoint_destroy) | Destroys the elliptic curve point. |

## Enum type description

### CryptoAsymKey_ParamType

```c
enum CryptoAsymKey_ParamType
```

**Description**

Defines asymmetric key parameter types.

**Since**: 12

| Enum item | Description |
| -- | -- |
| CRYPTO_DSA_P_DATABLOB = 101 | Prime p of the DSA algorithm.<br>**Since**: 12 |
| CRYPTO_DSA_Q_DATABLOB = 102 | Sub-prime q of the DSA algorithm.<br>**Since**: 12 |
| CRYPTO_DSA_G_DATABLOB = 103 | Base g of the DSA algorithm.<br>**Since**: 12 |
| CRYPTO_DSA_SK_DATABLOB = 104 | Private key of the DSA algorithm.<br>**Since**: 12 |
| CRYPTO_DSA_PK_DATABLOB = 105 | Public key of the DSA algorithm.<br>**Since**: 12 |
| CRYPTO_ECC_FP_P_DATABLOB = 201 | Prime p of the elliptic curve (EC) prime field.<br>**Since**: 12 |
| CRYPTO_ECC_A_DATABLOB = 202 | First coefficient a of the elliptic curve.<br>**Since**: 12 |
| CRYPTO_ECC_B_DATABLOB = 203 | Second coefficient b of the elliptic curve.<br>**Since**: 12 |
| CRYPTO_ECC_G_X_DATABLOB = 204 | Affine x-coordinate of the base point g.<br>**Since**: 12 |
| CRYPTO_ECC_G_Y_DATABLOB = 205 | Affine y-coordinate of the base point g.<br>**Since**: 12 |
| CRYPTO_ECC_N_DATABLOB = 206 | Order of the base point g.<br>**Since**: 12 |
| CRYPTO_ECC_H_INT = 207 | Cofactor of the elliptic curve.<br>**Since**: 12 |
| CRYPTO_ECC_SK_DATABLOB = 208 | Private key value of the ECC private key.<br>**Since**: 12 |
| CRYPTO_ECC_PK_X_DATABLOB = 209 | Affine x-coordinate of the public key point in the ECC public key.<br>**Since**: 12 |
| CRYPTO_ECC_PK_Y_DATABLOB = 210 | Affine y-coordinate of the public key point in the ECC public key.<br>**Since**: 12 |
| CRYPTO_ECC_FIELD_TYPE_STR = 211 | Finite field type of the elliptic curve.<br>**Since**: 12 |
| CRYPTO_ECC_FIELD_SIZE_INT = 212 | Bit length of the finite field.<br>**Since**: 12 |
| CRYPTO_ECC_CURVE_NAME_STR = 213 | Curve name of the SECG standard.<br>**Since**: 12 |
| CRYPTO_RSA_N_DATABLOB = 301 | Modulus n of the RSA algorithm.<br>**Since**: 12 |
| CRYPTO_RSA_D_DATABLOB = 302 | Private key exponent d of the RSA algorithm.<br>**Since**: 12 |
| CRYPTO_RSA_E_DATABLOB = 303 | Public key exponent e of the RSA algorithm.<br>**Since**: 12 |
| CRYPTO_DH_P_DATABLOB = 401 | Prime p of the DH algorithm.<br>**Since**: 12 |
| CRYPTO_DH_G_DATABLOB = 402 | Generator g of the DH algorithm.<br>**Since**: 12 |
| CRYPTO_DH_L_INT = 403 | Bit length of the private key in the DH algorithm.<br>**Since**: 12 |
| CRYPTO_DH_SK_DATABLOB = 404 | Private key value of the DH private key.<br>**Since**: 12 |
| CRYPTO_DH_PK_DATABLOB = 405 | Public key value of the DH public key.<br>**Since**: 12 |
| CRYPTO_ED25519_SK_DATABLOB = 501 | Private key value of the ED25519 private key.<br>**Since**: 12 |
| CRYPTO_ED25519_PK_DATABLOB = 502 | Public key value of the ED25519 public key.<br>**Since**: 12 |
| CRYPTO_X25519_SK_DATABLOB = 601 | Private key value of the X25519 private key.<br>**Since**: 12 |
| CRYPTO_X25519_PK_DATABLOB = 602 | Public key value of the X25519 public key.<br>**Since**: 12 |

### Crypto_EncodingType

```c
enum Crypto_EncodingType
```

**Description**

Defines the encoding type.

**Since**: 12

| Enum item | Description |
| -- | -- |
| CRYPTO_PEM = 0 | PEM format.<br>**Since**: 12 |
| CRYPTO_DER = 1 | DER format.<br>**Since**: 12 |

### CryptoPrivKeyEncoding_ParamType

```c
enum CryptoPrivKeyEncoding_ParamType
```

**Description**

Defines private key encoding parameter types.

**Since**: 20

| Enum item | Description |
| -- | -- |
| CRYPTO_PRIVATE_KEY_ENCODING_PASSWORD_STR = 0 | Password string.<br>**Since**: 20 |
| CRYPTO_PRIVATE_KEY_ENCODING_SYMMETRIC_CIPHER_STR = 1 | Symmetric cipher algorithm name, set via [OH_CryptoPrivKeyEncodingParams_SetParam](capi-crypto-asym-key-h.md#oh_cryptoprivkeyencodingparams_setparam). Values: "DES-EDE3-CBC", "AES-128-CBC", "AES-192-CBC", "AES-256-CBC".<br>**Since**: 20 |

### CryptoAsymKeySpec_Type

```c
enum CryptoAsymKeySpec_Type
```

**Description**

Defines asymmetric key specification types.

**Since**: 20

| Enum item | Description |
| -- | -- |
| CRYPTO_ASYM_KEY_COMMON_PARAMS_SPEC = 0 | Common parameter specification.<br>**Since**: 20 |
| CRYPTO_ASYM_KEY_PRIVATE_KEY_SPEC = 1 | Private key specification.<br>**Since**: 20 |
| CRYPTO_ASYM_KEY_PUBLIC_KEY_SPEC = 2 | Public key specification.<br>**Since**: 20 |
| CRYPTO_ASYM_KEY_KEY_PAIR_SPEC = 3 | Key pair specification.<br>**Since**: 20 |


## Function description

### OH_CryptoAsymKeyGenerator_Create()

```c
OH_Crypto_ErrCode OH_CryptoAsymKeyGenerator_Create(const char *algoName, OH_CryptoAsymKeyGenerator **ctx)
```

**Description**

Creates an asymmetric key generator based on the given algorithm name.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *algoName | [in] Asymmetric key algorithm name. Cannot be NULL. Values: - RSA series since API version 12: "RSA512", "RSA768", "RSA1024", "RSA2048", "RSA3072", "RSA4096", "RSA8192". Multi-prime format is supported, e.g. "RSA1024\|PRIMES_3", "RSA4096\|PRIMES_4", "RSA8192\|PRIMES_5". - ECC series since API version 12: "ECC224", "ECC256", "ECC384", "ECC521". - ECC BrainPool series since API version 12: "ECC_BrainPoolP160r1", "ECC_BrainPoolP160t1", "ECC_BrainPoolP192r1", "ECC_BrainPoolP192t1", "ECC_BrainPoolP224r1", "ECC_BrainPoolP224t1", "ECC_BrainPoolP256r1", "ECC_BrainPoolP256t1", "ECC_BrainPoolP320r1", "ECC_BrainPoolP320t1", "ECC_BrainPoolP384r1", "ECC_BrainPoolP384t1", "ECC_BrainPoolP512r1", "ECC_BrainPoolP512t1". - "SM2_256", "Ed25519", "X25519" supported since API version 12. - DSA series since API version 12: "DSA1024", "DSA2048", "DSA3072". - DH series since API version 12: "DH_modp1536", "DH_modp2048", "DH_modp3072", "DH_modp4096", "DH_modp6144", "DH_modp8192", "DH_ffdhe2048", "DH_ffdhe3072", "DH_ffdhe4096", "DH_ffdhe6144", "DH_ffdhe8192". - "ECC_Secp256k1" supported since API version 14. - "ECC192" supported since API version 26.0.0. |
| [OH_CryptoAsymKeyGenerator](capi-cryptoasymkeyapi-oh-cryptoasymkeygenerator.md) **ctx | [out] Pointer to the asymmetric key generator pointer. ctx cannot be NULL, *ctx must be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_INVALID_PARAMS} if ctx or algoName is NULL.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if the algorithm is not supported.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory allocation fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if crypto operation fails.</li>          </ul> |

**Reference**:

[OH_CryptoAsymKeyGenerator_Generate](capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_generate) Generates an asymmetric key pair
[OH_CryptoAsymKeyGenerator_Convert](capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_convert) Converts asymmetric key data to a key pair


### OH_CryptoAsymKeyGenerator_Generate()

```c
OH_Crypto_ErrCode OH_CryptoAsymKeyGenerator_Generate(OH_CryptoAsymKeyGenerator *ctx, OH_CryptoKeyPair **keyCtx)
```

**Description**

Generates an asymmetric key pair.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoAsymKeyGenerator](capi-cryptoasymkeyapi-oh-cryptoasymkeygenerator.md) *ctx | [in] Asymmetric key generator. Cannot be NULL. |
| [OH_CryptoKeyPair](capi-cryptoasymkeyapi-oh-cryptokeypair.md) **keyCtx | [out] Pointer to the key pair pointer. keyCtx cannot be NULL, *keyCtx must be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_INVALID_PARAMS} if ctx or keyCtx is NULL.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if unsupported operation or algorithm.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory operation fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if crypto operation fails.</li>          </ul> |

### OH_CryptoAsymKeyGenerator_Convert()

```c
OH_Crypto_ErrCode OH_CryptoAsymKeyGenerator_Convert(OH_CryptoAsymKeyGenerator *ctx, Crypto_EncodingType type, Crypto_DataBlob *pubKeyData, Crypto_DataBlob *priKeyData, OH_CryptoKeyPair **keyCtx)
```

**Description**

Converts asymmetric key data to a key pair.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoAsymKeyGenerator](capi-cryptoasymkeyapi-oh-cryptoasymkeygenerator.md) *ctx | [in] Asymmetric key generator. Cannot be NULL. |
| [Crypto_EncodingType](capi-crypto-asym-key-h.md#crypto_encodingtype) type | [in] Encoding type. |
| Crypto_DataBlob *pubKeyData | [in] Public key data. Cannot be NULL at the same time as priKeyData. |
| Crypto_DataBlob *priKeyData | [in] Private key data. Cannot be NULL at the same time as pubKeyData. |
| [OH_CryptoKeyPair](capi-cryptoasymkeyapi-oh-cryptokeypair.md) **keyCtx | [out] Pointer to the key pair pointer. keyCtx cannot be NULL, *keyCtx must be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_INVALID_PARAMS} if ctx is NULL, pubKeyData and<br>           priKeyData are both NULL, keyCtx is NULL, or type is not a valid Crypto_EncodingType.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if the key format is not supported.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory allocation fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if key conversion fails. Possible causes:             key data is corrupted or not valid PEM/DER format, key data does not match the algorithm,             or the password for an encrypted private key is incorrect.</li>          </ul> |

### OH_CryptoAsymKeyGenerator_GetAlgoName()

```c
const char *OH_CryptoAsymKeyGenerator_GetAlgoName(OH_CryptoAsymKeyGenerator *ctx)
```

**Description**

Obtains the algorithm name of the asymmetric key generator.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoAsymKeyGenerator](capi-cryptoasymkeyapi-oh-cryptoasymkeygenerator.md) *ctx | [in] Asymmetric key generator. Cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| const char * | <ul>          <li>Returns the asymmetric key algorithm name. No need to free by the caller. Invalid after the generator is              destroyed.</li>          <li>Returns NULL if ctx is NULL.</li>          </ul> |

### OH_CryptoAsymKeyGenerator_Destroy()

```c
void OH_CryptoAsymKeyGenerator_Destroy(OH_CryptoAsymKeyGenerator *ctx)
```

**Description**

Destroys the asymmetric key generator.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoAsymKeyGenerator](capi-cryptoasymkeyapi-oh-cryptoasymkeygenerator.md) *ctx | [in] Asymmetric key generator. |

### OH_CryptoKeyPair_Destroy()

```c
void OH_CryptoKeyPair_Destroy(OH_CryptoKeyPair *keyCtx)
```

**Description**

Destroys the key pair.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoKeyPair](capi-cryptoasymkeyapi-oh-cryptokeypair.md) *keyCtx | [in] Key pair. |

### OH_CryptoKeyPair_GetPubKey()

```c
OH_CryptoPubKey *OH_CryptoKeyPair_GetPubKey(OH_CryptoKeyPair *keyCtx)
```

**Description**

Obtains the public key from the key pair.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoKeyPair](capi-cryptoasymkeyapi-oh-cryptokeypair.md) *keyCtx | [in] Key pair. Cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_CryptoPubKey *](capi-cryptoasymkeyapi-oh-cryptopubkey.md) | <ul>          <li>Returns the public key from the key pair. It is an internal reference and does not need to be destroyed            separately. Invalid after the key pair is destroyed.</li>          <li>Returns NULL if keyCtx is NULL or the public key does not exist.</li>          </ul> |

### OH_CryptoKeyPair_GetPrivKey()

```c
OH_CryptoPrivKey *OH_CryptoKeyPair_GetPrivKey(OH_CryptoKeyPair *keyCtx)
```

**Description**

Obtains the private key from the key pair.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoKeyPair](capi-cryptoasymkeyapi-oh-cryptokeypair.md) *keyCtx | [in] Key pair. Cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_CryptoPrivKey *](capi-cryptoasymkeyapi-oh-cryptoprivkey.md) | <ul>          <li>Returns the private key from the key pair. It is an internal reference and does not need to be destroyed            separately. Invalid after the key pair is destroyed.</li>          <li>Returns NULL if keyCtx is NULL or the private key does not exist.</li>          </ul> |

### OH_CryptoPubKey_Encode()

```c
OH_Crypto_ErrCode OH_CryptoPubKey_Encode(OH_CryptoPubKey *key, Crypto_EncodingType type, const char *encodingStandard, Crypto_DataBlob *out)
```

**Description**

Encodes the public key.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoPubKey](capi-cryptoasymkeyapi-oh-cryptopubkey.md) *key | [in] Public key. Cannot be NULL. |
| [Crypto_EncodingType](capi-crypto-asym-key-h.md#crypto_encodingtype) type | [in] Encoding type. |
| const char *encodingStandard | [in] Encoding standard. Supports "X509". Cannot be NULL. |
| Crypto_DataBlob *out | [out] Pointer to the Crypto_DataBlob structure for storing the encoding result. Cannot be NULL. Initialize out to {0} before calling. Do not pre-allocate out->data. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_INVALID_PARAMS} if key, out, or encodingStandard is NULL, type is<br>           not a valid Crypto_EncodingType, or the encoding standard is incompatible with the key type.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if the encoding format is not supported.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory allocation fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if encoding fails.</li>          </ul> |

### OH_CryptoPubKey_GetParam()

```c
OH_Crypto_ErrCode OH_CryptoPubKey_GetParam(OH_CryptoPubKey *key, CryptoAsymKey_ParamType item, Crypto_DataBlob *value)
```

**Description**

Obtains the specified parameter of the public key.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoPubKey](capi-cryptoasymkeyapi-oh-cryptopubkey.md) *key | [in] Public key. Cannot be NULL. |
| [CryptoAsymKey_ParamType](capi-crypto-asym-key-h.md#cryptoasymkey_paramtype) item | [in] Asymmetric key parameter type. |
| Crypto_DataBlob *value | [out] Pointer to the Crypto_DataBlob structure for storing the output data. Cannot be NULL. Initialize value to {0} before calling. Do not pre-allocate value->data. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_INVALID_PARAMS} if key or value is NULL, or the<br>           parameter type is not supported for the key algorithm.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if the parameter type is not supported.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory allocation fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if getting param fails.</li>          </ul> |

### OH_CryptoAsymKeyGenerator_SetPassword()

```c
OH_Crypto_ErrCode OH_CryptoAsymKeyGenerator_SetPassword(OH_CryptoAsymKeyGenerator *ctx, const unsigned char *password, uint32_t passwordLen)
```

**Description**

Sets the password for the asymmetric key generator. Call this method to set the password if you need to use [OH_CryptoAsymKeyGenerator_Convert](capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_convert) to convert encrypted private key data to a key pair.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoAsymKeyGenerator](capi-cryptoasymkeyapi-oh-cryptoasymkeygenerator.md) *ctx | [in] Asymmetric key generator. Cannot be NULL. |
| const unsigned char *password | [in] Password. This function performs a deep copy of the data in password. The caller can release password immediately after the function returns. Cannot be NULL. |
| uint32_t passwordLen | [in] Byte length of the password. Must be greater than 0. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if unsupported operation or algorithm.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory allocation fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_PARAMETER_CHECK_FAILED} if ctx or password is NULL,<br>        or passwordLen is 0.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if crypto operation fails.</li>          </ul> |

### OH_CryptoPrivKeyEncodingParams_Create()

```c
OH_Crypto_ErrCode OH_CryptoPrivKeyEncodingParams_Create(OH_CryptoPrivKeyEncodingParams **ctx)
```

**Description**

Creates private key encoding parameters.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoPrivKeyEncodingParams](capi-cryptoasymkeyapi-oh-cryptoprivkeyencodingparams.md) **ctx | [out] Pointer to the private key encoding parameters pointer. ctx cannot be NULL, *ctx must be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_PARAMETER_CHECK_FAILED} if ctx is NULL.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if unsupported operation or algorithm.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory allocation fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if crypto operation fails.</li>          </ul> |

**Reference**:

[OH_CryptoPrivKeyEncodingParams_SetParam](capi-crypto-asym-key-h.md#oh_cryptoprivkeyencodingparams_setparam) Sets private key encoding parameters


### OH_CryptoPrivKeyEncodingParams_SetParam()

```c
OH_Crypto_ErrCode OH_CryptoPrivKeyEncodingParams_SetParam(OH_CryptoPrivKeyEncodingParams *ctx, CryptoPrivKeyEncoding_ParamType type, Crypto_DataBlob *value)
```

**Description**

Sets private key encoding parameters.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoPrivKeyEncodingParams](capi-cryptoasymkeyapi-oh-cryptoprivkeyencodingparams.md) *ctx | [in] Private key encoding parameters. Cannot be NULL. |
| [CryptoPrivKeyEncoding_ParamType](capi-crypto-asym-key-h.md#cryptoprivkeyencoding_paramtype) type | [in] Private key encoding parameter type. |
| Crypto_DataBlob *value | [in] Private key encoding parameter value. This function performs a deep copy of the data in value. The caller can release value immediately after the function returns. Cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_PARAMETER_CHECK_FAILED} if ctx or value is NULL,<br>           value->data is NULL, value->len is 0, or type is unrecognized.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if unsupported operation or algorithm.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory allocation for deep copy fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if crypto operation fails.</li>          </ul> |

### OH_CryptoPrivKeyEncodingParams_Destroy()

```c
void OH_CryptoPrivKeyEncodingParams_Destroy(OH_CryptoPrivKeyEncodingParams *ctx)
```

**Description**

Destroys private key encoding parameters.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoPrivKeyEncodingParams](capi-cryptoasymkeyapi-oh-cryptoprivkeyencodingparams.md) *ctx | [in] Private key encoding parameters. |

### OH_CryptoPrivKey_Encode()

```c
OH_Crypto_ErrCode OH_CryptoPrivKey_Encode(OH_CryptoPrivKey *key, Crypto_EncodingType type, const char *encodingStandard, OH_CryptoPrivKeyEncodingParams *params, Crypto_DataBlob *out)
```

**Description**

Encodes the private key.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoPrivKey](capi-cryptoasymkeyapi-oh-cryptoprivkey.md) *key | [in] Private key. Cannot be NULL. |
| [Crypto_EncodingType](capi-crypto-asym-key-h.md#crypto_encodingtype) type | [in] Encoding type. |
| const char *encodingStandard | [in] Encoding standard. Supports "PKCS8" and "PKCS1". "PKCS1" is only supported for RSA private keys. Cannot be NULL. |
| [OH_CryptoPrivKeyEncodingParams](capi-cryptoasymkeyapi-oh-cryptoprivkeyencodingparams.md) *params | [in] Private key encoding parameters. Can be NULL. Set this parameter if the private key needs to be encrypted. |
| Crypto_DataBlob *out | [out] Pointer to the Crypto_DataBlob structure for storing the encoding result. Cannot be NULL. Initialize out to {0} before calling. Do not pre-allocate out->data. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_PARAMETER_CHECK_FAILED} if key, out, or encodingStandard is NULL,<br>           type is not a valid Crypto_EncodingType, or the encoding standard is incompatible<br>           with the key type.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if the encoding format is not supported.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory allocation fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if encoding fails.</li>          </ul> |

### OH_CryptoPrivKey_GetParam()

```c
OH_Crypto_ErrCode OH_CryptoPrivKey_GetParam(OH_CryptoPrivKey *key, CryptoAsymKey_ParamType item, Crypto_DataBlob *value)
```

**Description**

Obtains the specified parameter of the private key.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoPrivKey](capi-cryptoasymkeyapi-oh-cryptoprivkey.md) *key | [in] Private key. Cannot be NULL. |
| [CryptoAsymKey_ParamType](capi-crypto-asym-key-h.md#cryptoasymkey_paramtype) item | [in] Asymmetric key parameter type. |
| Crypto_DataBlob *value | [out] Pointer to the Crypto_DataBlob structure for storing the output data. Cannot be NULL. Initialize value to {0} before calling. Do not pre-allocate value->data. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_PARAMETER_CHECK_FAILED} if key or value is NULL, or<br>           the parameter type is not supported for the key algorithm.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if the parameter type is not supported.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory allocation fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if getting param fails.</li>          </ul> |

### OH_CryptoAsymKeySpec_GenEcCommonParamsSpec()

```c
OH_Crypto_ErrCode OH_CryptoAsymKeySpec_GenEcCommonParamsSpec(const char *curveName, OH_CryptoAsymKeySpec **spec)
```

**Description**

Generates EC common parameter specification.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *curveName | [in] NID (Name Identifier) string of the ECC curve. Cannot be NULL. e.g. "NID_X9_62_prime256v1", "NID_secp384r1", "NID_secp521r1", "NID_sm2". |
| [OH_CryptoAsymKeySpec](capi-cryptoasymkeyapi-oh-cryptoasymkeyspec.md) **spec | [out] Pointer to the asymmetric key specification pointer. spec cannot be NULL, *spec must be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_PARAMETER_CHECK_FAILED} if curveName or spec is NULL,<br>           or the curve name is not a valid elliptic curve.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if the curve is not supported.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory allocation fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if generating spec fails.</li>          </ul> |

### OH_CryptoAsymKeySpec_GenDhCommonParamsSpec()

```c
OH_Crypto_ErrCode OH_CryptoAsymKeySpec_GenDhCommonParamsSpec(int pLen, int skLen, OH_CryptoAsymKeySpec **spec)
```

**Description**

Generates DH common parameter specification.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| int pLen | [in] Bit length of prime p. |
| int skLen | [in] Bit length of the private key. |
| [OH_CryptoAsymKeySpec](capi-cryptoasymkeyapi-oh-cryptoasymkeyspec.md) **spec | [out] Pointer to the asymmetric key specification pointer. spec cannot be NULL, *spec must be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_PARAMETER_CHECK_FAILED} if spec is NULL,<br>           pLen is negative, skLen is negative, or skLen is greater than pLen.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if unsupported operation or algorithm.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory allocation fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if crypto operation fails.</li>          </ul> |

### OH_CryptoAsymKeySpec_Create()

```c
OH_Crypto_ErrCode OH_CryptoAsymKeySpec_Create(const char *algoName, CryptoAsymKeySpec_Type type, OH_CryptoAsymKeySpec **spec)
```

**Description**

Creates an asymmetric key specification based on the given algorithm name and specification type.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *algoName | [in] Asymmetric key specification algorithm name. Cannot be NULL. Values: - "RSA", "ECC", "DSA", "SM2", "Ed25519", "X25519", "DH" supported since API version 20. |
| [CryptoAsymKeySpec_Type](capi-crypto-asym-key-h.md#cryptoasymkeyspec_type) type | [in] Asymmetric key specification type. |
| [OH_CryptoAsymKeySpec](capi-cryptoasymkeyapi-oh-cryptoasymkeyspec.md) **spec | [out] Pointer to the asymmetric key specification pointer. spec cannot be NULL, *spec must be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_PARAMETER_CHECK_FAILED} if algoName or spec is NULL,<br>            algoName is not a supported algorithm name.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if unsupported operation or algorithm.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory allocation fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if crypto operation fails.</li>          </ul> |

### OH_CryptoAsymKeySpec_SetParam()

```c
OH_Crypto_ErrCode OH_CryptoAsymKeySpec_SetParam(OH_CryptoAsymKeySpec *spec, CryptoAsymKey_ParamType type, Crypto_DataBlob *value)
```

**Description**

Sets the specified parameter of the asymmetric key specification.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoAsymKeySpec](capi-cryptoasymkeyapi-oh-cryptoasymkeyspec.md) *spec | [in] Asymmetric key specification. Cannot be NULL. |
| [CryptoAsymKey_ParamType](capi-crypto-asym-key-h.md#cryptoasymkey_paramtype) type | [in] Asymmetric key parameter type. |
| Crypto_DataBlob *value | [in] Input data. This function performs a deep copy of the data in value. The caller can release value immediately after the function returns. Cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_PARAMETER_CHECK_FAILED} if spec or value is NULL,<br>           value->data is NULL, value->len is 0, or the parameter type is not<br>           supported for the algorithm.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if unsupported operation or algorithm.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory allocation for deep copy fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if crypto operation fails.</li>          </ul> |

### OH_CryptoAsymKeySpec_SetCommonParamsSpec()

```c
OH_Crypto_ErrCode OH_CryptoAsymKeySpec_SetCommonParamsSpec(OH_CryptoAsymKeySpec *spec, OH_CryptoAsymKeySpec *commonParamsSpec)
```

**Description**

Sets the common parameter specification into the asymmetric key specification.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoAsymKeySpec](capi-cryptoasymkeyapi-oh-cryptoasymkeyspec.md) *spec | [in] Asymmetric key specification. Cannot be NULL. |
| [OH_CryptoAsymKeySpec](capi-cryptoasymkeyapi-oh-cryptoasymkeyspec.md) *commonParamsSpec | [in] Common parameter specification. This function performs a deep copy of the data in commonParamsSpec. The caller can release commonParamsSpec immediately after the function returns. Cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_PARAMETER_CHECK_FAILED} if spec or commonParamsSpec is NULL.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if unsupported operation or algorithm.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory allocation fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if crypto operation fails.</li>          </ul> |

### OH_CryptoAsymKeySpec_GetParam()

```c
OH_Crypto_ErrCode OH_CryptoAsymKeySpec_GetParam(OH_CryptoAsymKeySpec *spec, CryptoAsymKey_ParamType type, Crypto_DataBlob *value)
```

**Description**

Obtains the specified parameter of the asymmetric key specification.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoAsymKeySpec](capi-cryptoasymkeyapi-oh-cryptoasymkeyspec.md) *spec | [in] Asymmetric key specification. Cannot be NULL. |
| [CryptoAsymKey_ParamType](capi-crypto-asym-key-h.md#cryptoasymkey_paramtype) type | [in] Asymmetric key parameter type. |
| Crypto_DataBlob *value | [out] Pointer to the Crypto_DataBlob structure for storing the output data. Cannot be NULL. Initialize value to {0} before calling. Do not pre-allocate value->data. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_PARAMETER_CHECK_FAILED} if spec or value is NULL, or<br>           the parameter type is not supported for the algorithm.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if unsupported operation or algorithm.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory allocation fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if crypto operation fails.</li>          </ul> |

### OH_CryptoAsymKeySpec_Destroy()

```c
void OH_CryptoAsymKeySpec_Destroy(OH_CryptoAsymKeySpec *spec)
```

**Description**

Destroys the asymmetric key specification.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoAsymKeySpec](capi-cryptoasymkeyapi-oh-cryptoasymkeyspec.md) *spec | [in] Asymmetric key specification. |

### OH_CryptoAsymKeyGeneratorWithSpec_Create()

```c
OH_Crypto_ErrCode OH_CryptoAsymKeyGeneratorWithSpec_Create(OH_CryptoAsymKeySpec *keySpec, OH_CryptoAsymKeyGeneratorWithSpec **generator)
```

**Description**

Creates a key generator based on the asymmetric key specification.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoAsymKeySpec](capi-cryptoasymkeyapi-oh-cryptoasymkeyspec.md) *keySpec | [in] Asymmetric key specification. Cannot be NULL. |
| [OH_CryptoAsymKeyGeneratorWithSpec](capi-cryptoasymkeyapi-oh-cryptoasymkeygeneratorwithspec.md) **generator | [out] Pointer to the specification-based asymmetric key generator pointer. generator cannot be NULL, *generator must be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_PARAMETER_CHECK_FAILED} if keySpec or generator is NULL,<br>           or key specification parameters are incomplete or invalid.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if the algorithm is not supported.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory allocation fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if creating generator fails.</li>          </ul> |

**Reference**:

[OH_CryptoAsymKeyGeneratorWithSpec_GenKeyPair](capi-crypto-asym-key-h.md#oh_cryptoasymkeygeneratorwithspec_genkeypair) Generates a key pair based on the asymmetric key specification


### OH_CryptoAsymKeyGeneratorWithSpec_GenKeyPair()

```c
OH_Crypto_ErrCode OH_CryptoAsymKeyGeneratorWithSpec_GenKeyPair(OH_CryptoAsymKeyGeneratorWithSpec *generator, OH_CryptoKeyPair **keyPair)
```

**Description**

Generates a key pair based on the asymmetric key specification.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoAsymKeyGeneratorWithSpec](capi-cryptoasymkeyapi-oh-cryptoasymkeygeneratorwithspec.md) *generator | [in] Specification-based asymmetric key generator. Cannot be NULL. |
| [OH_CryptoKeyPair](capi-cryptoasymkeyapi-oh-cryptokeypair.md) **keyPair | [out] Pointer to the key pair pointer. keyPair cannot be NULL, *keyPair must be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_PARAMETER_CHECK_FAILED} if generator or keyPair is NULL.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if the operation is not supported.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory allocation fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if generating key pair fails. Possible causes:             key specification parameters are incomplete or inconsistent.</li>          </ul> |

### OH_CryptoAsymKeyGeneratorWithSpec_Destroy()

```c
void OH_CryptoAsymKeyGeneratorWithSpec_Destroy(OH_CryptoAsymKeyGeneratorWithSpec *generator)
```

**Description**

Destroys the specification-based asymmetric key generator.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoAsymKeyGeneratorWithSpec](capi-cryptoasymkeyapi-oh-cryptoasymkeygeneratorwithspec.md) *generator | [in] Specification-based asymmetric key generator. |

### OH_CryptoEcPoint_Create()

```c
OH_Crypto_ErrCode OH_CryptoEcPoint_Create(const char *curveName, Crypto_DataBlob *ecKeyData, OH_CryptoEcPoint **point)
```

**Description**

Creates an elliptic curve point.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *curveName | [in] NID (Name Identifier) string of the elliptic curve. Cannot be NULL. e.g. "NID_X9_62_prime256v1", "NID_secp384r1", "NID_secp521r1", "NID_sm2". |
| Crypto_DataBlob *ecKeyData | [in] Elliptic curve point data. Supports "04 \|\| x \|\| y", "02 \|\| x", or "03 \|\| x" format. Can be NULL. If ecKeyData is NULL, an empty elliptic curve point specification is created. |
| [OH_CryptoEcPoint](capi-cryptoasymkeyapi-oh-cryptoecpoint.md) **point | [out] Pointer to the elliptic curve point pointer. point cannot be NULL, *point must be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_PARAMETER_CHECK_FAILED} if curveName or point is NULL,<br>           or the curve name is invalid.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if the curve is not supported.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory allocation fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if creating EC point fails. Possible causes:             the point data format is incorrect.</li>          </ul> |

**Reference**:

[OH_CryptoEcPoint_GetCoordinate](capi-crypto-asym-key-h.md#oh_cryptoecpoint_getcoordinate) Obtains the x and y coordinates of the elliptic curve point
[OH_CryptoEcPoint_SetCoordinate](capi-crypto-asym-key-h.md#oh_cryptoecpoint_setcoordinate) Sets the x and y coordinates of the elliptic curve point


### OH_CryptoEcPoint_GetCoordinate()

```c
OH_Crypto_ErrCode OH_CryptoEcPoint_GetCoordinate(OH_CryptoEcPoint *point, Crypto_DataBlob *x, Crypto_DataBlob *y)
```

**Description**

Obtains the x and y coordinates of the elliptic curve point.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoEcPoint](capi-cryptoasymkeyapi-oh-cryptoecpoint.md) *point | [in] Elliptic curve point. Cannot be NULL. |
| Crypto_DataBlob *x | [out] Pointer to the Crypto_DataBlob structure for storing the x-coordinate. Cannot be NULL. Initialize x to {0} before calling. Do not pre-allocate x->data. |
| Crypto_DataBlob *y | [out] Pointer to the Crypto_DataBlob structure for storing the y-coordinate. Cannot be NULL. Initialize y to {0} before calling. Do not pre-allocate y->data. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_PARAMETER_CHECK_FAILED} if point, x, or y is NULL.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if unsupported operation or algorithm.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory allocation fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if crypto operation fails.</li>          </ul> |

### OH_CryptoEcPoint_SetCoordinate()

```c
OH_Crypto_ErrCode OH_CryptoEcPoint_SetCoordinate(OH_CryptoEcPoint *point, Crypto_DataBlob *x, Crypto_DataBlob *y)
```

**Description**

Sets the x and y coordinates of the elliptic curve point.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoEcPoint](capi-cryptoasymkeyapi-oh-cryptoecpoint.md) *point | [in] Elliptic curve point. Cannot be NULL. |
| Crypto_DataBlob *x | [in] x-coordinate of the elliptic curve point. This function performs a deep copy of the data in x and y. The caller can release x and y immediately after the function returns. Cannot be NULL. |
| Crypto_DataBlob *y | [in] y-coordinate of the elliptic curve point. Cannot be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_PARAMETER_CHECK_FAILED} if point, x, or y is NULL.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if unsupported operation or algorithm.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory allocation for deep copy fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if crypto operation fails.</li>          </ul> |

**Reference**:

[OH_CryptoEcPoint_Encode](capi-crypto-asym-key-h.md#oh_cryptoecpoint_encode) Encodes the elliptic curve point to the specified format


### OH_CryptoEcPoint_Encode()

```c
OH_Crypto_ErrCode OH_CryptoEcPoint_Encode(OH_CryptoEcPoint *point, const char *format, Crypto_DataBlob *out)
```

**Description**

Encodes the elliptic curve point to the specified format.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoEcPoint](capi-cryptoasymkeyapi-oh-cryptoecpoint.md) *point | [in] Elliptic curve point. Cannot be NULL. |
| const char *format | [in] Encoding format. Cannot be NULL. Supports "UNCOMPRESSED" and "COMPRESSED". |
| Crypto_DataBlob *out | [out] Pointer to the Crypto_DataBlob structure for storing the encoded point data. Cannot be NULL. Initialize out to {0} before calling. Do not pre-allocate out->data. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_PARAMETER_CHECK_FAILED} if point, format, or out is NULL,<br>           or the format string is not a valid point format.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if the format is not supported.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory allocation fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if encoding fails. Possible causes:             the point is not a valid curve point.</li>          </ul> |

### OH_CryptoEcPoint_Destroy()

```c
void OH_CryptoEcPoint_Destroy(OH_CryptoEcPoint *point)
```

**Description**

Destroys the elliptic curve point.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoEcPoint](capi-cryptoasymkeyapi-oh-cryptoecpoint.md) *point | [in] Elliptic curve point. |


