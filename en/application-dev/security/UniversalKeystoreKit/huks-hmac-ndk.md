# HMAC (C/C++)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

Hash-based Message Authentication Code (HMAC) is a specific type of message authentication code (MAC) involving a cryptographic has function and a secret cryptographic key. For details about the scenarios and supported algorithm specifications, see [HMAC Overview and Algorithm Specifications](huks-hmac-overview.md).

## Add the dynamic library in the CMake script.
```txt
target_link_libraries(entry PUBLIC libhuks_ndk.z.so)
```

## How to Develop

**Key Generation**

1. Specify the key alias. For details about the naming rules, see [Key Generation Overview and Algorithm Specifications](huks-key-generation-overview.md).

2. Initialize the key property set.

3. Use [OH_Huks_GenerateKeyItem](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_generatekeyitem) to generate a key. For details about the HMAC specifications supported, see [Supported Algorithms](huks-key-generation-overview.md#supported-algorithms).

You can also import a key. For details about the supported algorithms, see [Supported Algorithms](huks-key-import-overview.md#supported-algorithms).

**HMAC Generation**

1. Obtain the key alias.

2. Obtains the data to be calculated.

3. Use [OH_Huks_InitParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-param-h.md#oh_huks_initparamset) to set algorithm parameters.
   
4. Use [OH_Huks_InitSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_initsession) to initialize a key session and obtain the session handle.

5. Call [OH_Huks_FinishSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_finishsession) to finish the key session and obtain the hashed data.

```c++
#include "huks/native_huks_api.h"
#include "huks/native_huks_param.h"
#include "napi/native_api.h"
#include <string.h>

OH_Huks_Result InitParamSet(
    struct OH_Huks_ParamSet **paramSet,
    const struct OH_Huks_Param *params,
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

static struct OH_Huks_Param g_genHmacParams[] = {
    {
        .tag = OH_HUKS_TAG_ALGORITHM,
        .uint32Param = OH_HUKS_ALG_HMAC
    }, {
        .tag = OH_HUKS_TAG_PURPOSE,
        .uint32Param = OH_HUKS_KEY_PURPOSE_MAC
    }, {
        .tag = OH_HUKS_TAG_KEY_SIZE,
        .uint32Param = OH_HUKS_AES_KEY_SIZE_256
    }, {
        .tag = OH_HUKS_TAG_DIGEST,
        .uint32Param = OH_HUKS_DIGEST_SHA384
    }
};
static const uint32_t HMAC_COMMON_SIZE = 1024;
OH_Huks_Result HksHmacTest(
    const struct OH_Huks_Blob *keyAlias,	
    const struct OH_Huks_ParamSet *hmacParamSet,
    const struct OH_Huks_Blob *inData,
    struct OH_Huks_Blob *hashText)
{
    uint8_t handleE[sizeof(uint64_t)] = {0};
    struct OH_Huks_Blob handle = {sizeof(uint64_t), handleE};
    OH_Huks_Result ret = OH_Huks_InitSession(keyAlias, hmacParamSet, &handle, nullptr);
    if (ret.errorCode != OH_HUKS_SUCCESS) {
        return ret;
    }
    ret = OH_Huks_FinishSession(&handle, hmacParamSet, inData, hashText);
    return ret;
}

static napi_value HmacKey(napi_env env, napi_callback_info info)
{
    /* 1. Generate Key */
    /*
     * Simulate the key generation scenario.
     * 1.1. Set the key alias.
     */
    char tmpKeyAlias[] = "test_hmac";
    struct OH_Huks_Blob keyAlias = {(uint32_t)strlen(tmpKeyAlias), (uint8_t *)tmpKeyAlias};
    struct OH_Huks_ParamSet *hmacParamSet = nullptr;
    OH_Huks_Result ohResult;
    do {
        /*
         * 1.2. Obtain the parameters for key generation.
         */
        ohResult = InitParamSet(&hmacParamSet, g_genHmacParams, sizeof(g_genHmacParams) / sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        /*
         * 1.3. Call generateKeyItem to generate a key.
         */
        ohResult = OH_Huks_GenerateKeyItem(&keyAlias, hmacParamSet, nullptr);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        /* 2. HMAC */
        /*
         * Simulate a hash scenario.
         * 2.1. Obtain the key alias.
         */
        /*
         * 2.2. Obtain the data to be hashed.
         */
        char tmpInData[] = "HMAC_MAC_INDATA_1";
        struct OH_Huks_Blob inData = {(uint32_t)strlen(tmpInData), (uint8_t *)tmpInData};
        uint8_t cipher[HMAC_COMMON_SIZE] = {0};
        struct OH_Huks_Blob hashText = {HMAC_COMMON_SIZE, cipher};
        /*
         * 2.3. Call initSession to obtain a session handle.
         */
        /*
         * 2.4. Call finishSession to obtain the hashed data.
         */
        ohResult = HksHmacTest(&keyAlias, hmacParamSet, &inData, &hashText);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
    } while (0);
    OH_Huks_FreeParamSet(&hmacParamSet);
    napi_value ret;
    napi_create_int32(env, ohResult.errorCode, &ret);
    return ret;
}
```
