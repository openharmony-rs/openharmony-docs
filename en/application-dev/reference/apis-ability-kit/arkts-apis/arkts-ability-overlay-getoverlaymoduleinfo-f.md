# getOverlayModuleInfo

## Modules to Import

```TypeScript
import { overlay } from '@kit.AbilityKit';
```

<a id="getoverlaymoduleinfo1"></a>

## getOverlayModuleInfo

```TypeScript
function getOverlayModuleInfo(moduleName: string, callback: AsyncCallback<OverlayModuleInfo>): void
```

Obtains the OverlayModuleInfo of the overlay feature module in the current application. This API uses an asynchronous callback to return the result.

**Since:** 10

<!--Device-overlay-function getOverlayModuleInfo(moduleName: string, callback: AsyncCallback<OverlayModuleInfo>): void--><!--Device-overlay-function getOverlayModuleInfo(moduleName: string, callback: AsyncCallback<OverlayModuleInfo>): void-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Overlay

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| moduleName | string | Yes | Name of the overlay feature module in the current app. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[OverlayModuleInfo](arkts-ability-overlay-overlaymoduleinfo-t.md)&gt; | Yes | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md) used to return the result. If the [OverlayModuleInfo](arkts-ability-overlaymoduleinfo-i.md) of the specified module in the current app is obtained successfully, **err** is undefined. Otherwise, the callback returns a specific error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700002](../errorcode-bundle.md#17700002-module-name-does-not-exist) | The specified module name is not found. |
| [17700032](../errorcode-bundle.md#17700032-application-does-not-contain-a-module-with-the-overlay-feature) | The specified bundle does not contain any overlay module. |
| [17700033](../errorcode-bundle.md#17700033-module-is-not-configured-with-the-overlay-feature) | The specified module is not an overlay module. |

**Examples**

```TypeScript
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


<a id="getoverlaymoduleinfo2"></a>

## getOverlayModuleInfo

```TypeScript
function getOverlayModuleInfo(moduleName: string): Promise<OverlayModuleInfo>
```

Obtains the OverlayModuleInfo of the overlay feature module in the current application. This API uses a promise to return the result. If the API call fails, null may be returned. You need to verify the return value before using it.

**Since:** 10

<!--Device-overlay-function getOverlayModuleInfo(moduleName: string): Promise<OverlayModuleInfo>--><!--Device-overlay-function getOverlayModuleInfo(moduleName: string): Promise<OverlayModuleInfo>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Overlay

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| moduleName | string | Yes | Name of the overlay feature module in the current app. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[OverlayModuleInfo](arkts-ability-overlay-overlaymoduleinfo-t.md)&gt; | Promise used to return the result, which is an [OverlayModuleInfo](arkts-ability-overlaymoduleinfo-i.md) object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700002](../errorcode-bundle.md#17700002-module-name-does-not-exist) | The specified module name is not found. |
| [17700032](../errorcode-bundle.md#17700032-application-does-not-contain-a-module-with-the-overlay-feature) | The specified bundle does not contain any overlay module. |
| [17700033](../errorcode-bundle.md#17700033-module-is-not-configured-with-the-overlay-feature) | The specified module is not an overlay module. |

**Examples**

```TypeScript
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
