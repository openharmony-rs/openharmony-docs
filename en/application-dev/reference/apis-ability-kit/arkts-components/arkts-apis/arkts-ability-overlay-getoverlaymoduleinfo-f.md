# getOverlayModuleInfo

## Modules to Import

```TypeScript
import { overlay } from '@kit.AbilityKit';
```

## getOverlayModuleInfo

```TypeScript
function getOverlayModuleInfo(moduleName: string, callback: AsyncCallback<OverlayModuleInfo>): void
```

Obtains the OverlayModuleInfo about a module with the overlay feature in the current application. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.BundleManager.BundleFramework.Overlay

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| moduleName | string | Yes | Name of the module with the overlay feature. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[OverlayModuleInfo](arkts-ability-overlay-overlaymoduleinfo-t.md)&gt; | Yes | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md) used to return the result, which is an [OverlayModuleInfo](arkts-ability-overlaymoduleinfo-i.md) object. If the operation is successful, **err** is **null**; otherwise, **err** is an error object. |

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


<a id="getoverlaymoduleinfo-1"></a>

## getOverlayModuleInfo

```TypeScript
function getOverlayModuleInfo(moduleName: string): Promise<OverlayModuleInfo>
```

Obtains the OverlayModuleInfo about a module with the overlay feature in the current application. This API uses a promise to return the result.

**Since:** 10

**System capability:** SystemCapability.BundleManager.BundleFramework.Overlay

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| moduleName | string | Yes | Name of the module with the overlay feature. |

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
