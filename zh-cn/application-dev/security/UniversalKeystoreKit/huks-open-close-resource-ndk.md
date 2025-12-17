# 打开资源/关闭资源(C/C++)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

## 打开资源
应用密钥操作之前（密钥操作、通用操作、PIN码认证等），需要先调用[OH_Huks_OpenResource](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_openresource)打开资源。打开资源需要获取resourceId，resourceId通过[证书管理应用](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenauthorizedialog22)获取。

### 在CMake脚本中链接相关动态库
```txt
target_link_libraries(entry PUBLIC libhuks_ndk.z.so)
```

### 开发步骤

1. 通过[证书管理应用](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenauthorizedialog22)获取resourceId。

2. 调用[OH_Huks_InitExternalCryptoParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_initexternalcryptoparamset)初始化参数集。

3. 调用[OH_Huks_AddExternalCryptoParams](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_addexternalcryptoparams)添加输入参数。

4. 调用[OH_Huks_BuildExternalCryptoParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_buildexternalcryptoparamset)构建参数集。

5. 调用[OH_Huks_OpenResource](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_openresource)打开资源。

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

static struct OH_Huks_ExternalCryptoParam g_openResourceParamsTest[] = {};

static napi_value OpenResource(napi_env env, napi_callback_info info) 
{
    struct OH_Huks_Blob g_resourceId = {
        (uint32_t)strlen(resourceId),
        (uint8_t *)resourceId
    };
    struct OH_Huks_ExternalCryptoParamSet *openResourceParamSet = nullptr;
    OH_Huks_Result ohResult;
    do {
        ohResult = InitParamSet(&openResourceParamSet, g_openResourceParamsTest,
            sizeof(g_openResourceParamsTest) / sizeof(OH_Huks_ExternalCryptoParam));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        ohResult = OH_Huks_OpenResource(&g_resourceId, openResourceParamSet);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
    } while (0);
    OH_Huks_FreeExternalCryptoParamSet(&openResourceParamSet);
    
    napi_value ret;
    napi_create_int32(env, ohResult.errorCode, &ret);
    return ret;
}
```

## 关闭资源

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

生态应用调用证书HAP界面，展示证书列表，用户选择证书，生态应用拿到对应的resourceId，关闭资源依赖于对应的resourceId。具体的场景介绍及规格，请参考[资源管理介绍及规格](huks-resource-management-overview.md)。

### 在CMake脚本中链接相关动态库
```txt
target_link_libraries(entry PUBLIC libhuks_ndk.z.so)
```

### 开发步骤

1. 通过[证书管理应用](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenauthorizedialog22)获取resourceId。

2. 调用[OH_Huks_InitExternalCryptoParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_initexternalcryptoparamset)初始化参数集。

3. 调用[OH_Huks_AddExternalCryptoParams](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_addexternalcryptoparams)添加输入参数。

4. 调用[OH_Huks_BuildExternalCryptoParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_buildexternalcryptoparamset)构建参数集。

5. 调用[OH_Huks_CloseResource](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_closeresource)关闭资源。

```c++
#include "huks/native_huks_external_crypto_api.h"
#include "huks/native_huks_param.h"
#include "huks/native_huks_type.h"
#include "huks/native_huks_api.h"
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

static struct OH_Huks_ExternalCryptoParam g_closeResourceParamsTest[] = {};

static napi_value CloseResource(napi_env env, napi_callback_info info) 
{
    struct OH_Huks_Blob g_resourceId = {
        (uint32_t)strlen(resourceId),
        (uint8_t *)resourceId
    };
    struct OH_Huks_ExternalCryptoParamSet *closeResourceParamSet = nullptr;
    OH_Huks_Result ohResult;
    do {
        ohResult = InitParamSet(&closeResourceParamSet, g_closeResourceParamsTest,
            sizeof(g_closeResourceParamsTest) / sizeof(OH_Huks_ExternalCryptoParam));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        ohResult = OH_Huks_CloseResource(&g_resourceId, closeResourceParamSet);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
    } while (0);
    OH_Huks_FreeExternalCryptoParamSet(&closeResourceParamSet);
    
    napi_value ret;
    napi_create_int32(env, ohResult.errorCode, &ret);
    return ret;
}
```