# getTargetOverlayModuleInfos

## Modules to Import

```TypeScript
import { overlay } from '@kit.AbilityKit';
```

## getTargetOverlayModuleInfos

```TypeScript
function getTargetOverlayModuleInfos(targetModuleName: string, callback: AsyncCallback<Array<OverlayModuleInfo>>): void
```

Obtains the OverlayModuleInfo associated with the specified target module. Modules with the overlay feature generally provide an overlay resource file for other modules (target module) on the device. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.BundleManager.BundleFramework.Overlay

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| targetModuleName | string | Yes | Name of the target module specified by modules with the overlay feature. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[OverlayModuleInfo](arkts-ability-overlay-overlaymoduleinfo-t.md)&gt;&gt; | Yes | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md) used to return the result, which is an [OverlayModuleInfo](arkts-ability-overlaymoduleinfo-i.md) object. If the operation is successful, **err** is **null**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700002](../errorcode-bundle.md#17700002-module-name-does-not-exist) | The specified module name is not found. |
| [17700034](../errorcode-bundle.md#17700034-module-is-configured-with-the-overlay-feature) | The specified module is an overlay module. |

**Examples**

```TypeScript
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

```TypeScript
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


## getTargetOverlayModuleInfos

```TypeScript
function getTargetOverlayModuleInfos(targetModuleName: string): Promise<Array<OverlayModuleInfo>>
```

Obtains the OverlayModuleInfo associated with the specified target module. Modules with the overlay feature generally provide an overlay resource file for other modules (target module) on the device. This API uses a promise to return the result.

**Since:** 10

**System capability:** SystemCapability.BundleManager.BundleFramework.Overlay

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| targetModuleName | string | Yes | Name of the target module specified by modules with the overlay feature. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[OverlayModuleInfo](arkts-ability-overlay-overlaymoduleinfo-t.md)&gt;&gt; | Promise used to return the result, which is an array of [OverlayModuleInfo](arkts-ability-overlaymoduleinfo-i.md) objects. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700002](../errorcode-bundle.md#17700002-module-name-does-not-exist) | The specified module name is not found. |
| [17700034](../errorcode-bundle.md#17700034-module-is-configured-with-the-overlay-feature) | The specified module is an overlay module. |

**Examples**

See [getTargetOverlayModuleInfos](#gettargetoverlaymoduleinfos)
