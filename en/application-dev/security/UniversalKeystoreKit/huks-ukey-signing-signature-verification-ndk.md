# Signing and Signature Verification (C/C++)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

The following uses the key algorithm RSA, digest algorithm SHA-384, and padding mode PSS as an example to describe how to perform signing and verify a signature.

- [Key algorithm RSA, digest algorithm SHA-384, and padding mode PSS](#rsasha384pss)

For details about the scenarios and supported algorithm specifications, see [Signature and Signature Verification Overview and Algorithm Specifications](huks-ukey-signing-signature-verification-overview.md).

## Linking the Dynamic Library in the CMake Script
```txt
target_link_libraries(entry PUBLIC libhuks_ndk.z.so libhuks_external_crypto.z.so)
```

## How to Develop

**Signing**

1. Obtain [keyUri](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certreference22) as **resourceId** (also as a key alias) by referring to [certificate management for applications](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenauthorizedialog22), [open the resource](huks-open-close-resource-ndk.md#opening-resources), and complete PIN authentication.

2. Specify the plaintext to be signed.

3. Call [OH_Huks_InitParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-param-h.md#oh_huks_initparamset) to specify the algorithm parameter configuration and set **KeyClass**. The tag is [OH_HUKS_TAG_KEY_CLASS](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_tag), and the value is [OH_HUKS_KEY_CLASS_EXTENSION](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_keyclasstype).

4. Call [OH_Huks_InitSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_initsession) to initialize a key session and obtain the session handle.

5. Call [OH_Huks_FinishSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_finishsession) to finish the key session and obtain the signature.

**Signature verification**

1. Obtain [keyUri](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certreference22) as **resourceId** (also as a key alias) by referring to [certificate management for applications](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenauthorizedialog22), and [open the resource](huks-open-close-resource-ndk.md#opening-resources).

2. Obtain the signature to be verified.

3. Call [OH_Huks_InitParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-param-h.md#oh_huks_initparamset) to specify the algorithm parameter configuration and set **KeyClass**. The tag is [OH_HUKS_TAG_KEY_CLASS](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_tag), and the value is [OH_HUKS_KEY_CLASS_EXTENSION](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_keyclasstype).

4. Call [OH_Huks_InitSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_initsession) to initialize a key session and obtain the session handle.

5. Call [OH_Huks_UpdateSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_updatesession) to update the key session.

6. Call [OH_Huks_FinishSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_finishsession) to finish the key session and verify the signature.

## Development Cases

### RSA/SHA384/PSS
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
static const char *DATA_TO_SIGN = "Hks_RSA_Sign_Verify_Test_0000000000000000000000000000000000000000000000000000000"
                                  "00000000000000000000000000000000000000000000000000000000000000000000000000000000"
                                  "0000000000000000000000000000000000000000000000000000000000000000000000000_string";
static const char *KEY_ALIAS = "{\"providerName\":\"testProviderName\",\"abilityName\":\"CryptoExtension\","
                              "\"bundleName\":\"com.example.cryptoapplication\",\"index\":{\"key\":\"testKey\"}}";

static napi_value SignVerifyKey(napi_env env, napi_callback_info info) 
{
    // Assume that **keyAlias** is the value of **resourceId** obtained.
    struct OH_Huks_Blob keyAlias = {
        (uint32_t)strlen(KEY_ALIAS),
        (uint8_t *)KEY_ALIAS
    };
    struct OH_Huks_Blob inData = {
        (uint32_t)strlen(DATA_TO_SIGN),
        (uint8_t *)DATA_TO_SIGN
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
        ohResult = OH_Huks_InitSession(&keyAlias, signParamSet, &handleSign, nullptr);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        // Finish
        uint8_t outDataS[RSA_COMMON_SIZE] = {0};
        struct OH_Huks_Blob outDataSign = { RSA_COMMON_SIZE, outDataS };
        ohResult = OH_Huks_FinishSession(&handleSign, signParamSet,  &inData, &outDataSign);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        
        /* 2. Verify */
        // Init
        uint8_t handleV[sizeof(uint64_t)] = {0};
        struct OH_Huks_Blob handleVerify = { (uint32_t)sizeof(uint64_t), handleV };
        ohResult = OH_Huks_InitSession(&keyAlias, verifyParamSet, &handleVerify, nullptr);
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
