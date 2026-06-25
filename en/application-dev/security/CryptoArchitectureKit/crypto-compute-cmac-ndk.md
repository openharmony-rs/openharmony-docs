# Generating a CMAC (C/C++)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

A block cipher (such as AES) and a key are used to generate an authentication code, which verifies that a message has not been alerted during transmission.

## How to Develop

In the **update** API call, you can [pass in full data](#generating-a-cmac-by-passing-in-full-data) or [pass in data by segment](#generating-a-cmac-by-passing-in-data-by-segment). The same data will produce the same result no matter how the data is passed. Use the appropriate method based on the data size.

The following provides examples of CMAC operations with different data passing methods.

### Generating a CMAC by Passing in Full Data

1. Call [OH_CryptoSymKeyGenerator_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_create) and [OH_CryptoSymKeyGenerator_Generate](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_generate) to generate a symmetric key (**symKey**) with the key algorithm being AES-128.

2. Call [OH_CryptoMac_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-mac-h.md#oh_cryptomac_create) and specify the string parameter **CMAC** to create a MAC generator with the CMAC algorithm.

3. Call [OH_CryptoMac_SetParam](../../reference/apis-crypto-architecture-kit/capi-crypto-mac-h.md#oh_cryptomac_setparam) and specify **CRYPTO_MAC_CIPHER_NAME_STR** to set the block cipher algorithm name.

4. Call [OH_CryptoMac_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-mac-h.md#oh_cryptomac_init) and specify the shared symmetric key (**symKey**) to initialize the MAC object.

5. Call [OH_CryptoMac_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-mac-h.md#oh_cryptomac_update) to pass in the data.

6. Call [OH_CryptoMac_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-mac-h.md#oh_cryptomac_final) to obtain the MAC generation result.

7. Call [OH_CryptoMac_GetLength](../../reference/apis-crypto-architecture-kit/capi-crypto-mac-h.md#oh_cryptomac_getlength) to obtain the length of the MAC, in bytes.

<!-- @[message_auth_cmac_single_time](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/MessageAuthenticationCode/entry/src/main/cpp/types/project/cmac/singleTime.cpp) -->

``` C++

#include "CryptoArchitectureKit/crypto_architecture_kit.h"
#include <cstdio>
#include <cstring>

static OH_CryptoSymKey *GenerateAesKey(const char *algoName)
{
    OH_CryptoSymKeyGenerator *keyGen = nullptr;
    OH_Crypto_ErrCode ret = OH_CryptoSymKeyGenerator_Create(algoName, &keyGen);
    if (ret != CRYPTO_SUCCESS) {
        return nullptr;
    }
    OH_CryptoSymKey *keyCtx = nullptr;
    ret = OH_CryptoSymKeyGenerator_Generate(keyGen, &keyCtx);
    OH_CryptoSymKeyGenerator_Destroy(keyGen);
    if (ret != CRYPTO_SUCCESS) {
        return nullptr;
    }
    return keyCtx;
}

static OH_Crypto_ErrCode CreateCmacContext(OH_CryptoSymKey *keyCtx, OH_CryptoMac **ctx)
{
    OH_Crypto_ErrCode ret = OH_CryptoMac_Create("CMAC", ctx);
    if (ret != CRYPTO_SUCCESS) {
        return ret;
    }

    // Set the block cipher algorithm name to AES128.
    const char *cipherName = "AES128";
    Crypto_DataBlob cipherNameData = {
        .data = reinterpret_cast<uint8_t *>(const_cast<char *>(cipherName)),
        .len = strlen(cipherName)
    };
    ret = OH_CryptoMac_SetParam(*ctx, CRYPTO_MAC_CIPHER_NAME_STR, &cipherNameData);
    if (ret != CRYPTO_SUCCESS) {
        OH_CryptoMac_Destroy(*ctx);
        return ret;
    }

    // Initialize the CMAC object.
    ret = OH_CryptoMac_Init(*ctx, keyCtx);
    if (ret != CRYPTO_SUCCESS) {
        OH_CryptoMac_Destroy(*ctx);
        return ret;
    }

    return CRYPTO_SUCCESS;
}

static OH_Crypto_ErrCode UpdateCmacData(OH_CryptoMac *ctx)
{
    // Pass in full data.
    const char *message = "cmacTestMessage";
    Crypto_DataBlob input = {
        .data = reinterpret_cast<uint8_t *>(const_cast<char *>(message)),
        .len = strlen(message)
    };
    OH_Crypto_ErrCode ret = OH_CryptoMac_Update(ctx, &input);
    if (ret != CRYPTO_SUCCESS) {
        return ret;
    }

    return CRYPTO_SUCCESS;
}

static OH_Crypto_ErrCode FinalizeCmac(OH_CryptoMac *ctx, Crypto_DataBlob *out, uint32_t *macLen)
{
    // Finalize CMAC generation and obtain the result.
    OH_Crypto_ErrCode ret = OH_CryptoMac_Final(ctx, out);
    if (ret != CRYPTO_SUCCESS) {
        return ret;
    }

    // Obtain the length of the CMAC value.
    ret = OH_CryptoMac_GetLength(ctx, macLen);
    if (ret != CRYPTO_SUCCESS) {
        OH_Crypto_FreeDataBlob(out);
        return ret;
    }

    return CRYPTO_SUCCESS;
}

OH_Crypto_ErrCode doTestCmacOnce()
{
    OH_CryptoSymKey *keyCtx = nullptr;
    OH_CryptoMac *ctx = nullptr;
    Crypto_DataBlob out = {0};
    OH_Crypto_ErrCode ret = CRYPTO_SUCCESS;
    uint32_t macLen = 0;

    // Generate an AES-128 key.
    keyCtx = GenerateAesKey("AES128");
    if (keyCtx == nullptr) {
        ret = CRYPTO_OPERTION_ERROR;
        goto cleanup;
    }

    // Create a CMAC context.
    ret = CreateCmacContext(keyCtx, &ctx);
    if (ret != CRYPTO_SUCCESS) {
        goto cleanup;
    }

    // Pass in full data.
    ret = UpdateCmacData(ctx);
    if (ret != CRYPTO_SUCCESS) {
        goto cleanup;
    }

    // Complete CMAC calculation.
    ret = FinalizeCmac(ctx, &out, &macLen);
    if (ret != CRYPTO_SUCCESS) {
        goto cleanup;
    }

    printf("CMAC calculation success, length: %u\n", macLen);

cleanup:
    // Free resources.
    OH_Crypto_FreeDataBlob(&out);
    OH_CryptoMac_Destroy(ctx);
    OH_CryptoSymKey_Destroy(keyCtx);
    return ret;
}
```


### Generating a CMAC by Passing in Data by Segment

Unlike the first method, this one requires calling [OH_CryptoMac_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-mac-h.md#oh_cryptomac_update) multiple times to process segmented data.

<!-- @[message_auth_cmac_segmentation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/MessageAuthenticationCode/entry/src/main/cpp/types/project/cmac/segmentation.cpp) -->

``` C++

#include "CryptoArchitectureKit/crypto_architecture_kit.h"
#include <cstdio>
#include <cstring>

static OH_CryptoSymKey *GenerateAesKey(const char *algoName)
{
    OH_CryptoSymKeyGenerator *keyGen = nullptr;
    OH_Crypto_ErrCode ret = OH_CryptoSymKeyGenerator_Create(algoName, &keyGen);
    if (ret != CRYPTO_SUCCESS) {
        return nullptr;
    }
    OH_CryptoSymKey *keyCtx = nullptr;
    ret = OH_CryptoSymKeyGenerator_Generate(keyGen, &keyCtx);
    OH_CryptoSymKeyGenerator_Destroy(keyGen);
    if (ret != CRYPTO_SUCCESS) {
        return nullptr;
    }
    return keyCtx;
}

static OH_Crypto_ErrCode CreateCmacContext(OH_CryptoSymKey *keyCtx, OH_CryptoMac **ctx)
{
    OH_Crypto_ErrCode ret = OH_CryptoMac_Create("CMAC", ctx);
    if (ret != CRYPTO_SUCCESS) {
        return ret;
    }

    // Set the block cipher algorithm name to AES128.
    const char *cipherName = "AES128";
    Crypto_DataBlob cipherNameData = {
        .data = reinterpret_cast<uint8_t *>(const_cast<char *>(cipherName)),
        .len = strlen(cipherName)
    };
    ret = OH_CryptoMac_SetParam(*ctx, CRYPTO_MAC_CIPHER_NAME_STR, &cipherNameData);
    if (ret != CRYPTO_SUCCESS) {
        OH_CryptoMac_Destroy(*ctx);
        return ret;
    }

    // Initialize the CMAC object.
    ret = OH_CryptoMac_Init(*ctx, keyCtx);
    if (ret != CRYPTO_SUCCESS) {
        OH_CryptoMac_Destroy(*ctx);
        return ret;
    }

    return CRYPTO_SUCCESS;
}

static OH_Crypto_ErrCode ProcessCmacSegments(OH_CryptoMac *ctx)
{
    // Pass in data by segment.
    const char *message = "aaaaa.....bbbbb.....ccccc.....ddddd.....eee";
    size_t messageLen = strlen(message);
    size_t segmentSize = 20; // Divide the data into segments of 20 bytes each.

    for (size_t i = 0; i < messageLen; i += segmentSize) {
        size_t currentSize = (i + segmentSize <= messageLen) ? segmentSize : (messageLen - i);
        Crypto_DataBlob segment = {
            .data = reinterpret_cast<uint8_t *>(const_cast<char *>(message + i)),
            .len = currentSize
        };
        OH_Crypto_ErrCode ret = OH_CryptoMac_Update(ctx, &segment);
        if (ret != CRYPTO_SUCCESS) {
            return ret;
        }
    }

    return CRYPTO_SUCCESS;
}

static OH_Crypto_ErrCode FinalizeCmac(OH_CryptoMac *ctx, Crypto_DataBlob *out, uint32_t *macLen)
{
    // Finalize CMAC generation and obtain the result.
    OH_Crypto_ErrCode ret = OH_CryptoMac_Final(ctx, out);
    if (ret != CRYPTO_SUCCESS) {
        return ret;
    }

    // Obtain the length of the CMAC value.
    ret = OH_CryptoMac_GetLength(ctx, macLen);
    if (ret != CRYPTO_SUCCESS) {
        OH_Crypto_FreeDataBlob(out);
        return ret;
    }

    return CRYPTO_SUCCESS;
}

OH_Crypto_ErrCode doTestCmacBySegments()
{
    OH_CryptoSymKey *keyCtx = nullptr;
    OH_CryptoMac *ctx = nullptr;
    Crypto_DataBlob out = {0};
    OH_Crypto_ErrCode ret = CRYPTO_SUCCESS;
    uint32_t macLen = 0;

    // Generate an AES-128 key.
    keyCtx = GenerateAesKey("AES128");
    if (keyCtx == nullptr) {
        ret = CRYPTO_OPERTION_ERROR;
        goto cleanup;
    }

    // Create a CMAC context.
    ret = CreateCmacContext(keyCtx, &ctx);
    if (ret != CRYPTO_SUCCESS) {
        goto cleanup;
    }

    // Process data by segment.
    ret = ProcessCmacSegments(ctx);
    if (ret != CRYPTO_SUCCESS) {
        goto cleanup;
    }

    // Complete CMAC calculation.
    ret = FinalizeCmac(ctx, &out, &macLen);
    if (ret != CRYPTO_SUCCESS) {
        goto cleanup;
    }

    printf("CMAC calculation success, length: %u\n", macLen);

cleanup:
    // Free resources.
    OH_Crypto_FreeDataBlob(&out);
    OH_CryptoMac_Destroy(ctx);
    OH_CryptoSymKey_Destroy(keyCtx);
    return ret;
}
```
