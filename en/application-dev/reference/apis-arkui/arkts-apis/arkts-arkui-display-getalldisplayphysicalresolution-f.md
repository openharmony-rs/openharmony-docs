# getAllDisplayPhysicalResolution

## Modules to Import

```TypeScript
import { display } from '@kit.ArkUI';
```

## getAllDisplayPhysicalResolution

```TypeScript
function getAllDisplayPhysicalResolution(): Promise<Array<DisplayPhysicalResolution>>
```

Obtains all the display modes supported by the current device, along with the physical screen resolutions for each mode. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[DisplayPhysicalResolution](arkts-arkui-display-displayphysicalresolution-i.md)&gt;&gt; | Promise used to return all the DisplayPhysicalResolution objects. The objects are sorted in ascending order of physical screen resolution information in the array. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1400003](../errorcode-display.md#1400003-abnormal-display-manager-service) | This display manager service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let promise = display.getAllDisplayPhysicalResolution();
promise.then((resolutionObjects) => {
  console.info('Obtaining physical resolution length: ' + resolutionObjects.length);
  for (let i = 0; i < resolutionObjects.length; i++) {
     console.info(`resolutionObjects[${i}].foldDisplayMode: ${resolutionObjects[i].foldDisplayMode}`);
     console.info(`resolutionObjects[${i}].physicalWidth: ${resolutionObjects[i].physicalWidth}`); 
     console.info(`resolutionObjects[${i}].physicalHeight: ${resolutionObjects[i].physicalHeight}`); 
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain physical resolution. Code: ${err.code}, message: ${err.message}`);
});
```
