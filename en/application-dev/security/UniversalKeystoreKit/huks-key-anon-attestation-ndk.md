# Anonymous Key Attestation (C/C++)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=a1023e0df9a0b6e288b02fdc0444ceb52ccfe640 translatedAt=2026-11-20T03:27:24.543Z pushedAt=2026-11-20T06:46:19.955Z nl=1 -->

Ensure network connection during the operation.

## Linking the Dynamic Library in the CMake Script
```txt
target_link_libraries(entry PUBLIC libhuks_ndk.z.so)
```

## How to Develop

1. Specify the key alias. For details about the naming rules, see [Key Generation Overview and Algorithm Specifications](huks-key-generation-overview.md).

2. Initialize the parameter set: Construct **paramSet** via [OH_Huks_InitParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-param-h.md#oh_huks_initparamset), [OH_Huks_AddParams](../../reference/apis-universal-keystore-kit/capi-native-huks-param-h.md#oh_huks_addparams), and [OH_Huks_BuildParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-param-h.md#oh_huks_buildparamset). The parameter set must contain the [OH_Huks_KeyAlg](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_keyalg), [OH_Huks_KeySize](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_keysize), and [OH_Huks_KeyPurpose](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_keypurpose) attributes.

3. Use [OH_Huks_AnonAttestKeyItem](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_anonattestkeyitem) with the key alias and parameter set to perform key attestation.

## Development Case
<!-- @[anonymized_key_proof](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/AnonymousKeyProof/entry/src/main/cpp/napi_init.cpp) -->

``` C++
#include "huks/native_huks_api.h"
#include "huks/native_huks_param.h"
#include "napi/native_api.h"
#include <cstring>

OH_Huks_Result InitParamSet(struct OH_Huks_ParamSet **paramSet, const struct OH_Huks_Param *params,
                            uint32_t paramCount)
{
    OH_Huks_Result ret = OH_Huks_InitParamSet(paramSet);
    if (ret.errorCode != OH_HUKS_SUCCESS) {
        return ret;
    }
    ret = OH_Huks_AddParams(*paramSet, params, paramCount);
    if (ret.errorCode != OH_HUKS_SUCCESS) {
        OH_Huks_FreeParamSet(paramSet);
        return ret;
    }
    ret = OH_Huks_BuildParamSet(paramSet);
    if (ret.errorCode != OH_HUKS_SUCCESS) {
        OH_Huks_FreeParamSet(paramSet);
        return ret;
    }
    return ret;
}

static uint32_t g_size = 4096;
static uint32_t CERT_COUNT = 4;
void FreeCertChain(struct OH_Huks_CertChain *certChain, const uint32_t pos)
{
    if (certChain == nullptr || certChain->certs == nullptr) {
        return;
    }
    for (uint32_t j = 0; j < pos; j++) {
        if (certChain->certs[j].data != nullptr) {
            free(certChain->certs[j].data);
            certChain->certs[j].data = nullptr;
        }
    }
    if (certChain->certs != nullptr) {
        free(certChain->certs);
        certChain->certs = nullptr;
    }
}

int32_t ConstructDataToCertChain(struct OH_Huks_CertChain *certChain)
{
    if (certChain == nullptr) {
        return OH_HUKS_ERR_CODE_ILLEGAL_ARGUMENT;
    }
    certChain->certsCount = CERT_COUNT;

    certChain->certs = (struct OH_Huks_Blob *)malloc(sizeof(struct OH_Huks_Blob) * (certChain->certsCount));
    if (certChain->certs == nullptr) {
        return OH_HUKS_ERR_CODE_INTERNAL_ERROR;
    }
    for (uint32_t i = 0; i < certChain->certsCount; i++) {
        certChain->certs[i].size = g_size;
        certChain->certs[i].data = (uint8_t *)malloc(certChain->certs[i].size);
        if (certChain->certs[i].data == nullptr) {
            FreeCertChain(certChain, i);
            return OH_HUKS_ERR_CODE_ILLEGAL_ARGUMENT;
        }
    }
    return 0;
}

static struct OH_Huks_Param g_genAnonAttestParams[] = {
    {.tag = OH_HUKS_TAG_ALGORITHM, .uint32Param = OH_HUKS_ALG_RSA},
    {.tag = OH_HUKS_TAG_KEY_SIZE, .uint32Param = OH_HUKS_RSA_KEY_SIZE_2048},
    {.tag = OH_HUKS_TAG_PURPOSE, .uint32Param = OH_HUKS_KEY_PURPOSE_VERIFY},
    {.tag = OH_HUKS_TAG_DIGEST, .uint32Param = OH_HUKS_DIGEST_SHA256},
    {.tag = OH_HUKS_TAG_PADDING, .uint32Param = OH_HUKS_PADDING_PSS},
    {.tag = OH_HUKS_TAG_BLOCK_MODE, .uint32Param = OH_HUKS_MODE_ECB},
};

#define CHALLENGE_DATA "hi_challenge_data"
static struct OH_Huks_Blob g_challenge = {sizeof(CHALLENGE_DATA), (uint8_t *)CHALLENGE_DATA};
static napi_value AnonAttestKey(napi_env env, napi_callback_info info)
{
    /* 1. Set the key alias. */
    struct OH_Huks_Blob genAlias = {(uint32_t)strlen("test_anon_attest"), (uint8_t *)"test_anon_attest"};
    static struct OH_Huks_Param g_anonAttestParams[] = {
        {.tag = OH_HUKS_TAG_ATTESTATION_CHALLENGE, .blob = g_challenge},
        {.tag = OH_HUKS_TAG_ATTESTATION_ID_ALIAS, .blob = genAlias},
    };
    struct OH_Huks_ParamSet *genParamSet = nullptr;
    struct OH_Huks_ParamSet *anonAttestParamSet = nullptr;
    OH_Huks_Result ohResult;
    OH_Huks_Blob certs = {0};
    OH_Huks_CertChain certChain = {&certs, 0};
    do {
        /* 2. Initialize the key parameter set. */
        ohResult =
            InitParamSet(&genParamSet, g_genAnonAttestParams, sizeof(g_genAnonAttestParams) / sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        ohResult =
            InitParamSet(&anonAttestParamSet, g_anonAttestParams, sizeof(g_anonAttestParams) / sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        ohResult = OH_Huks_GenerateKeyItem(&genAlias, genParamSet, nullptr);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }

        (void)ConstructDataToCertChain(&certChain);
        /* 3. Attest the key. */
        ohResult = OH_Huks_AnonAttestKeyItem(&genAlias, anonAttestParamSet, &certChain);
    } while (0);
    FreeCertChain(&certChain, CERT_COUNT);
    OH_Huks_FreeParamSet(&genParamSet);
    OH_Huks_FreeParamSet(&anonAttestParamSet);
    (void)OH_Huks_DeleteKeyItem(&genAlias, NULL);

    napi_value ret;
    napi_create_int32(env, ohResult.errorCode, &ret);
    return ret;
}
```

## Asynchronous Anonymous Key Attestation

Starting from API version 26.1.0, asynchronous anonymous key attestation is supported. Anonymous attestation involves network communication, and its duration cannot be estimated. When you do not want the calling thread to be blocked by the attestation process (for example, when initiating attestation on the main thread or a latency-sensitive thread), you can use the asynchronous API [OH_Huks_AsyncAnonAttestKeyItem](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_asyncanonattestkeyitem)(): This API returns immediately after the request is accepted by the key management service, and the attestation result (error code and certificate chain) is subsequently delivered through the callback function [OH_Huks_AsyncAnonAttestCallback](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_asyncanonattestcallback)(). If the API returns a non-zero error code, the request was not accepted, and the callback will not be invoked.

> **NOTE**:
>
> The certificate chain is allocated by HUKS and is valid only during callback execution. HUKS releases it after the callback returns. If you need to retain the certificate chain, you must copy the data within the callback.
> The callback may be invoked before the API returns (when the certificate chain has already been generated at acceptance time, for example in software environments without DCM network requests).
> ctxData is held by the caller and is passed to the callback as-is. It can be used to distinguish concurrent requests and can be NULL.
> The callback runs on the IPC thread of HUKS. Do not perform time-consuming operations in the callback; it is recommended to hand the result over to a business thread for processing.

### How to Develop

1. Specify a key alias, construct a key generation parameter set, and generate a key (or use an existing key). This is the same as the steps for anonymous key attestation.

2. Initialize the attestation parameter set. The parameter set content is the same as that for [OH_Huks_AnonAttestKeyItem](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_anonattestkeyitem). Construct it using [OH_Huks_InitParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-param-h.md#oh_huks_initparamset), [OH_Huks_AddParams](../../reference/apis-universal-keystore-kit/capi-native-huks-param-h.md#oh_huks_addparams), and [OH_Huks_BuildParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-param-h.md#oh_huks_buildparamset).

3. Define a result callback function with the signature [OH_Huks_AsyncAnonAttestCallback](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_asyncanonattestcallback)(): In the callback, read the attestation result and certificate chain (copy them within the callback if you need to retain them), and notify the business thread that the result has been delivered.

4. Pass the key alias, the attestation parameter set, the callback function, and the user data ctxData to [OH_Huks_AsyncAnonAttestKeyItem](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_asyncanonattestkeyitem)(). The API returns immediately after accepting the request, and the attestation result is delivered via the callback.

### Development Cases

``` C++
#include "huks/native_huks_api.h"
#include "huks/native_huks_param.h"
#include "napi/native_api.h"
#include <atomic>
#include <cstring>
#include <unistd.h>

/* For the definitions of common functions such as InitParamSet and FreeCertChain, see the example above. */

/* Asynchronous attestation result context: passed in as ctxData and returned in the callback with the attestation result. */
struct AsyncAttestResult {
    std::atomic<uint32_t> done{0};
    int32_t result{-1};
    uint32_t certsCount{0};
};

#define CHALLENGE_DATA "hi_challenge_data"
static struct OH_Huks_Blob g_challenge = {sizeof(CHALLENGE_DATA), (uint8_t *)CHALLENGE_DATA};

static struct OH_Huks_Param g_genAnonAttestParams[] = {
    {.tag = OH_HUKS_TAG_ALGORITHM, .uint32Param = OH_HUKS_ALG_RSA},
    {.tag = OH_HUKS_TAG_KEY_SIZE, .uint32Param = OH_HUKS_RSA_KEY_SIZE_2048},
    {.tag = OH_HUKS_TAG_PURPOSE, .uint32Param = OH_HUKS_KEY_PURPOSE_VERIFY},
    {.tag = OH_HUKS_TAG_DIGEST, .uint32Param = OH_HUKS_DIGEST_SHA256},
    {.tag = OH_HUKS_TAG_PADDING, .uint32Param = OH_HUKS_PADDING_PSS},
    {.tag = OH_HUKS_TAG_BLOCK_MODE, .uint32Param = OH_HUKS_MODE_ECB},
};

/* Asynchronous anonymous attestation result callback: the certificate chain is valid only during callback execution. */
static void AsyncAnonAttestCallback(void *ctxData, int32_t result,
    const struct OH_Huks_CertChain *certChain)
{
    struct AsyncAttestResult *asyncResult = (struct AsyncAttestResult *)ctxData;
    asyncResult->result = result;
    if (result == OH_HUKS_SUCCESS && certChain != nullptr && certChain->certsCount > 0) {
        asyncResult->certsCount = certChain->certsCount;
        /* When the certificate chain needs to be retained, copy the data in certChain->certs here. */
    }
    asyncResult->done = 1;
}

static napi_value AsyncAnonAttestKey(napi_env env, napi_callback_info info)
{
    /* 1. Determine the key alias. */
    struct OH_Huks_Blob genAlias = {(uint32_t)strlen("test_async_anon_attest"),
                                    (uint8_t *)"test_async_anon_attest"};
    static struct OH_Huks_Param g_anonAttestParams[] = {
        {.tag = OH_HUKS_TAG_ATTESTATION_CHALLENGE, .blob = g_challenge},
        {.tag = OH_HUKS_TAG_ATTESTATION_ID_ALIAS, .blob = genAlias},
    };
    struct OH_Huks_ParamSet *genParamSet = nullptr;
    struct OH_Huks_ParamSet *anonAttestParamSet = nullptr;
    struct AsyncAttestResult asyncResult;
    OH_Huks_Result ohResult;
    do {
        /* 2. Initialize the key parameter set. */
        ohResult =
            InitParamSet(&genParamSet, g_genAnonAttestParams, sizeof(g_genAnonAttestParams) / sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        /* 3. Initialize the attestation parameter set. */
        ohResult =
            InitParamSet(&anonAttestParamSet, g_anonAttestParams, sizeof(g_anonAttestParams) / sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        /* 4. Generate the key to be attested. */
        ohResult = OH_Huks_GenerateKeyItem(&genAlias, genParamSet, nullptr);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        /* 5. Initiate asynchronous anonymous attestation: the API returns immediately after accepting the request, and the result is delivered via AsyncAnonAttestCallback. */
        ohResult = OH_Huks_AsyncAnonAttestKeyItem(&genAlias, anonAttestParamSet, AsyncAnonAttestCallback,
                                                 &asyncResult);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        /* 6. Wait for the callback to deliver the result (for demonstration only; in practice, the callback can directly notify the business thread without blocking). */
        for (uint32_t waited = 0; asyncResult.done == 0 && waited < 10000; waited += 10) {
            usleep(10000);
        }
    } while (0);
    OH_Huks_FreeParamSet(&genParamSet);
    OH_Huks_FreeParamSet(&anonAttestParamSet);
    (void)OH_Huks_DeleteKeyItem(&genAlias, NULL);

    /* When the API accepts the request successfully, the final result is subject to the result delivered by the callback. */
    int32_t finalResult = ohResult.errorCode;
    if (finalResult == OH_HUKS_SUCCESS && asyncResult.done != 0) {
        finalResult = asyncResult.result;
    }
    napi_value ret;
    napi_create_int32(env, finalResult, &ret);
    return ret;
}
```

<!--no_check-->