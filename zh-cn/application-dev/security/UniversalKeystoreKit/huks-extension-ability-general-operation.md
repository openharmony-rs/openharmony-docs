# 通用操作

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

HUKS在密钥管理扩展场景下提供一组“通用操作”接口，覆盖资源标识、资源打开/关闭、查询、属性设置、错误信息获取等场景。除getResourceId和getErrorInfo外，其他操作（getProperty、setProperty等）均要求资源已打开。

## 整体关系

| 类别 | 涉及接口 | 调用阶段 | 是否需要资源已打开 | 详细文档 |
|------|---------|---------|-------------------|---------|
| 资源生命周期 | openResource/closeResource | 密钥管理扩展操作前/后 | — | [打开/关闭资源](#打开关闭资源) |
| 资源标识 | getResourceId | 任何操作之前 | 否 | [获取资源ID](#获取资源id) |
| 查询 | getProperty | 资源打开后 | 是 | [查询](#查询) |
| 属性设置 | setProperty | 资源打开后 | 是 | [属性设置](#属性设置) |
| 错误信息 | getErrorInfo | 任意操作失败后 | 否 | [获取错误信息](#获取错误信息) |

> **说明**：
>
> 是否需要PIN认证取决于propertyId和密钥管理扩展的实现。查询设备信息等操作通常不需要；涉及密钥属性或敏感信息时，通常需要先完成PIN认证。

## 打开/关闭资源

从API版本22开始，huksExternalCrypto提供打开/关闭资源的C++接口；从API版本26.0.0开始，huksExternalCrypto提供打开/关闭资源功能的ArkTS接口。

应用在密钥操作、通用操作、PIN码认证等操作之前，需要先打开资源。打开资源需要[获取资源ID](#获取资源id)，执行完所有密钥管理扩展操作后必须手动关闭已打开的资源，避免资源泄漏。

### 开发步骤

**ArkTS接口**

1. 通过[获取资源ID](#获取资源id)，得到resourceId。

2. 调用[openResource](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptoopenresource)打开资源。

3. 操作执行完后，调用[closeResource](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptocloseresource)关闭资源。

**C++接口**

1. 在CMake脚本中链接相关动态库：
   ```txt
   target_link_libraries(entry PUBLIC libhuks_ndk.z.so libhuks_external_crypto.z.so)
   ```

2. 通过证书管理系统能力提供的[openAuthorizeDialog](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenauthorizedialog22)获取[keyUri](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certreference22)，并将其作为resourceId。

3. 初始化参数集：通过[OH_Huks_InitExternalCryptoParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_initexternalcryptoparamset)、[OH_Huks_AddExternalCryptoParams](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_addexternalcryptoparams)、[OH_Huks_BuildExternalCryptoParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_buildexternalcryptoparamset)构造参数集paramSet。

4. 调用[OH_Huks_OpenResource](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_openresource)打开资源。

### 开发示例

**ArkTS接口**

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';

const resourceId = JSON.stringify({
  providerName: 'testProviderName',
  bundleName: 'com.example.cryptoapplication',
  abilityName: 'CryptoExtension',
  index: {
    key: 'testKey'
  } as ESObject
});

// 打开资源
async function openResource(): Promise<void> {
  try {
    await huksExternalCrypto.openResource(resourceId, []);
    console.info('promise: openResource success.');
  } catch (error) {
    const e = error as BusinessError;
    console.error(`promise: openResource failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}

// 关闭资源
async function closeResource(): Promise<void> {
  try {
    await huksExternalCrypto.closeResource(resourceId, []);
    console.info('promise: closeResource success.');
  } catch (error) {
    const e = error as BusinessError;
    console.error(`promise: closeResource failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}
```

**C++接口**

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

static const char *g_resourceId = "{\"providerName\":\"testProviderName\",\"abilityName\":\"CryptoExtension\",\"bundleName\":\"com.example.cryptoapplication\",\"index\":{\"key\":\"testKey\"}}";

static struct OH_Huks_ExternalCryptoParam g_openResourceParamsTest[] = {};
static struct OH_Huks_ExternalCryptoParam g_closeResourceParamsTest[] = {};

// 打开资源
static napi_value OpenResource(napi_env env, napi_callback_info info) 
{
    struct OH_Huks_Blob resourceId = {
        (uint32_t)strlen(g_resourceId),
        (uint8_t *)g_resourceId
    };
    struct OH_Huks_ExternalCryptoParamSet *openResourceParamSet = nullptr;
    OH_Huks_Result ohResult;
    do {
        ohResult = InitParamSet(&openResourceParamSet, g_openResourceParamsTest,
            sizeof(g_openResourceParamsTest) / sizeof(OH_Huks_ExternalCryptoParam));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        ohResult = OH_Huks_OpenResource(&resourceId, openResourceParamSet);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
    } while (0);
    OH_Huks_FreeExternalCryptoParamSet(&openResourceParamSet);
    
    napi_value ret;
    napi_create_int32(env, ohResult.errorCode, &ret);
    return ret;
}

// 关闭资源
static napi_value CloseResource(napi_env env, napi_callback_info info) 
{
    struct OH_Huks_Blob resourceId = {
        (uint32_t)strlen(g_resourceId),
        (uint8_t *)g_resourceId
    };
    struct OH_Huks_ExternalCryptoParamSet *closeResourceParamSet = nullptr;
    OH_Huks_Result ohResult;
    do {
        ohResult = InitParamSet(&closeResourceParamSet, g_closeResourceParamsTest,
            sizeof(g_closeResourceParamsTest) / sizeof(OH_Huks_ExternalCryptoParam));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        ohResult = OH_Huks_CloseResource(&resourceId, closeResourceParamSet);
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

## 获取资源ID

在密钥管理扩展场景下，资源ID用于标识密钥管理扩展服务中的具体资源（如UKey设备、容器、密钥等）。从API版本26.0.0开始，应用可通过[getResourceId](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogetresourceid)获取资源ID，并使用该资源ID执行密钥生成与导入导出、通用查询、PIN码认证及清除PIN码认证状态等后续操作。

### 获取途径

执行具体的密钥管理扩展操作前需先获取resourceId，用于标识要操作的密钥管理扩展资源。resourceId长度为1-1024字节，可通过以下两种路径获取：

**证书管理服务获取**

适用于浏览器双向SSL认证等需要用户选择证书的场景。

通过[openAuthorizeDialog](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenauthorizedialog22)（由证书管理提供）展示证书列表，由用户选择证书。返回的[keyUri](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certreference22)即为resourceId，每个证书链对应1个resourceId。

**通过getResourceId接口获取**

从API版本26.0.0开始支持通过getResourceId接口获取resourceId的方式，适用于密钥生成、密钥导入等不需要证书选择的场景。

### 开发步骤

本文提供通过getResourceId接口获取resourceId的开发指导。

1. 传入提供者名称（providerName），建议包含厂商信息，全局唯一，长度最大为128字节。

2. 构造必选参数：
   - 通过[HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)传入CryptoExtensionAbility名称。
   - 通过[HUKS_EXT_CRYPTO_TAG_BUNDLE_NAME](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)传入应用包名，包名长度为7-127。
   - 通过[HUKS_EXT_CRYPTO_TAG_RESOURCE_INFO](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)传入厂商自定义的资源信息。

3. 调用[getResourceId](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogetresourceid)获取resourceId。

### 开发示例

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';

let providerName: string = 'testProviderName';
let abilityName: string = 'CryptoExtensionAbility1';
let bundleName: string = 'com.example.cryptoapplication';
// 资源信息，格式和内容由密钥管理扩展服务实现方定义
let resourceInfo: string = 'vendor_defined_resource_info';

function StringToUint8Array(str: string): Uint8Array {
  const encoder = new util.TextEncoder();
  return encoder.encodeInto(str);
}

async function getResourceId(): Promise<string> {
  const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [
    {
      tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_ABILITY_NAME,
      value: StringToUint8Array(abilityName),
    },
    {
      tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_BUNDLE_NAME,
      value: StringToUint8Array(bundleName),
    },
    {
      tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_RESOURCE_INFO,
      value: StringToUint8Array(resourceInfo),
    },
  ];

  try {
    const resourceId: string = await huksExternalCrypto.getResourceId(providerName, extProperties);
    console.info(`promise: getResourceId success, resourceId: ${resourceId}`);
    return resourceId;
  } catch (error) {
    const e = error as BusinessError;
    console.error(`promise: getResourceId failed, errCode: ${e.code}, errMsg: ${e.message}`);
    throw error;
  }
}
```

## 查询

从API版本22开始，huksExternalCrypto提供查询[getProperty](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogetproperty)接口。从密钥管理扩展服务中获取通用属性信息，完成属性查询操作。

### 规格说明

打开密钥管理扩展服务中的资源后，可调用该接口获取属性信息，由密钥管理扩展服务（即[CryptoExtensionAbility](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md)）实现方提供具体的propertyId。

- resourceId为已通过[打开/关闭资源](#打开关闭资源)步骤打开的资源ID，长度为1-1024字节。

- propertyId需要与密钥管理扩展约定调用规则，长度为1-100字节。建议采用GM/T 0016-2023标准中定义的SKF函数名称。

- 输出参数通过[HUKS_EXT_CRYPTO_TAG_EXTRA_DATA](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)携带，应用可以提取查询的属性数据，并按照和密钥管理扩展服务实现方的约定，解析数据。

### 开发步骤

**ArkTS接口**

1. 通过[获取资源ID](#获取资源id)获取resourceId，并传入该resourceId进行打开资源。

2. 构造propertyId和可选输入参数。

3. 调用[getProperty](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogetproperty)获取属性信息。

**C++接口**

1. 在CMake脚本中链接相关动态库：
   ```txt
   target_link_libraries(entry PUBLIC libhuks_ndk.z.so libhuks_external_crypto.z.so)
   ```

2. 构造resourceId和propertyId，先调用[OH_Huks_OpenResource](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_openresource)打开资源。

3. 初始化参数集：通过[OH_Huks_InitExternalCryptoParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_initexternalcryptoparamset)、[OH_Huks_AddExternalCryptoParams](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_addexternalcryptoparams)、[OH_Huks_BuildExternalCryptoParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_buildexternalcryptoparamset)构造参数集paramSet。

4. 调用[OH_Huks_GetProperty](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_getproperty)获取属性信息。

5. 调用[OH_Huks_GetExternalCryptoParam](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_getexternalcryptoparam)从输出参数集中提取结果。

6. 调用[OH_Huks_FreeExternalCryptoParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_freeexternalcryptoparamset)释放参数集资源。

### 开发示例

**ArkTS接口**

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function getDeviceInfo(): Promise<void> {
  // 假设已通过openResource打开resourceId
  const testResourceId = JSON.stringify({
    providerName: 'testProviderName',
    bundleName: 'com.example.cryptoapplication',
    abilityName: 'CryptoExtension',
    index: {
        key: 'testKey'
    } as ESObject
  });

  // 设置propertyId
  const propertyId = 'SKF_GetDevInfo';
  const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [];

  // 调用getProperty获取属性信息
  try {
    await huksExternalCrypto.getProperty(testResourceId, propertyId, extProperties)
      .then((data) => {
        console.info(`promise: getProperty success, data: ${JSON.stringify(data)}`);
      }).catch((error: BusinessError) => {
        console.error(`promise: getProperty failed, errCode: ${error.code}, errMsg: ${error.message}`);
      });
  } catch (error) {
    console.error('promise: getProperty input arg invalid.');
  }
}
```

**C++接口**

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
    const char *resourceIdStr = "{\"providerName\":\"testProviderName\",\"abilityName\":\"CryptoExtension\","
                              "\"bundleName\":\"com.example.cryptoapplication\",\"index\":{\"key\":\"testKey\"}}";
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
         * 输出参数集由函数内部分配，查询到的属性数据放在OH_HUKS_EXT_CRYPTO_TAG_EXTRA_DATA TAG中。
         * 下面展示如何遍历返回的params并安全提取返回的属性字符串（示例）。
         */
        if (paramSetOut != nullptr && paramSetOut->paramsCnt > 0) {
            for (uint32_t i = 0; i < paramSetOut->paramsCnt; i++) {
                OH_Huks_ExternalCryptoParam *param = &paramSetOut->params[i];
                /* 返回数据约定：GetProperty的结果放在OH_HUKS_EXT_CRYPTO_TAG_EXTRA_DATA TAG中（示例使用JSON文本） */
                if (param->tag == OH_HUKS_EXT_CRYPTO_TAG_EXTRA_DATA) {
                    /* 注意：param->blob.data可能不是以'\0'结尾，需拷贝并手动添加终止符 */
                    char *outStr = (char *)malloc(param->blob.size + 1);
                    if (outStr != NULL) {
                        memcpy(outStr, param->blob.data, param->blob.size);
                        outStr[param->blob.size] = '\0';
                        // 解析outStr（例如使用JSON解析库），示例：
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

## 属性设置

从API版本22开始，huksExternalCrypto提供设置属性[setProperty](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptosetproperty)的接口。

### 规格说明

打开密钥管理扩展服务中的资源后，可调用该接口设置指定资源的属性值，由密钥管理扩展服务（即[CryptoExtensionAbility](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md)）实现方提供具体的propertyId。

- resourceId为已通过[打开/关闭资源](#打开关闭资源)步骤打开的资源ID，长度为1-1024字节。

- propertyId需要与密钥管理扩展约定调用规则，长度为1-100字节。建议采用GM/T 0016-2023标准中定义的SKF函数名称。

### 开发步骤

1. 通过[获取资源ID](#获取资源id)获取resourceId，并传入该resourceId进行打开资源。

2. 构造propertyId和可选输入参数。

3. 调用[setProperty](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptosetproperty)设置属性值。

### 开发示例

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function setProperty(resourceId: string, propertyId: string): Promise<void> {
  try {
    await huksExternalCrypto.setProperty(resourceId, propertyId)
      .then(() => console.info('promise: setProperty success.'))
      .catch((error: BusinessError) => {
        console.error(`promise: setProperty failed, errCode: ${error.code}, errMsg: ${error.message}`);
      });
  } catch (error) {
    console.error('promise: setProperty input arg invalid.');
  }
}
```

## 获取错误信息

从API版本26.0.0开始，huksExternalCrypto提供[getErrorInfo](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogeterrorinfo)接口，用于获取最近一次密钥管理扩展操作的详细错误信息。

该错误信息由密钥管理扩展（[CryptoExtensionAbility](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md)）返回，可用于辅助定位问题。

### 规格说明

getErrorInfo接口返回值类型为[HuksExternalErrorInfo](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalerrorinfo)，其中errno字段为密钥管理扩展服务写入的详细错误码，errorDesc为密钥管理扩展服务写入的详细错误信息，最大长度为256字节，超出部分截断后返回。

**错误信息更新规则：**

| 场景 | errno | errorDesc |
| ---- | ----- | --------- |
| 密钥管理扩展返回错误信息 | 具体错误码（非0） | 扩展返回的描述（可能为空） |
| 密钥管理扩展未返回错误信息 | 默认值0 | 默认值空字符串 |

> **注意：**
> 
> 1. 此接口仅返回密钥管理扩展的详细错误信息，HUKS内部错误通过接口异常抛出。
> 2. 当密钥管理扩展未返回详细错误信息时（errno为0），errorDesc为空字符串，开发者应通过接口异常的错误码判断错误原因。
> 3. 建议在操作失败后立即调用getErrorInfo获取详细错误信息。errno非0时，表示扩展返回了错误信息，开发者应优先使用errno定位问题。
> 4. 错误信息覆盖范围：authUkeyPin、getUkeyPinAuthState、getProperty、setProperty、openResource、closeResource、clearUkeyPinAuthState、getResourceId等接口。

### 开发步骤

1. 调用密钥管理扩展接口（如authUkeyPin、getProperty等）。

2. 操作失败后，调用[getErrorInfo](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogeterrorinfo)获取Extension错误信息。

### 开发示例

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';

function StringToUint8Array(str: string): Uint8Array {
  const encoder = new util.TextEncoder();
  return encoder.encodeInto(str);
}

async function testExtensionError(): Promise<void> {
  /* 1.假设已打开的资源如下 */
  const testResourceId = JSON.stringify({
    providerName: 'testProviderName',
    bundleName: 'com.example.cryptoapplication',
    abilityName: 'CryptoExtension',
    index: {
        key: 'testKey'
    } as ESObject
  });

  /* 2.构造参数 */
  const pin = "123456";
  const params: Array<huksExternalCrypto.HuksExternalCryptoParam> = [
    {
      tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_UKEY_PIN,
      value: StringToUint8Array(pin)
    }
  ];
  
  /* 3.验证PIN码失败后获取错误信息 */
  try {
    await huksExternalCrypto.authUkeyPin(testResourceId, params);
  } catch (error) {
    const errorInfo = huksExternalCrypto.getErrorInfo();
    if (errorInfo.errno !== 0) {
      console.error(`Extension error code: ${errorInfo.errno}`);
      console.error(`Extension error desc: ${errorInfo.errorDesc}`);
    }
  }
}
```