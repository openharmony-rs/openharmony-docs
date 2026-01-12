# 查询认证状态(C/C++)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

从API 22开始，huksExternalCrypto提供PIN码认证状态查询功能接口。应用可以通过该接口查询PIN码是否认证通过。具体的场景介绍及规格，请参考[Ukey PIN码认证介绍及规格](huks-ukey-pin-authentication-management-overview.md)。

## 在CMake脚本中链接相关动态库
```txt
target_link_libraries(entry PUBLIC libhuks_ndk.z.so libhuks_external_crypto.z.so)
```

## 开发步骤

1. 通过[证书管理应用](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenauthorizedialog22)获取[keyUri](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certreference22)作为resourceId。

2. 调用[OH_Huks_InitExternalCryptoParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_initexternalcryptoparamset)指定参数配置。

3. 调用[OH_Huks_GetUkeyPinAuthState](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_getukeypinauthstate)获取PIN码认证状态。


```c++
#include "huks/native_huks_external_crypto_api.h"
#include "huks/native_huks_param.h"
#include "napi/native_api.h"
#include <string.h>

OH_Huks_Result InitParamSet(
    struct OH_Huks_ExternalCryptoParamSet **paramSet,
    const struct OH_Huks_ExternalCryptoParam *params,
    uint32_t paramCount)
{
    OH_Huks_Result ret = OH_Huks_InitExternalCryptoParamSet(paramSet);
    if (ret.errorCode != OH_HUKS_SUCCESS) {
        return ret;
    }
    ret = OH_Huks_AddExternalCryptoParams(*paramSet, params, paramCount);
    if (ret.errorCode != OH_HUKS_SUCCESS) {
        OH_Huks_FreeExternalCryptoParamSet(paramSet);
        return ret;
    }
    ret = OH_Huks_BuildExternalCryptoParamSet(paramSet);
    if (ret.errorCode != OH_HUKS_SUCCESS) {
        OH_Huks_FreeExternalCryptoParamSet(paramSet);
        return ret;
    }
    return ret;
}

static const char *resourceId = "{\"providerName\":\"testProviderName\",\"abilityName\":\"CryptoExtension\",\"bundleName\":\"com.example.cryptoapplication\",\"index\":{\"key\":\"testKey\"}}";

static struct OH_Huks_ExternalCryptoParam g_getPinStateParamsTest[] = {};

static napi_value GetUkeyPinAuthState(napi_env env, napi_callback_info info) 
{
    struct OH_Huks_Blob g_resourceId = {
        (uint32_t)strlen(resourceId),
        (uint8_t *)resourceId
    };
    struct OH_Huks_ExternalCryptoParamSet *pinStateParamSet = nullptr;
    OH_Huks_ExternalPinAuthState authState = OH_HUKS_EXT_CRYPTO_PIN_NO_AUTH;
    OH_Huks_Result ohResult;
    do {
        ohResult = InitParamSet(&pinStateParamSet, g_getPinStateParamsTest,
            sizeof(g_getPinStateParamsTest) / sizeof(OH_Huks_ExternalCryptoParam));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        ohResult = OH_Huks_GetUkeyPinAuthState(&g_resourceId, pinStateParamSet, &authState);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
    } while (0);
    OH_Huks_FreeExternalCryptoParamSet(&pinStateParamSet);
    
    napi_value ret;
    napi_create_int32(env, ohResult.errorCode, &ret);
    return ret;
}
```