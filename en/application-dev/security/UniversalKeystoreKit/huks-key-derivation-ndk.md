# Key Derivation (C/C++)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

This topic walks you through on how to derive a key using HKDF and PBKDF2. For details about the scenarios and supported algorithm specifications, see [Supported Algorithms](huks-key-derivation-overview.md#supported-algorithms).

## Linking the Dynamic Library in the CMake Script
```txt
target_link_libraries(entry PUBLIC libhuks_ndk.z.so)
```

## How to Develop

**Key Generation**

1. Specify the key alias. For details about the naming rules, see [Key Generation Overview and Algorithm Specifications](huks-key-generation-overview.md).

2. Initialize the key property set. You can set **OH_HUKS_TAG_DERIVED_AGREED_KEY_STORAGE_FLAG** (optional) to specify how the key derived from this key is managed.

    - If this tag is set to **OH_HUKS_STORAGE_ONLY_USED_IN_HUKS**, the derived key is managed by HUKS. That is, the derived key is always in a secure environment throughout its lifecycle.

    - If this tag is set to **OH_HUKS_STORAGE_KEY_EXPORT_ALLOWED**, the derived key will be returned to the caller for management. That is, the service side ensures the key security.

    - If this tag is not set, the derived key can be either managed by HUKS or returned to the caller for management. The key protection mode can be set in the subsequent key derivation on the service side.

3. Use [OH_Huks_GenerateKeyItem](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_generatekeyitem) to generate a key. For details, see [Key Generation Overview and Algorithm Specifications](huks-key-generation-overview.md).

Alternatively, you can [import a key](huks-key-import-overview.md).

**Key Derivation**

1. Obtain the key alias and set the **HuksOptions** parameter.

   You can set **OH_HUKS_TAG_DERIVED_AGREED_KEY_STORAGE_FLAG** to specify how the derived key is managed.

    | Key Generation| Key Derivation| Specifications|
    | -------- | -------- | -------- |
    | OH_HUKS_STORAGE_ONLY_USED_IN_HUKS | OH_HUKS_STORAGE_ONLY_USED_IN_HUKS | The key is managed by HUKS.|
    | OH_HUKS_STORAGE_KEY_EXPORT_ALLOWED | OH_HUKS_STORAGE_KEY_EXPORT_ALLOWED | The key is returned to the caller for management.|
    | The tag is not set.| OH_HUKS_STORAGE_ONLY_USED_IN_HUKS | The key is managed by HUKS.|
    | The tag is not set.| OH_HUKS_STORAGE_KEY_EXPORT_ALLOWED | The key is returned to the caller for management.|
    | The tag is not set.| The tag is not set.| The key is returned to the caller for management.|

    Note: The tag value set in key derivation should not conflict with the tag value set in key generation. The above table lists only valid settings.

2. Use [OH_Huks_InitSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_initsession) to initialize a key session and obtain the session handle.

3. Use [OH_Huks_UpdateSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_updatesession) to update the key session.

4. Use [OH_Huks_FinishSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_finishsession) to end the key session and finish derivation.

**Key Deletion**

Use **OH_Huks_DeleteKeyItem** to delete the key that is not required. For details, see [Deleting a Key](huks-delete-key-ndk.md).

## Development Cases
### HKDF
<!-- @[key_derivation_hkdf256_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/KeyUsage/KeyDerivation/entry/src/main/cpp/types/projects/napi_hkdf256.cpp) -->

``` C++
#include "huks/native_huks_api.h"
#include "huks/native_huks_param.h"
#include "napi/native_api.h"
#include <cstring>

static OH_Huks_Result InitParamSet(struct OH_Huks_ParamSet **paramSet, const struct OH_Huks_Param *params,
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

static const uint32_t DERIVE_KEY_SIZE_32 = 32;
static const uint32_t DERIVE_KEY_SIZE_256 = 256;
static struct OH_Huks_Blob g_deriveKeyAlias = {(uint32_t)strlen("test_derive"), (uint8_t *)"test_derive"};
static struct OH_Huks_Param g_genDeriveParams[] = {
    {.tag = OH_HUKS_TAG_ALGORITHM, .uint32Param = OH_HUKS_ALG_AES},
    {.tag = OH_HUKS_TAG_PURPOSE, .uint32Param = OH_HUKS_KEY_PURPOSE_DERIVE},
    {.tag = OH_HUKS_TAG_DIGEST, .uint32Param = OH_HUKS_DIGEST_SHA256},
    {.tag = OH_HUKS_TAG_KEY_SIZE, .uint32Param = OH_HUKS_AES_KEY_SIZE_256}};
static struct OH_Huks_Param g_hkdfParams[] = {{.tag = OH_HUKS_TAG_ALGORITHM, .uint32Param = OH_HUKS_ALG_HKDF},
                                              {.tag = OH_HUKS_TAG_PURPOSE, .uint32Param = OH_HUKS_KEY_PURPOSE_DERIVE},
                                              {.tag = OH_HUKS_TAG_DIGEST, .uint32Param = OH_HUKS_DIGEST_SHA256},
                                              {.tag = OH_HUKS_TAG_DERIVE_KEY_SIZE, .uint32Param = DERIVE_KEY_SIZE_32}};
static struct OH_Huks_Param g_hkdfFinishParams[] = {
    {.tag = OH_HUKS_TAG_DERIVED_AGREED_KEY_STORAGE_FLAG, .uint32Param = OH_HUKS_STORAGE_ONLY_USED_IN_HUKS},
    {.tag = OH_HUKS_TAG_KEY_ALIAS, .blob = g_deriveKeyAlias},
    {.tag = OH_HUKS_TAG_ALGORITHM, .uint32Param = OH_HUKS_ALG_AES},
    {.tag = OH_HUKS_TAG_KEY_SIZE, .uint32Param = DERIVE_KEY_SIZE_256},
    {.tag = OH_HUKS_TAG_PURPOSE, .uint32Param = OH_HUKS_KEY_PURPOSE_DERIVE},
    {.tag = OH_HUKS_TAG_DIGEST, .uint32Param = OH_HUKS_DIGEST_SHA256}};
static const uint32_t COMMON_SIZE = 2048;
static const char *G_DERIVE_IN_DATA = "Hks_HKDF_Derive_Test_0_string";
static OH_Huks_Result PerformHkdfDerivation(const struct OH_Huks_Blob *genAlias,
    struct OH_Huks_ParamSet *hkdfParamSet,
    struct OH_Huks_ParamSet *hkdfFinishParamSet,
    const struct OH_Huks_Blob &inData)
{
    OH_Huks_Result ohResult;
    // Init
    uint8_t handleD[sizeof(uint64_t)] = {0};
    struct OH_Huks_Blob handleDerive = {sizeof(uint64_t), handleD};
    ohResult = OH_Huks_InitSession(genAlias, hkdfParamSet, &handleDerive, nullptr);
    if (ohResult.errorCode != OH_HUKS_SUCCESS) {
        return ohResult;
    }
    // Update
    uint8_t tmpOut[COMMON_SIZE] = {0};
    struct OH_Huks_Blob outData = {COMMON_SIZE, tmpOut};
    ohResult = OH_Huks_UpdateSession(&handleDerive, hkdfParamSet, &inData, &outData);
    if (ohResult.errorCode != OH_HUKS_SUCCESS) {
        return ohResult;
    }
    // Finish
    uint8_t outDataD[COMMON_SIZE] = {0};
    struct OH_Huks_Blob outDataDerive = {COMMON_SIZE, outDataD};
    ohResult = OH_Huks_FinishSession(&handleDerive, hkdfFinishParamSet, &inData, &outDataDerive);
    return ohResult;
}

napi_value HkdfDeriveKey(napi_env env, napi_callback_info info)
{
    struct OH_Huks_Blob genAlias = {(uint32_t)strlen("test_signVerify"), (uint8_t *)"test_signVerify"};
    struct OH_Huks_Blob inData = {(uint32_t)strlen(G_DERIVE_IN_DATA), (uint8_t *)G_DERIVE_IN_DATA};
    struct OH_Huks_ParamSet *genParamSet = nullptr;
    struct OH_Huks_ParamSet *hkdfParamSet = nullptr;
    struct OH_Huks_ParamSet *hkdfFinishParamSet = nullptr;
    OH_Huks_Result ohResult;
    do {
        ohResult = InitParamSet(&genParamSet, g_genDeriveParams, sizeof(g_genDeriveParams) /
                     sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }

        ohResult = InitParamSet(&hkdfParamSet, g_hkdfParams, sizeof(g_hkdfParams) /
                     sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        // finish paramset
        ohResult =
            InitParamSet(&hkdfFinishParamSet, g_hkdfFinishParams, sizeof(g_hkdfFinishParams) /
              sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        /* 1. Generate a key. */
        ohResult = OH_Huks_GenerateKeyItem(&genAlias, genParamSet, nullptr);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        /* 2. Derive a key. */
        ohResult = PerformHkdfDerivation(&genAlias, hkdfParamSet, hkdfFinishParamSet, inData);
    } while (0);
    (void)OH_Huks_DeleteKeyItem(&genAlias, nullptr);
    (void)OH_Huks_DeleteKeyItem(&g_deriveKeyAlias, nullptr);
    OH_Huks_FreeParamSet(&genParamSet);
    OH_Huks_FreeParamSet(&hkdfParamSet);
    OH_Huks_FreeParamSet(&hkdfFinishParamSet);

    napi_value ret;
    napi_create_int32(env, ohResult.errorCode, &ret);
    return ret;
}
```

### PBKDF2
<!-- @[key_derivation_pbkdf2_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/KeyUsage/KeyDerivation/entry/src/main/cpp/types/projects/napi_pbkdf2.cpp) -->

``` C++
#include "huks/native_huks_api.h"
#include "huks/native_huks_param.h"
#include "napi/native_api.h"
#include <cstring>
#include "file.h"

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
static const uint32_t DERIVE_KEY_SIZE_32 = 32;
static const uint32_t DERIVE_KEY_SIZE_256 = 256;
static const uint32_t DERIVE_KEY_ITERATION = 10000;
static const uint32_t SALT_SIZE = 8;
static const char DERIVE_KEY_SALT[SALT_SIZE] = "mysalt1";
static struct OH_Huks_Blob g_deriveKeyAlias = {(uint32_t)strlen("test_derive"), (uint8_t *)"test_derive"};
static struct OH_Huks_Param g_genDeriveParams[] = {
    {.tag = OH_HUKS_TAG_ALGORITHM, .uint32Param = OH_HUKS_ALG_AES},
    {.tag = OH_HUKS_TAG_PURPOSE, .uint32Param = OH_HUKS_KEY_PURPOSE_DERIVE},
    {.tag = OH_HUKS_TAG_DIGEST, .uint32Param = OH_HUKS_DIGEST_SHA256},
    {.tag = OH_HUKS_TAG_KEY_SIZE, .uint32Param = OH_HUKS_AES_KEY_SIZE_256}};
static struct OH_Huks_Param g_hkdfParams[] = {{.tag = OH_HUKS_TAG_ALGORITHM, .uint32Param = OH_HUKS_ALG_PBKDF2},
                                              {.tag = OH_HUKS_TAG_PURPOSE, .uint32Param = OH_HUKS_KEY_PURPOSE_DERIVE},
                                              {.tag = OH_HUKS_TAG_DIGEST, .uint32Param = OH_HUKS_DIGEST_SHA256},
                                              {.tag = OH_HUKS_TAG_DERIVE_KEY_SIZE, .uint32Param = DERIVE_KEY_SIZE_32},
                                              {.tag = OH_HUKS_TAG_ITERATION, .uint32Param = DERIVE_KEY_ITERATION},
                                              {.tag = OH_HUKS_TAG_SALT,
                                               .blob = {
                                                   .size = SALT_SIZE,
                                                   .data = (uint8_t *) DERIVE_KEY_SALT
                                               }}};
static struct OH_Huks_Param g_hkdfFinishParams[] = {
    {.tag = OH_HUKS_TAG_DERIVED_AGREED_KEY_STORAGE_FLAG, .uint32Param = OH_HUKS_STORAGE_ONLY_USED_IN_HUKS},
    {.tag = OH_HUKS_TAG_KEY_ALIAS, .blob = g_deriveKeyAlias},
    {.tag = OH_HUKS_TAG_ALGORITHM, .uint32Param = OH_HUKS_ALG_AES},
    {.tag = OH_HUKS_TAG_KEY_SIZE, .uint32Param = DERIVE_KEY_SIZE_256},
    {.tag = OH_HUKS_TAG_PURPOSE, .uint32Param = OH_HUKS_KEY_PURPOSE_DERIVE},
    {.tag = OH_HUKS_TAG_DIGEST, .uint32Param = OH_HUKS_DIGEST_NONE},
    {.tag = OH_HUKS_TAG_PADDING, .uint32Param = OH_HUKS_PADDING_NONE},
    {.tag = OH_HUKS_TAG_BLOCK_MODE, .uint32Param = OH_HUKS_MODE_ECB}};
static const uint32_t COMMON_SIZE = 1024;
static const char *G_DERIVE_IN_DATA = "Hks_PBKDF2_Derive_Test_0_string";
static OH_Huks_Result PerformPbkdfDerivation(const struct OH_Huks_Blob *genAlias,
    struct OH_Huks_ParamSet *hkdfParamSet,
    struct OH_Huks_ParamSet *hkdfFinishParamSet,
    const struct OH_Huks_Blob &inData)
{
    OH_Huks_Result ohResult;
    // Init
    uint8_t handleD[sizeof(uint64_t)] = {0};
    struct OH_Huks_Blob handleDerive = {sizeof(uint64_t), handleD};
    ohResult = OH_Huks_InitSession(genAlias, hkdfParamSet, &handleDerive, nullptr);
    if (ohResult.errorCode != OH_HUKS_SUCCESS) {
        return ohResult;
    }
    // Update
    uint8_t tmpOut[COMMON_SIZE] = {0};
    struct OH_Huks_Blob outData = {COMMON_SIZE, tmpOut};
    ohResult = OH_Huks_UpdateSession(&handleDerive, hkdfParamSet, &inData, &outData);
    if (ohResult.errorCode != OH_HUKS_SUCCESS) {
        return ohResult;
    }
    // Finish
    uint8_t outDataD[COMMON_SIZE] = {0};
    struct OH_Huks_Blob outDataDerive = {COMMON_SIZE, outDataD};
    ohResult = OH_Huks_FinishSession(&handleDerive, hkdfFinishParamSet, &inData, &outDataDerive);
    return ohResult;
}

napi_value PbkdfDeriveKey(napi_env env, napi_callback_info info)
{
    struct OH_Huks_Blob genAlias = {(uint32_t)strlen("test_signVerify"), (uint8_t *)"test_signVerify"};
    struct OH_Huks_Blob inData = {(uint32_t)strlen(G_DERIVE_IN_DATA), (uint8_t *)G_DERIVE_IN_DATA};
    struct OH_Huks_ParamSet *genParamSet = nullptr;
    struct OH_Huks_ParamSet *hkdfParamSet = nullptr;
    struct OH_Huks_ParamSet *hkdfFinishParamSet = nullptr;
    OH_Huks_Result ohResult;
    do {
        ohResult = InitParamSet(&genParamSet, g_genDeriveParams, sizeof(g_genDeriveParams) /
                     sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        ohResult = InitParamSet(&hkdfParamSet, g_hkdfParams, sizeof(g_hkdfParams) /
                     sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        ohResult =InitParamSet(&hkdfFinishParamSet, g_hkdfFinishParams, sizeof(g_hkdfFinishParams) /
              sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        /* 1. Generate a key. */
        ohResult = OH_Huks_GenerateKeyItem(&genAlias, genParamSet, nullptr);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        /* 2. Derive a key. */
        ohResult = PerformPbkdfDerivation(&genAlias, hkdfParamSet, hkdfFinishParamSet, inData);
    } while (0);
    (void)OH_Huks_DeleteKeyItem(&genAlias, nullptr);
    (void)OH_Huks_DeleteKeyItem(&g_deriveKeyAlias, nullptr);
    OH_Huks_FreeParamSet(&genParamSet);
    OH_Huks_FreeParamSet(&hkdfParamSet);
    OH_Huks_FreeParamSet(&hkdfFinishParamSet);

    napi_value ret;
    napi_create_int32(env, ohResult.errorCode, &ret);
    return ret;
}
```
