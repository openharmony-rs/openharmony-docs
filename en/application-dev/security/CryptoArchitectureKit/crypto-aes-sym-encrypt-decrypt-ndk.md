# AES Symmetric Key Encryption and Decryption (C/C++)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=64044667f2ece520228c37a4e282d90b2e014ba4 translatedAt=2026-08-31T02:36:22.718Z pushedAt=2026-09-01T06:09:23.230Z -->

For details about the algorithm specifications, see [Symmetric Key Encryption and Decryption Algorithm Specifications: AES](crypto-encryption-decryption.md#aes).

## Linking Related Dynamic Libraries in the CMake Script
```txt
target_link_libraries(entry PUBLIC libohcrypto.so)
```

## How to Develop

### Encrypting and Decrypting with an AES Symmetric Key (GCM Mode)

**Encryption**

1. Call [OH_CryptoSymKeyGenerator_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_create) and [OH_CryptoSymKeyGenerator_Generate](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_generate) to generate a symmetric key (`OH_CryptoSymKey`) with the AES algorithm and a key length of 128 bits.

   To generate an AES symmetric key, refer to the following example, together with [Symmetric Key Generation and Conversion Specifications: AES](crypto-key-generation-conversion.md#aes) and [Randomly Generating a Symmetric Key](crypto-generate-sym-key-randomly-ndk.md). Note that the reference documents and the example may differ in input parameters.

2. Call [OH_CryptoSymCipher_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_create) and specify the string parameter 'AES128|GCM|PKCS7' to create a Cipher instance with the symmetric key type AES128, the block cipher mode GCM, and the padding mode PKCS7 for encryption.

3. Call [OH_CryptoSymCipherParams_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_create) to create a parameter object, and call [OH_CryptoSymCipherParams_SetParam](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_setparam) to set the corresponding encryption parameters.

4. Call [OH_CryptoSymCipher_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_init), set the mode to encryption (`CRYPTO_ENCRYPT_MODE`), and specify the symmetric key (`OH_CryptoSymKey`) and the encryption parameters (`OH_CryptoSymCipherParams`) corresponding to the GCM mode to initialize the encryption Cipher instance.

5. Call [OH_CryptoSymCipher_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_update) to update the data (plaintext).

   There is no limit on the length of a single `update` call. You can decide how to call `update` based on the data volume.

   - When the data volume is small, you can call `final` directly after `init` is complete.
   - When the data volume is large, you can call update multiple times, that is, [segmented encryption and decryption](crypto-aes-sym-encrypt-decrypt-ndk.md#encrypting-and-decrypting-with-an-aes-symmetric-key-gcm-mode).

6. Call [OH_CryptoSymCipher_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_final) to obtain the encrypted data.
   - Because data has already been passed in through update, pass null for data here.
   - The final output may be null. Before accessing the specific data, check whether the result is null to avoid exceptions.

   > **NOTE**
   >
   > In GCM mode, during a single encryption process, concatenating the results of each update call and the final call yields "ciphertext + authTag", where authTag is the last 16 bytes. The remaining part is the ciphertext. If null is passed for the data parameter of final, the result of final is the authTag.

**Decryption**

1. Call [OH_CryptoSymCipher_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_create) and specify the string parameter 'AES128|GCM|PKCS7' to create a Cipher instance with the symmetric key type AES128, block mode GCM, and padding mode PKCS7 for decryption.

2. Use [OH_CryptoSymCipherParams_SetParam](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_setparam) to set authTag as the authentication information for decryption.

3. Call [OH_CryptoSymCipher_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_init), set the mode to decryption (CRYPTO_DECRYPT_MODE), specify the decryption key (OH_CryptoSymKey) and the decryption parameters corresponding to GCM mode (OH_CryptoSymCipherParams), and initialize the decryption Cipher instance.

4. Call [OH_CryptoSymCipher_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_update) to update the data (ciphertext).

5. Call [OH_CryptoSymCipher_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_final) to obtain the decrypted data.

**Destroying Objects**

Call [OH_CryptoSymKeyGenerator_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_destroy), [OH_CryptoSymCipher_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_destroy), and [OH_CryptoSymCipherParams_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_destroy) to destroy the objects.

The following is an example:

<!-- @[gcm_encrypt_decrypt_aes_symkey](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceAes/entry/src/main/cpp/types/project/aes_gcm_encryption_decryption.cpp) -->

``` C++
#include "CryptoArchitectureKit/crypto_common.h"
#include "CryptoArchitectureKit/crypto_sym_cipher.h"
#include <cstring>
#include "file.h"

OH_Crypto_ErrCode doTestAesGcm()
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
    uint8_t iv[12] = {1, 2, 4, 12, 3, 4, 2, 3, 3, 2, 0, 4}; // Generate the IV using a secure random number.
    Crypto_DataBlob ivData = {.data = iv, .len = sizeof(iv)};
    Crypto_DataBlob aadData = {.data = aad, .len = sizeof(aad)};
    Crypto_DataBlob tagData = {.data = tag, .len = sizeof(tag)};
    Crypto_DataBlob tagOutPut = {.data = nullptr, .len = 0};
    char *plainText = const_cast<char *>("this is test!");
    Crypto_DataBlob msgBlob = {.data = (uint8_t *)(plainText), .len = strlen(plainText)};

    // Generate a symmetric key.
    OH_Crypto_ErrCode ret = OH_CryptoSymKeyGenerator_Create("AES128", &genCtx);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymKeyGenerator_Generate(genCtx, &keyCtx);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }

    // Set the parameters.
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

    // Encrypt.
    ret = OH_CryptoSymCipher_Create("AES128|GCM|PKCS7", &encCtx);
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

    // Decrypt.
    ret = OH_CryptoSymCipher_Create("AES128|GCM|PKCS7", &decCtx);
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

### Encrypting and Decrypting with an AES Symmetric Key (CCM Mode)

**Creating an Object**

Call [OH_CryptoSymKeyGenerator_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_create) and [OH_CryptoSymKeyGenerator_Generate](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_generate) to generate a 128-bit AES symmetric key (`OH_CryptoSymKey`).

   For details about how to generate an AES symmetric key, see the following sample code, together with [Symmetric Key Generation and Conversion Specifications: AES](crypto-key-generation-conversion.md#aes) and [Randomly Generating a Symmetric Key](crypto-generate-sym-key-randomly-ndk.md). Note that the parameters in the reference documents may differ from those in the current sample. Read them carefully to distinguish the differences.

**Encryption**

1. Call [OH_CryptoSymCipher_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_create) with the string parameter `'AES128|CCM'` to create a `Cipher` instance whose symmetric key type is AES128 and block mode is CCM, for encryption.

2. Call [OH_CryptoSymCipherParams_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_create) to create a parameter object, and call [OH_CryptoSymCipherParams_SetParam](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_setparam) to set the corresponding encryption parameters.

3. Call [OH_CryptoSymCipher_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_init) to set the mode to encryption (`CRYPTO_ENCRYPT_MODE`), specify the encryption key (`OH_CryptoSymKey`) and the encryption parameters (`OH_CryptoSymCipherParams`) corresponding to the CCM mode, and initialize the encryption `Cipher` instance.

4. Call [OH_CryptoSymCipher_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_update) to update the data (plaintext).

   A single `update` call has no length limit. Determine the length of the data passed to a single `update` call based on the plaintext length.
   > **NOTE**
   >
   > The CCM mode does not support segmented encryption and decryption.

5. Call [OH_CryptoSymCipher_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_final) to obtain the encrypted data.
   - Because data has already been passed in through `update`, pass `null` for `data` here.
   - The output of `final` may be `null`. Check whether the result is `null` before accessing the data.
   > **NOTE**
   > In CCM mode, `final` sets `authTag` as the initial authentication information for decryption, which must be saved.

6. Use [OH_CryptoSymCipherParams_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_create) to create `Params`, and use [OH_CryptoSymCipherParams_SetParam](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_setparam) to set `authTag` as the authentication information for decryption.

   In CCM mode, the algorithm library supports a 12-byte `authTag` for initial authentication during decryption. In the example, `authTag` is 12 bytes.

**Decryption**

1. Call [OH_CryptoSymCipher_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_create) and specify the parameter 'AES128|CCM' to create a `Cipher` instance with the symmetric key type AES128 and the block mode CCM for decryption.

2. During decryption, use [OH_CryptoSymCipherParams_SetParam](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_setparam) to set `authTag` as the initial authentication information.

3. Call [OH_CryptoSymCipher_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_init), set the mode to decryption, specify the decryption key and the decryption parameters for CCM mode, and initialize the decryption `Cipher` instance.

4. Call [OH_CryptoSymCipher_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_update) to update the data (ciphertext).

   There is no limit on the length of a single `update` call. You can determine the length of data to pass to a single `update` call based on the ciphertext length.
   > **NOTE**
   >
   > The CCM mode does not support segmented encryption or decryption.

5. Call [OH_CryptoSymCipher_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_final) to obtain the decrypted data.
   - If data has already been passed through `update`, pass `null` for `data` here.
   - Before accessing the specific data in the `final` output, check whether the result is `null` to avoid exceptions.

**Destroying Objects**

Call [OH_CryptoSymKeyGenerator_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_destroy), [OH_CryptoSymCipher_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_destroy), [OH_CryptoSymKey_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkey_destroy), and [OH_Crypto_FreeDataBlob](../../reference/apis-crypto-architecture-kit/capi-crypto-common-h.md#oh_crypto_freedatablob) to release the allocated memory and destroy the symmetric key, the Cipher instance, and the Params.

The following is an example:

<!-- @[ccm_encrypt_decrypt_aes_symkey](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceAes/entry/src/main/cpp/types/project/aes_ccm_encryption_decryption.cpp) -->

``` C++
#include "CryptoArchitectureKit/crypto_common.h"
#include "CryptoArchitectureKit/crypto_sym_cipher.h"
#include <cstring>
#include "file.h"

OH_Crypto_ErrCode doTestAesCcm()
{
    OH_CryptoSymKeyGenerator *genCtx = nullptr;
    OH_CryptoSymCipher *encCtx = nullptr;
    OH_CryptoSymCipher *decCtx = nullptr;
    OH_CryptoSymKey *keyCtx = nullptr;
    OH_CryptoSymCipherParams *params = nullptr;

    Crypto_DataBlob outUpdate = {.data = nullptr, .len = 0};
    Crypto_DataBlob decUpdate = {.data = nullptr, .len = 0};

    uint8_t aad[8] = {1, 2, 3, 4, 5, 6, 7, 8};
    uint8_t tag[12] = {0};
    uint8_t iv[7] = {1, 2, 4, 12, 3, 4, 2}; // Generate the IV using a secure random number.
    Crypto_DataBlob ivData = {.data = iv, .len = sizeof(iv)};
    Crypto_DataBlob aadData = {.data = aad, .len = sizeof(aad)};
    Crypto_DataBlob tagData = {.data = tag, .len = sizeof(tag)};
    Crypto_DataBlob tagOutPut = {.data = nullptr, .len = 0};
    char *plainText = const_cast<char *>("this is test!");
    Crypto_DataBlob msgBlob = {.data = (uint8_t *)(plainText), .len = strlen(plainText)};
    // Generate a symmetric key.
    OH_Crypto_ErrCode ret = OH_CryptoSymKeyGenerator_Create("AES128", &genCtx);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymKeyGenerator_Generate(genCtx, &keyCtx);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }

    // Set parameters
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

    // Encrypt
    ret = OH_CryptoSymCipher_Create("AES128|CCM", &encCtx);
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

    // Decrypt
    ret = OH_CryptoSymCipher_Create("AES128|CCM", &decCtx);
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
### Encrypting and Decrypting with an AES Symmetric Key (CBC Mode)

**Creating the Object**

Call [OH_CryptoSymKeyGenerator_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_create) and [OH_CryptoSymKeyGenerator_Generate](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_generate) to generate a 128-bit AES symmetric key (`OH_CryptoSymKey`).

   To generate an AES symmetric key, refer to the following example and understand it together with [Symmetric Key Generation and Conversion Specifications: AES](crypto-key-generation-conversion.md#aes) and [Randomly Generating a Symmetric Key](crypto-generate-sym-key-randomly-ndk.md). Note that the reference documents may differ from the current example in input parameters.

**Encryption**

1. Call [OH_CryptoSymCipher_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_create) with the string parameter `'AES128|CBC|PKCS7'` to create a `Cipher` instance with the AES128 symmetric key type, CBC block mode, and PKCS7 padding mode for encryption.

2. Call [OH_CryptoSymCipherParams_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_create) to create a parameter object, and call [OH_CryptoSymCipherParams_SetParam](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_setparam) to set the encryption parameters.

3. Call [OH_CryptoSymCipher_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_init), set the mode to encryption (`CRYPTO_ENCRYPT_MODE`), and specify the encryption key (`OH_CryptoSymKey`) and the encryption parameters corresponding to the CBC mode (`OH_CryptoSymCipherParams`) to initialize the encryption `Cipher` instance.

4. If the content to encrypt is short, call [OH_CryptoSymCipher_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_final) directly to obtain the encrypted data, without calling [OH_CryptoSymCipher_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_update).

**Decryption**

1. Call [OH_CryptoSymCipher_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_create) and specify the string parameter `'AES128|CBC|PKCS7'` to create a Cipher instance with the symmetric key type AES128, block mode CBC, and padding mode PKCS7 for decryption.

2. Call [OH_CryptoSymCipher_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_init), set the mode to decryption (`CRYPTO_DECRYPT_MODE`), and specify the decryption key (`OH_CryptoSymKey`) and the decryption parameters (`OH_CryptoSymCipherParams`) corresponding to the CBC mode to initialize the decryption Cipher instance.

3. When the content to decrypt is short, call [OH_CryptoSymCipher_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_final) directly to obtain the decrypted data, without calling [OH_CryptoSymCipher_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_update).

**Destroying Objects**

Call [OH_CryptoSymKeyGenerator_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_destroy), [OH_CryptoSymCipher_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_destroy), [OH_CryptoSymKey_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkey_destroy), and [OH_Crypto_FreeDataBlob](../../reference/apis-crypto-architecture-kit/capi-crypto-common-h.md#oh_crypto_freedatablob) to release the allocated memory and destroy the objects.

The following is an example:

<!-- @[cbc_encrypt_decrypt_aes_symkey](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceAes/entry/src/main/cpp/types/project/aes_cbc_encryption_decryption.cpp) -->

``` C++
#include "CryptoArchitectureKit/crypto_common.h"
#include "CryptoArchitectureKit/crypto_sym_cipher.h"
#include <cstring>
#include "file.h"

OH_Crypto_ErrCode doTestAesCbc()
{
    OH_CryptoSymKeyGenerator *genCtx = nullptr;
    OH_CryptoSymCipher *encCtx = nullptr;
    OH_CryptoSymCipher *decCtx = nullptr;
    OH_CryptoSymKey *keyCtx = nullptr;
    OH_CryptoSymCipherParams *params = nullptr;
    Crypto_DataBlob outUpdate = {.data = nullptr, .len = 0};
    Crypto_DataBlob decUpdate = {.data = nullptr, .len = 0};
    char *plainText = const_cast<char *>("this is test!");
    Crypto_DataBlob msgBlob = {.data = (uint8_t *)(plainText), .len = strlen(plainText)};
    uint8_t iv[16] = {1, 2, 4, 12, 3, 4, 2, 3, 3, 2, 0, 4, 3, 1, 0, 10}; // Generate the IV using a secure random number.
    Crypto_DataBlob ivBlob = {.data = iv, .len = sizeof(iv)};
    // Generate a symmetric key.
    OH_Crypto_ErrCode ret = OH_CryptoSymKeyGenerator_Create("AES128", &genCtx);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymKeyGenerator_Generate(genCtx, &keyCtx);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }

    // Set the parameters.
    ret = OH_CryptoSymCipherParams_Create(&params);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymCipherParams_SetParam(params, CRYPTO_IV_DATABLOB, &ivBlob);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }

    // Encrypt.
    ret = OH_CryptoSymCipher_Create("AES128|CBC|PKCS7", &encCtx);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymCipher_Init(encCtx, CRYPTO_ENCRYPT_MODE, keyCtx, params);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymCipher_Final(encCtx, &msgBlob, &outUpdate);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }

    // Decrypt.
    ret = OH_CryptoSymCipher_Create("AES128|CBC|PKCS7", &decCtx);
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

end:
    OH_CryptoSymCipherParams_Destroy(params);
    OH_CryptoSymCipher_Destroy(encCtx);
    OH_CryptoSymCipher_Destroy(decCtx);
    OH_CryptoSymKeyGenerator_Destroy(genCtx);
    OH_CryptoSymKey_Destroy(keyCtx);
    OH_Crypto_FreeDataBlob(&outUpdate);
    OH_Crypto_FreeDataBlob(&decUpdate);
    return ret;
}
```

### Encrypting and Decrypting with an AES Symmetric Key (ECB Mode)

**Creating an Object**

Call [OH_CryptoSymKeyGenerator_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_create) and [OH_CryptoSymKeyGenerator_Generate](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_generate) to generate a 128-bit AES symmetric key (`OH_CryptoSymKey`).

   To generate an AES symmetric key, refer to the following example and read it together with [Symmetric Key Generation and Conversion Specifications: AES](crypto-key-generation-conversion.md#aes) and [Randomly Generating a Symmetric Key](crypto-generate-sym-key-randomly-ndk.md). Note that the reference documents may differ from the current example in input parameters.

**Encryption**

1. Call [OH_CryptoSymCipher_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_create) with the string parameter `'AES128|ECB|PKCS7'` to create a Cipher instance with the symmetric key type AES128, block mode ECB, and padding mode PKCS7 for encryption.

2. Call [OH_CryptoSymCipher_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_init), set the mode to encryption (`CRYPTO_ENCRYPT_MODE`), and specify the encryption key (`OH_CryptoSymKey`) to initialize the encryption Cipher instance. The ECB mode requires no additional encryption parameters, so pass an empty parameter object.

3. When the content to encrypt is short, call [OH_CryptoSymCipher_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_final) directly to obtain the encrypted data without calling [OH_CryptoSymCipher_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_update).

**Decryption**

1. Call [OH_CryptoSymCipher_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_create) with the string parameter `'AES128|ECB|PKCS7'` to create a Cipher instance with the symmetric key type AES128, block mode ECB, and padding mode PKCS7 for decryption.

2. Call [OH_CryptoSymCipher_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_init), set the mode to decryption (`CRYPTO_DECRYPT_MODE`), specify the decryption key (`OH_CryptoSymKey`), and initialize the decryption Cipher instance. The ECB mode requires no additional encryption parameters; pass an empty parameter object.

3. When the content to decrypt is short, call [OH_CryptoSymCipher_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_final) directly to obtain the decrypted data, without calling [OH_CryptoSymCipher_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_update).

**Destroying objects**

Call [OH_CryptoSymKeyGenerator_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_destroy) to destroy the key generator. Call [OH_CryptoSymCipher_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_destroy) to destroy the cipher object.

The following is an example:

<!-- @[ecb_encrypt_decrypt_aes_symkey](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceAes/entry/src/main/cpp/types/project/aes_ecb_encryption_decryption.cpp) -->

``` C++
#include "CryptoArchitectureKit/crypto_common.h"
#include "CryptoArchitectureKit/crypto_sym_cipher.h"
#include <cstring>
#include "file.h"

OH_Crypto_ErrCode doTestAesEcb()
{
    OH_CryptoSymKeyGenerator *genCtx = nullptr;
    OH_CryptoSymCipher *encCtx = nullptr;
    OH_CryptoSymCipher *decCtx = nullptr;
    OH_CryptoSymKey *keyCtx = nullptr;
    OH_CryptoSymCipherParams *params = nullptr;
    char *plainText = const_cast<char *>("this is test");
    Crypto_DataBlob input = {.data = (uint8_t *)(plainText), .len = strlen(plainText)};
    Crypto_DataBlob outUpdate = {.data = nullptr, .len = 0};
    Crypto_DataBlob decUpdate = {.data = nullptr, .len = 0};

    // Randomly generate a symmetric key.
    OH_Crypto_ErrCode ret = OH_CryptoSymKeyGenerator_Create("AES128", &genCtx);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymKeyGenerator_Generate(genCtx, &keyCtx);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    // Create parameters.
    ret = OH_CryptoSymCipherParams_Create(&params);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }

    // Encryption operation.
    ret = OH_CryptoSymCipher_Create("AES128|ECB|PKCS7", &encCtx);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymCipher_Init(encCtx, CRYPTO_ENCRYPT_MODE, keyCtx, params);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymCipher_Final(encCtx, &input, &outUpdate);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }

    // Decryption operation.
    ret = OH_CryptoSymCipher_Create("AES128|ECB|PKCS7", &decCtx);
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

end:
    OH_CryptoSymCipherParams_Destroy(params);
    OH_CryptoSymCipher_Destroy(encCtx);
    OH_CryptoSymCipher_Destroy(decCtx);
    OH_CryptoSymKeyGenerator_Destroy(genCtx);
    OH_CryptoSymKey_Destroy(keyCtx);
    OH_Crypto_FreeDataBlob(&outUpdate);
    OH_Crypto_FreeDataBlob(&decUpdate);
    return ret;
}
```

### Encrypting and Decrypting with an AES Symmetric Key (GCM Mode) in Segments

**Creating an object**

Call [OH_CryptoSymKeyGenerator_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_create) and [OH_CryptoSymKeyGenerator_Generate](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_generate) to generate a symmetric key (OH_CryptoSymKey) with the AES algorithm and a key length of 128 bits.

For details about how to generate an AES symmetric key, refer to the following example together with [Symmetric Key Generation and Conversion Specifications: AES](crypto-key-generation-conversion.md#aes) and [Randomly Generating a Symmetric Key](crypto-generate-sym-key-randomly-ndk.md). Note that the reference documents may differ from the current example in input parameters.

**Encrypting**

1. Call [OH_CryptoSymCipher_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_create) and specify the string parameter 'AES128|GCM|PKCS7' to create a Cipher instance with the AES128 symmetric key algorithm, GCM block mode, and PKCS7 padding mode for encryption.

2. Call [OH_CryptoSymCipherParams_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_create) to create a parameter object, and call [OH_CryptoSymCipherParams_SetParam](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_setparam) to set the corresponding encryption parameters.

3. Call [OH_CryptoSymCipher_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_init), set the mode to encryption (CRYPTO_ENCRYPT_MODE), and specify the symmetric key (OH_CryptoSymKey) and the GCM-mode encryption parameters (OH_CryptoSymCipherParams) to initialize the encryption Cipher instance.

4. Set the amount of data passed in at a time to 20 bytes, and call [OH_CryptoSymCipher_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_update) multiple times to update the data (plaintext).

   - Currently, a single update call has no length limit. You can determine how to call update based on the amount of data.
   - It is recommended that you check whether the result of each `update` call is null, and when the result is not null, extract the ciphertext from it and concatenate it to form the complete ciphertext. This is because, in different modes, the result of `update` may be affected differently.

      1) For example, in ECB and CBC modes, encryption is always performed in units of blocks, and the encrypted block results produced by the current update are output. That is, when the current update operation fills a complete block, the ciphertext is output; if it does not fill a block, the current update outputs null, and the unencrypted data is concatenated with the data of the next input before being output in blocks. When the final `final` operation is performed, the unencrypted data is padded according to the specified padding mode, and then the remaining encryption results are output. The `update` operation during decryption follows the same logic.

      2) For stream cipher modes (such as CTR and OFB modes), the ciphertext length is usually equal to the plaintext length.

5. Call [OH_CryptoSymCipher_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_final) to obtain the ciphertext.

   - Because the data has already been passed in through `update`, pass null here.
   - The result of `final` may be null. Before accessing the specific data, check whether the result is null to avoid exceptions.

   > **NOTE**
   >
   > In GCM mode, during a single encryption process, concatenating the results of each `update` and the final `final` yields "ciphertext + authTag", where authTag is the last 16 bytes. The remaining part is the ciphertext. If the `data` parameter of `final` is passed as null, the result of `final` is the authTag.

**Decryption**

1. Call [OH_CryptoSymCipher_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_create), specifying the parameter 'AES128|GCM|PKCS7', to create a Cipher instance with the symmetric key type AES128, the block mode GCM, and the padding mode PKCS7, and complete the decryption operation.

2. Call [OH_CryptoSymCipherParams_SetParam](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_setparam) to set authTag as the authentication information for decryption.

In GCM mode, take the last 16 bytes from the encrypted data as the authentication information for decryption initialization. In this example, the authTag is exactly 16 bytes.

3. Call [OH_CryptoSymCipher_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_init) to set the mode to decryption (CRYPTO_DECRYPT_MODE), specify the decryption key (OH_CryptoSymKey) and the decryption parameters corresponding to GCM mode (OH_CryptoSymCipherParams), and initialize the decryption Cipher instance.

4. Set the amount of data passed in at a time to 20 bytes, and call [OH_CryptoSymCipher_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_update) multiple times to update the data (ciphertext).

5. Call [OH_CryptoSymCipher_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_final) to obtain the decrypted data.

**Destroying Objects**

Call [OH_CryptoSymKeyGenerator_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_destroy), [OH_CryptoSymCipher_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_destroy), and [OH_CryptoSymCipherParams_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_destroy) to destroy the objects.

The following is an example:

<!-- @[gcm_seg_encrypt_decrypt_aes_symkey](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceAes/entry/src/main/cpp/types/project/aes_gcm_segment_encryption_decryption.cpp) -->

``` C++
#include <cstring>
#include "CryptoArchitectureKit/crypto_common.h"
#include "CryptoArchitectureKit/crypto_sym_cipher.h"
#include "file.h"

#define OH_CRYPTO_GCM_TAG_LEN 16
#define OH_CRYPTO_MAX_TEST_DATA_LEN 128
OH_Crypto_ErrCode doTestAesGcmSeg()
{
    OH_CryptoSymKeyGenerator *genCtx = nullptr;
    OH_CryptoSymCipher *encCtx = nullptr;
    OH_CryptoSymCipher *decCtx = nullptr;
    OH_CryptoSymKey *keyCtx = nullptr;
    OH_CryptoSymCipherParams *params = nullptr;

    char *plainText = const_cast<char *>("aaaaa.....bbbbb.....ccccc.....ddddd.....eee");
    Crypto_DataBlob msgBlob = {.data = (uint8_t *)(plainText), .len = strlen(plainText)};

    uint8_t aad[8] = {1, 2, 3, 4, 5, 6, 7, 8};
    uint8_t tagArr[16] = {0};
    uint8_t iv[12] = {1, 2, 4, 12, 3, 4, 2, 3, 3, 2, 0, 4}; // Generate the IV using a secure random number.
    Crypto_DataBlob tag = {.data = nullptr, .len = 0};
    Crypto_DataBlob ivBlob = {.data = iv, .len = sizeof(iv)};
    Crypto_DataBlob aadBlob = {.data = aad, .len = sizeof(aad)};
    Crypto_DataBlob outUpdate = {.data = nullptr, .len = 0};
    Crypto_DataBlob decUpdate = {.data = nullptr, .len = 0};
    Crypto_DataBlob tagInit = {.data = tagArr, .len = sizeof(tagArr)};
    int32_t cipherLen = 0;
    int blockSize = 20;
    int32_t randomLen = strlen(plainText);
    int cnt = randomLen / blockSize;
    int rem = randomLen % blockSize;
    uint8_t cipherText[OH_CRYPTO_MAX_TEST_DATA_LEN] = {0};
    Crypto_DataBlob cipherBlob;
    
    // Generate the key.
    OH_Crypto_ErrCode ret = OH_CryptoSymKeyGenerator_Create("AES128", &genCtx);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymKeyGenerator_Generate(genCtx, &keyCtx);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    
    // Set the parameters.
    ret = OH_CryptoSymCipherParams_Create(&params);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymCipherParams_SetParam(params, CRYPTO_IV_DATABLOB, &ivBlob);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymCipherParams_SetParam(params, CRYPTO_AAD_DATABLOB, &aadBlob);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymCipherParams_SetParam(params, CRYPTO_TAG_DATABLOB, &tagInit);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    
    // Encrypt.
    ret = OH_CryptoSymCipher_Create("AES128|GCM|PKCS7", &encCtx);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymCipher_Init(encCtx, CRYPTO_ENCRYPT_MODE, keyCtx, params);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    
    for (int i = 0; i < cnt; i++) {
        msgBlob.len = blockSize;
        ret = OH_CryptoSymCipher_Update(encCtx, &msgBlob, &outUpdate);
        if (ret != CRYPTO_SUCCESS) {
            goto end;
        }
        msgBlob.data += blockSize;
        memcpy(&cipherText[cipherLen], outUpdate.data, outUpdate.len);
        cipherLen += outUpdate.len;
        OH_Crypto_FreeDataBlob(&outUpdate);
    }
    if (rem > 0) {
        msgBlob.len = rem;
        ret = OH_CryptoSymCipher_Update(encCtx, (Crypto_DataBlob *)&msgBlob, &outUpdate);
        if (ret != CRYPTO_SUCCESS) {
            goto end;
        }
        memcpy(&cipherText[cipherLen], outUpdate.data, outUpdate.len);
        cipherLen += outUpdate.len;
        OH_Crypto_FreeDataBlob(&outUpdate);
    }
    ret = OH_CryptoSymCipher_Final(encCtx, nullptr, &tag);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }

    // Decrypt.
    cipherBlob = {.data = reinterpret_cast<uint8_t *>(cipherText), .len = (size_t)cipherLen};
    msgBlob.data -= strlen(plainText) - rem;
    msgBlob.len = strlen(plainText);
    ret = OH_CryptoSymCipher_Create("AES128|GCM|PKCS7", &decCtx);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymCipherParams_SetParam(params, CRYPTO_TAG_DATABLOB, &tag);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymCipher_Init(decCtx, CRYPTO_DECRYPT_MODE, keyCtx, params);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymCipher_Final(decCtx, &cipherBlob, &decUpdate);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }

end:
    OH_CryptoSymCipherParams_Destroy(params);
    OH_CryptoSymCipher_Destroy(encCtx);
    OH_CryptoSymCipher_Destroy(decCtx);
    OH_CryptoSymKeyGenerator_Destroy(genCtx);
    OH_CryptoSymKey_Destroy(keyCtx);
    OH_Crypto_FreeDataBlob(&outUpdate);
    OH_Crypto_FreeDataBlob(&tag);
    OH_Crypto_FreeDataBlob(&decUpdate);
    return ret;
}
```
