# Encryption and Decryption with a 3DES Symmetric Key (C/C++)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=7bf845a7c8933b8c5015a7da3dfa1923d0e9dc57 translatedAt=2026-08-07T03:23:45.507Z pushedAt=2026-08-07T07:27:14.325Z -->

For the corresponding algorithm specifications, see [Symmetric Key Encryption and Decryption Algorithm Specifications: 3DES](crypto-encryption-decryption.md#3des).

## Adding the Dynamic Library in the CMake Script

```txt
target_link_libraries(entry PUBLIC libohcrypto.so)
```

## How to Develop

**Creating an Object**

Call [OH_CryptoSymKeyGenerator_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_create) and [OH_CryptoSymKeyGenerator_Generate](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_generate) to generate a symmetric key (**OH_CryptoSymKey**) with the key algorithm being 3DES and the key length being 192 bits.

    For details on how to generate a 3DES symmetric key, refer to the following example and also see [Symmetric Key Generation and Conversion Specifications: 3DES](crypto-key-generation-conversion.md#3des) and [Converting Binary Data into a Symmetric Key](crypto-convert-binary-data-to-sym-key-ndk.md). Note that the input parameters in the referenced documents may differ from those in the current example.

**Encrypting a Message**

1. Call [OH_CryptoSymCipher_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_create) with the string parameter **'3DES192|ECB|PKCS7'** to create a **Cipher** instance for encryption. The key type is **3DES192**, block cipher mode is **ECB**, and the padding mode is **PKCS7**.

2. Call [OH_CryptoSymCipher_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_init) to initialize the **Cipher** instance. Specifically, set **mode** to **CRYPTO_ENCRYPT_MODE**, and specify the key for encryption (**OH_CryptoSymKey**).

   ECB mode requires no additional encryption parameters. Simply create an empty parameter object and pass it in.

3. Call [OH_CryptoSymCipher_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_update) to update data (in plaintext).

   - If a small amount of data is to be encrypted, you can use **OH_CryptoSymCipher_Final()** immediately after **OH_CryptoSymCipher_Init()**.

   - If a large amount of data is to be encrypted, you can call **OH_CryptoSymCipher_Update** multiple times to pass in the data by segment.

4. Call [OH_CryptoSymCipher_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_final) to obtain the encrypted data.

   - If **OH_CryptoSymCipher_Update** is used to pass in data, set **data** to **null**. If **OH_CryptoSymCipher_Final** is used to pass in data, pass in the plaintext via **data**.

   - The output of **OH_CryptoSymCipher_Final** may be **null**. To avoid exceptions, always check whether the result is **null** before accessing specific data.

**Decryption**

1. Call [OH_CryptoSymCipher_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_create) with the string parameter **'3DES192|ECB|PKCS7'** to create a **Cipher** instance for decryption. The key type is **3DES192**, block cipher mode is **ECB**, and the padding mode is **PKCS7**.

2. Call [OH_CryptoSymCipher_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_init) to initialize the **Cipher** instance. Specifically, set the mode to decryption (**CRYPTO_DECRYPT_MODE**), specify the decryption key (**OH_CryptoSymKey**), and initialize the decryption **Cipher** instance. ECB mode requires no additional encryption parameters. Simply create an empty parameter object and pass it in.

3. Call [OH_CryptoSymCipher_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_update) to update data (in ciphertext).

   - If a small amount of data is to be decrypted, you can use **OH_CryptoSymCipher_Final()** immediately after **OH_CryptoSymCipher_Init()**.

   - If a large amount of data is to be decrypted, you can call **OH_CryptoSymCipher_Update** multiple times to pass in the data by segment.

   - You can decide the operation mode based on the data size. For example, use **update** when the data exceeds 1 KB.

4. Call [OH_CryptoSymCipher_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_final) to obtain the decrypted data.

   - If **OH_CryptoSymCipher_Update** is used to pass in data, set **data** to **null**. If **OH_CryptoSymCipher_Final** is used to pass in data, pass in the ciphertext via **data**.

   - The output of **OH_CryptoSymCipher_Final** may be **null**. To avoid exceptions, always check whether the result is **null** before accessing specific data.

**Destroying Objects**

Call [OH_CryptoSymKeyGenerator_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_destroy), [OH_CryptoSymCipher_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_destroy), [OH_CryptoSymKey_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkey_destroy), and [OH_Crypto_FreeDataBlob](../../reference/apis-crypto-architecture-kit/capi-crypto-common-h.md#oh_crypto_freedatablob) to release the allocated memory and destroy the object.

## Example

If the cipher mode is ECB, you do not need to set encryption and decryption parameters.

If the CBC, CTR, OFB, or CFB block cipher mode is used, you need to set the **iv** parameter for encryption and decryption. For details, see [Setting the IV](#setting-the-iv). You need to modify related parameters when generating and initializing the **Cipher** instance during encryption or decryption.

<!-- @[crypt_decrypt_flow](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidance3DES/entry/src/main/cpp/types/project/3des_ecb_encryption_decryption.cpp) -->

``` C++
#include "CryptoArchitectureKit/crypto_common.h"
#include "CryptoArchitectureKit/crypto_sym_cipher.h"
#include <cstring>
#include "file.h"

OH_Crypto_ErrCode doTest3DesEcb()
{
    OH_CryptoSymKeyGenerator *genCtx = nullptr;
    OH_CryptoSymCipher *encCtx = nullptr;
    OH_CryptoSymCipher *decCtx = nullptr;
    OH_CryptoSymKey *keyCtx = nullptr;
    OH_CryptoSymCipherParams *params = nullptr;
    char *plainText = const_cast<char *>("this is test!");
    Crypto_DataBlob input = {.data = (uint8_t *)(plainText), .len = strlen(plainText)};
    Crypto_DataBlob outUpdate = {.data = nullptr, .len = 0};
    Crypto_DataBlob decUpdate = {.data = nullptr, .len = 0};
    OH_Crypto_ErrCode ret = OH_CryptoSymKeyGenerator_Create("3DES192", &genCtx); // Randomly generate a symmetric key.
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymKeyGenerator_Generate(genCtx, &keyCtx);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymCipherParams_Create(&params); // Create parameters.
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymCipher_Create("3DES192|ECB|PKCS7", &encCtx); // Encryption operation.
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
    ret = OH_CryptoSymCipher_Create("3DES192|ECB|PKCS7", &decCtx); // Decryption operation.
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

### Setting the IV

The following example demonstrates how to set the IV when the CBC mode is used.

If CBC, CTR, OFB, or CFB mode is used, set the IV. In ECB mode, you don't need to set this parameter.

```c++
    OH_CryptoSymCipherParams *params = nullptr;
    uint8_t iv[8] = {1, 2, 4, 12, 3, 4, 2, 3}; // iv is generated from an array of secure random numbers.
    Crypto_DataBlob ivBlob = {.data = iv, .len = sizeof(iv)};

    ret = OH_CryptoSymCipherParams_Create(&params);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    // Set parameters.
    ret = OH_CryptoSymCipherParams_SetParam(params, CRYPTO_IV_DATABLOB, &ivBlob); // You only need to set iv if CBC mode is used.
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    
    // Encrypt data.
    ret = OH_CryptoSymCipher_Create("3DES192|CBC|PKCS7", &encCtx);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymCipher_Init(encCtx, CRYPTO_ENCRYPT_MODE, keyCtx, params);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    // This code only shows the differences between CBC, CTR, OFB, and CFB block cipher modes. For other processes, refer to the development example.
```

<!--no_check-->