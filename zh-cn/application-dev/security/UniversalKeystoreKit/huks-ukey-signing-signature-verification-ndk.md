# 签名/验签(C/C++)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

以密钥算法为RSA、摘要算法为SHA384、填充模式为PSS的密钥为例，完成签名、验签。具体的场景介绍及支持的算法规格，请参考[签名/验签支持的算法](huks-signing-signature-verification-overview.md#支持的算法)。

## 在CMake脚本中链接相关动态库
```txt
target_link_libraries(entry PUBLIC libhuks_ndk.z.so)
```

## 开发步骤

**签名**

1. 通过[证书管理应用](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenauthorizedialog22)获取resourceId作为密钥别名，并完成PIN码认证后打开资源。

2. 指定待签名的明文数据。

3. 调用[OH_Huks_InitParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-param-h.md#oh_huks_initparamset)指定算法参数配置。

4. 调用[OH_Huks_InitSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_initsession)初始化密钥会话，并获取会话的句柄handle。

5. 调用[OH_Huks_FinishSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_finishsession)结束密钥会话，获取签名signature。

**验签**

1. 通过[证书管理应用](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenauthorizedialog22)获取resourceId作为密钥别名。

2. 获取待验证的签名。

3. 调用[OH_Huks_InitParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-param-h.md#oh_huks_initparamset)指定[算法参数配置](../../reference/apis-universal-keystore-kit/capi-native-huks-param-h.md#oh_huks_initparamset)。

4. 调用[OH_Huks_InitSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_initsession)初始化密钥会话，并获取会话的句柄handle。

5. 调用[OH_Huks_UpdateSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_updatesession)更新密钥会话。

6. 调用[OH_Huks_FinishSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_finishsession)结束密钥会话，验证签名。

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

static struct OH_Huks_Param g_signParamsTest[] = {
    {
        .tag = OH_HUKS_TAG_ALGORITHM,
        .uint32Param = OH_HUKS_ALG_RSA
    }, {
        .tag = OH_HUKS_TAG_PURPOSE,
        .uint32Param = OH_HUKS_KEY_PURPOSE_SIGN
    }, {
        .tag = OH_HUKS_TAG_KEY_SIZE,
        .uint32Param = OH_HUKS_RSA_KEY_SIZE_2048
    }, {
        .tag = OH_HUKS_TAG_PADDING,
        .uint32Param = OH_HUKS_PADDING_PSS
    }, {
        .tag = OH_HUKS_TAG_DIGEST,
        .uint32Param = OH_HUKS_DIGEST_SHA384
    }, {
        .tag = OH_HUKS_TAG_KEY_CLASS,
        .uint32Param = OH_HUKS_KEY_CLASS_EXTENSION
    }
};

static struct OH_Huks_Param g_verifyParamsTest[] = {
    {
        .tag = OH_HUKS_TAG_ALGORITHM,
        .uint32Param = OH_HUKS_ALG_RSA
    }, {
        .tag = OH_HUKS_TAG_PURPOSE,
        .uint32Param = OH_HUKS_KEY_PURPOSE_VERIFY
    }, {
        .tag = OH_HUKS_TAG_KEY_SIZE,
        .uint32Param = OH_HUKS_RSA_KEY_SIZE_2048
    }, {
        .tag = OH_HUKS_TAG_PADDING,
        .uint32Param = OH_HUKS_PADDING_PSS
    }, {
        .tag = OH_HUKS_TAG_DIGEST,
        .uint32Param = OH_HUKS_DIGEST_SHA384
    }, {
        .tag = OH_HUKS_TAG_KEY_CLASS,
        .uint32Param = OH_HUKS_KEY_CLASS_EXTENSION
    }
};

static const uint32_t RSA_COMMON_SIZE = 1024;
static const char *g_dataToSign = "Hks_RSA_Sign_Verify_Test_0000000000000000000000000000000000000000000000000000000"
                                  "00000000000000000000000000000000000000000000000000000000000000000000000000000000"
                                  "0000000000000000000000000000000000000000000000000000000000000000000000000_string";
static const char *keyAlias = "{\"providerName\":\"testProviderName\",\"abilityName\":\"CryptoExtension\","
                              "\"bundleName\":\"com.example.cryptoapplication\",\"index\":{\"key\":\"testKey\"}}";

static napi_value SignVerifyKey(napi_env env, napi_callback_info info) 
{
    // 假设g_keyAlias是获取的resourceId
    struct OH_Huks_Blob g_keyAlias = {
        (uint32_t)strlen(keyAlias),
        (uint8_t *)keyAlias
    };
    struct OH_Huks_Blob inData = {
        (uint32_t)strlen(g_dataToSign),
        (uint8_t *)g_dataToSign
    };
    struct OH_Huks_ParamSet *signParamSet = nullptr;
    struct OH_Huks_ParamSet *verifyParamSet = nullptr;
    OH_Huks_Result ohResult;
    do {
        ohResult = InitParamSet(&signParamSet, g_signParamsTest, sizeof(g_signParamsTest) / sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        ohResult = InitParamSet(&verifyParamSet, g_verifyParamsTest,
            sizeof(g_verifyParamsTest) / sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        /* 1. Sign */
        // Init
        uint8_t handleS[sizeof(uint64_t)] = {0};
        struct OH_Huks_Blob handleSign = { (uint32_t)sizeof(uint64_t), handleS };
        ohResult = OH_Huks_InitSession(&g_keyAlias, signParamSet, &handleSign, nullptr);
        // Update
        uint8_t outDataS[RSA_COMMON_SIZE] = {0};
        struct OH_Huks_Blob outDataSign = { RSA_COMMON_SIZE, outDataS };
        ohResult = OH_Huks_UpdateSession(&handleSign, signParamSet,  &inData, &outDataSign);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        // Finish
        struct OH_Huks_Blob finishInData = { 0, NULL };
        ohResult = OH_Huks_FinishSession(&handleSign, signParamSet, &finishInData, &outDataSign);
        
        /* 2. Verify */
        // Init
        uint8_t handleV[sizeof(uint64_t)] = {0};
        struct OH_Huks_Blob handleVerify = { (uint32_t)sizeof(uint64_t), handleV };
        ohResult = OH_Huks_InitSession(&g_keyAlias, verifyParamSet, &handleVerify, nullptr);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        // Update loop
        uint8_t temp[] = "out";
        struct OH_Huks_Blob verifyOut = { (uint32_t)sizeof(temp), temp };
        ohResult = OH_Huks_UpdateSession(&handleVerify, verifyParamSet, &inData, &verifyOut);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        // Finish
        ohResult = OH_Huks_FinishSession(&handleVerify, verifyParamSet, &outDataSign, &verifyOut);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
    } while (0);
    OH_Huks_FreeParamSet(&signParamSet);
    OH_Huks_FreeParamSet(&verifyParamSet);
    
    napi_value ret;
    napi_create_int32(env, ohResult.errorCode, &ret);
    return ret;
}
```