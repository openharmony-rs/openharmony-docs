# setOverlayEnabled

## Modules to Import

```TypeScript
import { overlay } from '@kit.AbilityKit';
```

<a id="setoverlayenabled1"></a>

## setOverlayEnabled

```TypeScript
function setOverlayEnabled(moduleName:string, isEnabled: boolean, callback: AsyncCallback<void>): void
```

Sets the enabled/disabled state of the overlay feature module in the current application. This API uses an asynchronous callback to return the result.

**Since:** 10

<!--Device-overlay-function setOverlayEnabled(moduleName:string, isEnabled: boolean, callback: AsyncCallback<void>): void--><!--Device-overlay-function setOverlayEnabled(moduleName:string, isEnabled: boolean, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Overlay

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| moduleName | string | Yes | Name of the module with the overlay feature in the current app. |
| isEnabled | boolean | Yes | Whether to enable the module. The value **true** means enabled, and **false** means disabled. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md) invoked when the enabled/ disabled state of the overlay feature of the specified module is set successfully. In this case, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700002](../errorcode-bundle.md#17700002-module-name-does-not-exist) | The specified module name is not found. |
| [17700033](../errorcode-bundle.md#17700033-module-is-not-configured-with-the-overlay-feature) | The specified module is not an overlay module. |

**Examples**

```TypeScript
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


<a id="setoverlayenabled2"></a>

## setOverlayEnabled

```TypeScript
function setOverlayEnabled(moduleName:string, isEnabled: boolean): Promise<void>
```

Sets the enabled or disabled state of the overlay feature module in the current application. This API uses a promise to return the result. If the API call fails, null may be returned. You need to verify the return value before using it.

**Since:** 10

<!--Device-overlay-function setOverlayEnabled(moduleName:string, isEnabled: boolean): Promise<void>--><!--Device-overlay-function setOverlayEnabled(moduleName:string, isEnabled: boolean): Promise<void>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Overlay

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| moduleName | string | Yes | Name of the overlay feature module in the current app. |
| isEnabled | boolean | Yes | Whether to enable the overlay feature. The value **true** indicates enabled, and **false** indicates disabled. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700002](../errorcode-bundle.md#17700002-module-name-does-not-exist) | The specified module name is not found. |
| [17700033](../errorcode-bundle.md#17700033-module-is-not-configured-with-the-overlay-feature) | The specified module is not an overlay module. |

**Examples**

```TypeScript
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
