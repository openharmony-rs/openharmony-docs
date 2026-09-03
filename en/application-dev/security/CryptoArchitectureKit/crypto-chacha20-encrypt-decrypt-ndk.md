# Encryption and Decryption with a ChaCha20 Symmetric Key (C/C++)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=ee3aff3c192b61804c6eafd655527edff9eb980a translatedAt=2026-08-07T03:24:58.975Z pushedAt=2026-08-07T07:52:55.104Z -->

The algorithm library supports this algorithm since API version 22.

For the corresponding algorithm specifications, see [Symmetric Key Encryption/Decryption Algorithm Specifications: ChaCha20](crypto-encryption-decryption.md#chacha20).

## Adding the Dynamic Library in the CMake Script

```txt
target_link_libraries(entry PUBLIC libohcrypto.so)
```

## How to Develop

### Using ChaCha20 Symmetric Key Encryption/Decryption

**Creating an Object**

Call [OH_CryptoSymKeyGenerator_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_create) and [OH_CryptoSymKeyGenerator_Generate](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_generate) to generate a symmetric key (**OH_CryptoSymKey**) with the key algorithm being ChaCha20.

For how to generate a ChaCha20 symmetric key, refer to the following example and also see [Symmetric Key Generation and Conversion Specifications: ChaCha20](crypto-key-generation-conversion.md#chacha20) and [Randomly Generating a Symmetric Key](crypto-generate-sym-key-randomly-ndk.md). Note that the reference documents and examples may differ in input parameters.

**Encryption**

1. Call [OH_CryptoSymCipher_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_create) with the string parameter **'ChaCha20'** to create a **Cipher** instance for encryption. The key type is ChaCha20.

2. Call [OH_CryptoSymCipherParams_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_create) to create a parameter object and call [OH_CryptoSymCipherParams_SetParam](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_setparam) to set encryption parameters.

3. Call [OH_CryptoSymCipher_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_init) to initialize the **Cipher** instance. Specifically, set **mode** to **CRYPTO_ENCRYPT_MODE**, and specify the key for encryption (**OH_CryptoSymKey**) and the encryption parameter instance (**OH_CryptoSymCipherParams**).

4. Call [OH_CryptoSymCipher_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_update) to update data (in plaintext).

5. Call [OH_CryptoSymCipher_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_final) to obtain the encrypted data.

    > **NOTE**
    >
    > Since data has been passed in by update, pass in null in the data parameter here.
    >
    > The final output may be null. Before accessing the specific data, check whether the result is null to avoid exceptions.

6. Call [OH_CryptoSymKeyGenerator_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_destroy), [OH_CryptoSymCipher_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_destroy), and [OH_CryptoSymCipherParams_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_destroy) to destroy the objects.

**Decryption**

1. Call [OH_CryptoSymCipher_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_create) with the string parameter **'ChaCha20'** to create a **Cipher** instance for decryption. The key type is ChaCha20.

2. Call [OH_CryptoSymCipher_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_init) to initialize the **Cipher** instance. Specifically, set **mode** to **CRYPTO_DECRYPT_MODE**, and specify the decryption key (**OH_CryptoSymKey**) and the decryption parameter instance (**OH_CryptoSymCipherParams**).

3. Call [OH_CryptoSymCipher_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_update) to update data (in ciphertext).

4. Call [OH_CryptoSymCipher_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_final) to obtain the decrypted data.

<!-- @[encrypt_decrypt_chacha20_symkey](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceChaCha20/entry/src/main/cpp/types/project/chacha20_encryption_decryption.cpp) -->

``` C++
#include "CryptoArchitectureKit/crypto_common.h"
#include "CryptoArchitectureKit/crypto_sym_cipher.h"
#include <cstring>
#include "file.h"

// Set the parameter.
static OH_Crypto_ErrCode doChaCha20SetParams(Crypto_DataBlob *ivBlob, OH_CryptoSymCipherParams **params)
{
    OH_Crypto_ErrCode ret = OH_CryptoSymCipherParams_Create(params);
    if (ret != CRYPTO_SUCCESS) {
        return ret;
    }
    ret = OH_CryptoSymCipherParams_SetParam(*params, CRYPTO_IV_DATABLOB, ivBlob);
    if (ret != CRYPTO_SUCCESS) {
        OH_CryptoSymCipherParams_Destroy(*params);
        *params = nullptr;
        return ret;
    }
    return ret;
}

// Encrypt data.
static OH_Crypto_ErrCode doChaCha20Encrypt(OH_CryptoSymKey *keyCtx, OH_CryptoSymCipherParams *params,
    Crypto_DataBlob *msgBlob, Crypto_DataBlob *encData)
{
    OH_CryptoSymCipher *encCtx = nullptr;
    OH_Crypto_ErrCode ret = OH_CryptoSymCipher_Create("ChaCha20", &encCtx);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymCipher_Init(encCtx, CRYPTO_ENCRYPT_MODE, keyCtx, params);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymCipher_Final(encCtx, msgBlob, encData);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }

end:
    OH_CryptoSymCipher_Destroy(encCtx);
    return ret;
}

// Decrypt data.
static OH_Crypto_ErrCode doChaCha20Decrypt(OH_CryptoSymKey *keyCtx, OH_CryptoSymCipherParams *params,
    Crypto_DataBlob *encData, Crypto_DataBlob *decData)
{
    OH_CryptoSymCipher *decCtx = nullptr;
    OH_Crypto_ErrCode ret = OH_CryptoSymCipher_Create("ChaCha20", &decCtx);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymCipher_Init(decCtx, CRYPTO_DECRYPT_MODE, keyCtx, params); // The params value must be the same as that used in encryption.
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymCipher_Final(decCtx, encData, decData);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }

end:
    OH_CryptoSymCipher_Destroy(decCtx);
    return ret;
}

OH_Crypto_ErrCode doTestChaCha20()
{
    OH_CryptoSymKeyGenerator *genCtx = nullptr;
    OH_CryptoSymKey *keyCtx = nullptr;
    OH_CryptoSymCipherParams *params = nullptr;
    Crypto_DataBlob encData = {.data = nullptr, .len = 0};
    Crypto_DataBlob decData = {.data = nullptr, .len = 0};
    char *plainText = const_cast<char *>("this is test!");
    Crypto_DataBlob msgBlob = {.data = (uint8_t *)(plainText), .len = strlen(plainText)};
    uint8_t iv[16] = {1, 2, 4, 12, 3, 4, 2, 3, 3, 2, 0, 4, 3, 1, 0, 10}; // The iv value here is for reference only. You can use secure random numbers to generate it.
    Crypto_DataBlob ivBlob = {.data = iv, .len = sizeof(iv)};
    // Generate a symmetric key.
    OH_Crypto_ErrCode ret = OH_CryptoSymKeyGenerator_Create("ChaCha20", &genCtx);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymKeyGenerator_Generate(genCtx, &keyCtx);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }

    // Set the parameter.
    ret = doChaCha20SetParams(&ivBlob, &params);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }

    // Encrypt data.
    ret = doChaCha20Encrypt(keyCtx, params, &msgBlob, &encData);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }

    // Decrypt data.
    ret = doChaCha20Decrypt(keyCtx, params, &encData, &decData);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }

end:
    OH_CryptoSymCipherParams_Destroy(params);
    OH_CryptoSymKeyGenerator_Destroy(genCtx);
    OH_CryptoSymKey_Destroy(keyCtx);
    OH_Crypto_FreeDataBlob(&encData);
    OH_Crypto_FreeDataBlob(&decData);
    return ret;
}
```

### Using ChaCha20 Symmetric Key (Poly1305 Mode) Encryption/Decryption

**Creating an Object**

Call [OH_CryptoSymKeyGenerator_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_create) and [OH_CryptoSymKeyGenerator_Generate](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_generate) to generate a symmetric key (OH_CryptoSymKey) with the key algorithm ChaCha20.

For how to generate a ChaCha20 symmetric key, refer to the following example and also see [Symmetric Key Generation and Conversion Specifications: ChaCha20](crypto-key-generation-conversion.md#chacha20) and [Randomly Generating a Symmetric Key](crypto-generate-sym-key-randomly-ndk.md). Note that the reference documents and examples may differ in input parameters.

**Encryption**

1. Call [OH_CryptoSymCipher_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_create) with the string parameter **'ChaCha20|Poly1305'** to create a Cipher instance with the symmetric key type ChaCha20 and mode Poly1305 for encryption.

2. Call [OH_CryptoSymCipherParams_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_create) to create a parameter object, and call [OH_CryptoSymCipherParams_SetParam](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_setparam) to set the corresponding encryption parameters.

3. Call [OH_CryptoSymCipher_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_init) to set the mode to encryption (CRYPTO_ENCRYPT_MODE), specify the encryption key (OH_CryptoSymKey) and the encryption parameters (OH_CryptoSymCipherParams) for Poly1305 mode, and initialize the encryption Cipher instance.

4. Call [OH_CryptoSymCipher_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_update) to update data (plaintext).

5. Call [OH_CryptoSymCipher_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_final) to obtain the encrypted data.

    > **NOTE**
    >
    > Since data has been passed in by update, pass in null in the data parameter here.
    >
    > The final output may be null. Before accessing the specific data, check whether the result is null to avoid exceptions.

6. Use [OH_CryptoSymCipherParams_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_create) to create Params, and use [OH_CryptoSymCipherParams_SetParam](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_setparam) to set authTag as the authentication information for decryption. In Poly1305 mode, extract the last 16 bytes from the encrypted data as the authentication information for decryption initialization.

7. Call [OH_CryptoSymKeyGenerator_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_destroy), [OH_CryptoSymCipher_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_destroy), and [OH_CryptoSymCipherParams_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_destroy) to destroy the objects.

**Decryption**

1. Call [OH_CryptoSymCipher_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_create) with the string parameter **'ChaCha20|Poly1305'** to create a Cipher instance with the symmetric key type ChaCha20 and mode Poly1305 for decryption.

2. Call [OH_CryptoSymCipher_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_init) to set the mode to decryption (CRYPTO_DECRYPT_MODE), specify the decryption key (OH_CryptoSymKey) and the decryption parameters (OH_CryptoSymCipherParams) for Poly1305 mode, and initialize the decryption Cipher instance.

3. Call [OH_CryptoSymCipher_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_update) to update data (ciphertext).

4. Call [OH_CryptoSymCipher_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_final) to obtain the decrypted data.

<!-- @[poly1305_encrypt_decrypt_chacha20_symkey](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceChaCha20/entry/src/main/cpp/types/project/chacha20_poly1305_encryption_decryption.cpp) -->

``` C++
#include "CryptoArchitectureKit/crypto_common.h"
#include "CryptoArchitectureKit/crypto_sym_cipher.h"
#include <cstring>
#include "file.h"

// Parameter assignment function.
static OH_Crypto_ErrCode doChaCha20Poly1305SetParams(Crypto_DataBlob *ivData, Crypto_DataBlob *aadData,
    Crypto_DataBlob *tagData, OH_CryptoSymCipherParams **params)
{
    OH_Crypto_ErrCode ret = OH_CryptoSymCipherParams_Create(params);
    if (ret != CRYPTO_SUCCESS) {
        return ret;
    }
    ret = OH_CryptoSymCipherParams_SetParam(*params, CRYPTO_IV_DATABLOB, ivData);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymCipherParams_SetParam(*params, CRYPTO_AAD_DATABLOB, aadData);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymCipherParams_SetParam(*params, CRYPTO_TAG_DATABLOB, tagData);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    return ret;

end:
    OH_CryptoSymCipherParams_Destroy(*params);
    *params = nullptr;
    return ret;
}

// Encryption function.
static OH_Crypto_ErrCode doChaCha20Poly1305Encrypt(OH_CryptoSymKey *keyCtx, OH_CryptoSymCipherParams *params,
    Crypto_DataBlob *msgBlob, Crypto_DataBlob *outUpdate, Crypto_DataBlob *tagOutPut)
{
    OH_CryptoSymCipher *encCtx = nullptr;
    OH_Crypto_ErrCode ret = OH_CryptoSymCipher_Create("ChaCha20|Poly1305", &encCtx);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymCipher_Init(encCtx, CRYPTO_ENCRYPT_MODE, keyCtx, params);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymCipher_Update(encCtx, msgBlob, outUpdate);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymCipher_Final(encCtx, nullptr, tagOutPut);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }

end:
    OH_CryptoSymCipher_Destroy(encCtx);
    return ret;
}

// Decryption function.
static OH_Crypto_ErrCode doChaCha20Poly1305Decrypt(OH_CryptoSymKey *keyCtx, OH_CryptoSymCipherParams *params,
    Crypto_DataBlob *tagOutPut, Crypto_DataBlob *outUpdate, Crypto_DataBlob *decUpdate)
{
    OH_CryptoSymCipher *decCtx = nullptr;
    OH_Crypto_ErrCode ret = OH_CryptoSymCipherParams_SetParam(params, CRYPTO_TAG_DATABLOB, tagOutPut);
    if (ret != CRYPTO_SUCCESS) {
        return ret;
    }
    ret = OH_CryptoSymCipher_Create("ChaCha20|Poly1305", &decCtx);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymCipher_Init(decCtx, CRYPTO_DECRYPT_MODE, keyCtx, params);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymCipher_Final(decCtx, outUpdate, decUpdate);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }

end:
    OH_CryptoSymCipher_Destroy(decCtx);
    return ret;
}

OH_Crypto_ErrCode doTestChaCha20Poly1305()
{
    OH_CryptoSymKeyGenerator *genCtx = nullptr;
    OH_CryptoSymKey *keyCtx = nullptr;
    OH_CryptoSymCipherParams *params = nullptr;

    Crypto_DataBlob outUpdate = {.data = nullptr, .len = 0};
    Crypto_DataBlob decUpdate = {.data = nullptr, .len = 0};

    uint8_t aad[8] = {1, 2, 3, 4, 5, 6, 7, 8};
    uint8_t tag[16] = {0};
    uint8_t iv[12] = {1, 2, 4, 12, 3, 4, 2, 3, 3, 2, 0, 4}; // The IV is generated using a secure random number.
    Crypto_DataBlob ivData = {.data = iv, .len = sizeof(iv)};
    Crypto_DataBlob aadData = {.data = aad, .len = sizeof(aad)};
    Crypto_DataBlob tagData = {.data = tag, .len = sizeof(tag)};
    Crypto_DataBlob tagOutPut = {.data = nullptr, .len = 0};
    char *plainText = const_cast<char *>("this is test!");
    Crypto_DataBlob msgBlob = {.data = (uint8_t *)(plainText), .len = strlen(plainText)};
    OH_Crypto_ErrCode ret = OH_CryptoSymKeyGenerator_Create("ChaCha20", &genCtx);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymKeyGenerator_Generate(genCtx, &keyCtx);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }

    // Assign parameters.
    ret = doChaCha20Poly1305SetParams(&ivData, &aadData, &tagData, &params);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }

    // Encrypt.
    ret = doChaCha20Poly1305Encrypt(keyCtx, params, &msgBlob, &outUpdate, &tagOutPut);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }

    // Decrypt.
    ret = doChaCha20Poly1305Decrypt(keyCtx, params, &tagOutPut, &outUpdate, &decUpdate);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }

    // Release resources.
end:
    OH_CryptoSymCipherParams_Destroy(params);
    OH_CryptoSymKeyGenerator_Destroy(genCtx);
    OH_CryptoSymKey_Destroy(keyCtx);
    OH_Crypto_FreeDataBlob(&outUpdate);
    OH_Crypto_FreeDataBlob(&decUpdate);
    OH_Crypto_FreeDataBlob(&tagOutPut);
    return ret;
}
```

<!--no_check-->