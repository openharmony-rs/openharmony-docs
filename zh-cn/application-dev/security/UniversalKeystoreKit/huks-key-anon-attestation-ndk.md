# 匿名密钥证明(C/C++)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

在使用本功能时，需确保网络通畅。

## 在CMake脚本中链接相关动态库
```txt
target_link_libraries(entry PUBLIC libhuks_ndk.z.so)
```

## 开发步骤

1. 指定密钥别名，密钥别名命名规范参考[密钥生成介绍及算法规格](huks-key-generation-overview.md)。

2. 初始化参数集：通过[OH_Huks_InitParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-param-h.md#oh_huks_initparamset)、[OH_Huks_AddParams](../../reference/apis-universal-keystore-kit/capi-native-huks-param-h.md#oh_huks_addparams)、[OH_Huks_BuildParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-param-h.md#oh_huks_buildparamset)构造参数集paramSet，参数集中必须包含[OH_Huks_KeyAlg](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_keyalg)，[OH_Huks_KeySize](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_keysize)，[OH_Huks_KeyPurpose](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_keypurpose)属性。

3. 将密钥别名与参数集作为参数传入[OH_Huks_AnonAttestKeyItem](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_anonattestkeyitem)方法中，即可证明密钥。

## 开发案例
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
    /* 1.确定密钥别名 */
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
        /* 2.初始化密钥参数集 */
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
        /* 3.证明密钥 */
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

## 异步匿名密钥证明

从API版本26.1.0开始，支持异步匿名密钥证明能力。匿名证明涉及网络通信，耗时不可预估。当不希望调用线程被证明流程阻塞时（例如在主线程或时延敏感线程上发起证明），可以使用异步接口[OH_Huks_AsyncAnonAttestKeyItem](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_asyncanonattestkeyitem)()：该接口在请求被密钥管理服务受理后立即返回，证明结果（错误码和证书链）后续通过回调函数[OH_Huks_AsyncAnonAttestCallback](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_asyncanonattestcallback)()送达。若接口返回非0错误码，表示请求未被受理，回调不会被调用。

> **说明**：
>
> 证书链由HUKS分配，仅在回调执行期间有效，HUKS会在回调返回后释放；需要保留证书链时，必须在回调内复制数据。
> 回调可能在接口返回前被调用（当受理时证书链已经生成，如无DCM网络请求的软件环境）。
> ctxData由调用方持有，原样透传给回调，可用于区分并发请求，可以为NULL。
> 回调在HUKS的IPC线程中执行，回调内不应执行耗时操作，建议将结果转交业务线程处理。

### 开发步骤

1. 指定密钥别名，构造密钥生成参数集并生成密钥（或使用已有密钥），与匿名密钥证明的步骤相同。

2. 初始化证明参数集：参数集内容与[OH_Huks_AnonAttestKeyItem](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_anonattestkeyitem)相同，通过[OH_Huks_InitParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-param-h.md#oh_huks_initparamset)、[OH_Huks_AddParams](../../reference/apis-universal-keystore-kit/capi-native-huks-param-h.md#oh_huks_addparams)、[OH_Huks_BuildParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-param-h.md#oh_huks_buildparamset)构造。

3. 定义结果回调函数，签名为[OH_Huks_AsyncAnonAttestCallback](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_asyncanonattestcallback)()：在回调中读取证明结果和证书链（需要保留时在回调内复制），并通知业务线程结果已送达。

4. 将密钥别名、证明参数集、回调函数和用户数据ctxData传入[OH_Huks_AsyncAnonAttestKeyItem](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_asyncanonattestkeyitem)()，接口受理后立即返回，证明结果经回调送达。

### 开发案例

``` C++
#include "huks/native_huks_api.h"
#include "huks/native_huks_param.h"
#include "napi/native_api.h"
#include <atomic>
#include <cstring>
#include <unistd.h>

/* InitParamSet、FreeCertChain等公共函数的定义见上文示例 */

/* 异步证明结果上下文：作为ctxData传入，在回调中带回证明结果 */
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

/* 异步匿名证明结果回调：证书链仅在回调执行期间有效 */
static void AsyncAnonAttestCallback(void *ctxData, int32_t result,
    const struct OH_Huks_CertChain *certChain)
{
    struct AsyncAttestResult *asyncResult = (struct AsyncAttestResult *)ctxData;
    asyncResult->result = result;
    if (result == OH_HUKS_SUCCESS && certChain != nullptr && certChain->certsCount > 0) {
        asyncResult->certsCount = certChain->certsCount;
        /* 需要保留证书链时，必须在此处复制certChain->certs中的数据 */
    }
    asyncResult->done = 1;
}

static napi_value AsyncAnonAttestKey(napi_env env, napi_callback_info info)
{
    /* 1.确定密钥别名 */
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
        /* 2.初始化密钥参数集 */
        ohResult =
            InitParamSet(&genParamSet, g_genAnonAttestParams, sizeof(g_genAnonAttestParams) / sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        /* 3.初始化证明参数集 */
        ohResult =
            InitParamSet(&anonAttestParamSet, g_anonAttestParams, sizeof(g_anonAttestParams) / sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        /* 4.生成待证明的密钥 */
        ohResult = OH_Huks_GenerateKeyItem(&genAlias, genParamSet, nullptr);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        /* 5.发起异步匿名证明：接口受理后立即返回，结果经AsyncAnonAttestCallback送达 */
        ohResult = OH_Huks_AsyncAnonAttestKeyItem(&genAlias, anonAttestParamSet, AsyncAnonAttestCallback,
                                                 &asyncResult);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        /* 6.等待回调送达结果（仅为演示；实际应用中可由回调直接通知业务线程，无需阻塞等待） */
        for (uint32_t waited = 0; asyncResult.done == 0 && waited < 10000; waited += 10) {
            usleep(10000);
        }
    } while (0);
    OH_Huks_FreeParamSet(&genParamSet);
    OH_Huks_FreeParamSet(&anonAttestParamSet);
    (void)OH_Huks_DeleteKeyItem(&genAlias, NULL);

    /* 接口受理成功时，最终结果以回调送达的结果为准 */
    int32_t finalResult = ohResult.errorCode;
    if (finalResult == OH_HUKS_SUCCESS && asyncResult.done != 0) {
        finalResult = asyncResult.result;
    }
    napi_value ret;
    napi_create_int32(env, finalResult, &ret);
    return ret;
}
```