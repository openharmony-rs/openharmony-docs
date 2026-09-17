# capture

## Modules to Import

```TypeScript
import { screenshot } from '@kit.ArkUI';
```

## capture

```TypeScript
function capture(options?: CaptureOption): Promise<image.PixelMap>
```

Takes a screenshot of the entire screen. This API uses a promise to return the result.

This API allows you to take screenshots of different screens by setting various **displayId** values, but only full -screen captures are supported. The [pick](arkts-arkui-screenshot-pick-f.md) API allows you to take screenshots of a specified region.

**Since:** 14

**Required permissions:** 
- API version 22 and later: ohos.permission.CUSTOM_SCREEN_CAPTURE or ohos.permission.CUSTOM_SCREEN_RECORDING
- API versions 14 to 21: ohos.permission.CUSTOM_SCREEN_CAPTURE

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [CaptureOption](arkts-arkui-screenshot-captureoption-i.md) | No | Capture options. If this parameter is left blank, the display with ID 0 is captured by default.<br>**Since:** 22 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | Promise used to return a PixelMap object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Incorrect parameter types. 2.Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [1400003](../errorcode-display.md#1400003-abnormal-display-manager-service) | This display manager service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

// Set screenshot parameters and specify the screen whose displayId is 0.
let captureOption: screenshot.CaptureOption = {
  displayId: 0
};
try {
  // Call the capture API to obtain a full-screen screenshot.
  let promise = screenshot.capture(captureOption);
  promise.then((pixelMap: image.PixelMap) => {
    console.info(`Succeeded in saving screenshot. Pixel bytes number: ${pixelMap.getPixelBytesNumber()}`);
    pixelMap.release(); // Release the memory in time after the PixelMap is used.
  }).catch((err: BusinessError) => {
    console.error(`Failed to save screenshot. Code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to save screenshot. Code: ${exception.code}, message: ${exception.message}`);
}
```
