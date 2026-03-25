# Registering and Unregistering a Provider (C/C++)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

From API version 22, **huksExternalCrypto** provides the APIs for registering and unregistering a Provider.

## Registering a Provider

### Linking the Dynamic Library in the CMake Script
```txt
target_link_libraries(entry PUBLIC libhuks_ndk.z.so libhuks_external_crypto.z.so)
```

### How to Develop

1. Construct registration parameters. You need to pass [OH_HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-type-h.md#oh_huks_externalcryptotag).

2. Call [OH_Huks_RegisterProvider](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_registerprovider).

```c++
#include "napi/native_api.h"
#include "huks/native_huks_api.h"
#include "huks/native_huks_type.h"
#include "huks/native_huks_param.h"
#include "huks/native_huks_external_crypto_api.h"
#include <cstring>

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

static struct OH_Huks_Blob g_abilityName = {
    (uint32_t)strlen("testAbility"),
    (uint8_t *)"testAbility"
};

struct OH_Huks_Blob g_providerName = {
    (uint32_t)strlen("testProviderName"),
    (uint8_t *)"testProviderName"
};

static struct OH_Huks_ExternalCryptoParam g_abilityParams[] = {
    {
        .tag = OH_HUKS_EXT_CRYPTO_TAG_ABILITY_NAME,
        .blob = g_abilityName
    },
};

static napi_value registerProvider(napi_env env, napi_callback_info info) 
{
    struct OH_Huks_ExternalCryptoParamSet *providerParamSet = nullptr;
    OH_Huks_Result ohResult;
    do {
        ohResult = InitParamSet(&providerParamSet, g_abilityParams,
            sizeof(g_abilityParams) / sizeof(OH_Huks_ExternalCryptoParam));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        ohResult = OH_Huks_RegisterProvider(&g_providerName, providerParamSet);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
    } while (0);
    OH_Huks_FreeExternalCryptoParamSet(&providerParamSet);

    napi_value ret;
    napi_create_int32(env, ohResult.errorCode, &ret);
    return ret;
}
```

## Unregistering a Provider

### Linking the Dynamic Library in the CMake Script
```txt
target_link_libraries(entry PUBLIC libhuks_ndk.z.so libhuks_external_crypto.z.so)
```

### How to Develop

1. Construct unregistration parameters. To unregister a single ability, you need to pass [OH_HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-type-h.md#oh_huks_externalcryptotag). This parameter does not need to be passed for batch unregistration.

2. Call [OH_Huks_UnregisterProvider](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_unregisterprovider).

**Single unregistration**
```c++
#include "napi/native_api.h"
#include "huks/native_huks_api.h"
#include "huks/native_huks_type.h"
#include "huks/native_huks_param.h"
#include "huks/native_huks_external_crypto_api.h"
#include <cstring>

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

static struct OH_Huks_Blob g_abilityName = {
    (uint32_t)strlen("testAbility"),
    (uint8_t *)"testAbility"
};

struct OH_Huks_Blob g_providerName = {
    (uint32_t)strlen("testProviderName"),
    (uint8_t *)"testProviderName"
};

static struct OH_Huks_ExternalCryptoParam g_abilityParams[] = {
    {
        .tag = OH_HUKS_EXT_CRYPTO_TAG_ABILITY_NAME,
        .blob = g_abilityName
    },
};

static napi_value unregisterProvider(napi_env env, napi_callback_info info) 
{
    struct OH_Huks_ExternalCryptoParamSet *providerParamSet = nullptr;
    OH_Huks_Result ohResult;
    do {
        ohResult = InitParamSet(&providerParamSet, g_abilityParams,
            sizeof(g_abilityParams) / sizeof(OH_Huks_ExternalCryptoParam));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        ohResult = OH_Huks_UnregisterProvider(&g_providerName, providerParamSet);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
    } while (0);
    OH_Huks_FreeExternalCryptoParamSet(&providerParamSet);

    napi_value ret;
    napi_create_int32(env, ohResult.errorCode, &ret);
    return ret;
}
```

**Batch unregistration**
```c++
#include "napi/native_api.h"
#include "huks/native_huks_api.h"
#include "huks/native_huks_type.h"
#include "huks/native_huks_param.h"
#include "huks/native_huks_external_crypto_api.h"
#include <cstring>

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

static struct OH_Huks_Blob g_abilityName = {
    (uint32_t)strlen("testAbility"),
    (uint8_t *)"testAbility"
};

struct OH_Huks_Blob g_providerName = {
    (uint32_t)strlen("testProviderName"),
    (uint8_t *)"testProviderName"
};

static struct OH_Huks_ExternalCryptoParam g_abilityParams[] = {};

static napi_value unregisterProvider(napi_env env, napi_callback_info info) 
{
    struct OH_Huks_ExternalCryptoParamSet *providerParamSet = nullptr;
    OH_Huks_Result ohResult;
    do {
        ohResult = InitParamSet(&providerParamSet, g_abilityParams,
            sizeof(g_abilityParams) / sizeof(OH_Huks_ExternalCryptoParam));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        ohResult = OH_Huks_UnregisterProvider(&g_providerName, providerParamSet);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
    } while (0);
    OH_Huks_FreeExternalCryptoParamSet(&providerParamSet);

    napi_value ret;
    napi_create_int32(env, ohResult.errorCode, &ret);
    return ret;
}
```
