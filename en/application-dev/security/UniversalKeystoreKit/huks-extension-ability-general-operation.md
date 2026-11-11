# General Operations

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=f70f62268656d3b182431efa45d33eb33ec094f1 translatedAt=2026-11-10T03:00:04.924Z pushedAt=2026-11-10T06:35:27.291Z nl=1 -->

HUKS provides a set of "general operations" interfaces in the key management extension scenario, covering resource identification, resource open and close, query, property settings, and error information acquisition. Except for getResourceId and getErrorInfo, all other operations (getProperty, setProperty, and so on) require the resource to be opened.

## Overall Relationship

| Category | Involved Interfaces | Call Phase | Resource Opening Required | Detailed Documentation |
|------|---------|---------|-------------------|---------|
| Resource lifecycle | openResource/closeResource | Before/after key management extension operations | — | [Opening and Closing Resource](#opening-and-closing-resources) |
| Resource Identifier | getResourceId | Before any operation | No | [Obtaining a Resource ID](#obtaining-a-resource-id) |
| Query | getProperty | After resource opening | Yes | [Querying Properties](#querying-properties) |
| Attribute settings | setProperty | After resource opening | Yes | [Setting Properties](#setting-properties) |
| Error Message | getErrorInfo | After any operation fails | No | [Obtaining Error Information](#obtaining-error-information) |

> **NOTE**
>
> Whether PIN authentication is required depends on the propertyId and the implementation of the key management extension. Operations such as querying device information usually do not require it; when key attributes or sensitive information are involved, PIN authentication usually needs to be completed first.

## Opening and Closing Resources

Starting from API version 22, huksExternalCrypto provides C++ interfaces for opening and closing resources; starting from API version 26.0.0, huksExternalCrypto provides ArkTS interfaces for the open and close resource function.

Before performing operations such as key operations, general operations, and PIN authentication, the application needs to open the resource first. Opening the resource requires [Obtaining a Resource ID](#obtaining-a-resource-id). After all key management extension operations are completed, the opened resource must be manually closed to avoid resource leaks.

### How to Develop

**ArkTS API**

1. Obtain the resourceId through [Obtaining a Resource ID](#obtaining-a-resource-id).

2. Call [openResource](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptoopenresource) to open the resource.

3. After the operation is completed, call [closeResource](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptocloseresource) to close the resource.

**C++ API**

1. Link the dynamic libraries in the CMake script:
   ```txt
   target_link_libraries(entry PUBLIC libhuks_ndk.z.so libhuks_external_crypto.z.so)
   ```

2. Call [openAuthorizeDialog](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenauthorizedialog22) provided by the certificate management system capability to obtain [keyUri](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certreference22), and use it as `resourceId`.

3. Initialize the parameter set: Construct the parameter set **paramSet** by using [OH_Huks_InitExternalCryptoParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_initexternalcryptoparamset), [OH_Huks_AddExternalCryptoParams](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_addexternalcryptoparams), and [OH_Huks_BuildExternalCryptoParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_buildexternalcryptoparamset).

4. Call [OH_Huks_OpenResource](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_openresource) to open the resource.

### Development Examples

**ArkTS API**

Open resource:

<!-- @[open_resource_arkts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/UkeyExtension/entry/src/main/ets/pages/OpenResource.ets) -->

``` TypeScript
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

const openResourceParams: huksExternalCrypto.HuksExternalCryptoParam[] = [];

async function openResource(): Promise<void> {
  try {
    await huksExternalCrypto.openResource(resourceId, openResourceParams)
      .then(() => {
        console.info('promise: openResource success.');
      }).catch((error: BusinessError) => {
        console.error(`promise: openResource failed, errCode : ${error.code}, errMsg : ${error.message}`);
      });
  } catch (error) {
    console.error('promise: openResource input arg invalid.');
  }
}
```

Close resource:

<!-- @[close_resource_arkts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/UkeyExtension/entry/src/main/ets/pages/CloseResource.ets) -->

``` TypeScript
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

const closeResourceParams: huksExternalCrypto.HuksExternalCryptoParam[] = [];

async function closeResource(): Promise<void> {
  try {
    await huksExternalCrypto.closeResource(resourceId, closeResourceParams)
      .then(() => {
        console.info('promise: closeResource success.');
      }).catch((error: BusinessError) => {
        console.error(`promise: closeResource failed, errCode : ${error.code}, errMsg : ${error.message}`);
      });
  } catch (error) {
    console.error('promise: closeResource input arg invalid.');
  }
}
```

**C++ API**

Open resource:

<!-- @[open_resource_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/UkeyExtension/entry/src/main/cpp/napi_init.cpp) -->

```c++
static const char *OPEN_RESOURCE_ID =
    "{\"providerName\":\"testProviderName\","
    "\"abilityName\":\"CryptoExtension\","
    "\"bundleName\":\"com.example.cryptoapplication\","
    "\"index\":{\"key\":\"testKey\"}}";

static struct OH_Huks_ExternalCryptoParam g_openResourceParamsTest[] = {};

static napi_value OpenResource(napi_env env, napi_callback_info info)
{
    struct OH_Huks_Blob resourceId = {
        (uint32_t)strlen(OPEN_RESOURCE_ID),
        (uint8_t *)OPEN_RESOURCE_ID
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
```

Close resource:

<!-- @[close_resource_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/UkeyExtension/entry/src/main/cpp/napi_init.cpp) -->

```c++
static const char *CLOSE_RESOURCE_ID =
    "{\"providerName\":\"testProviderName\","
    "\"abilityName\":\"CryptoExtension\","
    "\"bundleName\":\"com.example.cryptoapplication\","
    "\"userid\":100,"
    "\"index\":{\"key\":\"testKey\"}}";

static struct OH_Huks_ExternalCryptoParam g_closeResourceParamsTest[] = {};

static napi_value CloseResource(napi_env env, napi_callback_info info)
{
    struct OH_Huks_Blob resourceId = {
        (uint32_t)strlen(CLOSE_RESOURCE_ID),
        (uint8_t *)CLOSE_RESOURCE_ID
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

## Obtaining a Resource ID

In the key management extension scenario, a resource ID is used to identify a specific resource (such as a UKey device, container, or key) in the key management extension service. Starting from API version 26.0.0, an application can obtain a resource ID through [getResourceId](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogetresourceid), and use the resource ID to perform subsequent operations such as key generation, import and export, general query, PIN authentication, and clearing the PIN authentication state.

### Ways to Obtain

Before performing specific key management extension operations, you need to obtain the `resourceId`, which identifies the key management extension resource to be operated. The `resourceId` length is 1-1024 bytes and can be obtained through the following two paths:

**Obtaining Through the Certificate Management Service**

Applicable to scenarios that require the user to select a certificate, such as two-way SSL authentication in browsers.

Call [openAuthorizeDialog](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenauthorizedialog22) (provided by certificate management) to display the certificate list, and the user selects a certificate. The returned [keyUri](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certreference22) is the `resourceId`, with each certificate chain corresponding to one `resourceId`.

**Obtaining Through the getResourceId API**

Starting from API version 26.0.0, the `resourceId` can be obtained through the `getResourceId` API. This method is applicable to scenarios that do not require certificate selection, such as key generation and key import.

### How to Develop

This document provides development guidance on obtaining the `resourceId` through the `getResourceId` API.

1. Prepare the provider name (**providerName**), which is recommended to include vendor information and be globally unique. The maximum length is 128 bytes.

2. Construct the mandatory parameters:
   - Pass the **CryptoExtensionAbility** name through [HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag).
   - Pass the application bundle name through [HUKS_EXT_CRYPTO_TAG_BUNDLE_NAME](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag). The bundle name length is 7-127.
   - Pass vendor-defined resource information through [HUKS_EXT_CRYPTO_TAG_RESOURCE_INFO](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag).

3. Call [getResourceId](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogetresourceid) to obtain the resourceId.

### Development Examples

<!-- @[get_resource_id_arkts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/UkeyExtension/entry/src/main/ets/pages/GetResourceId.ets) -->

``` TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { util } from '@kit.ArkTS';

let providerName: string = 'testProviderName';
let abilityName: string = 'CryptoExtension';
let bundleName: string = 'com.example.cryptoapplication';
// Resource information. The format and content are defined by the key management extension service implementer.
let resourceInfo: string = 'vendor_defined_resource_info';

function stringToUint8Array(str: string): Uint8Array {
  return new util.TextEncoder().encodeInto(str);
}

async function getResourceId(): Promise<string> {
  const extProperties: huksExternalCrypto.HuksExternalCryptoParam[] = [
    {
      tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_ABILITY_NAME,
      value: stringToUint8Array(abilityName),
    },
    {
      tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_BUNDLE_NAME,
      value: stringToUint8Array(bundleName),
    },
    {
      tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_RESOURCE_INFO,
      value: stringToUint8Array(resourceInfo),
    },
  ];

  const resourceId: string = await huksExternalCrypto.getResourceId(providerName, extProperties);
  console.info(`promise: getResourceId success, resourceId: ${resourceId}`);
  return resourceId;
}
```

## Querying Properties

Starting from API version 22, huksExternalCrypto provides the query [getProperty](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogetproperty) interface. It obtains universal property information from the key management extension service to complete the property query operation.

### **Specifications**

After opening a resource in the key management extension service, you can call this interface to obtain property information. The specific propertyId is provided by the implementer of the key management extension service (that is, [CryptoExtensionAbility](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md)).

- resourceId is the resource ID opened through the [Opening and Closing Resource](#opening-and-closing-resources) steps, and its length is 1 to 1024 bytes.

- propertyId must follow the call rules agreed upon with the key management extension, and its length is 1 to 100 bytes. It is recommended to use the SKF function names defined in the GM/T 0016-2023 standard.

- The output parameter is carried through [HUKS_EXT_CRYPTO_TAG_EXTRA_DATA](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag). The application can extract the queried property data and parse the data according to the agreement with the implementer of the key management extension service.

### How to Develop

**ArkTS API**

1. Obtain the resourceId through [Obtaining a Resource ID](#obtaining-a-resource-id), and pass in this resourceId to open the resource.

2. Construct the propertyId and optional input parameters.

3. Call [getProperty](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogetproperty) to obtain the property information.

**C++ API**

1. Link the dynamic libraries in the CMake script:
   ```txt
   target_link_libraries(entry PUBLIC libhuks_ndk.z.so libhuks_external_crypto.z.so)
   ```

2. Construct the resourceId and propertyId, and call [OH_Huks_OpenResource](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_openresource) to open the resource.

3. Initialize the parameter set: Construct the parameter set **paramSet** by using [OH_Huks_InitExternalCryptoParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_initexternalcryptoparamset), [OH_Huks_AddExternalCryptoParams](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_addexternalcryptoparams), and [OH_Huks_BuildExternalCryptoParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_buildexternalcryptoparamset).

4. Call [OH_Huks_GetProperty](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_getproperty) to obtain the property information.

5. Call [OH_Huks_GetExternalCryptoParam](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_getexternalcryptoparam) to extract the result from the output parameter set.

6. Call [OH_Huks_FreeExternalCryptoParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_freeexternalcryptoparamset) to release the parameter set resource.

### Development Examples

**ArkTS API**

<!-- @[get_property_arkts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/UkeyExtension/entry/src/main/ets/pages/GetProperty.ets) -->

``` TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function getDeviceInfo(): Promise<void> {
  // Assume that resourceId has been opened through openResource.
  const testResourceId = JSON.stringify({
    providerName: 'testProviderName',
    bundleName: 'com.example.cryptoapplication',
    abilityName: 'CryptoExtension',
    index: {
        key: 'testKey'
    } as ESObject
  });

  // Set propertyId.
  const propertyId = 'SKF_GetDevInfo';
  const extProperties: huksExternalCrypto.HuksExternalCryptoParam[] = [];

  // Call getProperty to obtain the property information.
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

**C++ API**

<!-- @[get_property_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/UkeyExtension/entry/src/main/cpp/napi_init.cpp) -->

```c++
static void ExtractPropertyResult(OH_Huks_ExternalCryptoParamSet *paramSetOut)
{
    if (paramSetOut == nullptr || paramSetOut->paramsCnt == 0) {
        return;
    }
    for (uint32_t i = 0; i < paramSetOut->paramsCnt; i++) {
        OH_Huks_ExternalCryptoParam *param = &paramSetOut->params[i];
        if (param->tag != OH_HUKS_EXT_CRYPTO_TAG_EXTRA_DATA) {
            continue;
        }
        char *outStr = static_cast<char *>(malloc(param->blob.size + 1));
        if (outStr == nullptr) {
            continue;
        }
        if (memcpy_s(outStr, param->blob.size + 1, param->blob.data, param->blob.size) == EOK) {
            outStr[param->blob.size] = '\0';
        }
        free(outStr);
    }
}

static napi_value GetProperty(napi_env env, napi_callback_info info)
{
    /* 1. Assume that resourceId has been opened. */
    const char *resourceIdStr = "{\"providerName\":\"testProviderName\",\"abilityName\":\"CryptoExtension\","
                              "\"bundleName\":\"com.example.cryptoapplication\",\"index\":{\"key\":\"testKey\"}}";
    const char *propertyIdStr = "SKF_GetDevInfo";

    struct OH_Huks_Blob resourceId = {
        (uint32_t)strlen(resourceIdStr),
        (uint8_t *)resourceIdStr
    };
    struct OH_Huks_Blob propertyId = {
        (uint32_t)strlen(propertyIdStr),
        (uint8_t *)propertyIdStr
    };

    /* 2. Construct the input parameters. */
    OH_Huks_ExternalCryptoParam params[] = {};
    OH_Huks_ExternalCryptoParamSet *paramSetIn = nullptr;
    OH_Huks_ExternalCryptoParamSet *paramSetOut = nullptr;
    OH_Huks_Result ohResult;

    do {
        /* 3. Initialize and construct the input parameter set. */
        ohResult = InitParamSet(&paramSetIn, params,
            sizeof(params) / sizeof(OH_Huks_ExternalCryptoParam));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }

        /* 4. Call OH_Huks_GetProperty to obtain the property. */
        ohResult = OH_Huks_GetProperty(&resourceId, &propertyId, paramSetIn, &paramSetOut);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }

        /* 5. Extract the result from the output parameter set. */
        ExtractPropertyResult(paramSetOut);
    } while (0);

    /* 6. Release resources. */
    OH_Huks_FreeExternalCryptoParamSet(&paramSetIn);
    OH_Huks_FreeExternalCryptoParamSet(&paramSetOut);

    napi_value ret;
    napi_create_int32(env, ohResult.errorCode, &ret);
    return ret;
}
```

## Setting Properties

Starting from API version 22, huksExternalCrypto provides the interface for setting attributes [setProperty](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptosetproperty).

### **Specifications**

After opening a resource in the key management extension service, you can call this interface to set the property value of the specified resource. The specific propertyId is provided by the implementer of the key management extension service (that is, [CryptoExtensionAbility](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md)).

- resourceId is the resource ID opened through the [Opening and Closing Resources](#opening-and-closing-resources) steps, and its length is 1 to 1024 bytes.

- propertyId must follow the call rules agreed upon with the key management extension, and its length is 1 to 100 bytes. It is recommended to use the SKF function names defined in the GM/T 0016-2023 standard.

### How to Develop

1. Obtain the resourceId through [Obtaining a Resource ID](#obtaining-a-resource-id), and pass in this resourceId to open the resource.

2. Construct the propertyId and optional input parameters.

3. Call [setProperty](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptosetproperty) to set the property value.

### Development Examples

<!-- @[set_property_arkts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/UkeyExtension/entry/src/main/ets/pages/SetProperty.ets) -->

``` TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function setProperty(resourceId: string, propertyId: string): Promise<void> {
  try {
    await huksExternalCrypto.setProperty(resourceId, propertyId)
      .then(() => {
        console.info('promise: setProperty success.');
      }).catch((error: BusinessError) => {
        console.error(`promise: setProperty failed, errCode : ${error.code}, errMsg : ${error.message}`);
      });
  } catch (error) {
    console.error('promise: setProperty input arg invalid.');
  }
}
```

## Obtaining Error Information

Starting from API version 26.0.0, **huksExternalCrypto** provides the [getErrorInfo](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogeterrorinfo) API for obtaining the detailed error information of the most recent key management extension operation.

This error information is returned by the key management extension ([CryptoExtensionAbility](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md)) and can be used to help locate issues.

### **Specifications**

The return value type of the **getErrorInfo** API is [HuksExternalErrorInfo](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalerrorinfo), where the **errno** field is the detailed error code written by the key management extension service, and **errorDesc** is the detailed error information written by the key management extension service. The maximum length is 256 bytes, and any excess is truncated before being returned.

**Error information update rules:**

| Scenario | errno | errorDesc |
| ---- | ----- | --------- |
| The key management extension returns error information | Specific error code (non-zero) | Description returned by the extension (may be empty) |
| The key management extension does not return error information | Default value 0 | Default value empty string |

> **Note:**
> 
> 1. This API returns only the detailed error information of the key management extension. Internal HUKS errors are thrown through API exceptions.
> 2. When the key management extension does not return detailed error information (**errno** is 0), **errorDesc** is an empty string. Developers should determine the cause of the error through the error code of the API exception.
> 3. It is recommended to call **getErrorInfo** immediately after an operation fails to obtain the detailed error information. When **errno** is non-zero, it indicates that the extension has returned error information, and developers should prioritize using **errno** to locate the issue.
> 4. Error information coverage: **authUkeyPin**, **getUkeyPinAuthState**, **getProperty**, **setProperty**, **openResource**, **closeResource**, **clearUkeyPinAuthState**, **getResourceId**, and other APIs.

### How to Develop

1. Call a key management extension API (such as **authUkeyPin** and **getProperty**).

2. After the operation fails, call [getErrorInfo](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogeterrorinfo) to obtain the error information from the Extension.

### Development Examples

<!-- @[extension_error_arkts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/UkeyExtension/entry/src/main/ets/pages/ExtensionError.ets) -->

``` TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { util } from '@kit.ArkTS';

function stringToUint8Array(str: string): Uint8Array {
  return new util.TextEncoder().encodeInto(str);
}

async function testExtensionError(): Promise<void> {
  /* 1. Assume that the following resources are opened: */
  const testResourceId = JSON.stringify({
    providerName: 'testProviderName',
    bundleName: 'com.example.cryptoapplication',
    abilityName: 'CryptoExtension',
    index: {
        key: 'testKey'
    } as ESObject
  });

  /* 2. Construct parameters. */
  const pin = '123456';
  const params: huksExternalCrypto.HuksExternalCryptoParam[] = [
    {
      tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_UKEY_PIN,
      value: stringToUint8Array(pin)
    }
  ];
  
  /* 3. Obtain error information after PIN verification fails. */
  try {
    await huksExternalCrypto.getUkeyPinAuthState(testResourceId, params);
  } catch (error) {
    const errorInfo = huksExternalCrypto.getErrorInfo();
    if (errorInfo.errno !== 0) {
      console.error(`Extension error code: ${errorInfo.errno}`);
      console.error(`Extension error desc: ${errorInfo.errorDesc}`);
    }
  }
}
```