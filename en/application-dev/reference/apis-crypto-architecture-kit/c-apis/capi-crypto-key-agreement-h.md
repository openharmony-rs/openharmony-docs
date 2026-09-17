# crypto_key_agreement.h

## Overview

Defines the key agreement interfaces.

**Include**: <CryptoArchitectureKit/crypto_key_agreement.h>

**Library**: libohcrypto.so

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 20

**Related module**: [CryptoKeyAgreementApi](capi-cryptokeyagreementapi.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_CryptoKeyAgreement](capi-cryptokeyagreementapi-oh-cryptokeyagreement.md) | OH_CryptoKeyAgreement | Key agreement structure, representing a key agreement context. |

### Function

| Name | Description |
| -- | -- |
| [OH_Crypto_ErrCode OH_CryptoKeyAgreement_Create(const char *algoName, OH_CryptoKeyAgreement **ctx)](#oh_cryptokeyagreement_create) | Creates a key agreement context based on the given algorithm name. |
| [OH_Crypto_ErrCode OH_CryptoKeyAgreement_GenerateSecret(OH_CryptoKeyAgreement *ctx, OH_CryptoPrivKey *privkey, OH_CryptoPubKey *pubkey, Crypto_DataBlob *secret)](#oh_cryptokeyagreement_generatesecret) | Generates a shared secret. |
| [void OH_CryptoKeyAgreement_Destroy(OH_CryptoKeyAgreement *ctx)](#oh_cryptokeyagreement_destroy) | Destroys the key agreement context. |

## Function description

### OH_CryptoKeyAgreement_Create()

```c
OH_Crypto_ErrCode OH_CryptoKeyAgreement_Create(const char *algoName, OH_CryptoKeyAgreement **ctx)
```

**Description**

Creates a key agreement context based on the given algorithm name.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *algoName | [in] Key agreement algorithm name. Cannot be NULL. Values: - ECDH series since API version 20: "ECC224", "ECC256", "ECC384", "ECC521". - ECDH BrainPool series since API version 20: "ECC_BrainPoolP160r1", "ECC_BrainPoolP160t1", "ECC_BrainPoolP192r1", "ECC_BrainPoolP192t1", "ECC_BrainPoolP224r1", "ECC_BrainPoolP224t1", "ECC_BrainPoolP256r1", "ECC_BrainPoolP256t1", "ECC_BrainPoolP320r1", "ECC_BrainPoolP320t1", "ECC_BrainPoolP384r1", "ECC_BrainPoolP384t1", "ECC_BrainPoolP512r1", "ECC_BrainPoolP512t1". - "ECC_Secp256k1" supported since API version 20. - "X25519" supported since API version 20. - DH series since API version 20: "DH_modp1536", "DH_modp2048", "DH_modp3072", "DH_modp4096", "DH_modp6144", "DH_modp8192", "DH_ffdhe2048", "DH_ffdhe3072", "DH_ffdhe4096", "DH_ffdhe6144", "DH_ffdhe8192". - "ECC192" supported since API version 26.0.0. |
| [OH_CryptoKeyAgreement](capi-cryptokeyagreementapi-oh-cryptokeyagreement.md) **ctx | [out] Pointer to the key agreement context pointer. ctx cannot be NULL, *ctx must be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_PARAMETER_CHECK_FAILED} if algoName or ctx is NULL.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if the algorithm is not supported.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory allocation fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if key agreement operation fails.</li>          </ul> |

**Reference**:

[OH_CryptoKeyAgreement_GenerateSecret](capi-crypto-key-agreement-h.md#oh_cryptokeyagreement_generatesecret) Generates a shared secret


### OH_CryptoKeyAgreement_GenerateSecret()

```c
OH_Crypto_ErrCode OH_CryptoKeyAgreement_GenerateSecret(OH_CryptoKeyAgreement *ctx, OH_CryptoPrivKey *privkey, OH_CryptoPubKey *pubkey, Crypto_DataBlob *secret)
```

**Description**

Generates a shared secret.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoKeyAgreement](capi-cryptokeyagreementapi-oh-cryptokeyagreement.md) *ctx | [in] Key agreement context. Cannot be NULL. |
| OH_CryptoPrivKey *privkey | [in] Private key. Cannot be NULL. |
| OH_CryptoPubKey *pubkey | [in] Public key. Cannot be NULL. |
| Crypto_DataBlob *secret | [out] Pointer to the Crypto_DataBlob structure for storing the shared secret. Cannot be NULL. Initialize secret to {0} before calling. Do not pre-allocate secret->data. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Crypto_ErrCode | <ul>          <li>{@link OH_Crypto_ErrCode#CRYPTO_SUCCESS} if the operation succeeds.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_PARAMETER_CHECK_FAILED} if ctx, privkey, pubkey, or secret is NULL.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_NOT_SUPPORTED} if the algorithm is not supported.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_MEMORY_ERROR} if memory allocation fails.</li><br>        <li>{@link OH_Crypto_ErrCode#CRYPTO_OPERTION_ERROR} if the key agreement operation fails.             Possible causes: the public key and private key do not belong to the same curve or             algorithm, or the public key data is invalid.</li>          </ul> |

### OH_CryptoKeyAgreement_Destroy()

```c
void OH_CryptoKeyAgreement_Destroy(OH_CryptoKeyAgreement *ctx)
```

**Description**

Destroys the key agreement context.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CryptoKeyAgreement](capi-cryptokeyagreementapi-oh-cryptokeyagreement.md) *ctx | [in] Key agreement context. |


