# crypto_key_agreement.h

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=76caeef80126e754bb89b8cf8b2b7380f3d3d3a7 translatedAt=2026-09-02T07:17:30.327Z pushedAt=2026-09-04T03:49:32.789Z -->

## Overview

Defines key agreement APIs.

**Header file**: <CryptoArchitectureKit/crypto_key_agreement.h>

**Library**: libohcrypto.so

**System capability**: SystemCapability.Security.CryptoFramework

**Since**: 20

**Related module**: [CryptoKeyAgreementApi](capi-cryptokeyagreementapi.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_CryptoKeyAgreement](capi-cryptokeyagreementapi-oh-cryptokeyagreement.md) | OH_CryptoKeyAgreement | Defines a struct for key agreement, which indicates the key agreement context. |

### Functions

| Name| Description|
| -- | -- |
| [OH_Crypto_ErrCode OH_CryptoKeyAgreement_Create(const char *algoName, OH_CryptoKeyAgreement **ctx)](#oh_cryptokeyagreement_create) | Creates a key agreement context based on the given algorithm name.<br> Note: The created resource must be destroyed by calling [OH_CryptoKeyAgreement_Destroy](capi-crypto-key-agreement-h.md#oh_cryptokeyagreement_destroy).  |
| [OH_Crypto_ErrCode OH_CryptoKeyAgreement_GenerateSecret(OH_CryptoKeyAgreement *ctx, OH_CryptoPrivKey *privkey, OH_CryptoPubKey *pubkey, Crypto_DataBlob *secret)](#oh_cryptokeyagreement_generatesecret) | Generates a shared secret value.<br> Note: After the use is complete, the memory for storing the **secret** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob).  |
| [void OH_CryptoKeyAgreement_Destroy(OH_CryptoKeyAgreement *ctx)](#oh_cryptokeyagreement_destroy) | Destroys the key agreement context. |

## Function Description

### OH_CryptoKeyAgreement_Create()

```c
OH_Crypto_ErrCode OH_CryptoKeyAgreement_Create(const char *algoName, OH_CryptoKeyAgreement **ctx)
```

**Description**

Creates a key agreement context based on the given algorithm name.

Note: The created resource must be destroyed by calling [OH_CryptoKeyAgreement_Destroy](capi-crypto-key-agreement-h.md#oh_cryptokeyagreement_destroy).

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| const char *algoName | Input parameter, indicating the key agreement algorithm name, which cannot be null. The options are as follows:<br>- ECDH algorithms supported since API version 20: **ECC224**, **ECC256**, **ECC384**, and **ECC521**.<br>- ECDH BrainPool algorithms supported since API version 20: **ECC_BrainPoolP160r1**, **ECC_BrainPoolP160t1**, **ECC_BrainPoolP192r1**, **ECC_BrainPoolP192t1**, **ECC_BrainPoolP224r1**, **ECC_BrainPoolP224t1**, **ECC_BrainPoolP256r1**, **ECC_BrainPoolP256t1**, **ECC_BrainPoolP320r1**, **ECC_BrainPoolP320t1**, **ECC_BrainPoolP384r1**, **ECC_BrainPoolP384t1**, **ECC_BrainPoolP512r1**, and **ECC_BrainPoolP512t1**.<br>- Since API version 20, **ECC_Secp256k1** is supported.<br>- Since API version 20, **X25519** is supported.<br>-  DH algorithms supported since API version 20: **DH_modp1536**, **DH_modp2048**, **DH_modp3072**, **DH_modp4096**, **DH_modp6144**, **DH_modp8192**, **DH_ffdhe2048**, **DH_ffdhe3072**, **DH_ffdhe4096**, **DH_ffdhe6144**, and **DH_ffdhe8192**.<br>- Since API version 26.0.0, **ECC192** is supported. |
| [OH_CryptoKeyAgreement](capi-cryptokeyagreementapi-oh-cryptokeyagreement.md) **ctx | Output parameter, indicating a pointer to the key agreement context. The value of **ctx** cannot be null, but the value of ***ctx** must be null. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: **algoName** or **ctx** is **NULL**.<br>**CRYPTO_NOT_SUPPORTED**: The algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation fails.<br>**CRYPTO_OPERTION_ERROR**: Key agreement fails. |

**Reference**

[OH_CryptoKeyAgreement_GenerateSecret](capi-crypto-key-agreement-h.md#oh_cryptokeyagreement_generatesecret) for generating a shared secret value.


### OH_CryptoKeyAgreement_GenerateSecret()

```c
OH_Crypto_ErrCode OH_CryptoKeyAgreement_GenerateSecret(OH_CryptoKeyAgreement *ctx, OH_CryptoPrivKey *privkey, OH_CryptoPubKey *pubkey, Crypto_DataBlob *secret)
```

**Description**

Generates a shared secret value.

Note: After the use is complete, the memory for storing the **secret** parameter must be released by calling [OH_Crypto_FreeDataBlob](capi-crypto-common-h.md#oh_crypto_freedatablob).

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoKeyAgreement](capi-cryptokeyagreementapi-oh-cryptokeyagreement.md) *ctx | Input parameter, indicating a pointer to the key agreement context. The value cannot be null. |
| [OH_CryptoPrivKey](capi-cryptoasymkeyapi-oh-cryptoprivkey.md) *privkey | Input parameter, indicating a private key. The value cannot be null. |
| [OH_CryptoPubKey](capi-cryptoasymkeyapi-oh-cryptopubkey.md) *pubkey | Input parameter, indicating a public key. The value cannot be null. |
| [Crypto_DataBlob](capi-cryptocommonapi-crypto-datablob.md) *secret | Output parameter, indicating a pointer to the **Crypto_DataBlob** struct used to store the shared secret value. The value cannot be null. Before calling this method, initialize **secret** to 0. Do not set the **data** field of **secret**. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Crypto_ErrCode](capi-crypto-common-h.md#oh_crypto_errcode) | **CRYPTO_SUCCESS**: The operation is successful.<br>**CRYPTO_PARAMETER_CHECK_FAILED**: **ctx**, **privkey**, **pubkey**, or **secret** is null.<br>**CRYPTO_NOT_SUPPORTED**: The algorithm is not supported.<br>**CRYPTO_MEMORY_ERROR**: Memory allocation fails.<br>**CRYPTO_OPERTION_ERROR**: The key agreement operation fails. Possible causes: The public key and private key do not belong to the same curve or algorithm, or the public key data is invalid. |

### OH_CryptoKeyAgreement_Destroy()

```c
void OH_CryptoKeyAgreement_Destroy(OH_CryptoKeyAgreement *ctx)
```

**Description**

Destroys the key agreement context.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_CryptoKeyAgreement](capi-cryptokeyagreementapi-oh-cryptokeyagreement.md) *ctx | Input parameter, indicating a pointer to the key agreement context. |


