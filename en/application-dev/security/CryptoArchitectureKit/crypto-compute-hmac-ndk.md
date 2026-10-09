# Generating an HMAC (C/C++)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

A hash-based message authentication code (HMAC) uses a specified digest algorithm to generate a MAC based on the key and message shared by communicating parties. The MAC is used to check the integrity of transmitted packets. The HMAC adds key input on the basis of the message digest algorithm to ensure information correctness. The generated MAC has a fixed length.

## How to Develop

In the **update** API call, you can [pass in full data](#generating-an-hmac-by-passing-in-full-data) or [pass in data by segment](#generating-an-hmac-by-passing-in-data-by-segment). The same data will produce the same result no matter how the data is passed. Use the appropriate method based on the data size.

The following provides examples with different data passing methods.

### Generating an HMAC by Passing In Full Data

1. Call [OH_CryptoSymKeyGenerator_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_create) and [OH_CryptoSymKeyGenerator_Generate](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_generate) to generate a symmetric key (**symKey**) with the key algorithm being HMAC.

2. Call [OH_CryptoMac_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-mac-h.md#oh_cryptomac_create) and specify the string parameter **HMAC** to create a MAC generator with the HMAC algorithm.

3. Call [OH_CryptoMac_SetParam](../../reference/apis-crypto-architecture-kit/capi-crypto-mac-h.md#oh_cryptomac_setparam) and specify **CRYPTO_MAC_DIGEST_NAME_STR** to set the digest algorithm name.

4. Call [OH_CryptoMac_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-mac-h.md#oh_cryptomac_init) and specify the shared symmetric key (**symKey**) to initialize the MAC object.

5. Call [OH_CryptoMac_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-mac-h.md#oh_cryptomac_update) to pass in the data.

6. Call [OH_CryptoMac_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-mac-h.md#oh_cryptomac_final) to obtain the MAC generation result.

7. Call [OH_CryptoMac_GetLength](../../reference/apis-crypto-architecture-kit/capi-crypto-mac-h.md#oh_cryptomac_getlength) to obtain the length of the MAC, in bytes.

<!-- @[message_auth_hmac_single_time](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/MessageAuthenticationCode/entry/src/main/cpp/types/project/hmac/singleTime.cpp) -->

``` C++

#include "CryptoArchitectureKit/crypto_architecture_kit.h"
#include <cstdio>
#include <cstring>

static OH_CryptoSymKey *GenerateHmacKey(const char *algoName)
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

static OH_Crypto_ErrCode CreateHmacContext(OH_CryptoSymKey *keyCtx, OH_CryptoMac **ctx)
{
    OH_Crypto_ErrCode ret = OH_CryptoMac_Create("HMAC", ctx);
    if (ret != CRYPTO_SUCCESS) {
        return ret;
    }

    // Set the digest algorithm name to SM3.
    const char *digestName = "SM3";
    Crypto_DataBlob digestNameData = {
        .data = reinterpret_cast<uint8_t *>(const_cast<char *>(digestName)),
        .len = strlen(digestName)
    };
    ret = OH_CryptoMac_SetParam(*ctx, CRYPTO_MAC_DIGEST_NAME_STR, &digestNameData);
    if (ret != CRYPTO_SUCCESS) {
        OH_CryptoMac_Destroy(*ctx);
        return ret;
    }

    // Initialize the HMAC object.
    ret = OH_CryptoMac_Init(*ctx, keyCtx);
    if (ret != CRYPTO_SUCCESS) {
        OH_CryptoMac_Destroy(*ctx);
        return ret;
    }

    return CRYPTO_SUCCESS;
}

static OH_Crypto_ErrCode UpdateHmacData(OH_CryptoMac *ctx)
{
    // Pass in full data.
    const char *message = "hmacTestMessage";
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

static OH_Crypto_ErrCode FinalizeHmac(OH_CryptoMac *ctx, Crypto_DataBlob *out, uint32_t *macLen)
{
    // Finalize HMAC generation and obtain the result.
    OH_Crypto_ErrCode ret = OH_CryptoMac_Final(ctx, out);
    if (ret != CRYPTO_SUCCESS) {
        return ret;
    }

    // Obtain the length of the HMAC value.
    ret = OH_CryptoMac_GetLength(ctx, macLen);
    if (ret != CRYPTO_SUCCESS) {
        OH_Crypto_FreeDataBlob(out);
        return ret;
    }

    return CRYPTO_SUCCESS;
}

OH_Crypto_ErrCode doTestHmacOnce()
{
    OH_CryptoSymKey *keyCtx = nullptr;
    OH_CryptoMac *ctx = nullptr;
    Crypto_DataBlob out = {0};
    OH_Crypto_ErrCode ret = CRYPTO_SUCCESS;
    uint32_t macLen = 0;

    // Generate an HMAC key, using SM3 as the digest algorithm.
    keyCtx = GenerateHmacKey("HMAC|SM3");
    if (keyCtx == nullptr) {
        ret = CRYPTO_OPERTION_ERROR;
        goto cleanup;
    }

    // Create an HMAC context.
    ret = CreateHmacContext(keyCtx, &ctx);
    if (ret != CRYPTO_SUCCESS) {
        goto cleanup;
    }

    // Pass in full data.
    ret = UpdateHmacData(ctx);
    if (ret != CRYPTO_SUCCESS) {
        goto cleanup;
    }

    // Complete HMAC calculation.
    ret = FinalizeHmac(ctx, &out, &macLen);
    if (ret != CRYPTO_SUCCESS) {
        goto cleanup;
    }

    printf("HMAC calculation success, length: %u\n", macLen);

cleanup:
    // Free resources.
    OH_Crypto_FreeDataBlob(&out);
    OH_CryptoMac_Destroy(ctx);
    OH_CryptoSymKey_Destroy(keyCtx);
    return ret;
}
```


### Generating an HMAC by Passing in Data by Segment

Unlike the first method, this one requires calling [OH_CryptoMac_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-mac-h.md#oh_cryptomac_update) multiple times to process segmented data.

<!-- @[message_auth_hmac_segmentation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/MessageAuthenticationCode/entry/src/main/cpp/types/project/hmac/segmentation.cpp) -->

``` C++

#include "CryptoArchitectureKit/crypto_architecture_kit.h"
#include <cstdio>
#include <cstring>

static OH_CryptoSymKey *GenerateHmacKey(const char *algoName)
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

static OH_Crypto_ErrCode CreateHmacContext(OH_CryptoSymKey *keyCtx, OH_CryptoMac **ctx)
{
    OH_Crypto_ErrCode ret = OH_CryptoMac_Create("HMAC", ctx);
    if (ret != CRYPTO_SUCCESS) {
        return ret;
    }

    // Set the digest algorithm name to SM3.
    const char *digestName = "SM3";
    Crypto_DataBlob digestNameData = {
        .data = reinterpret_cast<uint8_t *>(const_cast<char *>(digestName)),
        .len = strlen(digestName)
    };
    ret = OH_CryptoMac_SetParam(*ctx, CRYPTO_MAC_DIGEST_NAME_STR, &digestNameData);
    if (ret != CRYPTO_SUCCESS) {
        OH_CryptoMac_Destroy(*ctx);
        return ret;
    }

    // Initialize the HMAC object.
    ret = OH_CryptoMac_Init(*ctx, keyCtx);
    if (ret != CRYPTO_SUCCESS) {
        OH_CryptoMac_Destroy(*ctx);
        return ret;
    }

    return CRYPTO_SUCCESS;
}

static OH_Crypto_ErrCode ProcessHmacSegments(OH_CryptoMac *ctx)
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

static OH_Crypto_ErrCode FinalizeHmac(OH_CryptoMac *ctx, Crypto_DataBlob *out, uint32_t *macLen)
{
    // Finalize HMAC generation and obtain the result.
    OH_Crypto_ErrCode ret = OH_CryptoMac_Final(ctx, out);
    if (ret != CRYPTO_SUCCESS) {
        return ret;
    }

    // Obtain the length of the HMAC value.
    ret = OH_CryptoMac_GetLength(ctx, macLen);
    if (ret != CRYPTO_SUCCESS) {
        OH_Crypto_FreeDataBlob(out);
        return ret;
    }

    return CRYPTO_SUCCESS;
}

OH_Crypto_ErrCode doTestHmacBySegments()
{
    OH_CryptoSymKey *keyCtx = nullptr;
    OH_CryptoMac *ctx = nullptr;
    Crypto_DataBlob out = {0};
    OH_Crypto_ErrCode ret = CRYPTO_SUCCESS;
    uint32_t macLen = 0;

    // Generate an HMAC key, using SM3 as the digest algorithm.
    keyCtx = GenerateHmacKey("HMAC|SM3");
    if (keyCtx == nullptr) {
        ret = CRYPTO_OPERTION_ERROR;
        goto cleanup;
    }

    // Create an HMAC context.
    ret = CreateHmacContext(keyCtx, &ctx);
    if (ret != CRYPTO_SUCCESS) {
        goto cleanup;
    }

    // Process data by segment.
    ret = ProcessHmacSegments(ctx);
    if (ret != CRYPTO_SUCCESS) {
        goto cleanup;
    }

    // Complete HMAC calculation.
    ret = FinalizeHmac(ctx, &out, &macLen);
    if (ret != CRYPTO_SUCCESS) {
        goto cleanup;
    }

    printf("HMAC calculation success, length: %u\n", macLen);

cleanup:
    // Free resources.
    OH_Crypto_FreeDataBlob(&out);
    OH_CryptoMac_Destroy(ctx);
    OH_CryptoSymKey_Destroy(keyCtx);
    return ret;
}
```
