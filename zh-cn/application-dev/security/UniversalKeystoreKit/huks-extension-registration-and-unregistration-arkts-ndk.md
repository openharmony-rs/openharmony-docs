# CryptoExtensionAbility注册与注销

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

从API版本22开始，huksExternalCrypto提供Provider注册和注销功能接口，包括ArkTS接口和C++接口。

## 注册CryptoExtensionAbility

密钥管理扩展应用检测到密钥管理设备或服务可用时，向系统注册CryptoExtensionAbility。具体的可用性检测方式因接入的设备/服务形态而异，例如UKey物理设备监听USB插拔事件。详细规格见[接入能力](huks-extension-ability-support-overview.md#接入能力)。

### 开发步骤

**ArkTS接口**

1. 构造注册参数，包含[HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)字段，值为Ability名称的UTF-8字节流，长度为1-128字节。

2. 调用[registerProvider](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptoregisterprovider)接口，需捕获BusinessError处理失败。

**C++接口**

1. 在CMake脚本中链接相关动态库：

   ```txt
   target_link_libraries(entry PUBLIC libhuks_ndk.z.so libhuks_external_crypto.z.so)
   ```

2. 构造注册参数，需要传入[OH_HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-type-h.md#oh_huks_externalcryptotag)。

3. 调用注册接口[OH_Huks_RegisterProvider](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_registerprovider)。

### 开发示例

**ArkTS接口**

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { util } from '@kit.ArkTS';

// 字符串 → UTF-8字节流
function stringToUint8Array(str: string): Uint8Array {
    return new util.TextEncoder().encodeInto(str);
}

// 注册Provider（仅注册CryptoExtensionAbility，不注册自定义PIN弹窗）
async function registerProvider(): Promise<void> {
  // providerName建议包含厂商+产品信息以保证全局唯一
  const providerName = 'VendorA_ProductX';
  // abilityName须与module.json5中extensionAbilities.name保持一致
  const abilityName = 'CryptoExtensionAbility1';

  const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [
    {
       tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_ABILITY_NAME,
       value: stringToUint8Array(abilityName),
    },
  ];

  try {
    await huksExternalCrypto.registerProvider(providerName, extProperties);
    console.info('promise: registerProvider success.');
  } catch (error) {
    const e = error as BusinessError;
    console.error(`promise: registerProvider failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}

async function testRegisterProvider(): Promise<void> {
  await registerProvider();
}
```

**C++接口**

以下工具函数被所有示例共用，建议在实际项目中放置于公共源文件：

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
OH_Huks_Result InitParamSet(struct OH_Huks_ExternalCryptoParamSet **paramSet,
    const struct OH_Huks_ExternalCryptoParam *params, uint32_t paramCount)
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

注册CryptoExtensionAbility：

```c++
static napi_value RegisterProvider(napi_env env, napi_callback_info info)
{
    // providerName建议包含厂商+产品信息以保证全局唯一
    auto providerName = StringToBlob("VendorA_ProductX");
    // abilityName须与module.json5中extensionAbilities.name保持一致
    auto abilityName = StringToBlob("CryptoExtensionAbility1");

    struct OH_Huks_ExternalCryptoParam params[] = {
        { .tag = OH_HUKS_EXT_CRYPTO_TAG_ABILITY_NAME, .blob = abilityName }
    };

    struct OH_Huks_ExternalCryptoParamSet *providerParamSet = nullptr;
    OH_Huks_Result ohResult;
    do {
        ohResult = InitParamSet(&providerParamSet, params, sizeof(params) / sizeof(OH_Huks_ExternalCryptoParam));
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

## 注册CryptoExtensionAbility及UIExtensionAbility

从API版本26.0.0开始，支持同步注册UIExtensionAbility到系统中，仅在ArkTS接口下支持。详细规格见[接入能力](huks-extension-ability-support-overview.md#接入能力)。

### 开发步骤

1. 构造注册参数，包含[HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)字段，值为Ability名称的UTF-8字节流。

2. 构造UIExtensionAbility注册参数，包含[HUKS_EXT_CRYPTO_TAG_ABILITY_INFO](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)字段。

3. 调用[registerProvider](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptoregisterprovider)接口，需捕获BusinessError处理失败。

### 开发示例

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError, deviceInfo } from '@kit.BasicServicesKit';
import { util } from '@kit.ArkTS';

// 字符串 → UTF-8字节流
function stringToUint8Array(str: string): Uint8Array {
  return new util.TextEncoder().encodeInto(str);
}

// 自定义PIN弹窗UIExtensionAbility列表
const abilityInfoList: Array<{ abilityName: string; index: string }> = [
  { abilityName: 'UiAbility1', index: '' },
  { abilityName: 'UiAbility2', index: 'string2' },
];

// 注册Provider并注册自定义PIN弹窗UIExtensionAbility
async function registerProvider(): Promise<void> {
  try {
    /* 1.构造注册参数ability name */
    const providerName = "testProvider";
    /* 2.构造ability info */
    const abilityInfo = '[' +
       '{"abilityName":"UiAbility1","index":""},' +
       '{"abilityName":"UiAbility2","index":"string2"}]';
    const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [
      {
        tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_ABILITY_NAME,
        value: StringToUint8Array("CryptoExtension")
      }, {
        tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_ABILITY_INFO,
        value: StringToUint8Array(abilityInfo)
      }
    ];

  const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [
    {
      tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_ABILITY_NAME,
      value: stringToUint8Array(abilityName),
    },
  ];

  // API版本26.0.0开始，支持自定义PIN弹窗注册
  if (deviceInfo.sdkApiVersion >= 26) {
    extProperties.push({
       tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_ABILITY_INFO,
       value: stringToUint8Array(JSON.stringify(abilityInfoList)),
    });
  }

  try {
    await huksExternalCrypto.registerProvider(providerName, extProperties);
    console.info('promise: registerProvider success.');
  } catch (error) {
    const e = error as BusinessError;
    console.error(`promise: registerProvider failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}

async function testRegisterProvider(): Promise<void> {
  await registerProvider();
}
```

## 注销CryptoExtensionAbility

密钥管理扩展应用检测到密钥管理设备或服务不可用时，从系统注销CryptoExtensionAbility。具体的可用性检测方式因接入的设备/服务形态而异，例如UKey物理设备监听USB插拔事件、数字盾（虚拟智能卡）在应用退出时检测。详细规格见[接入能力](huks-extension-ability-support-overview.md#接入能力)。

### 开发步骤

**ArkTS接口**

1. 构造注销参数，注销单个ability需要传入[HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)参数。批量注销不需要传入[HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)参数。

2. 调用注销接口[unregisterProvider](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptounregisterprovider)。

**C++接口**

1. 在CMake脚本中链接相关动态库：
   ```txt
   target_link_libraries(entry PUBLIC libhuks_ndk.z.so libhuks_external_crypto.z.so)
   ```

2. 构造注销参数，注销单个ability需要传入[OH_HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-type-h.md#oh_huks_externalcryptotag)。批量注销不需要传入[OH_HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-type-h.md#oh_huks_externalcryptotag)。

3. 调用注销接口[OH_Huks_UnregisterProvider](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_unregisterprovider)。

### 开发示例

**ArkTS接口**

**注销单个ability**
```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { util } from '@kit.ArkTS';

// 字符串 → UTF-8字节流
function stringToUint8Array(str: string): Uint8Array {
  return new util.TextEncoder().encodeInto(str);
}

// 注销单个Ability：精确注销指定providerName+abilityName的CryptoExtensionAbility
async function unregisterProvider(): Promise<void> {
  // providerName须与注册时使用的名称一致
  const providerName = 'testProvider';
  // abilityName须与module.json5中extensionAbilities.name保持一致
  const abilityName = 'CryptoExtensionAbility1';

  const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [
    {
       tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_ABILITY_NAME,
       value: stringToUint8Array(abilityName),
    },
  ];

  try {
    await huksExternalCrypto.unregisterProvider(providerName, extProperties);
    console.info('promise: unregisterProvider success.');
  } catch (error) {
    const e = error as BusinessError;
    console.error(`promise: unregisterProvider failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}

async function testUnregisterProvider(): Promise<void> {
  await unregisterProvider();
}
```

**批量注销**
```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { util } from '@kit.ArkTS';

// 字符串 → UTF-8字节流
function stringToUint8Array(str: string): Uint8Array {
  return new util.TextEncoder().encodeInto(str);
}

// 批量注销：注销providerName下的所有CryptoExtensionAbility
async function unregisterProvider(): Promise<void> {
  // providerName 须与注册时使用的名称一致
  const providerName = 'testProvider';

  // 批量注销：extProperties留空或不指定HUKS_EXT_CRYPTO_TAG_ABILITY_NAME
  const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [];

  try {
    await huksExternalCrypto.unregisterProvider(providerName, extProperties);
    console.info('promise: unregisterProvider success.');
  } catch (error) {
    const e = error as BusinessError;
    console.error(`promise: unregisterProvider failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}

async function testUnregisterProvider(): Promise<void> {
  await unregisterProvider();
}
```

**C++接口**

以下工具函数被所有示例共用，建议在实际项目中放置于公共源文件：

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
OH_Huks_Result InitParamSet(struct OH_Huks_ExternalCryptoParamSet **paramSet, const struct OH_Huks_ExternalCryptoParam *params, uint32_t paramCount)
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

**注销单个ability：**

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

**批量注销：**

```c++
static napi_value UnregisterAllAbilities(napi_env env, napi_callback_info info)
{
    auto providerName = StringToBlob("VendorA_ProductX");

    // 批量注销：extProperties留空
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