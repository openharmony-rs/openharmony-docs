# 签名/验签(C/C++)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

当前指导提供以下示例，供开发者参考完成签名、验签开发：

- [密钥算法为ECC256、摘要算法为SHA256](#ecc256sha256)
- [密钥算法为SM2、摘要算法为SM3](#sm2sm3)
- [密钥算法为SM2、摘要算法为NoDigest](#sm2nodigest)
- [密钥算法为RSA、摘要算法为SHA256、填充模式为PSS](#rsasha256pss)
- [密钥算法为RSA、摘要算法为SHA256、填充模式为PKCS1_V1_5](#rsasha256pkcs1_v1_5)
- [密钥算法为RSA、摘要算法为SHA384、填充模式为PSS](#rsa2048sha384pss)
<!--RP1--><!--RP1End-->

具体的场景介绍及支持的算法规格，请参考[签名/验签支持的算法](huks-signing-signature-verification-overview.md#支持的算法)。


## 在CMake脚本中链接相关动态库
```txt
target_link_libraries(entry PUBLIC libhuks_ndk.z.so)
```

## 开发步骤

**生成密钥**
1. 指定密钥别名，密钥别名命名规范参考[密钥生成介绍及算法规格](huks-key-generation-overview.md)。

2. 初始化密钥属性集。

3. 调用[OH_Huks_GenerateKeyItem](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_generatekeyitem)生成密钥，具体请参考[密钥生成](huks-key-generation-overview.md)。

除此之外，开发者也可以参考[密钥导入](huks-key-import-overview.md)，导入已有的密钥。

**签名**

1. 获取密钥别名。

2. 指定待签名的明文数据。

3. 调用[OH_Huks_InitParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-param-h.md#oh_huks_initparamset)指定算法参数配置。

4. 调用[OH_Huks_InitSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_initsession)初始化密钥会话，并获取会话的句柄handle。

5. 调用[OH_Huks_FinishSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_finishsession)结束密钥会话，获取签名signature。

**验签**

1. 获取密钥别名。

2. 获取待验证的签名signature。

3. 调用[OH_Huks_InitParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-param-h.md#oh_huks_initparamset)指定[算法参数配置](../../reference/apis-universal-keystore-kit/capi-native-huks-param-h.md#oh_huks_initparamset)。

4. 调用[OH_Huks_InitSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_initsession)初始化密钥会话，并获取会话的句柄handle。

5. 调用[OH_Huks_UpdateSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_updatesession)更新密钥会话。

6. 调用[OH_Huks_FinishSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_finishsession)结束密钥会话，验证签名。

**删除密钥**

当密钥废弃不用时，需要调用[OH_Huks_DeleteKeyItem](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_deletekeyitem)删除密钥，具体请参考[密钥删除](huks-delete-key-ndk.md)。

## 开发案例

### ECC256/SHA256
<!-- @[key_algorithm_ecc_sha256_sign_verify_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/KeyUsage/SigningVerification/entry/src/main/cpp/ecc_sha256_sign_verify.cpp) -->
### SM2/SM3
<!-- @[key_algorithm_sm2_sm3_sign_verify_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/KeyUsage/SigningVerification/entry/src/main/cpp/sm2_sm3_sign_verify.cpp) -->
### SM2/NoDigest
<!-- @[key_algorithm_sm2_nodigest_sign_verify_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/KeyUsage/SigningVerification/entry/src/main/cpp/sm2_nodigest_sign_verify.cpp) -->
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

/* 1. 生成密钥 */
static OH_Huks_Result GenerateKey(const struct OH_Huks_Blob *keyAlias,
                                  const struct OH_Huks_ParamSet *genParamSet)
{
    return OH_Huks_GenerateKeyItem(keyAlias, genParamSet, nullptr);
}

/* 2. 签名 */
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

/* 3. 验签 */
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

/* 1. 生成密钥 */
static OH_Huks_Result GenerateKey(const struct OH_Huks_Blob *keyAlias, const struct OH_Huks_ParamSet *genParamSet)
{
    return OH_Huks_GenerateKeyItem(keyAlias, genParamSet, nullptr);
}

/* 2. 验签 */
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

/* 3. 验签 */
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