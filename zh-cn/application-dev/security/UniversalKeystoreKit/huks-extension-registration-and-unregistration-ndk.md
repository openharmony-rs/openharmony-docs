# 注册/注销(C/C++)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

从API版本22开始，huksExternalCrypto提供Provider注册和注销功能接口。

## 开发准备

1. 在CMake脚本中链接相关动态库：
```txt
target_link_libraries(entry PUBLIC libhuks_ndk.z.so libhuks_external_crypto.z.so)
```

2. 撰写公共工具函数，以下工具函数被所有示例共用，建议在实际项目中放置于公共源文件：

```c++
#include "napi/native_api.h"
#include "huks/native_huks_api.h"
#include "huks/native_huks_type.h"
#include "huks/native_huks_param.h"
#include "huks/native_huks_external_crypto_api.h"
#include "huks/native_huks_external_crypto_type.h"
#include <cstring>
#include <string>

// 初始化参数集
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

// 字符串 → Blob
struct OH_Huks_Blob StringToBlob(const std::string &str)
{
    return { (uint32_t)str.size(), (uint8_t *)str.c_str() };
}
```

## 注册Provider

密钥管理扩展应用检测到密钥管理设备或服务可用时，向系统注册CryptoExtensionAbility。具体的可用性检测方式因接入的设备/服务形态而异，例如UKey物理设备监听USB插拔事件、数字盾（虚拟智能卡）在应用启动或服务就绪时检测。详细规格见[注册注销](huks-extension-ability-support-overview.md#注册注销)。

### 开发步骤

1. 构造注册参数，需要传入[OH_HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-type-h.md#oh_huks_externalcryptotag)。

2. 调用注册接口[OH_Huks_RegisterProvider](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_registerprovider)。

## 开发案例

```c++
static napi_value RegisterProvider(napi_env env, napi_callback_info info)
{
    // providerName 建议包含厂商+产品信息以保证全局唯一
    auto providerName = StringToBlob("VendorA_ProductX");
    // abilityName 须与 module.json5 中 extensionAbilities.name 保持一致
    auto abilityName = StringToBlob("CryptoExtensionAbility1");

    struct OH_Huks_ExternalCryptoParam params[] = {
        { .tag = OH_HUKS_EXT_CRYPTO_TAG_ABILITY_NAME, .blob = abilityName }
    };

    struct OH_Huks_ExternalCryptoParamSet *providerParamSet = nullptr;
    OH_Huks_Result ohResult;
    do {
        ohResult = InitParamSet(&providerParamSet, params,
            sizeof(params) / sizeof(OH_Huks_ExternalCryptoParam));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) break;
        ohResult = OH_Huks_RegisterProvider(&providerName, providerParamSet);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) break;
    } while (0);
    OH_Huks_FreeExternalCryptoParamSet(&providerParamSet);

    napi_value ret;
    napi_create_int32(env, ohResult.errorCode, &ret);
    return ret;
}
```

## 注销Provider

密钥管理扩展应用检测到密钥管理设备或服务不可用时，从系统注销CryptoExtensionAbility。具体的可用性检测方式因接入的设备/服务形态而异，例如UKey物理设备监听USB插拔事件、数字盾（虚拟智能卡）在应用退出时检测。详细规格见[注册注销](huks-extension-ability-support-overview.md#注册注销)。

### 开发步骤

1. 构造注销参数，注销单个ability需要传入[OH_HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-type-h.md#oh_huks_externalcryptotag)。批量注销不需要传入[OH_HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-type-h.md#oh_huks_externalcryptotag)。

2. 调用注销接口[OH_Huks_UnregisterProvider](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_unregisterprovider)。

**注销单个ability**
```c++
static napi_value UnregisterSingleAbility(napi_env env, napi_callback_info info)
{
    auto providerName = StringToBlob("VendorA_ProductX");
    auto abilityName = StringToBlob("CryptoExtensionAbility1");

    struct OH_Huks_ExternalCryptoParam params[] = {
        { .tag = OH_HUKS_EXT_CRYPTO_TAG_ABILITY_NAME, .blob = abilityName }
    };

    struct OH_Huks_ExternalCryptoParamSet *providerParamSet = nullptr;
    OH_Huks_Result ohResult;
    do {
        ohResult = InitParamSet(&providerParamSet, params,
            sizeof(params) / sizeof(OH_Huks_ExternalCryptoParam));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) break;
        ohResult = OH_Huks_UnregisterProvider(&providerName, providerParamSet);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) break;
    } while (0);
    OH_Huks_FreeExternalCryptoParamSet(&providerParamSet);

    napi_value ret;
    napi_create_int32(env, ohResult.errorCode, &ret);
    return ret;
}
```

**批量注销**
```c++
static napi_value UnregisterAllAbilities(napi_env env, napi_callback_info info)
{
    auto providerName = StringToBlob("VendorA_ProductX");

    // 批量注销：extProperties 留空
    struct OH_Huks_ExternalCryptoParam params[] = {};

    struct OH_Huks_ExternalCryptoParamSet *providerParamSet = nullptr;
    OH_Huks_Result ohResult;
    do {
        ohResult = InitParamSet(&providerParamSet, params, 0);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) break;
        ohResult = OH_Huks_UnregisterProvider(&providerName, providerParamSet);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) break;
    } while (0);
    OH_Huks_FreeExternalCryptoParamSet(&providerParamSet);

    napi_value ret;
    napi_create_int32(env, ohResult.errorCode, &ret);
    return ret;
}
```