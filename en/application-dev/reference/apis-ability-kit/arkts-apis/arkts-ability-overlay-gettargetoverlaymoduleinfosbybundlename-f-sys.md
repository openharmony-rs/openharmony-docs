# getTargetOverlayModuleInfosByBundleName (System API)

## Modules to Import

```TypeScript
import { overlay } from '@kit.AbilityKit';
```

## getTargetOverlayModuleInfosByBundleName

```TypeScript
function getTargetOverlayModuleInfosByBundleName(targetBundleName: string,
      callback: AsyncCallback<Array<OverlayModuleInfo>>): void
```

Obtains the information about all modules with the overlay feature in another application. This API uses an asynchronous callback to return the result.

No permission is required when the specified application is the caller itself.

**Since:** 10

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.BundleManager.BundleFramework.Overlay

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| targetBundleName | string | Yes | Bundle name of the application. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[OverlayModuleInfo](arkts-ability-overlay-overlaymoduleinfo-t.md)&gt;&gt; | Yes | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md) used to return the result, which is an array of [OverlayModuleInfo](arkts-ability-overlaymoduleinfo-i.md) objects. If the operation is successful, **err** is **null**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundleName is not found. |
| [17700035](../errorcode-bundle.md#17700035-application-contains-only-modules-with-the-overlay-feature) | The specified bundle is an overlay bundle. |

**Examples**

```TypeScript
import { overlay } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let targetBundleName = "com.example.myapplication_xxxxx";

try {
  overlay.getTargetOverlayModuleInfosByBundleName(targetBundleName, (err, data) => {
    if (err) {
      console.error('getTargetOverlayModuleInfosByBundleName failed due to err code : ' + err.code + ' ' + 'message :' +
      err.message);
      return;
    }
    console.info('overlayModuleInfo is ' + JSON.stringify(data));
  });
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error('getTargetOverlayModuleInfosByBundleName failed due to err code : ' + code + ' ' + 'message :' +
    message);
}
```


<a id="gettargetoverlaymoduleinfosbybundlename-1"></a>

## getTargetOverlayModuleInfosByBundleName

```TypeScript
function getTargetOverlayModuleInfosByBundleName(targetBundleName: string, moduleName: string, callback: AsyncCallback<Array<OverlayModuleInfo>>): void
```

Obtains the information about modules with the overlay feature in another application based on the target module name. This API uses an asynchronous callback to return the result.

No permission is required when the specified application is the caller itself.

**Since:** 10

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.BundleManager.BundleFramework.Overlay

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| targetBundleName | string | Yes | Bundle name of the application. |
| moduleName | string | Yes | Name of the target module. If this parameter is not specified, the API obtains the information associated with all modules in that application. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[OverlayModuleInfo](arkts-ability-overlay-overlaymoduleinfo-t.md)&gt;&gt; | Yes | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md) used to return the result, which is an array of [OverlayModuleInfo](arkts-ability-overlaymoduleinfo-i.md) objects. If the operation is successful, **err** is **null**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundleName is not found. |
| [17700002](../errorcode-bundle.md#17700002-module-name-does-not-exist) | The specified module name is not found. |
| [17700034](../errorcode-bundle.md#17700034-module-is-configured-with-the-overlay-feature) | The specified module is an overlay module. |
| [17700035](../errorcode-bundle.md#17700035-application-contains-only-modules-with-the-overlay-feature) | The specified bundle is an overlay bundle. |

**Examples**

```TypeScript
import { overlay } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let targetBundleName = "com.example.myapplication_xxxxx";
let moduleName = "feature";

try {
  overlay.getTargetOverlayModuleInfosByBundleName(targetBundleName, moduleName, (err, data) => {
    if (err) {
      console.error('getTargetOverlayModuleInfosByBundleName failed due to err code : ' + err.code + ' ' + 'message :' +
      err.message);
      return;
    }
    console.info('overlayModuleInfo is ' + JSON.stringify(data));
  });
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error('getTargetOverlayModuleInfosByBundleName failed due to err code : ' + code + ' ' + 'message :' +
    message);
}
```


<a id="gettargetoverlaymoduleinfosbybundlename-2"></a>

## getTargetOverlayModuleInfosByBundleName

```TypeScript
function getTargetOverlayModuleInfosByBundleName(targetBundleName: string, moduleName?: string): Promise<Array<OverlayModuleInfo>>
```

Obtains the information about modules with the overlay feature in another application based on the target module name. This API uses a promise to return the result.

No permission is required when the specified application is the caller itself.

**Since:** 10

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.BundleManager.BundleFramework.Overlay

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| targetBundleName | string | Yes | Bundle name of the application. |
| moduleName | string | No | Name of the target module. By default, no value is passed, and the API obtains the information associated with all modules in that application. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[OverlayModuleInfo](arkts-ability-overlay-overlaymoduleinfo-t.md)&gt;&gt; | Promise used to return the result, which is an array of [OverlayModuleInfo](arkts-ability-overlaymoduleinfo-i.md) objects. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundleName is not found. |
| [17700002](../errorcode-bundle.md#17700002-module-name-does-not-exist) | The specified module name is not found. |
| [17700034](../errorcode-bundle.md#17700034-module-is-configured-with-the-overlay-feature) | The specified module is an overlay module. |
| [17700035](../errorcode-bundle.md#17700035-application-contains-only-modules-with-the-overlay-feature) | The specified bundle is an overlay bundle. |

**Examples**

```TypeScript
import { overlay } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let targetBundleName = "com.example.myapplication_xxxxx";
let moduleName = "feature";

(async () => {
  try {
    let overlayModuleInfos = await overlay.getTargetOverlayModuleInfosByBundleName(targetBundleName, moduleName);
    console.info('overlayModuleInfos are ' + JSON.stringify(overlayModuleInfos));
  } catch (err) {
    let code = (err as BusinessError).code;
    let message = (err as BusinessError).message;
    console.error('getTargetOverlayModuleInfosByBundleName failed due to err code : ' + code + ' ' + 'message :' +
      message);
  }
})();
```
