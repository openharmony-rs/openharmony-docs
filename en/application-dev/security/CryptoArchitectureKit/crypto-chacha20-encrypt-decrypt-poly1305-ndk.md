# Encryption and Decryption with a ChaCha20 Symmetric Key Pair (Poly1305) (C/C++)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

The Crypto framework supports this algorithm since API version 22.

For details about the algorithm specifications, see [ChaCha20](crypto-sym-encrypt-decrypt-spec.md#chacha20).

## Adding the Dynamic Library in the CMake Script
```txt
target_link_libraries(entry PUBLIC libohcrypto.so)
```
## How to Develop

**Creating an Object**

Call [OH_CryptoSymKeyGenerator_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_create) and [OH_CryptoSymKeyGenerator_Generate](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_generate) to generate a symmetric key (**OH_CryptoSymKey**) with the key algorithm being ChaCha20.
   
   For details about how to generate a ChaCha20 symmetric key, see the following example. To learn more, see [Symmetric Key Generation and Conversion Specifications: ChaCha20](crypto-sym-key-generation-conversion-spec.md#chacha20) and [Randomly Generating a Symmetric Key](crypto-generate-sym-key-randomly-ndk.md). There may be differences between the input parameters in the reference documents and those in the following example.

**Encryption**

1. Call [OH_CryptoSymCipher_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_create) with the string parameter **'ChaCha20|Poly1305'** to create a **Cipher** instance for encryption. The key type is ChaCha20, and the mode is Poly1305.

2. Call [OH_CryptoSymCipherParams_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_create) to create a parameter object and call [OH_CryptoSymCipherParams_SetParam](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_setparam) to set encryption parameters.

3. Call [OH_CryptoSymCipher_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_init) to initialize the **Cipher** instance. Specifically, set **mode** to **CRYPTO_ENCRYPT_MODE**, and specify the key for encryption (**OH_CryptoSymKey**) and the encryption parameter instance (**OH_CryptoSymCipherParams**) corresponding to the Poly1305 mode.

4. Call [OH_CryptoSymCipher_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_update) to update data (in plaintext).

5. Call [OH_CryptoSymCipher_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_final) to obtain the encrypted data.

    > **NOTE**
    >
    > If data has been passed in by **Cipher.update**, pass in **null** in the **data** parameter of **Cipher.doFinal**.
    >
    > The output of **Cipher.doFinal** may be **null**. To avoid exceptions, always check whether the result is **null** before accessing specific data.

6. Call [OH_CryptoSymCipherParams_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_create) to create a **Params** instance, and call [OH_CryptoSymCipherParams_SetParam](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_setparam) to set **authTag** as the authentication information for decryption. In Poly1305 mode, extract the last 16 bytes from the encrypted data as the authentication information for initializing the **Cipher** instance in decryption.

7. Call [OH_CryptoSymKeyGenerator_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_destroy), [OH_CryptoSymCipher_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_destroy), and [OH_CryptoSymCipherParams_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_destroy) to destroy the objects.

**Decryption**

1. Call [OH_CryptoSymCipher_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_create) with the string parameter **'ChaCha20|Poly1305'** to create a **Cipher** instance for decryption. The key type is ChaCha20, and the mode is Poly1305.

2. Call [OH_CryptoSymCipher_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_init) to initialize the **Cipher** instance. Specifically, set **mode** to **CRYPTO_DECRYPT_MODE**, and specify the decryption key (**OH_CryptoSymKey**) and the decryption parameter instance (**OH_CryptoSymCipherParams**) corresponding to the Poly1305 mode.

3. Call [OH_CryptoSymCipher_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_update) to update data (in ciphertext).

4. Call [OH_CryptoSymCipher_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_final) to obtain the decrypted data.

```c++
#include "CryptoArchitectureKit/crypto_common.h"
#include "CryptoArchitectureKit/crypto_sym_cipher.h"
#include <string.h>

static OH_Crypto_ErrCode doTestChaCha20Poly1305()
{
    OH_CryptoSymKeyGenerator *genCtx = nullptr;
    OH_CryptoSymCipher *encCtx = nullptr;
    OH_CryptoSymCipher *decCtx = nullptr;
    OH_CryptoSymKey *keyCtx = nullptr;
    OH_CryptoSymCipherParams *params = nullptr;

    Crypto_DataBlob outUpdate = {.data = nullptr, .len = 0};
    Crypto_DataBlob decUpdate = {.data = nullptr, .len = 0};

    uint8_t aad[8] = {1, 2, 3, 4, 5, 6, 7, 8};
    uint8_t tag[16] = {0};
    uint8_t iv[16] = {1, 2, 4, 12, 3, 4, 2, 3, 3, 2, 0, 4, 2, 4, 12, 3}; // iv is generated from an array of secure random numbers.
    Crypto_DataBlob ivData = {.data = iv, .len = sizeof(iv)};
    Crypto_DataBlob aadData = {.data = aad, .len = sizeof(aad)};
    Crypto_DataBlob tagData = {.data = tag, .len = sizeof(tag)};
    Crypto_DataBlob tagOutPut = {.data = nullptr, .len = 0};
    char *plainText = const_cast<char *>("this is test!");
    Crypto_DataBlob msgBlob = {.data = (uint8_t *)(plainText), .len = strlen(plainText)};
    // Generate a symmetric key.
    OH_Crypto_ErrCode ret;
    ret = OH_CryptoSymKeyGenerator_Create("ChaCha20", &genCtx);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymKeyGenerator_Generate(genCtx, &keyCtx);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }

    // Set parameters.
    ret = OH_CryptoSymCipherParams_Create(&params);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymCipherParams_SetParam(params, CRYPTO_IV_DATABLOB, &ivData);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymCipherParams_SetParam(params, CRYPTO_AAD_DATABLOB, &aadData);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymCipherParams_SetParam(params, CRYPTO_TAG_DATABLOB, &tagData);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }

    // Encrypt data.
    ret = OH_CryptoSymCipher_Create("ChaCha20|Poly1305", &encCtx);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymCipher_Init(encCtx, CRYPTO_ENCRYPT_MODE, keyCtx, params);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymCipher_Update(encCtx, &msgBlob, &outUpdate);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymCipher_Final(encCtx, nullptr, &tagOutPut);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }

    // Decrypt data.
    ret = OH_CryptoSymCipher_Create("ChaCha20|Poly1305", &decCtx);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymCipherParams_SetParam(params, CRYPTO_TAG_DATABLOB, &tagOutPut);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymCipher_Init(decCtx, CRYPTO_DECRYPT_MODE, keyCtx, params);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymCipher_Final(decCtx, &outUpdate, &decUpdate);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }

    // Release the instance.
end:
    OH_CryptoSymCipherParams_Destroy(params);
    OH_CryptoSymCipher_Destroy(encCtx);
    OH_CryptoSymCipher_Destroy(decCtx);
    OH_CryptoSymKeyGenerator_Destroy(genCtx);
    OH_CryptoSymKey_Destroy(keyCtx);
    OH_Crypto_FreeDataBlob(&outUpdate);
    OH_Crypto_FreeDataBlob(&decUpdate);
    OH_Crypto_FreeDataBlob(&tagOutPut);
    return ret;
}
```
