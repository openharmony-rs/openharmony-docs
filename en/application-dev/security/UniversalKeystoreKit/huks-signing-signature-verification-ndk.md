# Signing and Signature Verification (C/C++)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

This topic provides signing and signature verification development cases with the following algorithms:

- [Key algorithm ECC256 and digest algorithm SHA-256](#ecc256sha256)
- [Key algorithm SM2 and digest algorithm SM3](#sm2sm3)
- [Key algorithm SM2 and digest algorithm NoDigest](#sm2nodigest)
- [Key algorithm RSA, digest algorithm SHA-256, and padding mode PSS](#rsasha256pss)
- [Key algorithm RSA, digest algorithm SHA-256, and padding mode PKCS #1 v1.5](#rsasha256pkcs1_v1_5)
- [Key algorithm RSA, digest algorithm SHA-384, and padding mode PSS](#rsa2048sha384pss)
<!--RP1--><!--RP1End-->

For details about the scenarios and supported algorithms, see [Supported Algorithms](huks-signing-signature-verification-overview.md#supported-algorithms).


## Linking the Dynamic Library in the CMake Script
```txt
target_link_libraries(entry PUBLIC libhuks_ndk.z.so)
```

## How to Develop

**Key Generation**
1. Specify the key alias. For details about the naming rules, see [Key Generation Overview and Algorithm Specifications](huks-key-generation-overview.md).

2. Initialize the key property set.

3. Use [OH_Huks_GenerateKeyItem](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_generatekeyitem) to generate a key. For details, see [Key Generation Overview and Algorithm Specifications](huks-key-generation-overview.md).

Alternatively, you can [import a key](huks-key-import-overview.md).

**Signing**

1. Obtain the key alias.

2. Obtain the plaintext to be signed.

3. Use [OH_Huks_InitParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-param-h.md#oh_huks_initparamset) to set algorithm parameters.

4. Use [OH_Huks_InitSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_initsession) to initialize a key session and obtain the session handle.

5. Use [OH_Huks_FinishSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_finishsession) to end the key session and obtain the signature.

**Signature Verification**

1. Obtain the key alias.

2. Obtain the signature to be verified.

3. Use [OH_Huks_InitParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-param-h.md#oh_huks_initparamset) to [set algorithm parameters](../../reference/apis-universal-keystore-kit/capi-native-huks-param-h.md#oh_huks_initparamset).

4. Use [OH_Huks_InitSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_initsession) to initialize a key session and obtain the session handle.

5. Use [OH_Huks_UpdateSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_updatesession) to update the key session.

6. Use [OH_Huks_FinishSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_finishsession) to end the key session and verify the signature.

**Key Deletion**

When a key is no longer used, you need to call [OH_Huks_DeleteKeyItem](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_deletekeyitem) to delete the key. For details, see [Deleting a Key](huks-delete-key-ndk.md).

## Development Cases

### ECC256/SHA256
<!-- @[key_algorithm_ecc_sha256_sign_verify_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/KeyUsage/SigningVerification/entry/src/main/cpp/ecc_sha256_sign_verify.cpp) -->

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

static struct OH_Huks_Param g_genSignVerifyParamsTestECC[] = {
    {.tag = OH_HUKS_TAG_ALGORITHM, .uint32Param = OH_HUKS_ALG_ECC},
    {.tag = OH_HUKS_TAG_PURPOSE, .uint32Param = OH_HUKS_KEY_PURPOSE_SIGN | OH_HUKS_KEY_PURPOSE_VERIFY},
    {.tag = OH_HUKS_TAG_KEY_SIZE, .uint32Param = OH_HUKS_ECC_KEY_SIZE_256},
    {.tag = OH_HUKS_TAG_DIGEST, .uint32Param = OH_HUKS_DIGEST_SHA256},
};

static struct OH_Huks_Param g_signParamsTestECC[] = {
    {.tag = OH_HUKS_TAG_ALGORITHM, .uint32Param = OH_HUKS_ALG_ECC},
    {.tag = OH_HUKS_TAG_PURPOSE, .uint32Param = OH_HUKS_KEY_PURPOSE_SIGN},
    {.tag = OH_HUKS_TAG_KEY_SIZE, .uint32Param = OH_HUKS_ECC_KEY_SIZE_256},
    {.tag = OH_HUKS_TAG_DIGEST, .uint32Param = OH_HUKS_DIGEST_SHA256}};

static struct OH_Huks_Param g_verifyParamsTestECC[] = {
    {.tag = OH_HUKS_TAG_ALGORITHM, .uint32Param = OH_HUKS_ALG_ECC},
    {.tag = OH_HUKS_TAG_PURPOSE, .uint32Param = OH_HUKS_KEY_PURPOSE_VERIFY},
    {.tag = OH_HUKS_TAG_KEY_SIZE, .uint32Param = OH_HUKS_ECC_KEY_SIZE_256},
    {.tag = OH_HUKS_TAG_DIGEST, .uint32Param = OH_HUKS_DIGEST_SHA256}};

static const uint32_t ECC_COMMON_SIZE = 256;
static const char *DATA_TO_SIGN_ECC = "Hks_ECC_Sign_Verify_Test_0000000000000000000000000000000000000000000000000000000"
                                      "00000000000000000000000000000000000000000000000000000000000000000000000000000000"
                                      "00000000000000000000000000000000000000000000000000"
                                      "00000000000000000000000_string";

/* 1. Generate a key. */
static OH_Huks_Result GenerateKeyECC(const struct OH_Huks_Blob *keyAlias,
                                     const struct OH_Huks_ParamSet *genParamSet)
{
    return OH_Huks_GenerateKeyItem(keyAlias, genParamSet, nullptr);
}

/* 2. Create a signature. */
static OH_Huks_Result SignDataECC(const struct OH_Huks_Blob *keyAlias,
                                  const struct OH_Huks_ParamSet *signParamSet,
                                  const struct OH_Huks_Blob *inData,
                                  struct OH_Huks_Blob *outDataSign)
{
    uint8_t handleS[sizeof(uint64_t)] = {0};
    struct OH_Huks_Blob handleSign = {(uint32_t)sizeof(uint64_t), handleS};
    
    OH_Huks_Result ohResult = OH_Huks_InitSession(keyAlias, signParamSet, &handleSign, nullptr);
    if (ohResult.errorCode != OH_HUKS_SUCCESS) {
        return ohResult;
    }

    ohResult = OH_Huks_UpdateSession(&handleSign, signParamSet, inData, outDataSign);
    if (ohResult.errorCode != OH_HUKS_SUCCESS) {
        return ohResult;
    }

    struct OH_Huks_Blob finishInData = {0, NULL};
    ohResult = OH_Huks_FinishSession(&handleSign, signParamSet, &finishInData, outDataSign);
    
    return ohResult;
}

/* 3. Verify the signature. */
static OH_Huks_Result VerifySignatureECC(const struct OH_Huks_Blob *keyAlias,
                                         const struct OH_Huks_ParamSet *verifyParamSet,
                                         const struct OH_Huks_Blob *inData,
                                         const struct OH_Huks_Blob *signature)
{
    uint8_t handleV[sizeof(uint64_t)] = {0};
    struct OH_Huks_Blob handleVerify = {(uint32_t)sizeof(uint64_t), handleV};
    
    OH_Huks_Result ohResult = OH_Huks_InitSession(keyAlias, verifyParamSet, &handleVerify, nullptr);
    if (ohResult.errorCode != OH_HUKS_SUCCESS) {
        return ohResult;
    }

    uint8_t temp[] = "out";
    struct OH_Huks_Blob verifyOut = {(uint32_t)sizeof(temp), temp};
    ohResult = OH_Huks_UpdateSession(&handleVerify, verifyParamSet, inData, &verifyOut);
    if (ohResult.errorCode != OH_HUKS_SUCCESS) {
        return ohResult;
    }
    
    ohResult = OH_Huks_FinishSession(&handleVerify, verifyParamSet, signature, &verifyOut);
    
    return ohResult;
}

napi_value SignVerifyKeyECC(napi_env env, napi_callback_info info)
{
    struct OH_Huks_Blob g_keyAlias = {(uint32_t)strlen("test_signVerify_ECC"), (uint8_t *)"test_signVerify_ECC"};
    struct OH_Huks_Blob inData = {(uint32_t)strlen(DATA_TO_SIGN_ECC), (uint8_t *)DATA_TO_SIGN_ECC};
    struct OH_Huks_ParamSet *genParamSet = nullptr;
    struct OH_Huks_ParamSet *signParamSet = nullptr;
    struct OH_Huks_ParamSet *verifyParamSet = nullptr;
    OH_Huks_Result ohResult;
    
    do {
        ohResult = InitParamSet(&genParamSet, g_genSignVerifyParamsTestECC,
                                sizeof(g_genSignVerifyParamsTestECC) / sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        
        ohResult = InitParamSet(&signParamSet, g_signParamsTestECC,
                                sizeof(g_signParamsTestECC) / sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        
        ohResult = InitParamSet(&verifyParamSet, g_verifyParamsTestECC,
                                sizeof(g_verifyParamsTestECC) / sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }

        /* 1. Generate a key. */
        ohResult = GenerateKeyECC(&g_keyAlias, genParamSet);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }

        /* 2. Create a signature. */
        uint8_t outDataS[ECC_COMMON_SIZE] = {0};
        struct OH_Huks_Blob outDataSign = {ECC_COMMON_SIZE, outDataS};
        ohResult = SignDataECC(&g_keyAlias, signParamSet, &inData, &outDataSign);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }

        /* 3. Verify the signature. */
        ohResult = VerifySignatureECC(&g_keyAlias, verifyParamSet, &inData, &outDataSign);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
    } while (0);
    
    (void)OH_Huks_DeleteKeyItem(&g_keyAlias, genParamSet);
    OH_Huks_FreeParamSet(&genParamSet);
    OH_Huks_FreeParamSet(&signParamSet);
    OH_Huks_FreeParamSet(&verifyParamSet);

    napi_value ret;
    napi_create_int32(env, ohResult.errorCode, &ret);
    return ret;
}
```
### SM2/SM3
<!-- @[key_algorithm_sm2_sm3_sign_verify_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/KeyUsage/SigningVerification/entry/src/main/cpp/sm2_sm3_sign_verify.cpp) -->

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

static struct OH_Huks_Param g_genSignVerifyParamsSM2[] = {
    {.tag = OH_HUKS_TAG_ALGORITHM, .uint32Param = OH_HUKS_ALG_SM2},
    {.tag = OH_HUKS_TAG_KEY_SIZE, .uint32Param = OH_HUKS_SM2_KEY_SIZE_256},
    {.tag = OH_HUKS_TAG_PURPOSE, .uint32Param = OH_HUKS_KEY_PURPOSE_SIGN | OH_HUKS_KEY_PURPOSE_VERIFY},
    {.tag = OH_HUKS_TAG_DIGEST, .uint32Param = OH_HUKS_DIGEST_SM3},
};

static struct OH_Huks_Param g_signParamsSM2[] = {
    {.tag = OH_HUKS_TAG_ALGORITHM, .uint32Param = OH_HUKS_ALG_SM2},
    {.tag = OH_HUKS_TAG_KEY_SIZE, .uint32Param = OH_HUKS_SM2_KEY_SIZE_256},
    {.tag = OH_HUKS_TAG_PURPOSE, .uint32Param = OH_HUKS_KEY_PURPOSE_SIGN},
    {.tag = OH_HUKS_TAG_DIGEST, .uint32Param = OH_HUKS_DIGEST_SM3}
};

static struct OH_Huks_Param g_verifyParamsSM2[] = {
    {.tag = OH_HUKS_TAG_ALGORITHM, .uint32Param = OH_HUKS_ALG_SM2},
    {.tag = OH_HUKS_TAG_KEY_SIZE, .uint32Param = OH_HUKS_SM2_KEY_SIZE_256},
    {.tag = OH_HUKS_TAG_PURPOSE, .uint32Param = OH_HUKS_KEY_PURPOSE_VERIFY},
    {.tag = OH_HUKS_TAG_DIGEST, .uint32Param = OH_HUKS_DIGEST_SM3}
};

static const uint32_t SM2_COMMON_SIZE = 256;
static const char *DATA_TO_SIGN_SM2 = "Hks_SM2_Sign_Verify_Test_0000000000000000000000000000000000000000000000000000000"
                                      "00000000000000000000000000000000000000000000000000000000000000000000000000000000"
                                      "0000000000000000000000000000000000000000000000000"
                                      "000000000000000000000000_string";

/* 1. Generate a key. */
static OH_Huks_Result GenerateKeySM2(const struct OH_Huks_Blob *keyAlias,
                                     const struct OH_Huks_ParamSet *genParamSet)
{
    return OH_Huks_GenerateKeyItem(keyAlias, genParamSet, nullptr);
}

/* 2. Create a signature. */
static OH_Huks_Result SignDataSM2(const struct OH_Huks_Blob *keyAlias,
                                  const struct OH_Huks_ParamSet *signParamSet,
                                  const struct OH_Huks_Blob *inData,
                                  struct OH_Huks_Blob *outDataSign)
{
    uint8_t handleS[sizeof(uint64_t)] = {0};
    struct OH_Huks_Blob handleSign = {(uint32_t)sizeof(uint64_t), handleS};
    
    OH_Huks_Result ohResult = OH_Huks_InitSession(keyAlias, signParamSet, &handleSign, nullptr);
    if (ohResult.errorCode != OH_HUKS_SUCCESS) {
        return ohResult;
    }

    ohResult = OH_Huks_UpdateSession(&handleSign, signParamSet, inData, outDataSign);
    if (ohResult.errorCode != OH_HUKS_SUCCESS) {
        return ohResult;
    }

    struct OH_Huks_Blob finishInData = {0, NULL};
    ohResult = OH_Huks_FinishSession(&handleSign, signParamSet, &finishInData, outDataSign);
    
    return ohResult;
}

/* 3. Verify the signature. */
static OH_Huks_Result VerifySignatureSM2(const struct OH_Huks_Blob *keyAlias,
                                         const struct OH_Huks_ParamSet *verifyParamSet,
                                         const struct OH_Huks_Blob *inData,
                                         const struct OH_Huks_Blob *signature)
{
    uint8_t handleV[sizeof(uint64_t)] = {0};
    struct OH_Huks_Blob handleVerify = {(uint32_t)sizeof(uint64_t), handleV};
    
    OH_Huks_Result ohResult = OH_Huks_InitSession(keyAlias, verifyParamSet, &handleVerify, nullptr);
    if (ohResult.errorCode != OH_HUKS_SUCCESS) {
        return ohResult;
    }

    uint8_t temp[] = "out";
    struct OH_Huks_Blob verifyOut = {(uint32_t)sizeof(temp), temp};
    ohResult = OH_Huks_UpdateSession(&handleVerify, verifyParamSet, inData, &verifyOut);
    if (ohResult.errorCode != OH_HUKS_SUCCESS) {
        return ohResult;
    }
    
    ohResult = OH_Huks_FinishSession(&handleVerify, verifyParamSet, signature, &verifyOut);
    
    return ohResult;
}

napi_value SignVerifyKeySM2SM3(napi_env env, napi_callback_info info)
{
    struct OH_Huks_Blob g_keyAlias = {(uint32_t)strlen("test_signVerify_SM2_SM3"),
        (uint8_t *)"test_signVerify_SM2_SM3"};
    struct OH_Huks_Blob inData = {(uint32_t)strlen(DATA_TO_SIGN_SM2), (uint8_t *)DATA_TO_SIGN_SM2};
    struct OH_Huks_ParamSet *genParamSet = nullptr;
    struct OH_Huks_ParamSet *signParamSet = nullptr;
    struct OH_Huks_ParamSet *verifyParamSet = nullptr;
    OH_Huks_Result ohResult;
    
    do {
        ohResult = InitParamSet(&genParamSet, g_genSignVerifyParamsSM2,
                                sizeof(g_genSignVerifyParamsSM2) / sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        
        ohResult = InitParamSet(&signParamSet, g_signParamsSM2,
                                sizeof(g_signParamsSM2) / sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        
        ohResult = InitParamSet(&verifyParamSet, g_verifyParamsSM2,
                                sizeof(g_verifyParamsSM2) / sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }

        /* 1. Generate a key. */
        ohResult = GenerateKeySM2(&g_keyAlias, genParamSet);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }

        /* 2. Create a signature. */
        uint8_t outDataS[SM2_COMMON_SIZE] = {0};
        struct OH_Huks_Blob outDataSign = {SM2_COMMON_SIZE, outDataS};
        ohResult = SignDataSM2(&g_keyAlias, signParamSet, &inData, &outDataSign);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }

        /* 3. Verify the signature. */
        ohResult = VerifySignatureSM2(&g_keyAlias, verifyParamSet, &inData, &outDataSign);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
    } while (0);
    
    (void)OH_Huks_DeleteKeyItem(&g_keyAlias, genParamSet);
    OH_Huks_FreeParamSet(&genParamSet);
    OH_Huks_FreeParamSet(&signParamSet);
    OH_Huks_FreeParamSet(&verifyParamSet);

    napi_value ret;
    napi_create_int32(env, ohResult.errorCode, &ret);
    return ret;
}
```
### SM2/NoDigest
<!-- @[key_algorithm_sm2_nodigest_sign_verify_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/KeyUsage/SigningVerification/entry/src/main/cpp/sm2_nodigest_sign_verify.cpp) -->

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

static struct OH_Huks_Param g_genSignVerifyParamsSM2NoDigest[] = {
    {.tag = OH_HUKS_TAG_ALGORITHM, .uint32Param = OH_HUKS_ALG_SM2},
    {.tag = OH_HUKS_TAG_KEY_SIZE, .uint32Param = OH_HUKS_SM2_KEY_SIZE_256},
    {.tag = OH_HUKS_TAG_PURPOSE, .uint32Param = OH_HUKS_KEY_PURPOSE_SIGN | OH_HUKS_KEY_PURPOSE_VERIFY},
    {.tag = OH_HUKS_TAG_DIGEST, .uint32Param = OH_HUKS_DIGEST_NONE},
};

static struct OH_Huks_Param g_signParamsSM2NoDigest[] = {
    {.tag = OH_HUKS_TAG_ALGORITHM, .uint32Param = OH_HUKS_ALG_SM2},
    {.tag = OH_HUKS_TAG_KEY_SIZE, .uint32Param = OH_HUKS_SM2_KEY_SIZE_256},
    {.tag = OH_HUKS_TAG_PURPOSE, .uint32Param = OH_HUKS_KEY_PURPOSE_SIGN},
    {.tag = OH_HUKS_TAG_DIGEST, .uint32Param = OH_HUKS_DIGEST_NONE}
};

static struct OH_Huks_Param g_verifyParamsSM2NoDigest[] = {
    {.tag = OH_HUKS_TAG_ALGORITHM, .uint32Param = OH_HUKS_ALG_SM2},
    {.tag = OH_HUKS_TAG_KEY_SIZE, .uint32Param = OH_HUKS_SM2_KEY_SIZE_256},
    {.tag = OH_HUKS_TAG_PURPOSE, .uint32Param = OH_HUKS_KEY_PURPOSE_VERIFY},
    {.tag = OH_HUKS_TAG_DIGEST, .uint32Param = OH_HUKS_DIGEST_NONE}
};

static const uint32_t SM2_COMMON_SIZE = 256;
static const char *DATA_TO_SIGN_SM2_NODIGEST = "12345678901234567890123456789012";

/* 1. Generate a key. */
static OH_Huks_Result GenerateKeySM2(const struct OH_Huks_Blob *keyAlias,
                                     const struct OH_Huks_ParamSet *genParamSet)
{
    return OH_Huks_GenerateKeyItem(keyAlias, genParamSet, nullptr);
}

/* 2. Create a signature. */
static OH_Huks_Result SignDataSM2NoDigest(const struct OH_Huks_Blob *keyAlias,
                                          const struct OH_Huks_ParamSet *signParamSet,
                                          const struct OH_Huks_Blob *inData,
                                          struct OH_Huks_Blob *outDataSign)
{
    uint8_t handleS[sizeof(uint64_t)] = {0};
    struct OH_Huks_Blob handleSign = {(uint32_t)sizeof(uint64_t), handleS};

    OH_Huks_Result ohResult = OH_Huks_InitSession(keyAlias, signParamSet, &handleSign, nullptr);
    if (ohResult.errorCode != OH_HUKS_SUCCESS) {
        return ohResult;
    }

    ohResult = OH_Huks_FinishSession(&handleSign, signParamSet, inData, outDataSign);

    return ohResult;
}

/* 3. Verify the signature. */
static OH_Huks_Result VerifySignatureSM2NoDigest(const struct OH_Huks_Blob *keyAlias,
                                                 const struct OH_Huks_ParamSet *verifyParamSet,
                                                 const struct OH_Huks_Blob *inData,
                                                 const struct OH_Huks_Blob *signature)
{
    uint8_t handleV[sizeof(uint64_t)] = {0};
    struct OH_Huks_Blob handleVerify = {(uint32_t)sizeof(uint64_t), handleV};
    
    OH_Huks_Result ohResult = OH_Huks_InitSession(keyAlias, verifyParamSet, &handleVerify, nullptr);
    if (ohResult.errorCode != OH_HUKS_SUCCESS) {
        return ohResult;
    }

    uint8_t temp[] = "out";
    struct OH_Huks_Blob verifyOut = {(uint32_t)sizeof(temp), temp};
    ohResult = OH_Huks_UpdateSession(&handleVerify, verifyParamSet, inData, &verifyOut);
    if (ohResult.errorCode != OH_HUKS_SUCCESS) {
        return ohResult;
    }
    
    ohResult = OH_Huks_FinishSession(&handleVerify, verifyParamSet, signature, &verifyOut);
    
    return ohResult;
}

napi_value SignVerifyKeySM2NoDigest(napi_env env, napi_callback_info info)
{
    struct OH_Huks_Blob g_keyAlias = {(uint32_t)strlen("test_signVerify_SM2_NoDigest"),
        (uint8_t *)"test_signVerify_SM2_NoDigest"};
    struct OH_Huks_Blob inData = {(uint32_t)strlen(DATA_TO_SIGN_SM2_NODIGEST), (uint8_t *)DATA_TO_SIGN_SM2_NODIGEST};
    struct OH_Huks_ParamSet *genParamSet = nullptr;
    struct OH_Huks_ParamSet *signParamSet = nullptr;
    struct OH_Huks_ParamSet *verifyParamSet = nullptr;
    OH_Huks_Result ohResult;

    do {
        ohResult = InitParamSet(&genParamSet, g_genSignVerifyParamsSM2NoDigest,
                                sizeof(g_genSignVerifyParamsSM2NoDigest) / sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }

        ohResult = InitParamSet(&signParamSet, g_signParamsSM2NoDigest,
                                sizeof(g_signParamsSM2NoDigest) / sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }

        ohResult = InitParamSet(&verifyParamSet, g_verifyParamsSM2NoDigest,
                                sizeof(g_verifyParamsSM2NoDigest) / sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }

        /* 1. Generate a key. */
        ohResult = GenerateKeySM2(&g_keyAlias, genParamSet);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }

        /* 2. Create a signature. */
        uint8_t outDataS[SM2_COMMON_SIZE] = {0};
        struct OH_Huks_Blob outDataSign = {SM2_COMMON_SIZE, outDataS};
        ohResult = SignDataSM2NoDigest(&g_keyAlias, signParamSet, &inData, &outDataSign);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }

        /* 3. Verify the signature. */
        ohResult = VerifySignatureSM2NoDigest(&g_keyAlias, verifyParamSet, &inData, &outDataSign);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
    } while (0);

    (void)OH_Huks_DeleteKeyItem(&g_keyAlias, genParamSet);
    OH_Huks_FreeParamSet(&genParamSet);
    OH_Huks_FreeParamSet(&signParamSet);
    OH_Huks_FreeParamSet(&verifyParamSet);

    napi_value ret;
    napi_create_int32(env, ohResult.errorCode, &ret);
    return ret;
}
```
### RSA/SHA256/PSS
<!-- @[key_algorithm_rsa_sha256_pss_sign_verify_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/KeyUsage/SigningVerification/entry/src/main/cpp/rsa_sha256_pss_sign_verify.cpp) -->

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

static struct OH_Huks_Param g_genSignVerifyParamsRsaPss[] = {
    {.tag = OH_HUKS_TAG_ALGORITHM, .uint32Param = OH_HUKS_ALG_RSA},
    {.tag = OH_HUKS_TAG_KEY_SIZE, .uint32Param = OH_HUKS_RSA_KEY_SIZE_2048},
    {.tag = OH_HUKS_TAG_PURPOSE, .uint32Param = OH_HUKS_KEY_PURPOSE_SIGN | OH_HUKS_KEY_PURPOSE_VERIFY},
    {.tag = OH_HUKS_TAG_PADDING, .uint32Param = OH_HUKS_PADDING_PSS},
    {.tag = OH_HUKS_TAG_DIGEST, .uint32Param = OH_HUKS_DIGEST_SHA256},
};

static struct OH_Huks_Param g_signParamsRsaPss[] = {
    {.tag = OH_HUKS_TAG_ALGORITHM, .uint32Param = OH_HUKS_ALG_RSA},
    {.tag = OH_HUKS_TAG_KEY_SIZE, .uint32Param = OH_HUKS_RSA_KEY_SIZE_2048},
    {.tag = OH_HUKS_TAG_PADDING, .uint32Param = OH_HUKS_PADDING_PSS},
    {.tag = OH_HUKS_TAG_DIGEST, .uint32Param = OH_HUKS_DIGEST_SHA256},
    {.tag = OH_HUKS_TAG_PURPOSE, .uint32Param = OH_HUKS_KEY_PURPOSE_SIGN}
};

static struct OH_Huks_Param g_verifyParamsRsaPss[] = {
    {.tag = OH_HUKS_TAG_ALGORITHM, .uint32Param = OH_HUKS_ALG_RSA},
    {.tag = OH_HUKS_TAG_KEY_SIZE, .uint32Param = OH_HUKS_RSA_KEY_SIZE_2048},
    {.tag = OH_HUKS_TAG_PADDING, .uint32Param = OH_HUKS_PADDING_PSS},
    {.tag = OH_HUKS_TAG_DIGEST, .uint32Param = OH_HUKS_DIGEST_SHA256},
    {.tag = OH_HUKS_TAG_PURPOSE, .uint32Param = OH_HUKS_KEY_PURPOSE_VERIFY}
};

static const uint32_t RSA_COMMON_SIZE = 1024;
static const char *DATA_TO_SIGN_RSA_PSS = "Hks_RSA_PSS_Sign_Verify_Test_0000000000000000000000000000000000000000000"
                                          "000000000000000000000000000000000000000000000000000000000000000000000000"
                                          "000000000000000000000000000000000000000000000000000000000000000_string";

/* 1. Generate a key. */
static OH_Huks_Result GenerateKey(const struct OH_Huks_Blob *keyAlias,
                                  const struct OH_Huks_ParamSet *genParamSet)
{
    return OH_Huks_GenerateKeyItem(keyAlias, genParamSet, nullptr);
}

/* 2. Create a signature. */
static OH_Huks_Result SignData(const struct OH_Huks_Blob *keyAlias,
                               const struct OH_Huks_ParamSet *signParamSet,
                               const struct OH_Huks_Blob *inData,
                               struct OH_Huks_Blob *outDataSign)
{
    uint8_t handleS[sizeof(uint64_t)] = {0};
    struct OH_Huks_Blob handleSign = {(uint32_t)sizeof(uint64_t), handleS};
    
    OH_Huks_Result ohResult = OH_Huks_InitSession(keyAlias, signParamSet, &handleSign, nullptr);
    if (ohResult.errorCode != OH_HUKS_SUCCESS) {
        return ohResult;
    }

    ohResult = OH_Huks_UpdateSession(&handleSign, signParamSet, inData, outDataSign);
    if (ohResult.errorCode != OH_HUKS_SUCCESS) {
        return ohResult;
    }

    struct OH_Huks_Blob finishInData = {0, nullptr};
    ohResult = OH_Huks_FinishSession(&handleSign, signParamSet, &finishInData, outDataSign);
    
    return ohResult;
}

/* 3. Verify the signature. */
static OH_Huks_Result VerifySignature(const struct OH_Huks_Blob *keyAlias,
                                      const struct OH_Huks_ParamSet *verifyParamSet,
                                      const struct OH_Huks_Blob *inData,
                                      const struct OH_Huks_Blob *signature)
{
    uint8_t handleV[sizeof(uint64_t)] = {0};
    struct OH_Huks_Blob handleVerify = {(uint32_t)sizeof(uint64_t), handleV};
    
    OH_Huks_Result ohResult = OH_Huks_InitSession(keyAlias, verifyParamSet, &handleVerify, nullptr);
    if (ohResult.errorCode != OH_HUKS_SUCCESS) {
        return ohResult;
    }

    uint8_t temp[] = "out";
    struct OH_Huks_Blob verifyOut = {(uint32_t)sizeof(temp), temp};
    ohResult = OH_Huks_UpdateSession(&handleVerify, verifyParamSet, inData, &verifyOut);
    if (ohResult.errorCode != OH_HUKS_SUCCESS) {
        return ohResult;
    }
    
    ohResult = OH_Huks_FinishSession(&handleVerify, verifyParamSet, signature, &verifyOut);
    
    return ohResult;
}

napi_value SignVerifyKeyRsaSha256Pss(napi_env env, napi_callback_info info)
{
    struct OH_Huks_Blob g_keyAlias = {(uint32_t)strlen("test_signVerify_RSA_SHA256_PSS"),
        (uint8_t *)"test_signVerify_RSA_SHA256_PSS"};
    struct OH_Huks_Blob inData = {(uint32_t)strlen(DATA_TO_SIGN_RSA_PSS), (uint8_t *)DATA_TO_SIGN_RSA_PSS};
    struct OH_Huks_ParamSet *genParamSet = nullptr;
    struct OH_Huks_ParamSet *signParamSet = nullptr;
    struct OH_Huks_ParamSet *verifyParamSet = nullptr;
    OH_Huks_Result ohResult;

    do {
        ohResult = InitParamSet(&genParamSet, g_genSignVerifyParamsRsaPss,
                                sizeof(g_genSignVerifyParamsRsaPss) / sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }

        ohResult = InitParamSet(&signParamSet, g_signParamsRsaPss, sizeof(g_signParamsRsaPss) / sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }

        ohResult = InitParamSet(&verifyParamSet, g_verifyParamsRsaPss,
                                sizeof(g_verifyParamsRsaPss) / sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }

        ohResult = GenerateKey(&g_keyAlias, genParamSet);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }

        uint8_t outDataS[RSA_COMMON_SIZE] = {0};
        struct OH_Huks_Blob outDataSign = {RSA_COMMON_SIZE, outDataS};
        ohResult = SignData(&g_keyAlias, signParamSet, &inData, &outDataSign);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }

        ohResult = VerifySignature(&g_keyAlias, verifyParamSet, &inData, &outDataSign);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
    } while (0);

    (void)OH_Huks_DeleteKeyItem(&g_keyAlias, genParamSet);
    OH_Huks_FreeParamSet(&genParamSet);
    OH_Huks_FreeParamSet(&signParamSet);
    OH_Huks_FreeParamSet(&verifyParamSet);

    napi_value ret;
    napi_create_int32(env, ohResult.errorCode, &ret);
    return ret;
}
```
### RSA/SHA256/PKCS1_V1_5
<!-- @[key_algorithm_rsa_sha256_pkcs1_v1_5_sign_verify_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/KeyUsage/SigningVerification/entry/src/main/cpp/rsa_sha256_pkcs1_v1_5_sign_verify.cpp) -->

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

static struct OH_Huks_Param g_genSignVerifyParamsRsaPkcs1[] = {
    {.tag = OH_HUKS_TAG_ALGORITHM, .uint32Param = OH_HUKS_ALG_RSA},
    {.tag = OH_HUKS_TAG_KEY_SIZE, .uint32Param = OH_HUKS_RSA_KEY_SIZE_2048},
    {.tag = OH_HUKS_TAG_PURPOSE, .uint32Param = OH_HUKS_KEY_PURPOSE_SIGN | OH_HUKS_KEY_PURPOSE_VERIFY},
    {.tag = OH_HUKS_TAG_PADDING, .uint32Param = OH_HUKS_PADDING_PKCS1_V1_5},
    {.tag = OH_HUKS_TAG_DIGEST, .uint32Param = OH_HUKS_DIGEST_SHA256},
};

static struct OH_Huks_Param g_signParamsRsaPkcs1[] = {
    {.tag = OH_HUKS_TAG_ALGORITHM, .uint32Param = OH_HUKS_ALG_RSA},
    {.tag = OH_HUKS_TAG_KEY_SIZE, .uint32Param = OH_HUKS_RSA_KEY_SIZE_2048},
    {.tag = OH_HUKS_TAG_PURPOSE, .uint32Param = OH_HUKS_KEY_PURPOSE_SIGN},
    {.tag = OH_HUKS_TAG_PADDING, .uint32Param = OH_HUKS_PADDING_PKCS1_V1_5},
    {.tag = OH_HUKS_TAG_DIGEST, .uint32Param = OH_HUKS_DIGEST_SHA256}
};

static struct OH_Huks_Param g_verifyParamsRsaPkcs1[] = {
    {.tag = OH_HUKS_TAG_ALGORITHM, .uint32Param = OH_HUKS_ALG_RSA},
    {.tag = OH_HUKS_TAG_KEY_SIZE, .uint32Param = OH_HUKS_RSA_KEY_SIZE_2048},
    {.tag = OH_HUKS_TAG_PURPOSE, .uint32Param = OH_HUKS_KEY_PURPOSE_VERIFY},
    {.tag = OH_HUKS_TAG_PADDING, .uint32Param = OH_HUKS_PADDING_PKCS1_V1_5},
    {.tag = OH_HUKS_TAG_DIGEST, .uint32Param = OH_HUKS_DIGEST_SHA256}
};

static const uint32_t RSA_COMMON_SIZE = 1024;
static const char *DATA_TO_SIGN_RSA_PKCS1 = "Hks_RSA_PKCS1_V1_5_Sign_Verify_Test_000000000000000000000000000000"
                                            "000000000000000000000000000000000000000000000000000000000000000000"
                                            "000000000000000000000000000000000000000000000000000000000000_string";

/* 1. Generate a key. */
static OH_Huks_Result GenerateKey(const struct OH_Huks_Blob *keyAlias, const struct OH_Huks_ParamSet *genParamSet)
{
    return OH_Huks_GenerateKeyItem(keyAlias, genParamSet, nullptr);
}

/* 2. Verify the signature. */
static OH_Huks_Result SignData(const struct OH_Huks_Blob *keyAlias,
                               const struct OH_Huks_ParamSet *signParamSet,
                               const struct OH_Huks_Blob *inData,
                               struct OH_Huks_Blob *outDataSign)
{
    uint8_t handleS[sizeof(uint64_t)] = {0};
    struct OH_Huks_Blob handleSign = {(uint32_t)sizeof(uint64_t), handleS};
    
    OH_Huks_Result ohResult = OH_Huks_InitSession(keyAlias, signParamSet, &handleSign, nullptr);
    if (ohResult.errorCode != OH_HUKS_SUCCESS) {
        return ohResult;
    }

    ohResult = OH_Huks_UpdateSession(&handleSign, signParamSet, inData, outDataSign);
    if (ohResult.errorCode != OH_HUKS_SUCCESS) {
        return ohResult;
    }

    struct OH_Huks_Blob finishInData = {0, nullptr};
    ohResult = OH_Huks_FinishSession(&handleSign, signParamSet, &finishInData, outDataSign);
    
    return ohResult;
}

/* 3. Verify the signature. */
static OH_Huks_Result VerifySignature(const struct OH_Huks_Blob *keyAlias,
                                      const struct OH_Huks_ParamSet *verifyParamSet,
                                      const struct OH_Huks_Blob *inData,
                                      const struct OH_Huks_Blob *signature)
{
    uint8_t handleV[sizeof(uint64_t)] = {0};
    struct OH_Huks_Blob handleVerify = {(uint32_t)sizeof(uint64_t), handleV};
    
    OH_Huks_Result ohResult = OH_Huks_InitSession(keyAlias, verifyParamSet, &handleVerify, nullptr);
    if (ohResult.errorCode != OH_HUKS_SUCCESS) {
        return ohResult;
    }

    uint8_t temp[] = "out";
    struct OH_Huks_Blob verifyOut = {(uint32_t)sizeof(temp), temp};
    ohResult = OH_Huks_UpdateSession(&handleVerify, verifyParamSet, inData, &verifyOut);
    if (ohResult.errorCode != OH_HUKS_SUCCESS) {
        return ohResult;
    }
    
    ohResult = OH_Huks_FinishSession(&handleVerify, verifyParamSet, signature, &verifyOut);
    
    return ohResult;
}

napi_value SignVerifyKeyRsaSha256Pkcs1V15(napi_env env, napi_callback_info info)
{
    struct OH_Huks_Blob g_keyAlias = {(uint32_t)strlen("test_signVerify_RSA_SHA256_PKCS1"),
        (uint8_t *)"test_signVerify_RSA_SHA256_PKCS1"};
    struct OH_Huks_Blob inData = {(uint32_t)strlen(DATA_TO_SIGN_RSA_PKCS1), (uint8_t *)DATA_TO_SIGN_RSA_PKCS1};
    struct OH_Huks_ParamSet *genParamSet = nullptr;
    struct OH_Huks_ParamSet *signParamSet = nullptr;
    struct OH_Huks_ParamSet *verifyParamSet = nullptr;
    OH_Huks_Result ohResult;

    do {
        ohResult = InitParamSet(&genParamSet, g_genSignVerifyParamsRsaPkcs1,
                                sizeof(g_genSignVerifyParamsRsaPkcs1) / sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }

        ohResult = InitParamSet(&signParamSet, g_signParamsRsaPkcs1,
                                sizeof(g_signParamsRsaPkcs1) / sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }

        ohResult = InitParamSet(&verifyParamSet, g_verifyParamsRsaPkcs1,
                                sizeof(g_verifyParamsRsaPkcs1) / sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        
        ohResult = GenerateKey(&g_keyAlias, genParamSet);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        
        uint8_t outDataS[RSA_COMMON_SIZE] = {0};
        struct OH_Huks_Blob outDataSign = {RSA_COMMON_SIZE, outDataS};
        ohResult = SignData(&g_keyAlias, signParamSet, &inData, &outDataSign);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        
        ohResult = VerifySignature(&g_keyAlias, verifyParamSet, &inData, &outDataSign);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
    } while (0);

    (void)OH_Huks_DeleteKeyItem(&g_keyAlias, genParamSet);
    OH_Huks_FreeParamSet(&genParamSet);
    OH_Huks_FreeParamSet(&signParamSet);
    OH_Huks_FreeParamSet(&verifyParamSet);

    napi_value ret;
    napi_create_int32(env, ohResult.errorCode, &ret);
    return ret;
}
```
### RSA2048/SHA384/PSS
<!-- @[key_algorithm_rsa_sha384_pss_sign_verify_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/KeyUsage/SigningVerification/entry/src/main/cpp/rsa_sha384_pss_sign_verify.cpp) -->

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

static struct OH_Huks_Param g_genSignVerifyParamsRsaSha384Pss[] = {
    {.tag = OH_HUKS_TAG_ALGORITHM, .uint32Param = OH_HUKS_ALG_RSA},
    {.tag = OH_HUKS_TAG_KEY_SIZE, .uint32Param = OH_HUKS_RSA_KEY_SIZE_2048},
    {.tag = OH_HUKS_TAG_PURPOSE, .uint32Param = OH_HUKS_KEY_PURPOSE_SIGN | OH_HUKS_KEY_PURPOSE_VERIFY},
    {.tag = OH_HUKS_TAG_PADDING, .uint32Param = OH_HUKS_PADDING_PSS},
    {.tag = OH_HUKS_TAG_DIGEST, .uint32Param = OH_HUKS_DIGEST_SHA384},
};

static struct OH_Huks_Param g_signParamsRsaSha384Pss[] = {
    {.tag = OH_HUKS_TAG_ALGORITHM, .uint32Param = OH_HUKS_ALG_RSA},
    {.tag = OH_HUKS_TAG_KEY_SIZE, .uint32Param = OH_HUKS_RSA_KEY_SIZE_2048},
    {.tag = OH_HUKS_TAG_PADDING, .uint32Param = OH_HUKS_PADDING_PSS},
    {.tag = OH_HUKS_TAG_DIGEST, .uint32Param = OH_HUKS_DIGEST_SHA384},
    {.tag = OH_HUKS_TAG_PURPOSE, .uint32Param = OH_HUKS_KEY_PURPOSE_SIGN}
};

static struct OH_Huks_Param g_verifyParamsRsaSha384Pss[] = {
    {.tag = OH_HUKS_TAG_ALGORITHM, .uint32Param = OH_HUKS_ALG_RSA},
    {.tag = OH_HUKS_TAG_KEY_SIZE, .uint32Param = OH_HUKS_RSA_KEY_SIZE_2048},
    {.tag = OH_HUKS_TAG_PADDING, .uint32Param = OH_HUKS_PADDING_PSS},
    {.tag = OH_HUKS_TAG_DIGEST, .uint32Param = OH_HUKS_DIGEST_SHA384},
    {.tag = OH_HUKS_TAG_PURPOSE, .uint32Param = OH_HUKS_KEY_PURPOSE_VERIFY}
};

static const uint32_t RSA_COMMON_SIZE = 1024;
static const char *DATA_TO_SIGN_RSA_SHA384_PSS = "Hks_RSA_SHA384_PSS_Sign_Verify_Test_000000000000000000000000000"
                                                  "000000000000000000000000000000000000000000000000000000000000"
                                                  "000000000000000000000000000000000000000000000000000000_string";

/* 1. Generate a key. */
static OH_Huks_Result GenerateKeyRSA(const struct OH_Huks_Blob *keyAlias,
                                     const struct OH_Huks_ParamSet *genParamSet)
{
    return OH_Huks_GenerateKeyItem(keyAlias, genParamSet, nullptr);
}

/* 2. Create a signature. */
static OH_Huks_Result SignDataRSA(const struct OH_Huks_Blob *keyAlias,
                                  const struct OH_Huks_ParamSet *signParamSet,
                                  const struct OH_Huks_Blob *inData,
                                  struct OH_Huks_Blob *outDataSign)
{
    uint8_t handleS[sizeof(uint64_t)] = {0};
    struct OH_Huks_Blob handleSign = {(uint32_t)sizeof(uint64_t), handleS};

    OH_Huks_Result ohResult = OH_Huks_InitSession(keyAlias, signParamSet, &handleSign, nullptr);
    if (ohResult.errorCode != OH_HUKS_SUCCESS) {
        return ohResult;
    }

    ohResult = OH_Huks_UpdateSession(&handleSign, signParamSet, inData, outDataSign);
    if (ohResult.errorCode != OH_HUKS_SUCCESS) {
        return ohResult;
    }

    struct OH_Huks_Blob finishInData = {0, NULL};
    ohResult = OH_Huks_FinishSession(&handleSign, signParamSet, &finishInData, outDataSign);
    
    return ohResult;
}

/* 3. Verify the signature. */
static OH_Huks_Result VerifySignatureRSA(const struct OH_Huks_Blob *keyAlias,
                                         const struct OH_Huks_ParamSet *verifyParamSet,
                                         const struct OH_Huks_Blob *inData,
                                         const struct OH_Huks_Blob *signature)
{
    uint8_t handleV[sizeof(uint64_t)] = {0};
    struct OH_Huks_Blob handleVerify = {(uint32_t)sizeof(uint64_t), handleV};

    OH_Huks_Result ohResult = OH_Huks_InitSession(keyAlias, verifyParamSet, &handleVerify, nullptr);
    if (ohResult.errorCode != OH_HUKS_SUCCESS) {
        return ohResult;
    }

    uint8_t temp[] = "out";
    struct OH_Huks_Blob verifyOut = {(uint32_t)sizeof(temp), temp};
    ohResult = OH_Huks_UpdateSession(&handleVerify, verifyParamSet, inData, &verifyOut);
    if (ohResult.errorCode != OH_HUKS_SUCCESS) {
        return ohResult;
    }

    ohResult = OH_Huks_FinishSession(&handleVerify, verifyParamSet, signature, &verifyOut);

    return ohResult;
}

napi_value SignVerifyKey(napi_env env, napi_callback_info info)
{
    struct OH_Huks_Blob g_keyAlias = {(uint32_t)strlen("test_signVerify_RSA_SHA384_PSS"),
        (uint8_t *)"test_signVerify_RSA_SHA384_PSS"};
    struct OH_Huks_Blob inData = {(uint32_t)strlen(DATA_TO_SIGN_RSA_SHA384_PSS),
        (uint8_t *)DATA_TO_SIGN_RSA_SHA384_PSS};
    struct OH_Huks_ParamSet *genParamSet = nullptr;
    struct OH_Huks_ParamSet *signParamSet = nullptr;
    struct OH_Huks_ParamSet *verifyParamSet = nullptr;
    OH_Huks_Result ohResult;

    do {
        ohResult = InitParamSet(&genParamSet, g_genSignVerifyParamsRsaSha384Pss,
                                sizeof(g_genSignVerifyParamsRsaSha384Pss) / sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }

        ohResult = InitParamSet(&signParamSet, g_signParamsRsaSha384Pss,
                                sizeof(g_signParamsRsaSha384Pss) / sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }

        ohResult = InitParamSet(&verifyParamSet, g_verifyParamsRsaSha384Pss,
                                sizeof(g_verifyParamsRsaSha384Pss) / sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }

        /* 1. Generate a key. */
        ohResult = GenerateKeyRSA(&g_keyAlias, genParamSet);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }

        /* 2. Create a signature. */
        uint8_t outDataS[RSA_COMMON_SIZE] = {0};
        struct OH_Huks_Blob outDataSign = {RSA_COMMON_SIZE, outDataS};
        ohResult = SignDataRSA(&g_keyAlias, signParamSet, &inData, &outDataSign);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }

        /* 3. Verify the signature. */
        ohResult = VerifySignatureRSA(&g_keyAlias, verifyParamSet, &inData, &outDataSign);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
    } while (0);

    (void)OH_Huks_DeleteKeyItem(&g_keyAlias, genParamSet);
    OH_Huks_FreeParamSet(&genParamSet);
    OH_Huks_FreeParamSet(&signParamSet);
    OH_Huks_FreeParamSet(&verifyParamSet);

    napi_value ret;
    napi_create_int32(env, ohResult.errorCode, &ret);
    return ret;
}
```
