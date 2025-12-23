# 通用查询(C/C++)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

从API 22开始，huksExternalCrypto提供通用查询功能接口。从Ukey获取通用属性信息，完成属性查询操作。具体的场景介绍请参考[获取属性介绍及规格](huks-ukey-general-query-overview.md)。

## 在CMake脚本中链接相关动态库
```txt
target_link_libraries(entry PUBLIC libhuks_ndk.z.so libhuks_external_crypto.z.so)
```

## 开发步骤

**获取属性**

1. 构造resourceId和propertyId，先调用[OH_Huks_OpenResource](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_openresource)打开资源。

2. 调用[OH_Huks_InitExternalCryptoParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_initexternalcryptoparamset)初始化参数集。

3. 调用[OH_Huks_AddExternalCryptoParams](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_addexternalcryptoparams)添加输入参数。

4. 调用[OH_Huks_BuildExternalCryptoParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_buildexternalcryptoparamset)构建参数集。

5. 调用[OH_Huks_GetProperty](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_getproperty)获取属性信息。

6. 调用[OH_Huks_GetExternalCryptoParam](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_getexternalcryptoparam)从输出参数集中提取结果。

7. 调用[OH_Huks_FreeExternalCryptoParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_freeexternalcryptoparamset)释放参数集资源。

```c++
#include "huks/native_huks_external_crypto_api.h"
#include "huks/native_huks_external_crypto_type.h"
#include "napi/native_api.h"
#include <string.h>

OH_Huks_Result InitExternalCryptoParamSet(
    OH_Huks_ExternalCryptoParamSet **paramSet,
    const OH_Huks_ExternalCryptoParam *params,
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

static napi_value GetProperty(napi_env env, napi_callback_info info) 
{
    /* 1.假设已经打开了resourceId */
    const char *resourceIdStr = "testResourceId";
    const char *propertyIdStr = "SKF_GetDevInfo"; // 定义在GMT 0016-2023标准中的属性函数名称
    
    struct OH_Huks_Blob resourceId = {
        (uint32_t)strlen(resourceIdStr),
        (uint8_t *)resourceIdStr
    };
    struct OH_Huks_Blob propertyId = {
        (uint32_t)strlen(propertyIdStr),
        (uint8_t *)propertyIdStr
    };
    
    /* 2.构造输入参数 */
    OH_Huks_ExternalCryptoParam params[] = {};
    OH_Huks_ExternalCryptoParamSet *paramSetIn = nullptr;
    OH_Huks_ExternalCryptoParamSet *paramSetOut = nullptr;
    OH_Huks_Result ohResult;
    
    do {
        /* 3.初始化并构建输入参数集 */
        ohResult = InitExternalCryptoParamSet(&paramSetIn, params,
            sizeof(params) / sizeof(OH_Huks_ExternalCryptoParam));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        
        /* 4.调用OH_Huks_GetProperty获取属性 */
        ohResult = OH_Huks_GetProperty(&resourceId, &propertyId, paramSetIn, &paramSetOut);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        
        /* 5.从输出参数集中提取结果
         * 输出参数集由函数内部分配，查询到的属性数据放在 OH_HUKS_EXT_CRYPTO_TAG_EXTRA_DATA TAG 中。
         * 下面展示如何遍历返回的 params 并安全提取返回的属性字符串（示例）。
         */
        if (paramSetOut != nullptr && paramSetOut->paramsCnt > 0) {
            for (uint32_t i = 0; i < paramSetOut->paramsCnt; i++) {
                OH_Huks_ExternalCryptoParam *param = &paramSetOut->params[i];
                /* 返回数据约定：GetProperty 的结果放在 OH_HUKS_EXT_CRYPTO_TAG_EXTRA_DATA TAG 中（示例使用 JSON 文本）*/
                if (param->tag == OH_HUKS_EXT_CRYPTO_TAG_EXTRA_DATA) {
                    /* 注意：param->blob.data 可能不是以 '\0' 结尾，需拷贝并手动添加终止符 */
                    char *outStr = (char *)malloc(param->blob.size + 1);
                    if (outStr != NULL) {
                        memcpy(outStr, param->blob.data, param->blob.size);
                        outStr[param->blob.size] = '\0';
                        // 解析 outStr（例如使用 JSON 解析库），示例：
                        // parse_json(outStr);
                        free(outStr);
                    }
                }
            }
        }
    } while (0);
    
    /* 6.释放资源 */
    OH_Huks_FreeExternalCryptoParamSet(&paramSetIn);
    OH_Huks_FreeExternalCryptoParamSet(&paramSetOut);
    
    napi_value ret;
    napi_create_int32(env, ohResult.errorCode, &ret);
    return ret;
}
```

