# @ohos.bundle.overlay (overlay Module)

<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @memghaiyang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=850c7d4f71d6bc50d82f299a21bb9cea3a266f3d translatedAt=2026-08-13T02:42:19.353Z pushedAt=2026-08-13T07:42:56.544Z -->

This module provides APIs for querying the [OverlayModuleInfo](js-apis-bundleManager-overlayModuleInfo.md) of an application with the overlay feature, and disabling and enabling the feature.

An overlay feature module means that the current module contains an overlay resource package, and the application to which the current module belongs is an application with the overlay feature. For details about the overlay resource package, see [Overlay Mechanism](../../quick-start/resource-categories-and-access.md#overlay-mechanism).

> **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs provided by this module apply only to the stage model and [static overlay](../../quick-start/resource-categories-and-access.md#using-overlay-in-static-mode) mode.

## Modules to Import

``` ts
import { overlay } from '@kit.AbilityKit';
```

## overlay.setOverlayEnabled

setOverlayEnabled(moduleName:string, isEnabled: boolean): Promise\<void>

Sets the enabled/disabled state of the overlay feature module in the current application. This API uses a promise to return the result.

**System capability**: SystemCapability.BundleManager.BundleFramework.Overlay

**Parameters**

| Name      | Type    | Mandatory  | Description                                   |
| ----------- | ------ | ---- | --------------------------------------- |
| moduleName  | string | Yes    | Name of the overlay feature module in the current app.               |
| isEnabled   | boolean  | Yes  | Whether to enable the overlay feature. The value **true** indicates enabled, and **false** indicates disabled. |

**Return value**

| Type                       | Description                |
| ------------------------- | ------------------ |
| Promise\<void> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bundle Error Codes](errorcode-bundle.md).

| ID| Error Message                               |
| ------ | -------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|
| 17700002 | The specified module name is not found. |
| 17700033 | The specified module is not an overlay module. |

**Example**

```ts
import { overlay } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let moduleName = "feature";
let isEnabled = false;

try {
  overlay.setOverlayEnabled(moduleName, isEnabled)
    .then(() => {
      console.info('setOverlayEnabled success');
    }).catch((err: BusinessError) => {
    console.error('setOverlayEnabled failed due to err code: ' + err.code + ' ' + 'message:' + err.message);
  });
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error('setOverlayEnabled failed due to err code: ' + code + ' ' + 'message:' + message);
}
```

## overlay.setOverlayEnabled

setOverlayEnabled(moduleName: string, isEnabled: boolean, callback: AsyncCallback\<void>): void

Sets the enabled/disabled state of the overlay feature module in the current application. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.BundleManager.BundleFramework.Overlay

**Parameters**

| Name      | Type    | Mandatory  | Description                                   |
| ----------- | ------ | ---- | --------------------------------------- |
| moduleName  | string | Yes    | Name of the module with the overlay feature in the current app.    |
| isEnabled   | boolean  | Yes  | Whether to enable the module. The value **true** means enabled, and **false** means disabled. |
| callback    | AsyncCallback\<void> | Yes    | [AsyncCallback](../apis-basic-services-kit/js-apis-base.md#asynccallback) invoked when the enabled/disabled state of the overlay feature of the specified module is set successfully. In this case, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bundle Error Codes](errorcode-bundle.md).

| ID| Error Message                               |
| ------ | -------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|
| 17700002 | The specified module name is not found. |
| 17700033 | The specified module is not an overlay module. |

**Example**

```ts
import { overlay } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let moduleName = "feature";
let isEnabled = false;

try {
  overlay.setOverlayEnabled(moduleName, isEnabled, (err, data) => {
    if (err) {
      console.error('setOverlayEnabled failed due to err code: ' + err.code + ' ' + 'message:' + err.message);
      return;
    }
    console.info('setOverlayEnabled success');
  });
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error('setOverlayEnabled failed due to err code: ' + code + ' ' + 'message:' + message);
}
```

## overlay.getOverlayModuleInfo

getOverlayModuleInfo(moduleName: string): Promise\<OverlayModuleInfo>

Obtains the OverlayModuleInfo of the overlay feature module in the current application. This API uses a promise to return the result.

**System capability**: SystemCapability.BundleManager.BundleFramework.Overlay

**Parameters**

| Name      | Type    | Mandatory  | Description                                   |
| ----------- | ------ | ---- | ------------------------------------------ |
| moduleName | string | Yes    | Name of the overlay feature module in the current app.     |

**Return value**

| Type                       | Description                |
| ------------------------- | ------------------ |
| Promise\<[OverlayModuleInfo](js-apis-bundleManager-overlayModuleInfo.md)> | Promise used to return the result, which is an [OverlayModuleInfo](js-apis-bundleManager-overlayModuleInfo.md) object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bundle Error Codes](errorcode-bundle.md).

| ID| Error Message                               |
| ------ | -------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|
| 17700002 | The specified module name is not found. |
| 17700032 | The specified bundle does not contain any overlay module. |
| 17700033 | The specified module is not an overlay module. |

**Example**

```ts
import { overlay } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let moduleName = "feature";

(async () => {
  try {
    let overlayModuleInfo = await overlay.getOverlayModuleInfo(moduleName);
    console.info('overlayModuleInfo is ' + JSON.stringify(overlayModuleInfo));
  } catch (err) {
    let code = (err as BusinessError).code;
    let message = (err as BusinessError).message;
    console.error('getOverlayModuleInfo failed due to err code : ' + code + ' ' + 'message :' + message);
  }
})();
```

## overlay.getOverlayModuleInfo

getOverlayModuleInfo(moduleName: string, callback: AsyncCallback\<OverlayModuleInfo>): void

Obtains the OverlayModuleInfo of the overlay feature module in the current application. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.BundleManager.BundleFramework.Overlay

**Parameters**

| Name      | Type    | Mandatory  | Description                                   |
| ----------- | ------ | ---- | --------------------------------------- |
| moduleName | string | Yes    | Name of the overlay feature module in the current app.     |
| callback    | AsyncCallback\<[OverlayModuleInfo](js-apis-bundleManager-overlayModuleInfo.md)> | Yes    | [AsyncCallback](../apis-basic-services-kit/js-apis-base.md#asynccallback) used to return the result. If the [OverlayModuleInfo](js-apis-bundleManager-overlayModuleInfo.md) of the specified module in the current app is obtained successfully, **err** is undefined. Otherwise, the callback returns a specific error object.                   |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bundle Error Codes](errorcode-bundle.md).

| ID| Error Message                               |
| ------ | -------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|
| 17700002 | The specified module name is not found. |
| 17700032 | The specified bundle does not contain any overlay module. |
| 17700033 | The specified module is not an overlay module. |

**Example**

```ts
import { overlay } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let moduleName = "feature";

try {
  overlay.getOverlayModuleInfo(moduleName, (err, data) => {
    if (err) {
      console.error('getOverlayModuleInfo failed due to err code : ' + err.code + ' ' + 'message :' + err.message);
      return;
    }
    console.info('overlayModuleInfo is ' + JSON.stringify(data));
  });
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error('getOverlayModuleInfo failed due to err code : ' + code + ' ' + 'message :' + message);
}
```

## overlay.getTargetOverlayModuleInfos

getTargetOverlayModuleInfos(targetModuleName: string): Promise\<Array\<OverlayModuleInfo>>

Obtains the OverlayModuleInfo associated with the specified target module. Modules with the overlay feature generally provide an overlay resource file for other modules (target module) on the device. This API uses a promise to return the result.

**System capability**: SystemCapability.BundleManager.BundleFramework.Overlay

**Parameters**

| Name      | Type    | Mandatory  | Description                                   |
| ----------- | ------ | ---- | --------------------------------------- |
| targetModuleName | string | Yes   | Name of the target module specified by modules with the overlay feature.    |

**Return value**

| Type                                                        | Description                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Promise\<Array\<[OverlayModuleInfo](js-apis-bundleManager-overlayModuleInfo.md)>> | Promise used to return the result, which is an array of [OverlayModuleInfo](js-apis-bundleManager-overlayModuleInfo.md) objects.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bundle Error Codes](errorcode-bundle.md).

| ID| Error Message                               |
| ------ | -------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|
| 17700002 | The specified module name is not found. |
| 17700034 | The specified module is an overlay module. |

**Example**

```ts
import { overlay } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let targetModuleName = "feature";

(async () => {
  try {
    let overlayModuleInfos = await overlay.getTargetOverlayModuleInfos(targetModuleName);
    console.info('overlayModuleInfos are ' + JSON.stringify(overlayModuleInfos));
  } catch (err) {
    let code = (err as BusinessError).code;
    let message = (err as BusinessError).message;
    console.error('getTargetOverlayModuleInfos failed due to err code : ' + code + ' ' + 'message :' + message);
  }
})();
```

## overlay.getTargetOverlayModuleInfos

getTargetOverlayModuleInfos(targetModuleName: string, callback: AsyncCallback\<Array\<OverlayModuleInfo>>): void

Obtains the OverlayModuleInfo associated with the specified target module. Modules with the overlay feature generally provide an overlay resource file for other modules (target module) on the device. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.BundleManager.BundleFramework.Overlay

**Parameters**

| Name      | Type    | Mandatory  | Description                                   |
| ----------- | ------ | ---- | --------------------------------------- |
| targetModuleName | string | Yes   | Name of the target module specified by modules with the overlay feature.    |
| callback    | AsyncCallback\<Array\<[OverlayModuleInfo](js-apis-bundleManager-overlayModuleInfo.md)>> | Yes    | [AsyncCallback](../apis-basic-services-kit/js-apis-base.md#asynccallback). When the [OverlayModuleInfo](js-apis-bundleManager-overlayModuleInfo.md) of the specified target module is obtained successfully, **err** returns **undefined**. Otherwise, the callback returns a specific error object.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bundle Error Codes](errorcode-bundle.md).

| ID| Error Message                               |
| ------ | -------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.|
| 17700002 | The specified module name is not found.  |
| 17700034 | The specified module is an overlay module. |

**Example**

```ts
import { overlay } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let targetModuleName = "feature";

try {
  overlay.getTargetOverlayModuleInfos(targetModuleName, (err, data) => {
    if (err) {
      console.error('getTargetOverlayModuleInfos failed due to err code : ' + err.code + ' ' + 'message :' +
      err.message);
      return;
    }
    console.info('overlayModuleInfo is ' + JSON.stringify(data));
  });
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error('getTargetOverlayModuleInfos failed due to err code : ' + code + ' ' + 'message :' + message);
}
```

## OverlayModuleInfo

type OverlayModuleInfo = _OverlayModuleInfo.OverlayModuleInfo

OverlayModuleInfo contains the configuration information of the overlay feature module, such as its name, state, and target module, and is used to describe and manage the resource overlay configuration of an application.

**System capability**: SystemCapability.BundleManager.BundleFramework.Overlay

| Type                                                        | Description          |
| ------------------------------------------------------------ | -------------- |
| [_OverlayModuleInfo.OverlayModuleInfo](js-apis-bundleManager-overlayModuleInfo.md#overlaymoduleinfo-1) |Information about a module with the overlay feature.|