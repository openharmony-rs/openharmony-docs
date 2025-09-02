# Encryption and Decryption by Segment with an SM4 Symmetric Key (GCM Mode) (C/C++)

For details about the algorithm specifications, see [SM4](crypto-sym-encrypt-decrypt-spec.md#sm4).

## Adding the Dynamic Library in the CMake Script
```txt
target_link_libraries(entry PUBLIC libohcrypto.so)
```

**Encryption**

1. Call [OH_CryptoSymKeyGenerator_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_create) and [OH_CryptoSymKeyGenerator_Generate](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_generate) to generate a symmetric key (**OH_CryptoSymKey**) with the key algorithm being SM4 and the key length being 128 bits.
   
   In addition to the example in this topic, [SM4](crypto-sym-key-generation-conversion-spec.md#sm4) and [Randomly Generating a Symmetric Key](crypto-generate-sym-key-randomly-ndk.md) may help you better understand how to generate an SM4 symmetric key. Note that the input parameters in the reference documents may be different from those in the example below.

2. Call [OH_CryptoSymCipher_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_create) with the string parameter **'SM4_128|GCM|PKCS7'** to create a **Cipher** instance for encryption. The key type is **SM4_128**, block cipher mode is **GCM**, and the padding mode is **PKCS7**.

3. Call [OH_CryptoSymCipherParams_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_create) to create a parameter object and call [OH_CryptoSymCipherParams_SetParam](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_setparam) to set encryption parameters.

4. Call [OH_CryptoSymCipher_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_init) to initialize the **Cipher** instance. Specifically, set **mode** to **CRYPTO_ENCRYPT_MODE**, and specify the key for encryption (**OH_CryptoSymKey**) and the encryption parameter instance (**OH_CryptoSymCipherParams**) corresponding to the GCM mode.

5. Set the size of the data to be passed in each time to 20 bytes, and call [OH_CryptoSymCipher_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_update) multiple times to pass in the data (plaintext) to be encrypted.
   
   - Currently, the amount of the data to be passed in by a single **OH_CryptoSymCipher_Update()** is not limited. You can determine how to pass in data based on the data volume.
   - You are advised to check the result of each **OH_CryptoSymCipher_Update()**. If the result is not **null**, obtain the data and combine the data segments into complete ciphertext. The **OH_CryptoSymCipher_Update()** result may vary with the key specifications.
      
      If a block cipher mode (ECB or CBC) is used, data is encrypted and output based on the block size. That is, if the data of an **OH_CryptoSymCipher_Update()** operation matches the block size, the ciphertext is output. Otherwise, **null** is output, and the plaintext will be combined with the input data of the next **OH_CryptoSymCipher_Update()** to form a block. When **OH_CryptoSymCipher_Final()** is called, the unencrypted data is padded to the block size based on the specified padding mode, and then encrypted. The **OH_CryptoSymCipher_Update()** API works in the same way in decryption.

      If a stream cipher mode (CTR or OFB) is used, the ciphertext length is usually the same as the plaintext length.

6. Call [OH_CryptoSymCipher_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_final) to obtain the encrypted data.
   
   - If data has been passed in by **OH_CryptoSymCipher_Update()**, pass in **null** in the **data** parameter of **OH_CryptoSymCipher_Final**.
   - The output of **OH_CryptoSymCipher_Final** may be **null**. To avoid exceptions, always check whether the result is **null** before accessing specific data.

7. Call [OH_CryptoSymCipherParams_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_create) to create a **Params** instance, and call [OH_CryptoSymCipherParams_SetParam](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_setparam) to set **authTag** as the authentication information for decryption.
   In GCM mode, extract the last 16 bytes from the encrypted data as the authentication information for initializing the **Cipher** instance in decryption. In the example, **authTag** is of 16 bytes.

8. Call [OH_CryptoSymKeyGenerator_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_destroy), [OH_CryptoSymCipher_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_destroy), and [OH_CryptoSymCipherParams_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_destroy) to destroy the objects.

**Decryption**

1. Call [OH_CryptoSymCipher_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_create) with the string parameter **'SM4_128|GCM|PKCS7'** to create a **Cipher** instance for decryption. The key type is **SM4_128**, block cipher mode is **GCM**, and the padding mode is **PKCS7**.

2. Call [OH_CryptoSymCipher_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_init) to initialize the **Cipher** instance. Specifically, set **mode** to **CRYPTO_DECRYPT_MODE**, and specify the decryption key (**OH_CryptoSymKey**) and the decryption parameter instance (**OH_CryptoSymCipherParams**) corresponding to the GCM mode.

3. Set the size of the data to be passed in each time to 20 bytes, and call [OH_CryptoSymCipher_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_update) multiple times to pass in the data (ciphertext) to be encrypted.

4. Call [OH_CryptoSymCipher_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_final) to obtain the decrypted data.

- **Example**

```c++
#include <string.h>
#include "CryptoArchitectureKit/crypto_common.h"
#include "CryptoArchitectureKit/crypto_sym_cipher.h"
#include <string.h>

#define OH_CRYPTO_GCM_TAG_LEN 16
#define OH_CRYPTO_MAX_TEST_DATA_LEN 128
static OH_Crypto_ErrCode doTestSm4GcmSeg()
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
    uint8_t iv[12] = {1, 2, 4, 12, 3, 4, 2, 3, 3, 2, 0, 4}; // iv is generated from an array of secure random numbers.
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

    // Generate a key.
    OH_Crypto_ErrCode ret;
    ret = OH_CryptoSymKeyGenerator_Create("SM4_128", &genCtx);
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

    // Encrypt the message.
    ret = OH_CryptoSymCipher_Create("SM4_128|GCM|PKCS7", &encCtx);
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
    }
    if (rem > 0) {
        msgBlob.len = rem;
        ret = OH_CryptoSymCipher_Update(encCtx, (Crypto_DataBlob *)&msgBlob, &outUpdate);
        if (ret != CRYPTO_SUCCESS) {
            goto end;
        }
        memcpy(&cipherText[cipherLen], outUpdate.data, outUpdate.len);
        cipherLen += outUpdate.len;
    }
    ret = OH_CryptoSymCipher_Final(encCtx, nullptr, &tag);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    
    // Decrypt the message.
    cipherBlob = {.data = reinterpret_cast<uint8_t *>(cipherText), .len = (size_t)cipherLen};
    msgBlob.data -= strlen(plainText) - rem;
    msgBlob.len = strlen(plainText);
    ret = OH_CryptoSymCipher_Create("SM4_128|GCM|PKCS7", &decCtx);
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
