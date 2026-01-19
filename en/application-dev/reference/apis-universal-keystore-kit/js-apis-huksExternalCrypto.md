# @ohos.security.huksExternalCrypto (External Key Management)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

Provides the functionalities such as registration and deregistration of external key management extension, PIN authentication, and acquisition of authentication state.

> **Description**
>
> The initial APIs of this module are supported since API version 22. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
```

## HuksExternalCryptoTagType

Enumerates the external encrypted data types.

**System capability**: SystemCapability.Security.Huks.CryptoExtension

| Name | Value  | Description   |
| ----- | ---- | -------- |
| HUKS_EXT_CRYPTO_TAG_TYPE_INT | 1 << 28   | The tag value is an integer.|
| HUKS_EXT_CRYPTO_TAG_TYPE_BYTES | 5 << 28  | The tag value is a byte array.|

## HuksExternalCryptoTag

Enumerates the tag types of a specified parameter.

**System capability**: SystemCapability.Security.Huks.CryptoExtension

| Name   | Value  | Description  |
| ------- | ---- | -------- |
| HUKS_EXT_CRYPTO_TAG_UKEY_PIN | HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_BYTES \| 200001    | Tag of the PIN.|
| HUKS_EXT_CRYPTO_TAG_ABILITY_NAME | HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_BYTES \| 200002    | Name of [CryptoExtensionAbility](js-apis-CryptoExtensionAbility.md).|
| HUKS_EXT_CRYPTO_TAG_EXTRA_DATA | HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_BYTES \| 200003    | External data, which indicates the return data in the common query scenario.|
| HUKS_EXT_CRYPTO_TAG_UID | HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_INT \| 200004    | UID of the caller.|
| HUKS_EXT_CRYPTO_TAG_PURPOSE | HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_INT \| 200005    | Usage type of the key corresponding to the certificate chain. For details, see [CertificatePurpose](../apis-device-certificate-kit/js-apis-certManager.md#certificatepurpose22).|

## HuksExternalCryptoParam

Defines the input parameter types.

**System capability**: SystemCapability.Security.Huks.CryptoExtension

| Name| Type       | Read-Only| Optional| Description        |
| ------ | ----------------------------------- | ---- | ---- | ------------ |
| tag    | [HuksExternalCryptoTag](#huksexternalcryptotag)  | No  | No  | Parameter tag, which is used to distinguish parameters.|
| value  | boolean\|number\|bigint\|Uint8Array | No  | No  | Value of the tag.|

## HuksExternalPinAuthState

Enumerates the Ukey PIN authentication states.

**System capability**: SystemCapability.Security.Huks.CryptoExtension

| Name   | Value  | Description  |
| ------- | ---- | -------- |
| HUKS_EXT_CRYPTO_PIN_NO_AUTH | 0 | The Ukey PIN is not authenticated.|
| HUKS_EXT_CRYPTO_PIN_AUTH_SUCCEEDED | 1 | The Ukey PIN is authenticated successfully.|
| HUKS_EXT_CRYPTO_PIN_LOCKED  | 2 | The Ukey PIN is locked.|


## huksExternalCrypto.registerProvider

registerProvider(providerName: string, params: Array\<HuksExternalCryptoParam>): Promise\<void>

Registers a specified external provider. This API uses a promise to return the result.

**Required permissions**: ohos.permission.CRYPTO_EXTENSION_REGISTER

**System capability**: SystemCapability.Security.Huks.CryptoExtension

**Parameters**

| Name  | Type | Mandatory| Description |
| -------- | ------- | ---- | -------|
| providerName | string | Yes  | Provider name, which contains a maximum of 128 characters. It is recommended that the value contain the vendor information, be globally unique, and not contain sensitive data such as personal contact information.<br>A maximum of 10 providers can be registered.|
| params  | Array<[HuksExternalCryptoParam](#huksexternalcryptoparam)> | Yes | Parameters to be passed during the operation. The mandatory tag is [HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](#huksexternalcryptotag), indicating the ability name. Set this parameter based on the actual service requirements.|

**Return value**

| Type | Description |
| ------------- | --------|
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [HUKS Error Codes](errorcode-huks.md).

| ID| Error Message     |
| -------- | ------------- |
| 201 | check permission failed. |
| 801 | api is not supported. |
| 12000002 | the ability name param is missing. |
| 12000005 | IPC communication failed. |
| 12000014 | memory is insufficient. |
| 12000018 | the input parameter is invalid. |
| 12000019 | the provider is already registered. |
| 12000020 | an error occurred in the dependent module. |
| 12000025 | the number of providers exceeds the limit. |

**Example**

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';

function StringToUint8Array(str: string) {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

const providerName = "testProviderName";
const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [
  {
    tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_ABILITY_NAME,
    value: StringToUint8Array("CryptoExtension")
  }
];
huksExternalCrypto.registerProvider(providerName, extProperties)
    .then((data) => {
        console.info(`promise: registerProvider success`);
    });
```

## huksExternalCrypto.unregisterProvider

unregisterProvider(providerName: string, params?: Array\<HuksExternalCryptoParam>): Promise\<void>

Unregister a provider. This API uses a promise to return the result.

**Required permissions**: ohos.permission.CRYPTO_EXTENSION_REGISTER

**System capability**: SystemCapability.Security.Huks.CryptoExtension

**Parameters**

| Name  | Type| Mandatory| Description |
| -------- | ------| ---- | -----|
| providerName | string | Yes  | Provider name, which contains a maximum of 128 characters. It is recommended that the value contain the vendor information, be globally unique, and not contain sensitive data such as personal contact information. If a provider has registered multiple extension capabilities, all the extension capabilities of the provider will be unregistered.|
| params  | Array\<[HuksExternalCryptoParam](#huksexternalcryptoparam)> | No| Parameters to be passed during the operation.<br>You can specify [HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](#huksexternalcryptotag) in the **params** parameter to unregister the corresponding **cryptoExtensionAbility** based on the bundle name, **providerName**, and **abilityName**.<br>If [HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](#huksexternalcryptotag) is not specified in the **params** parameter or the **params** parameter is not passed, all providers under the corresponding **providerName** are unregistered.|

**Return value**

| Type  | Description  |
| -------| ------ |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [HUKS Error Codes](errorcode-huks.md).

| ID| Error Message     |
| -------- | ------------- |
| 201 | check permission failed. |
| 801 | api is not supported. |
| 12000005 | IPC communication failed. |
| 12000011 | the provider is not found. |
| 12000012 | Device environment or input parameter abnormal. This may happen for several reasons, such as the model already being unloaded. |
| 12000014 | memory is insufficient. |
| 12000018 | the input parameter is invalid. |

**Example**

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';

function StringToUint8Array(str: string) {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

const providerName = "testProviderName";
const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [
  {
    tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_ABILITY_NAME,
    value: StringToUint8Array("CryptoExtension")
  }
];
huksExternalCrypto.unregisterProvider(providerName, extProperties)
    .then((data) => {
        console.info(`promise: unregisterProvider success`);
    });
```

## huksExternalCrypto.getUkeyPinAuthState

getUkeyPinAuthState(resourceId: string, params?: Array\<HuksExternalCryptoParam>): Promise\<HuksExternalPinAuthState>

Obtains the PIN authentication state. This API uses a promise to return the result.

**System capability**: SystemCapability.Security.Huks.CryptoExtension

**Parameters**

| Name  | Type | Mandatory| Description |
| -------- | ------- | ---- | ----------|
| resourceId | string | Yes  | Resource ID, which can be obtained using [certificateManagerDialog.openAuthorizeDialog22+](../apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenauthorizedialog22). The result contains **resourceId**.|
| params  | Array\<[HuksExternalCryptoParam](#huksexternalcryptoparam)> | No  | Operation parameters. If a non-system application passes [HUKS_EXT_CRYPTO_TAG_UID](#huksexternalcryptotag), the parameter is invalid.|

**Return value**

| Type  | Description  |
| -------- | ------- |
| Promise\<[HuksExternalPinAuthState](#huksexternalpinauthstate)> | Promise used to return the authentication result.<br>**HUKS_EXT_CRYPTO_PIN_NO_AUTH**: The PIN authentication fails. **HUKS_EXT_CRYPTO_PIN_AUTH_SUCCEEDED**: The PIN authentication is successful. **HUKS_EXT_CRYPTO_PIN_LOCKED**: The PIN is locked.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [HUKS Error Codes](errorcode-huks.md).

| ID| Error Message     |
| -------- | ------------- |
| 801 | api is not supported. |
| 12000005 | IPC communication failed. |
| 12000006 | the Ukey driver operation failed. |
| 12000011 | queried entity does not exist. queried entity does not exist. This may happen because the resource ID has not been opened. |
| 12000012 | Device environment or input parameter abnormal. This error may occur if the process function is not found, or due to other issues. |
| 12000014 | memory is insufficient. |
| 12000018 | the input parameter is invalid. |
| 12000020 | the provider operation failed. |
| 12000024 | the provider or Ukey is busy. |

**Example**

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';

function StringToUint8Array(str: string) {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

const testResourceId = "{\"providerName\":\"testProviderName\", \"bundleName\":\"com.example.cryptoapplication\", \"abilityName\":\"CryptoExtension\",\"index\":{\"key\":\"testKey\"}}";
const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [];
huksExternalCrypto.getUkeyPinAuthState(testResourceId, extProperties)
    .then((data) => {
      console.info(`promise: getUkeyPinAuthState success, data: ${data}`);
    });
```

## huksExternalCrypto.getProperty

getProperty(resourceId: string, propertyId: string, params?: Array\<HuksExternalCryptoParam>): Promise\<Array\<HuksExternalCryptoParam>>

Obtains a property value. This API uses a promise to return the result. **propertyId** indicates the ID of the property to be queried. Currently, only the SKF API names defined in GMT 0016-2023 can be used as property IDs. The supported IDs are as follows:

- SKF_EnumDev
- SKF_GetDevInfo
- SKF_EnumApplication
- SKF_EnumContainer

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Security.Huks.CryptoExtension

**Parameters**

| Name  | Type | Mandatory| Description |
| -------- | ------- | ---- | ----------|
| resourceId | string | Yes  | Resource ID, which can be obtained using [certificateManagerDialog.openAuthorizeDialog22+](../apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenauthorizedialog22). The result contains **resourceId**.|
| propertyId | string | Yes  | Property name for the search operation, which is the SKF API name defined in GMT 0016-2023. You need to make adaptation based on the API name.|
| params  | Array\<[HuksExternalCryptoParam](#huksexternalcryptoparam)> | No  | Input parameters to be passed to the **ExtensionAbility**. If a non-system application passes [HUKS_EXT_CRYPTO_TAG_UID](#huksexternalcryptotag), the parameter is invalid.|

**Return value**

| Type  | Description  |
| -------- | ------- |
| Promise\<Array\<[HuksExternalCryptoParam](#huksexternalcryptoparam)>> | Param array that contains the property result to be queried.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [HUKS Error Codes](errorcode-huks.md).

| ID| Error Message     |
| -------- | ------------- |
| 801 | api is not supported. |
| 12000005 | IPC communication failed. |
| 12000006 | If the Ukey driver operation failed. Possible causes: 1. Error reported when the provider accesses the SKF interface of Ukey. |
| 12000011 | If the cached resource ID is not found. |
| 12000012 | Device environment or input parameter abnormal. This error may occur if the process function is not found, or due to other issues. |
| 12000014 | If the memory is insufficient. |
| 12000018 | the input parameter is invalid. Possible causes: 1. The resourceId or propertyId length is invalid. 2. The params contain invalid tags or invalid value types. |
| 12000020 | If the provider operation failed. Possible causes: 1. The provider occurred internal processing error. |
| 12000022 | the Ukey PIN is incorrect. |
| 12000023 | the Ukey PIN not authenticated. |
| 12000024 | If the provider or Ukey is busy. |

**Example**

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';

const testResourceId = JSON.stringify({
  providerName: "testProviderName",
  bundleName: "com.example.cryptoapplication",
  abilityName: "CryptoExtension",
  index: {
    key: "testKey"
  } as ESObject
});

let propertyId = "SKF_EnumDev";
const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [];

console.info(`promise: await huksExternalCrypto getProperty`);
async function testFunction() : Promise<void>
{
  try {
    await huksExternalCrypto.getProperty(testResourceId, propertyId, extProperties)
      .then((data) => {
        console.info(`promise: getProperty success, data: ` + JSON.stringify(data));
      });
  } catch (error) {
    console.error(`promise: getProperty failed, errCode : ${error.code}, errMsg : ${error.message}`);
  }
}
```
