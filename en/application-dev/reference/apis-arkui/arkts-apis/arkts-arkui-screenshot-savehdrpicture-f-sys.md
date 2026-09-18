# saveHdrPicture (System API)

## Modules to Import

```TypeScript
import { screenshot } from '@kit.ArkUI';
```

## saveHdrPicture

```TypeScript
function saveHdrPicture(options?: HdrScreenshotOptions): Promise<Array<image.PixelMap>>
```

Obtains a screenshot. This API uses a promise to return the result. SDR stands for Standard Dynamic Range, and HDR stands for High Dynamic Range.

- If the screen contains HDR resources (even if they are partially obscured), this API returns an array with both  
SDR and HDR PixelMaps, regardless of whether HDR is enabled.  
- If there are no HDR resources, it returns an array with a single SDR PixelMap. Unlike the [save](arkts-arkui-screenshot-save-f-sys.md) API, which returns a single SDR PixelMap, this API always returns an array. Additionally, this API does not support cropping, stretching, or rotating features available in the [save](arkts-arkui-screenshot-save-f-sys.md) API.

**Since:** 20

**Required permissions:** 
- API version 22 and later: ohos.permission.CAPTURE_SCREEN or ohos.permission.CUSTOM_SCREEN_RECORDING
- API versions 20 to 21: ohos.permission.CAPTURE_SCREEN

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [HdrScreenshotOptions](arkts-arkui-screenshot-hdrscreenshotoptions-i-sys.md) | No | Information about the HDR snapshot. This parameter is left unspecified by default. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt;&gt; | Promise used to return an array of PixelMap objects. If the screen contains HDR resources (even if they are partially obscured), the array contains two PixelMaps: the first is an SDR PixelMap, and the second is an HDR PixelMap. If there are no HDR resources, the array contains a single SDR PixelMap. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [1400001](../errorcode-display.md#1400001-invalid-display-or-screen) | Invalid display or screen. |
| [1400003](../errorcode-display.md#1400003-abnormal-display-manager-service) | This display manager service works abnormally. |
| [1400004](../errorcode-display.md#1400004-parameter-error) | Parameter error. Possible cause: 1.Invalid parameter range. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

let hdrScreenshotOptions: screenshot.HdrScreenshotOptions = {
  displayId: 0,
  isNotificationNeeded: true,
  isCaptureFullOfScreen: true,
  displayIntent: screenshot.DisplayIntentType.CANONICAL
};
try {
  let promise = screenshot.saveHdrPicture(hdrScreenshotOptions);
  promise.then((pixelMapArray: Array<image.PixelMap>) => {
    for (let i = 0; i < pixelMapArray.length; i++) {
      const pixelMap = pixelMapArray[i];
      console.info(`Succeeded in saving screenshot ${i}. Pixel bytes number: ${pixelMap.getPixelBytesNumber()}`);
      pixelMap.release();
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to save SDR and HDR screenshot. Code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to save SDR and HDR screenshot. Code: ${exception.code}, message: ${exception.message}`);
}
```
