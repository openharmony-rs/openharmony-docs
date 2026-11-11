# CryptoExtensionAbility Registration and Unregistration

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=f70f62268656d3b182431efa45d33eb33ec094f1 translatedAt=2026-11-10T03:08:34.928Z pushedAt=2026-11-10T06:54:53.384Z nl=1 -->

Starting from API version 22, huksExternalCrypto provides Provider registration and unregistration function interfaces, including ArkTS interfaces and C++ interfaces. Developers must first implement CryptoExtensionAbility, and then access HUKS through the registration interface before using the capability. After use, unregister to disconnect.

## Registering CryptoExtensionAbility

When the key management extension application detects that a key management device or service is available, it registers CryptoExtensionAbility with the system. The specific availability detection method varies depending on the form of the connected device/service. For example, a UKey physical device listens for USB plug-in and plug-out events. For detailed specifications, see [Access Capability](huks-extension-ability-support-overview.md#access-capabilities).

### Configuring CryptoExtensionAbility

Before registering CryptoExtensionAbility, configure it in [extensionAbilities](../../quick-start/module-configuration-file.md#extensionabilities) of module.json5.

- name: Ability name, which must be consistent with [HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag) passed when registering the Provider later. The maximum length is 127 bytes.
- srcEntry: Code path of the CryptoExtensionAbility implementation class.
- type: Fixed to crypto.
- exported: Recommended to be set to false, indicating that third-party applications are not allowed to call it directly.

```json5
// entry/src/main/module.json5
{
  "module": {
    // ...
    "extensionAbilities": [
      {
        "name": "yourCryptoExtensionAbilityName", // Custom CryptoExtensionAbility name
        "srcEntry": "./ets/yourAbilitySourcePath",
        "type": "crypto",
        "exported": false
      }
    ],
  }
}
```

**ArkTS API**

1. Construct the registration parameters, including the [HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag) field, whose value is the UTF-8 byte stream of the Ability name, with a length of 1 to 128 bytes.

2. Call the [registerProvider](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptoregisterprovider) API. You need to catch BusinessError to handle failures.

**C++ API**

1. Link the dynamic libraries in the CMake script:

   ```txt
   target_link_libraries(entry PUBLIC libhuks_ndk.z.so libhuks_external_crypto.z.so)
   ```

2. Construct registration parameters. You need to pass [OH_HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-type-h.md#oh_huks_externalcryptotag).

3. Call the registration API [OH_Huks_RegisterProvider](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_registerprovider).

### Development Examples

**ArkTS API**

<!-- @[register_provider_arkts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/UkeyExtension/entry/src/main/ets/pages/RegisterProvider.ets) -->

``` TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';

function stringToUint8Array(str: string) {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

async function registerProvider(): Promise<void> {
  try {
    /* 1. Construct the registration parameters. */
    const providerName = 'testProvider';
    const extProperties: huksExternalCrypto.HuksExternalCryptoParam[] = [
      {
        tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_ABILITY_NAME,
        value: stringToUint8Array('CryptoExtension')
      }
    ];

    /* 2. Call registerProvider. */
    await huksExternalCrypto.registerProvider(providerName, extProperties)
      .then(() => {
        console.info('promise: registerProvider success.');
      }).catch((error: BusinessError) => {
        console.error(`promise: registerProvider failed, errCode : ${error.code}, errMsg : ${error.message}`);
      });
  } catch (error) {
    console.error('promise: registerProvider input arg invalid.');
  }
}

async function testRegisterProvider() {
  await registerProvider();
}
```

**C++ API**

The following utility functions are shared by all examples. It is recommended to place them in a common source file in actual projects:

```c++
#include "napi/native_api.h"
#include "huks/native_huks_api.h"
#include "huks/native_huks_type.h"
#include "huks/native_huks_param.h"
#include "huks/native_huks_external_crypto_api.h"
#include "huks/native_huks_external_crypto_type.h"
#include <string>

// Initialize the parameter set.
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

// String → Blob
struct OH_Huks_Blob StringToBlob(const std::string &str)
{
    return { (uint32_t)str.size(), (uint8_t *)str.c_str() };
}
```

Register CryptoExtensionAbility:

<!-- @[register_provider_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/UkeyExtension/entry/src/main/cpp/napi_init.cpp) -->

```c++
static struct OH_Huks_Blob g_abilityName = {
    (uint32_t)strlen("testAbility"),
    (uint8_t *)"testAbility"
};

static struct OH_Huks_Blob g_providerName = {
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

## Registering CryptoExtensionAbility and Custom Authentication UI

Starting from API version 26.0.0, synchronous registration of UIAbility to the system is supported, and it is supported only through the ArkTS interface. Developers implement the UI layout and interaction logic of UIAbility by themselves.

Starting from API version 26.0.1, registration of [UkeyAuthExtensionAbility](../../reference/apis-device-certificate-kit/js-apis-UkeyAuthExtensionAbility.md#ukeyauthextensionability) is newly supported. Developers can inherit it and implement the UI layout and interaction logic by themselves. During registration, the abilityType field is used to distinguish the type: 0 indicates the UIAbility type (the default when not passed), and 1 indicates the UkeyAuthExtensionAbility type.

For the differences between the two approaches, refer to the comparison table in [Custom Authentication UI](huks-extension-ability-support-overview.md#customized-authentication-ui).

### Configuring Custom Authentication UI

Before registering a UIAbility or UkeyAuthExtensionAbility, you need to configure it in module.json5 first. The two types of abilities are configured in different locations: UIAbility is configured in the [abilities tag](../../quick-start/module-configuration-file.md#abilities), and UkeyAuthExtensionAbility is configured in the [extensionAbilities tag](../../quick-start/module-configuration-file.md#extensionabilities).

**Configuring UIAbility**

Configure it in the abilities tag:
- name: Ability name, which must be consistent with the abilityName field in [HUKS_EXT_CRYPTO_TAG_ABILITY_INFO](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag) at registration. The maximum length is 127 bytes.
- srcEntry: Code path of the UIAbility implementation class.
- exported: It is recommended to set it to true to allow the certificate management service to launch it.

```json5
// entry/src/main/module.json5
{
  "module": {
    // ...
    "abilities": [
      {
        "name": "yourUIAbility", // Custom UIAbility name
        "srcEntry": "./ets/yourUIAbilitySourcePath",
        "exported": true
      },
    ],
  }
}
```

**Configuring UkeyAuthExtensionAbility**

Configure it in the extensionAbilities tag, with type fixed to ukeyAuth:
- name: Ability name, which must be consistent with the abilityName field in [HUKS_EXT_CRYPTO_TAG_ABILITY_INFO](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag) at registration. The maximum length is 127 bytes.
- srcEntry: Code path of the UkeyAuthExtensionAbility implementation class.
- type: Fixed to ukeyAuth.
- exported: It is recommended to set it to true to allow the certificate management service to launch it.

```json5
// entry/src/main/module.json5
{
  "module": {
    // ...
    "extensionAbilities": [
      {
        "name": "yourUKeyAuthExtensionAbility", // Custom UkeyAuthExtensionAbility name
        "srcEntry": "./ets/yourUkeyAuthAbilitySourcePath",
        "type": "ukeyAuth",
        "exported": true
      },
    ],
  }
}
```

### How to Develop

1. Construct registration parameters, including the [HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag) field, whose value is the UTF-8 byte stream of the Ability name.

2. Construct the customized authentication UI registration parameters, including the [HUKS_EXT_CRYPTO_TAG_ABILITY_INFO](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag) field.

3. Call the [registerProvider](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptoregisterprovider) API. You need to catch BusinessError to handle failures.

### Development Examples

<!-- @[register_provider_with_auth_ui_arkts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/UkeyExtension/entry/src/main/ets/pages/RegisterProviderWithAuthUI.ets) -->

``` TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';

interface AbilityInfo {
  abilityName: string;
  index: string;
}

function stringToUint8Array(str: string) {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

async function registerProvider(): Promise<void> {
  try {
    /* 1. Construct the registration parameter ability name. */
    const providerName = 'testProvider';
    /* 2. Construct the ability info. */
    const abilityInfoList: AbilityInfo[] = [
      { abilityName: 'UiAbility1', index: '' },
      { abilityName: 'UiAbility2', index: 'string2' },
    ];
    const abilityInfo = JSON.stringify(abilityInfoList);
    const extProperties: huksExternalCrypto.HuksExternalCryptoParam[] = [
      {
        tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_ABILITY_NAME,
        value: stringToUint8Array('CryptoExtension')
      }, {
        tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_ABILITY_INFO,
        value: stringToUint8Array(abilityInfo)
      }
    ];

    /* 3. Call registerProvider. */
    await huksExternalCrypto.registerProvider(providerName, extProperties)
      .then(() => {
        console.info('promise: registerProvider success.');
      }).catch((error: BusinessError) => {
        console.error(`promise: registerProvider failed, errCode : ${error.code}, errMsg : ${error.message}`);
      });
  } catch (error) {
    console.error('promise: registerProvider input arg invalid.');
  }
}

async function testRegisterProvider() {
  await registerProvider();
}
```

**Register UkeyAuthExtensionAbility (customized authentication UI)**

Starting from API version 26.0.1, developers can register UkeyAuthExtensionAbility and use a self-implemented UI layout. When registering, the abilityType field must be set to 1.

``` TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError, deviceInfo } from '@kit.BasicServicesKit';
import { util } from '@kit.ArkTS';

// String → UTF-8 byte stream.
function stringToUint8Array(str: string): Uint8Array {
  return new util.TextEncoder().encodeInto(str);
}

// Custom authentication UI information.
interface AbilityInfo {
  abilityName: string;
  index: string;
  abilityType?: number; // Starting from API version 26.0.1: 0 = UIAbility, 1 = UkeyAuthExtensionAbility. If not passed, the default is 0.
}

// Register the Provider and register UkeyAuthExtensionAbility (custom authentication UI).
async function registerProviderWithUkeyAuthExtension(): Promise<void> {
  const providerName = "testProvider";
  const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [
    {
      tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_ABILITY_NAME,
      value: stringToUint8Array("CryptoExtension")
    }
  ];

  // Starting from API version 26.0.1, registering UkeyAuthExtensionAbility is supported.
  if (deviceInfo.sdkApiVersion > 26 ||
    (deviceInfo.sdkApiVersion === 26 && deviceInfo.sdkPatchApiVersion >= 1)) {
    const abilityInfoList: AbilityInfo[] = [
      // abilityType=1 indicates the UkeyAuthExtensionAbility type.
      { abilityName: 'UkeyAuthExtensionAbility1', index: '', abilityType: 1 },
    ];

    extProperties.push({
      tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_ABILITY_INFO,
      value: stringToUint8Array(JSON.stringify(abilityInfoList)),
    });
  }

  try {
    await huksExternalCrypto.registerProvider(providerName, extProperties);
    console.info('promise: registerProvider with UkeyAuthExtensionAbility success.');
  } catch (error) {
    const e = error as BusinessError;
    console.error(`promise: registerProvider failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}

async function testRegisterProviderWithUkeyAuthExtension(): Promise<void> {
  await registerProviderWithUkeyAuthExtension();
}
```

## Unregistering CryptoExtensionAbility

When the key management extension application detects that the key management device or service is unavailable, it unregisters CryptoExtensionAbility from the system. The specific availability detection method varies depending on the device/service form being accessed. For example, a UKey physical device listens for USB plug-in and plug-out events, and a digital shield (virtual smart card) performs detection when the application exits. For detailed specifications, see [Access Capability](huks-extension-ability-support-overview.md#access-capabilities).

### How to Develop

**ArkTS API**

1. Construct unregistration parameters. To unregister a single ability, you need to pass [HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag). This parameter does not need to be passed for batch unregistration.

2. Call [unregisterProvider](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptounregisterprovider).

**C++ API**

1. Link the dynamic libraries in the CMake script:
   ```txt
   target_link_libraries(entry PUBLIC libhuks_ndk.z.so libhuks_external_crypto.z.so)
   ```

2. Construct unregistration parameters. To unregister a single ability, you need to pass [OH_HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-type-h.md#oh_huks_externalcryptotag). This parameter does not need to be passed for batch unregistration.

3. Call the unregistration API [OH_Huks_UnregisterProvider](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_unregisterprovider).

### Development Examples

**ArkTS API**

**Single unregistration**

<!-- @[unregister_single_arkts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/UkeyExtension/entry/src/main/ets/pages/UnregisterSingleAbility.ets) -->

``` TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';

function stringToUint8Array(str: string) {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

async function unregisterProvider(): Promise<void> {
  try {
    /* 1. Construct the unregister parameters. */
    const providerName = 'testProvider';
    const extProperties: huksExternalCrypto.HuksExternalCryptoParam[] = [
      {
        tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_ABILITY_NAME,
        value: stringToUint8Array('CryptoExtension')
      }
    ];

    /* 2. Call unregisterProvider. */
    await huksExternalCrypto.unregisterProvider(providerName, extProperties)
      .then(() => {
        console.info('promise: unregisterProvider success.');
      }).catch((error: BusinessError) => {
        console.error(`promise: unregisterProvider failed, errCode : ${error.code}, errMsg : ${error.message}`);
      });
  } catch (error) {
    console.error('promise: unregisterProvider input arg invalid.');
  }
}

async function testRegisterProvider() {
  await unregisterProvider();
}
```

**Batch unregistration**

<!-- @[unregister_all_arkts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/UkeyExtension/entry/src/main/ets/pages/UnregisterAllAbilities.ets) -->

``` TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function unregisterProvider(): Promise<void> {
  try {
    /* 1. Construct the unregister parameters. */
    const providerName = 'testProvider';
    const extProperties: huksExternalCrypto.HuksExternalCryptoParam[] = [];

    /* 2. Call unregisterProvider. */
    await huksExternalCrypto.unregisterProvider(providerName, extProperties)
      .then(() => {
        console.info('promise: unregisterProvider success.');
      }).catch((error: BusinessError) => {
        console.error(`promise: unregisterProvider failed, errCode : ${error.code}, errMsg : ${error.message}`);
      });
  } catch (error) {
    console.error('promise: unregisterProvider input arg invalid.');
  }
}

async function testRegisterProvider() {
  await unregisterProvider();
}
```

**C++ API**

The following utility functions are shared by all examples. It is recommended to place them in a common source file in actual projects:

```c++
#include "napi/native_api.h"
#include "huks/native_huks_api.h"
#include "huks/native_huks_type.h"
#include "huks/native_huks_param.h"
#include "huks/native_huks_external_crypto_api.h"
#include "huks/native_huks_external_crypto_type.h"
#include <string>

// Initialize the parameter set.
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

// String → Blob.
struct OH_Huks_Blob StringToBlob(const std::string &str)
{
    return { (uint32_t)str.size(), (uint8_t *)str.c_str() };
}
```

**Unregister a single ability:**

<!-- @[unregister_single_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/UkeyExtension/entry/src/main/cpp/napi_init.cpp) -->

```c++
static napi_value unregisterSingleProvider(napi_env env, napi_callback_info info)
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

**Batch Unregister:**

<!-- @[unregister_all_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/UkeyExtension/entry/src/main/cpp/napi_init.cpp) -->

```c++
static struct OH_Huks_ExternalCryptoParam g_emptyAbilityParams[] = {};

static napi_value unregisterAllProvider(napi_env env, napi_callback_info info)
{
    struct OH_Huks_ExternalCryptoParamSet *providerParamSet = nullptr;
    OH_Huks_Result ohResult;
    do {
        ohResult = InitParamSet(&providerParamSet, g_emptyAbilityParams,
            sizeof(g_emptyAbilityParams) / sizeof(OH_Huks_ExternalCryptoParam));
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