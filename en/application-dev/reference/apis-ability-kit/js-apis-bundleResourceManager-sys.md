# @ohos.bundle.bundleResourceManager (bundleResourceManager Module) (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @memghaiyang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=14b72ddf869de3f3c39d4e82220102199a232a2f translatedAt=2026-11-25T11:24:22.904Z pushedAt=2026-11-26T02:52:48.085Z nl=1 -->

The module provides APIs for obtaining resource information, including [BundleResourceInfo](js-apis-bundleManager-BundleResourceInfo-sys.md) and [LauncherAbilityResourceInfo](js-apis-LauncherAbilityResourceInfo-sys.md).

> **NOTE**
>
> The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> Since API version 12, this module supports querying the icon and name resources of disabled applications and applications installed on the device (regardless of user).
>
> This module is a system API.

## Modules to Import

```ts
import { bundleResourceManager } from '@kit.AbilityKit';
```

## Enums

### ResourceFlag

Enumerates the resource information flags, which indicate the type of resource information to obtain.

**System API**: This is a system API.

**System capability:** SystemCapability.BundleManager.BundleFramework.Resource

| Name                                                    | Value        | Description                                                        |
| -------------------------------------------------------- | ---------- | ------------------------------------------------------------ |
| GET_RESOURCE_INFO_ALL                                    | 0x00000001 | Both the application icon and label are obtained.                               |
| GET_RESOURCE_INFO_WITH_LABEL                             | 0x00000002 | Only the application label is obtained.                     |
| GET_RESOURCE_INFO_WITH_ICON                              | 0x00000004 | Only the application icon is obtained.                     |
| GET_RESOURCE_INFO_WITH_SORTED_BY_LABEL                   | 0x00000008 | Used to obtain information sorted by label. It cannot be used separately and must be used together with GET_RESOURCE_INFO_ALL or GET_RESOURCE_INFO_WITH_LABEL. |
| GET_RESOURCE_INFO_WITH_DRAWABLE_DESCRIPTOR<sup>12+</sup> | 0x00000010 | The [drawableDescriptor](../apis-arkui/js-apis-arkui-drawableDescriptor-sys.md) object of the application icon is obtained.|
| GET_RESOURCE_INFO_ONLY_WITH_MAIN_ABILITY<sup>20+</sup>   | 0x00000020 | The resource information about abilities that show icons only on the home screen is obtained. It is valid only in the [getLauncherAbilityResourceInfo](#bundleresourcemanagergetlauncherabilityresourceinfo) and [getAllLauncherAbilityResourceInfo](#bundleresourcemanagergetalllauncherabilityresourceinfo) APIs.|


## APIs

### bundleResourceManager.getBundleResourceInfo

getBundleResourceInfo(bundleName: string, resourceFlags?: number): [BundleResourceInfo](js-apis-bundleManager-BundleResourceInfo-sys.md)

Synchronously obtains the application's BundleResourceInfo based on the given bundleName and resourceFlags.

**System API**: This is a system API.

**Required permissions**: ohos.permission.GET_BUNDLE_RESOURCES

**System capability**: SystemCapability.BundleManager.BundleFramework.Resource

**Parameters**

| Name    | Type  | Mandatory| Description               |
| ----------- | ------ | ---- | --------------------- |
| bundleName | string | Yes  | Bundle name of the application.|
| resourceFlags | number | No | Information contained in the BundleResourceInfo specified to return. |

**Return value**

| Type                                                       | Description                                 |
| ----------------------------------------------------------- | ------------------------------------- |
| [BundleResourceInfo](js-apis-bundleManager-BundleResourceInfo-sys.md) | Resource information of the application obtained.|


**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bundle Error Codes](errorcode-bundle.md).

| ID| Error Message                             |
| -------- | ------------------------------------- |
| 201 | Permission denied. |
| 202 | Permission denied, non-system app called system api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|
| 17700001 | The specified bundleName is not found. |


**Example**

```ts
import { bundleResourceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.example.myapplication";
let resourceFlag = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
try {
  let resourceInfo = bundleResourceManager.getBundleResourceInfo(bundleName, resourceFlag);
  hilog.info(0x0000, 'testTag', 'getBundleResourceInfo successfully. Data label: %{public}s',
    JSON.stringify(resourceInfo.label));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getBundleResourceInfo failed: %{public}s', message);
}
```

### bundleResourceManager.getLauncherAbilityResourceInfo

getLauncherAbilityResourceInfo(bundleName: string, resourceFlags?: number): Array<[LauncherAbilityResourceInfo](js-apis-LauncherAbilityResourceInfo-sys.md)>

Synchronously obtains the application's LauncherAbilityResourceInfo based on the given bundleName and resourceFlags.

**System API**: This is a system API.

**Required permissions**: ohos.permission.GET_BUNDLE_RESOURCES

**System capability**: SystemCapability.BundleManager.BundleFramework.Resource

**Parameters**

| Name    | Type  | Mandatory| Description               |
| ----------- | ------ | ---- | --------------------- |
| bundleName | string | Yes  | Bundle name of the application.|
| resourceFlags | number | No | Information contained in the LauncherAbilityResourceInfo specified to return. The default value is [ResourceFlag](#resourceflag).GET_RESOURCE_INFO_ALL. |

**Return value**

| Type                                                       | Description                                 |
| ----------------------------------------------------------- | ------------------------------------- |
| Array<[LauncherAbilityResourceInfo](js-apis-LauncherAbilityResourceInfo-sys.md)> | Resource information of the entry ability obtained.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bundle Error Codes](errorcode-bundle.md).

| ID| Error Message                             |
| -------- | ------------------------------------- |
| 201 | Permission denied. |
| 202 | Permission denied, non-system app called system api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|
| 17700001 | The specified bundleName is not found. |


**Example**

```ts
import { bundleResourceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.example.myapplication";
let resourceFlag = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
try {
  let resourceInfo = bundleResourceManager.getLauncherAbilityResourceInfo(bundleName, resourceFlag);
  hilog.info(0x0000, 'testTag', 'getLauncherAbilityResourceInfo successfully. Data label: %{public}s',
    JSON.stringify(resourceInfo[0].label));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getLauncherAbilityResourceInfo failed: %{public}s', message);
}
```

### bundleResourceManager.getAllBundleResourceInfo

getAllBundleResourceInfo(resourceFlags: number, callback: AsyncCallback<Array<[BundleResourceInfo](js-apis-bundleManager-BundleResourceInfo-sys.md)>>): void

Obtains the bundle resource information of all applications based on the given resource flags. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.GET_INSTALLED_BUNDLE_LIST and ohos.permission.GET_BUNDLE_RESOURCES

**System capability**: SystemCapability.BundleManager.BundleFramework.Resource

**Parameters**

| Name    | Type  | Mandatory| Description               |
| ----------- | ------ | ---- | --------------------- |
| resourceFlags | number | Yes | Information contained in the BundleResourceInfo specified to return. |
| callback | AsyncCallback\<Array<[BundleResourceInfo](js-apis-bundleManager-BundleResourceInfo-sys.md)>> | Yes | [AsyncCallback](../apis-basic-services-kit/js-apis-base.md#asynccallback). If the operation is successful, err is undefined and data is the array of BundleResourceInfo objects obtained; otherwise, err is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                             |
| -------- | ------------------------------------- |
| 201 | Permission denied. |
| 202 | Permission denied, non-system app called system api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|

**Example**

```ts
import { bundleResourceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let resourceFlag = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
try {
  bundleResourceManager.getAllBundleResourceInfo(resourceFlag, (err, data) => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'getAllBundleResourceInfo failed. err: %{public}s', err.message);
      return;
    }
    hilog.info(0x0000, 'testTag', 'getAllBundleResourceInfo successfully. Data length: %{public}s',
      JSON.stringify(data.length));
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllBundleResourceInfo failed: %{public}s', message);
}
```

### bundleResourceManager.getAllBundleResourceInfo

getAllBundleResourceInfo(resourceFlags: number): Promise<Array<[BundleResourceInfo](js-apis-bundleManager-BundleResourceInfo-sys.md)>>;

Obtains the bundle resource information of all applications based on the given resource flags. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.GET_INSTALLED_BUNDLE_LIST and ohos.permission.GET_BUNDLE_RESOURCES

**System capability**: SystemCapability.BundleManager.BundleFramework.Resource

**Parameters**

| Name    | Type  | Mandatory| Description               |
| ----------- | ------ | ---- | --------------------- |
| resourceFlags | number | Yes | Information contained in the BundleResourceInfo specified to return. |

**Return value**

| Type                                                        | Description                            |
| ------------------------------------------------------------ | -------------------------------- |
| Promise\<Array<[BundleResourceInfo](js-apis-bundleManager-BundleResourceInfo-sys.md)>> | Promise used to return the BundleResourceInfo array.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                             |
| -------- | ------------------------------------- |
| 201 | Permission denied. |
| 202 | Permission denied, non-system app called system api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|

**Example**

```ts
import { bundleResourceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let resourceFlag = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
try {
  bundleResourceManager.getAllBundleResourceInfo(resourceFlag).then(data => {
    hilog.info(0x0000, 'testTag', 'getAllBundleResourceInfo successfully. Data length: %{public}s',
      JSON.stringify(data.length));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getAllBundleResourceInfo failed. err: %{public}s', err.message);
  })
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllBundleResourceInfo failed: %{public}s', message);
}
```

### bundleResourceManager.getAllLauncherAbilityResourceInfo

getAllLauncherAbilityResourceInfo(resourceFlags: number, callback: AsyncCallback<Array<[LauncherAbilityResourceInfo](js-apis-LauncherAbilityResourceInfo-sys.md)>>): void

Obtains the resource information of the entry abilities of the current application based on the given resource flags. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.GET_INSTALLED_BUNDLE_LIST and ohos.permission.GET_BUNDLE_RESOURCES

**System capability**: SystemCapability.BundleManager.BundleFramework.Resource

**Parameters**

| Name    | Type  | Mandatory| Description               |
| ----------- | ------ | ---- | --------------------- |
| resourceFlags | number | Yes | Information contained in the LauncherAbilityResourceInfo specified to return. |
| callback | AsyncCallback\<Array<[LauncherAbilityResourceInfo](js-apis-LauncherAbilityResourceInfo-sys.md)>> | Yes | [AsyncCallback](../apis-basic-services-kit/js-apis-base.md#asynccallback). If the operation is successful, **err** is **undefined**, and data is the array of LauncherAbilityResourceInfo obtained. Otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                             |
| -------- | ------------------------------------- |
| 201 | Permission denied. |
| 202 | Permission denied, non-system app called system api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|

**Example**

```ts
import { bundleResourceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let resourceFlag = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
try {
  bundleResourceManager.getAllLauncherAbilityResourceInfo(resourceFlag, (err, data) => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'getAllLauncherAbilityResourceInfo failed. err: %{public}s', err.message);
      return;
    }
    hilog.info(0x0000, 'testTag', 'getAllLauncherAbilityResourceInfo successfully. Data length: %{public}s',
      JSON.stringify(data.length));
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllLauncherAbilityResourceInfo failed: %{public}s', message);
}
```

### bundleResourceManager.getAllLauncherAbilityResourceInfo

getAllLauncherAbilityResourceInfo(resourceFlags: number): Promise<Array<[LauncherAbilityResourceInfo](js-apis-LauncherAbilityResourceInfo-sys.md)>>

Obtains the resource information of the entry abilities of the current application based on the given resource flags. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.GET_INSTALLED_BUNDLE_LIST and ohos.permission.GET_BUNDLE_RESOURCES

**System capability**: SystemCapability.BundleManager.BundleFramework.Resource

**Parameters**

| Name    | Type  | Mandatory| Description               |
| ----------- | ------ | ---- | --------------------- |
| resourceFlags | number | Yes | Information contained in the LauncherAbilityResourceInfo specified to return. |

**Return value**

| Type                                                        | Description                            |
| ------------------------------------------------------------ | -------------------------------- |
| Promise\<Array<[LauncherAbilityResourceInfo](js-apis-LauncherAbilityResourceInfo-sys.md)>> | Promise used to return the LauncherAbilityResourceInfo array.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                             |
| -------- | ------------------------------------- |
| 201 | Permission denied. |
| 202 | Permission denied, non-system app called system api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|

**Example**
```ts
import { bundleResourceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let resourceFlag = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
try {
  bundleResourceManager.getAllLauncherAbilityResourceInfo(resourceFlag).then(data => {
    hilog.info(0x0000, 'testTag', 'getAllLauncherAbilityResourceInfo successfully. Data length: %{public}s',
      JSON.stringify(data.length));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getAllLauncherAbilityResourceInfo failed. err: %{public}s', err.message);
  })
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllLauncherAbilityResourceInfo failed: %{public}s', message);
}
```

### bundleResourceManager.getBundleResourceInfo<sup>12+</sup>

getBundleResourceInfo(bundleName: string, resourceFlags?: number, appIndex?: number): [BundleResourceInfo](js-apis-bundleManager-BundleResourceInfo-sys.md)

Synchronously based on the given bundleName, resourceFlags, and appIndex, obtain the application's or application clone's BundleResourceInfo.

**System API**: This is a system API.

**Required permissions**: ohos.permission.GET_BUNDLE_RESOURCES

**System capability**: SystemCapability.BundleManager.BundleFramework.Resource

**Parameters**

| Name    | Type  | Mandatory| Description               |
| ----------- | ------ | ---- | --------------------- |
| bundleName | string | Yes  | Bundle name of the application.|
| resourceFlags | number | No | Information contained in the BundleResourceInfo specified to return. |
| appIndex | number | No  | Index of the application clone. The default value is **0**.|

**Return value**

| Type                                                       | Description                                 |
| ----------------------------------------------------------- | ------------------------------------- |
| [BundleResourceInfo](js-apis-bundleManager-BundleResourceInfo-sys.md) | Resource information of the application obtained.|


**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bundle Error Codes](errorcode-bundle.md).

| ID| Error Message                             |
| -------- | ------------------------------------- |
| 201 | Permission denied. |
| 202 | Permission denied, non-system app called system api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|
| 17700001 | The specified bundleName is not found. |
| 17700061 | AppIndex not in valid range or not found. |


**Example**

```ts
import { bundleResourceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.example.myapplication";
let resourceFlag = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
let appIndex = 1;
try {
  let resourceInfo = bundleResourceManager.getBundleResourceInfo(bundleName, resourceFlag, appIndex);
  hilog.info(0x0000, 'testTag', 'getBundleResourceInfo successfully. Data label: %{public}s',
    JSON.stringify(resourceInfo.label));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getBundleResourceInfo failed: %{public}s', message);
}
```

### bundleResourceManager.getLauncherAbilityResourceInfo<sup>12+</sup>

getLauncherAbilityResourceInfo(bundleName: string, resourceFlags?: number, appIndex?: number): Array<[LauncherAbilityResourceInfo](js-apis-LauncherAbilityResourceInfo-sys.md)>

Synchronously based on the given bundleName, resourceFlags, and appIndex, obtain the application's or application clone's LauncherAbilityResourceInfo.

**System API**: This is a system API.

**Required permissions**: ohos.permission.GET_BUNDLE_RESOURCES

**System capability**: SystemCapability.BundleManager.BundleFramework.Resource

**Parameters**

| Name    | Type  | Mandatory| Description               |
| ----------- | ------ | ---- | --------------------- |
| bundleName | string | Yes  | Bundle name of the application.|
| resourceFlags | number | No | Information contained in the LauncherAbilityResourceInfo specified to return. The default value is [ResourceFlag](#resourceflag).GET_RESOURCE_INFO_ALL. |
| appIndex | number | No  | Index of the application clone. The default value is **0**.|

**Return value**

| Type                                                       | Description                                 |
| ----------------------------------------------------------- | ------------------------------------- |
| Array<[LauncherAbilityResourceInfo](js-apis-LauncherAbilityResourceInfo-sys.md)> | Resource information of the entry ability obtained.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bundle Error Codes](errorcode-bundle.md).

| ID| Error Message                             |
| -------- | ------------------------------------- |
| 201 | Permission denied. |
| 202 | Permission denied, non-system app called system api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|
| 17700001 | The specified bundleName is not found. |
| 17700061 | AppIndex not in valid range or not found. |

**Example**

```ts
import { bundleResourceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.example.myapplication";
let resourceFlag = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
let appIndex = 1;
try {
  let resourceInfo = bundleResourceManager.getLauncherAbilityResourceInfo(bundleName, resourceFlag, appIndex);
  hilog.info(0x0000, 'testTag', 'getLauncherAbilityResourceInfo successfully. Data label: %{public}s',
    JSON.stringify(resourceInfo[0].label));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getLauncherAbilityResourceInfo failed: %{public}s', message);
}
```

### bundleResourceManager.getExtensionAbilityResourceInfo<sup>20+</sup>

getExtensionAbilityResourceInfo(bundleName: string, extensionAbilityType: bundleManager.ExtensionAbilityType, resourceFlags: number, appIndex?: number): Array\<LauncherAbilityResourceInfo>

Obtains the ExtensionAbility resource information of an application based on the bundle name, ExtensionAbility type, resource flags, and clone ID. This API returns the result synchronously.

**System API**: This is a system API.

**Required permissions**: ohos.permission.GET_BUNDLE_RESOURCES

**System capability**: SystemCapability.BundleManager.BundleFramework.Resource

**Parameters**

| Name    | Type  | Mandatory| Description               |
| ----------- | ------ | ---- | --------------------- |
| bundleName | string | Yes  | Bundle name of the application.|
| extensionAbilityType | [bundleManager.ExtensionAbilityType](js-apis-bundleManager.md#extensionabilitytype) | Yes  | ExtensionAbility type. Only **ExtensionAbilityType.INPUT_METHOD**, **ExtensionAbilityType.SHARE** and **ExtensionAbilityType.ACTION** are supported.|
| [resourceFlags](#resourceflag) | number | Yes  | Resource information flags, which indicate the type of resource information to obtain.|
| appIndex | number | No  | ID of the application clone. The default value is **0**. The value ranges from 0 to 5. The value **0** indicates the main application.|

**Return value**

| Type                                                       | Description                                 |
| ----------------------------------------------------------- | ------------------------------------- |
| Array<[LauncherAbilityResourceInfo](js-apis-LauncherAbilityResourceInfo-sys.md)> | ExtensionAbility resource information of the application, including the icon and name.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bundle Error Codes](errorcode-bundle.md).

| ID| Error Message                             |
| -------- | ------------------------------------- |
| 201 | Permission denied. |
| 202 | Permission denied, non-system app called system api. |
| 17700001 | The specified bundleName is not found. |
| 17700061 | AppIndex not in valid range or not found. |

**Example**

```ts
import { bundleManager, bundleResourceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.example.myapplication";
let extensionAbilityType = bundleManager.ExtensionAbilityType.INPUT_METHOD;
let resourceFlag = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
try {
  let resourceInfo =
    bundleResourceManager.getExtensionAbilityResourceInfo(bundleName, extensionAbilityType, resourceFlag);
  hilog.info(0x0000, 'testTag', 'getExtensionAbilityResourceInfo successfully. Data label: %{public}s',
    JSON.stringify(resourceInfo[0].label));
} catch (err) {
  let message = (err as BusinessError).message;
  let code = (err as BusinessError).code;
  hilog.error(0x0000, 'testTag', 'getExtensionAbilityResourceInfo failed: %{public}d %{public}s', code, message);
}
```

### bundleResourceManager.getAllUninstalledBundleResourceInfo<sup>21+</sup>

getAllUninstalledBundleResourceInfo(resourceFlags: number): Promise\<Array\<BundleResourceInfo>>

Obtains the bundle resource information of all uninstalled applications that have retained data based on the given resource flags. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.GET_BUNDLE_RESOURCES

**System capability**: SystemCapability.BundleManager.BundleFramework.Resource

**Parameters**

| Name    | Type  | Mandatory| Description               |
| ----------- | ------ | ---- | --------------------- |
| resourceFlags | number | Yes  | Type of the resource information to obtain. For details, see [ResourceFlag](#resourceflag).|

**Return value**

| Type                                                        | Description                            |
| ------------------------------------------------------------ | -------------------------------- |
| Promise\<Array<[BundleResourceInfo](js-apis-bundleManager-BundleResourceInfo-sys.md)>> | Promise used to return the BundleResourceInfo array.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                             |
| -------- | ------------------------------------- |
| 201 | Permission denied. |
| 202 | Permission denied, non-system app called system api. |

**Example**

```ts
import { bundleResourceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let resourceFlag = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
try {
  bundleResourceManager.getAllUninstalledBundleResourceInfo(resourceFlag).then(data => {
    hilog.info(0x0000, 'testTag', 'getAllUninstalledBundleResourceInfo successfully. Data length: %{public}s',
      JSON.stringify(data.length));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getAllUninstalledBundleResourceInfo failed. err: %{public}s', err.message);
  })
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllUninstalledBundleResourceInfo failed: %{public}s', message);
}
```

### bundleResourceManager.getLauncherAbilityResourceInfoList<sup>23+</sup>

getLauncherAbilityResourceInfoList(optionsList: Array\<BundleOptions>, resourceFlags: number): Promise\<Array\<LauncherAbilityResourceInfo>>

Obtains the launcher ability resource information of each application corresponding to the **BundleOptions** element in **optionsList**. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.GET_INSTALLED_BUNDLE_LIST and ohos.permission.GET_BUNDLE_RESOURCES

**System capability**: SystemCapability.BundleManager.BundleFramework.Resource

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name       | Type                                                        | Mandatory| Description                                                        |
| ------------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| optionsList   | Array\<[BundleOptions](js-apis-bundleManager-BundleInfo-sys.md#bundleoptions)> | Yes  | Parameters of the applications to query.<br>**bundleName**, **moduleName**, and **abilityName** are mandatory parameters.<br>Value range of **appIndex**: [0, 5]. The default value is **0** if not specified.<br>**userId** is an invalid parameter. It does not need to be passed, and will not take effect if passed.|
| resourceFlags | number                                                       | Yes  | Resource information flags, which indicate the type of resource information to obtain. The value is an enumerated value of [ResourceFlag](#resourceflag), excluding [ResourceFlag](#resourceflag).GET_RESOURCE_INFO_WITH_SORTED_BY_LABEL and [ResourceFlag](#resourceflag).GET_RESOURCE_INFO_ONLY_WITH_MAIN_ABILITY.|

**Return value**

| Type                                                        | Description                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Promise\<Array<[LauncherAbilityResourceInfo](js-apis-LauncherAbilityResourceInfo-sys.md#launcherabilityresourceinfo)>> | Promise used to return the launcher ability resource information of the specified application list.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bundle Error Codes](errorcode-bundle.md).

| ID| Error Message                                            |
| -------- | ---------------------------------------------------- |
| 201      | Permission denied.                                   |
| 202      | Permission denied. A non-system application is not allowed to call a system API. |
| 801      | Capability not supported. |
| 17700001 | The specified bundle is not found.  |
| 17700002 | The specified module is not found.  |
| 17700003 | The specified ability is not found. |
| 17700061 | The specified app index is invalid. |

**Example**

```ts
import { bundleManager, bundleResourceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

// Replace the application information with the actual one.
let option: bundleManager.BundleOptions = {
  bundleName: 'com.example.demo',
  moduleName: 'entry',
  abilityName: 'EntryAbility',
  appIndex: 0
};

let optionsList: Array<bundleManager.BundleOptions> = [];
optionsList.push(option);
let resourceFlag = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
try {
  bundleResourceManager.getLauncherAbilityResourceInfoList(optionsList, resourceFlag).then(data => {
    hilog.info(0x0000, 'testTag', 'getLauncherAbilityResourceInfoList successfully. Data length: %{public}s',
      JSON.stringify(data.length));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getLauncherAbilityResourceInfoList failed. err: %{public}s', err.message);
  })
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getLauncherAbilityResourceInfoList failed: %{public}s', message);
}
```

### bundleResourceManager.getBundleResourceArchiveInfo

getBundleResourceArchiveInfo(filePath: string, resourceFlags?: number): Promise\<BundleResourceInfo>

Obtains the BundleResourceInfo of the application based on the given bundle file path and resourceFlags. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions:** ohos.permission.GET_BUNDLE_RESOURCES

**System capability:** SystemCapability.BundleManager.BundleFramework.Resource

**Model restriction**: This API can be used only in the stage model.

**Since:** 26.0.1

**Parameters**

| Name | Type | Mandatory | Description |
| ----------- | ------ | ---- | --------------------- |
| filePath | string | Yes | Path to the stored bundle file. Both the absolute path of the current application and the sandbox path of the data directory are supported. |
| resourceFlags | number | No | Information contained in the BundleResourceInfo specified to return. The value is a [ResourceFlag](#resourceflag) enum value, and the default value is GET_RESOURCE_INFO_ALL. |

**Return value**

| Type | Description |
| ------------------------------------------------------------ | ------------------------------------- |
| Promise\<[BundleResourceInfo](js-apis-bundleManager-BundleResourceInfo-sys.md)> | Promise object used to return the BundleResourceInfo of the specified application. |


**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bundle Error Codes](errorcode-bundle.md).

| ID | Error Message |
| -------- | ------------------------------------- |
| 201 | Permission verification failed. |
| 202 | Permission verification failed. A non-system application calls a system api. |
| 17700022 | The filePath is invalid. |
| 17700101 | Bundle manager service is excepted. |


**Example**

```ts
import { bundleResourceManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

// Replace it with the actual application to query path.

let filePath = "/data/storage/el2/base/files/entry.hap";
let resourceFlag = bundleResourceManager.ResourceFlag.GET_RESOURCE_INFO_ALL;
try {
  bundleResourceManager.getBundleResourceArchiveInfo(filePath, resourceFlag).then(data => {
    hilog.info(0x0000, 'testTag', 'getBundleResourceArchiveInfo successfully. Data label: %{public}s',
      JSON.stringify(data.label));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getBundleResourceArchiveInfo failed. err: %{public}s', err.message);
  })
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getBundleResourceArchiveInfo failed: %{public}s', message);
}
```

## BundleResourceInfo

type BundleResourceInfo = _BundleResourceInfo

Defines the icon and name of an application.

**System API**: This is a system API.

**System capability**: SystemCapability.BundleManager.BundleFramework.Resource

| Type                                                        | Description          |
| ------------------------------------------------------------ | -------------- |
| [_BundleResourceInfo](js-apis-bundleManager-BundleResourceInfo-sys.md#bundleresourceinfo) |Icon and name of the application.|

## LauncherAbilityResourceInfo

type LauncherAbilityResourceInfo = _LauncherAbilityResourceInfo

Defines the entry icon and name of an application.

**System API**: This is a system API.

**System capability**: SystemCapability.BundleManager.BundleFramework.Resource

| Type                                                        | Description          |
| ------------------------------------------------------------ | -------------- |
| [_LauncherAbilityResourceInfo](js-apis-LauncherAbilityResourceInfo-sys.md#launcherabilityresourceinfo) |Defines the entry icon and name of an application.|