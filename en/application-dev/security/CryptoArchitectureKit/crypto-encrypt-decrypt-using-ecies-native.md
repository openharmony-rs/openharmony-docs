# Encryption and Decryption Using ECIES (C/C++)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

The ECIES algorithm is supported since API version 26.0.0. It is an encryption algorithm based on elliptic curve cryptography.

**Constraints**

- Key agreement algorithms ECC256, ECC384, and ECC521 are supported.
- Among key derivation algorithms, only X963KDF is supported. Digest algorithms SHA-1, SHA-256, SHA-384, and SHA-512 are supported.
- Symmetric encryption algorithms AES-128, AES-192, and AES-256 are supported.
- Among block cipher modes, only GCM is supported.

## Linking the Dynamic Library in the CMake Script
```txt
target_link_libraries(entry PUBLIC libohcrypto.so)
```

## Development Procedure

### Encryption

1. Call [OH_CryptoAsymKeyGenerator_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_create) and [OH_CryptoAsymKeyGenerator_Generate](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_generate) to generate a key pair using the ECC algorithm.

2. Call [OH_CryptoKeyAgreement_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-key-agreement-h.md#oh_cryptokeyagreement_create) and [OH_CryptoKeyAgreement_GenerateSecret](../../reference/apis-crypto-architecture-kit/capi-crypto-key-agreement-h.md#oh_cryptokeyagreement_generatesecret) to perform key agreement based on the local private key (KeyPair.priKey) and peer public key (KeyPair.pubKey) and return the shared key.

3. Call [OH_CryptoKdf_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-kdf-h.md#oh_cryptokdf_create) and [OH_CryptoKdf_Derive](../../reference/apis-crypto-architecture-kit/capi-crypto-kdf-h.md#oh_cryptokdf_derive) to derive a key based on the shared key (Secret) using the X963KDF algorithm and return the derived key.

4. Call [OH_CryptoSymCipher_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_create) with the string parameter **'AES128|GCM'** to create a **Cipher** instance for encryption. The key type is AES128, and the block cipher mode is GCM.

5. Call [OH_CryptoSymCipher_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_init) to initialize the **Cipher** instance. Specifically, set the mode to **CRYPTO_ENCRYPT_MODE** and specify the encryption key (**OH_CryptoSymKey**).

6. Call [OH_CryptoSymCipher_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_update) to update data (in plaintext) and obtain the encrypted data.

7. Call [OH_CryptoSymCipher_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_final) to obtain **authTag**.

   > **NOTE**
   >
   > If the GCM mode is used, **authTag** returned by **OH_CryptoSymCipher_Final()** will be used to initialize the authentication information during decryption and needs to be manually saved.
   >
   > In GCM mode, the algorithm library currently supports only 16‑byte values for **authTag**, which serve as authentication information for initialization during decryption..

### Decryption

1. Call [OH_CryptoAsymKeyGenerator_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_create) and [OH_CryptoAsymKeyGenerator_Generate](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_generate) to generate a key pair using the ECC algorithm.

2. Call [OH_CryptoKeyAgreement_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-key-agreement-h.md#oh_cryptokeyagreement_create) and [OH_CryptoKeyAgreement_GenerateSecret](../../reference/apis-crypto-architecture-kit/capi-crypto-key-agreement-h.md#oh_cryptokeyagreement_generatesecret) to perform key agreement based on the local private key (KeyPair.priKey) and peer public key (KeyPair.pubKey) and return the shared key.

3. Call [OH_CryptoKdf_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-kdf-h.md#oh_cryptokdf_create) and [OH_CryptoKdf_Derive](../../reference/apis-crypto-architecture-kit/capi-crypto-kdf-h.md#oh_cryptokdf_derive) to derive a key based on the shared key (Secret) using the X963KDF algorithm and return the derived key.

4. Call [OH_CryptoSymCipher_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_create) with the string parameter **'AES128|GCM'** to create a **Cipher** instance for decryption. The key type is AES128, and the block cipher mode is GCM.

5. Call [OH_CryptoSymCipher_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_init) to initialize the **Cipher** instance. Specifically, set the mode to **CRYPTO_DECRYPT_MODE** and key to **OH_CryptoSymKey** for decryption.

6. Call [OH_CryptoSymCipher_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_update) to update data (in ciphertext).

7. Call [OH_CryptoSymCipher_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_final) to obtain the decrypted data.

### Example Code

<!-- @[use_sample_native_test](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceECIES/entry/src/main/cpp/project/native_test.cpp) -->

``` C++
#include <cstring>
#include <hilog/log.h>
#include "CryptoArchitectureKit/crypto_architecture_kit.h"
#include "native_test.h"

namespace ECIES {
uint8_t aad[] = { 0x00, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07 };
uint8_t tag[] = { 0x00, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x0A, 0x0B, 0x0C, 0x0D, 0x0E, 0x0F };
const uint8_t ivSize = 16;
const uint8_t keySize = 16;

struct CryptoContext {
    OH_CryptoKeyPair *keyPair;
    OH_CryptoSymKey *symKey;
    Crypto_DataBlob secret;
    Crypto_DataBlob ivData; // The first 16 bytes of the secret are used as the IV, and shallow copy is performed.
};

OH_Crypto_ErrCode GenerateKeyPair(OH_CryptoKeyPair **keyPair)
{
    OH_CryptoAsymKeyGenerator *asyKeyGenerator = nullptr;
    OH_Crypto_ErrCode ret = OH_CryptoAsymKeyGenerator_Create("ECC256", &asyKeyGenerator);
    if (ret != CRYPTO_SUCCESS) {
        return ret;
    }
    ret = OH_CryptoAsymKeyGenerator_Generate(asyKeyGenerator, keyPair);
    OH_CryptoAsymKeyGenerator_Destroy(asyKeyGenerator);
    return ret;
}

OH_Crypto_ErrCode GenerateSecret(OH_CryptoPrivKey *privKey, OH_CryptoPubKey *pubKey, Crypto_DataBlob *secret)
{
    // EC key agreement.
    OH_CryptoKeyAgreement *keyAgreement = nullptr;
    OH_Crypto_ErrCode ret = OH_CryptoKeyAgreement_Create("ECC256", &keyAgreement);
    if (ret != CRYPTO_SUCCESS) {
        return ret;
    }
    ret = OH_CryptoKeyAgreement_GenerateSecret(keyAgreement, privKey, pubKey, secret);
    OH_CryptoKeyAgreement_Destroy(keyAgreement);
    return ret;
}

OH_Crypto_ErrCode KdfDeriveSecret(OH_CryptoPrivKey *privKey, OH_CryptoPubKey *pubKey, Crypto_DataBlob *secret)
{
    // Derive the key using X963KDF.
    OH_CryptoKdfParams *params = nullptr;
    OH_Crypto_ErrCode ret = OH_CryptoKdfParams_Create("X963KDF", &params);
    if (ret != CRYPTO_SUCCESS) {
        return ret;
    }
    Crypto_DataBlob keyData = {};
    ret = GenerateSecret(privKey, pubKey, &keyData);
    if (ret != CRYPTO_SUCCESS) {
        OH_CryptoKdfParams_Destroy(params);
        return ret;
    }
    ret = OH_CryptoKdfParams_SetParam(params, CRYPTO_KDF_KEY_DATABLOB, &keyData);
    OH_Crypto_FreeDataBlob(&keyData);
    if (ret != CRYPTO_SUCCESS) {
        OH_CryptoKdfParams_Destroy(params);
        return ret;
    }
    const char *info = "infostring";
    Crypto_DataBlob infoData = { .data = (uint8_t *)info, .len = strlen(info) };
    ret = OH_CryptoKdfParams_SetParam(params, CRYPTO_KDF_INFO_DATABLOB, &infoData);
    if (ret != CRYPTO_SUCCESS) {
        OH_CryptoKdfParams_Destroy(params);
        return ret;
    }
    OH_CryptoKdf *x963Kdf = nullptr;
    ret = OH_CryptoKdf_Create("X963KDF|SHA256", &x963Kdf);
    if (ret != CRYPTO_SUCCESS) {
        OH_CryptoKdfParams_Destroy(params);
        return ret;
    }
    ret = OH_CryptoKdf_Derive(x963Kdf, params, ivSize + keySize, secret);
    OH_CryptoKdf_Destroy(x963Kdf);
    OH_CryptoKdfParams_Destroy(params);
    return ret;
}

OH_Crypto_ErrCode GenerateSymKey(const Crypto_DataBlob *secret, OH_CryptoSymKey **symKey)
{
    OH_CryptoSymKeyGenerator *symKeyGenerator = nullptr;
    OH_Crypto_ErrCode ret = OH_CryptoSymKeyGenerator_Create("AES128", &symKeyGenerator);
    if (ret != CRYPTO_SUCCESS) {
        return ret;
    }
    Crypto_DataBlob keyData = { .data = secret->data + ivSize, .len = keySize };
    ret = OH_CryptoSymKeyGenerator_Convert(symKeyGenerator, &keyData, symKey);
    OH_CryptoSymKeyGenerator_Destroy(symKeyGenerator);
    return ret;
}

void SetCipherIvData(CryptoContext *ctx, Crypto_DataBlob *secret)
{
    ctx->ivData.data = secret->data;
    ctx->ivData.len = ivSize;
}

OH_Crypto_ErrCode SetCipherParams(OH_CryptoSymCipherParams *params, Crypto_DataBlob *ivBlob, Crypto_DataBlob *tagBlob)
{
    Crypto_DataBlob aadBlob = { .data = aad, .len = sizeof(aad) };
    OH_Crypto_ErrCode ret = OH_CryptoSymCipherParams_SetParam(params, CRYPTO_AAD_DATABLOB, &aadBlob);
    if (ret != CRYPTO_SUCCESS) {
        return ret;
    }
    ret = OH_CryptoSymCipherParams_SetParam(params, CRYPTO_IV_DATABLOB, ivBlob);
    if (ret != CRYPTO_SUCCESS) {
        return ret;
    }
    ret = OH_CryptoSymCipherParams_SetParam(params, CRYPTO_TAG_DATABLOB, tagBlob);
    return ret;
}

OH_Crypto_ErrCode Encrypt(CryptoContext *ctx, Crypto_DataBlob *plainText, Crypto_DataBlob *cipherText,
    Crypto_DataBlob *tagBlob)
{
    // AES-GCM symmetric encryption
    OH_CryptoSymCipherParams *params = nullptr;
    OH_Crypto_ErrCode ret = OH_CryptoSymCipherParams_Create(&params);
    if (ret != CRYPTO_SUCCESS) {
        return ret;
    }
    Crypto_DataBlob tagInit = { .data = tag, .len = sizeof(tag) };
    ret = SetCipherParams(params, &ctx->ivData, &tagInit);
    if (ret != CRYPTO_SUCCESS) {
        OH_CryptoSymCipherParams_Destroy(params);
        return ret;
    }
    OH_CryptoSymCipher *encCtx = nullptr;
    ret = OH_CryptoSymCipher_Create("AES128|GCM", &encCtx);
    if (ret != CRYPTO_SUCCESS) {
        OH_CryptoSymCipherParams_Destroy(params);
        return ret;
    }
    ret = OH_CryptoSymCipher_Init(encCtx, CRYPTO_ENCRYPT_MODE, ctx->symKey, params);
    OH_CryptoSymCipherParams_Destroy(params);
    if (ret != CRYPTO_SUCCESS) {
        OH_CryptoSymCipher_Destroy(encCtx);
        return ret;
    }
    ret = OH_CryptoSymCipher_Update(encCtx, plainText, cipherText);
    if (ret != CRYPTO_SUCCESS) {
        OH_CryptoSymCipher_Destroy(encCtx);
        return ret;
    }
    ret = OH_CryptoSymCipher_Final(encCtx, nullptr, tagBlob);
    OH_CryptoSymCipher_Destroy(encCtx);
    return ret;
}

OH_Crypto_ErrCode Decrypt(CryptoContext *ctx, Crypto_DataBlob *cipherText, Crypto_DataBlob *plainText,
    Crypto_DataBlob *tagBlob)
{
    // AES-GCM symmetric decryption.
    OH_CryptoSymCipherParams *params = nullptr;
    OH_Crypto_ErrCode ret = OH_CryptoSymCipherParams_Create(&params);
    if (ret != CRYPTO_SUCCESS) {
        return ret;
    }
    ret = SetCipherParams(params, &ctx->ivData, tagBlob);
    if (ret != CRYPTO_SUCCESS) {
        OH_CryptoSymCipherParams_Destroy(params);
        return ret;
    }
    OH_CryptoSymCipher *decCtx = nullptr;
    ret = OH_CryptoSymCipher_Create("AES128|GCM", &decCtx);
    if (ret != CRYPTO_SUCCESS) {
        OH_CryptoSymCipherParams_Destroy(params);
        return ret;
    }
    ret = OH_CryptoSymCipher_Init(decCtx, CRYPTO_DECRYPT_MODE, ctx->symKey, params);
    if (ret != CRYPTO_SUCCESS) {
        OH_CryptoSymCipher_Destroy(decCtx);
        OH_CryptoSymCipherParams_Destroy(params);
        return ret;
    }
    ret = OH_CryptoSymCipher_Final(decCtx, cipherText, plainText);
    OH_CryptoSymCipher_Destroy(decCtx);
    OH_CryptoSymCipherParams_Destroy(params);
    return ret;
}

void CleanupDataBlob(Crypto_DataBlob *plainData, Crypto_DataBlob *cipherData, Crypto_DataBlob *tagBlob)
{
    OH_Crypto_FreeDataBlob(plainData);
    OH_Crypto_FreeDataBlob(cipherData);
    OH_Crypto_FreeDataBlob(tagBlob);
}

void CleanupContext(CryptoContext *ctx)
{
    OH_Crypto_FreeDataBlob(&ctx->secret);
    OH_CryptoSymKey_Destroy(ctx->symKey);
    OH_CryptoKeyPair_Destroy(ctx->keyPair);
}
} // namespace ECIES

OH_Crypto_ErrCode doNativeTest()
{
    ECIES::CryptoContext ctxA = {};
    ECIES::CryptoContext ctxB = {};
    Crypto_DataBlob plainData = {};
    Crypto_DataBlob cipherData = {};
    Crypto_DataBlob tagBlob = {};
    OH_Crypto_ErrCode ret = CRYPTO_INVALID_PARAMS;
    do {
        ret = ECIES::GenerateKeyPair(&ctxA.keyPair);
        if (ret != CRYPTO_SUCCESS) {
            break;
        }
        ret = ECIES::GenerateKeyPair(&ctxB.keyPair);
        if (ret != CRYPTO_SUCCESS) {
            break;
        }

        // Key agreement at end A: private key of end A + public key of end B
        ret = ECIES::KdfDeriveSecret(OH_CryptoKeyPair_GetPrivKey(ctxA.keyPair),
            OH_CryptoKeyPair_GetPubKey(ctxB.keyPair), &ctxA.secret);
        if (ret != CRYPTO_SUCCESS) {
            break;
        }
        ret = ECIES::GenerateSymKey(&ctxA.secret, &ctxA.symKey);
        if (ret != CRYPTO_SUCCESS) {
            break;
        }
        // Use the first 16 bytes of the key derived at end A as the IV for encryption and decryption.
        ECIES::SetCipherIvData(&ctxA, &ctxA.secret);
        ECIES::SetCipherIvData(&ctxB, &ctxA.secret);
        // Encryption at end A.
        uint8_t message[] = { 0x00, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x0A, 0x0B };
        Crypto_DataBlob plainText = { .data = message, .len = sizeof(message) };
        ret = ECIES::Encrypt(&ctxA, &plainText, &cipherData, &tagBlob);
        if (ret != CRYPTO_SUCCESS) {
            break;
        }

        // Key agreement at end B: private key of end B + public key of end A
        ret = ECIES::KdfDeriveSecret(OH_CryptoKeyPair_GetPrivKey(ctxB.keyPair),
            OH_CryptoKeyPair_GetPubKey(ctxA.keyPair), &ctxB.secret);
        if (ret != CRYPTO_SUCCESS) {
            break;
        }
        ret = ECIES::GenerateSymKey(&ctxB.secret, &ctxB.symKey);
        if (ret != CRYPTO_SUCCESS) {
            break;
        }
        // Decryption at end B.
        ret = ECIES::Decrypt(&ctxB, &cipherData, &plainData, &tagBlob);
    } while (0);

    ECIES::CleanupDataBlob(&plainData, &cipherData, &tagBlob);
    ECIES::CleanupContext(&ctxA);
    ECIES::CleanupContext(&ctxB);
    OH_LOG_INFO(LOG_APP, "doNativeTest result: %{public}s", (ret == 0 ? "Success" : "Failed"));
    return ret;
}
```
