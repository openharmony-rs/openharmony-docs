# @ohos.screenshot (Screenshot) (System API)
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @oh_wangxk; @logn-->
<!--Designer: @hejunfei1991-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

The **Screenshot** module provides APIs for you to set information such as the region to capture and the size of the screen region when capturing a screen. It serves scenarios such as screen content sharing, feedback, and test verification. Supporting common and HDR screenshot capture modes, this module provides features such as region selection, rotation, multi-screen, and screenshot capture notifications, helping you flexibly obtain screen content.

>  **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> This topic describes only system APIs provided by the module. For details about its public APIs, see [@ohos.screenshot](js-apis-screenshot.md).

## Modules to Import

```ts
import { screenshot } from '@kit.ArkUI';
```

## ScreenshotOptions

Describes the screenshot options.

**System API**: This is a system API.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

| Name                | Type         |  Read-Only|  Optional| Description                                                        |
| ---------------------- | ------------- | ---- | ---- | ------------------------------------------------------------ |
| screenRect             | [Rect](js-apis-screenshot.md#rect) | No | Yes| Region of the screen to capture. If no value is passed, the region of the logical screen associated with the specified display ID is returned.                      |
| imageSize              | [Size](#size) | No| Yes | Size of the captured image. If no value is passed, the size of the logical screen associated with the specified display ID is returned. If **screenRect** is smaller than **imageSize**, the image is stretched to **imageSize**; otherwise, it is compressed to **imageSize**.                      |
| rotation               | number        | No | Yes| Rotation angle of the captured image. Currently, only the value **0** is supported. The default value is **0**. If other values are passed, the default value is used.    |
| displayId<sup>8+</sup> | number        | No| Yes | ID of the [display](js-apis-display.md#display) device on which the screen region is to be captured. The value must be an integer. The default value is **0**.|
| isNotificationNeeded<sup>14+</sup>| boolean        | No | Yes| Whether to send a notification after a snapshot is captured. **true** to send, **false** otherwise. The default value is **true**. Such a notification can be listened for through [captureStatusChange](js-apis-display.md#displayoncapturestatuschange12).  |
| isCaptureFullOfScreen<sup>20+</sup> | boolean        | No | Yes| Whether to capture all displays on the current screen. If the screen contains multiple displays, the value **true** means that the entire screen is captured, and **false** means that only the region of the logical screen associated with the specified display ID is captured.|

## HdrScreenshotOptions<sup>20+</sup>

Describes the HDR screenshot options.

**System API**: This is a system API.

**System capability**: SystemCapability.Window.SessionManager

| Name                | Type         |  Read-Only|  Optional| Description                                                        |
| ---------------------- | ------------- | --- | ---- | ------------------------------------------------------------ |
| displayId | number        | No| Yes  | ID of the [display](js-apis-display.md#display) device on which the screen region is to be captured. The value must be an integer. The default value is **0**.|
| isNotificationNeeded| boolean        | No| Yes  | Whether to send a notification after a snapshot is captured. **true** to send, **false** otherwise. The default value is **true**. Such a notification can be listened for through [captureStatusChange](js-apis-display.md#displayoncapturestatuschange12).  |
| isCaptureFullOfScreen | boolean        | No| Yes  | Whether to capture all displays on the current screen. If the screen contains multiple displays, the value **true** means that the entire screen is captured, and **false** means that only the region of the logical screen associated with the specified display ID is captured. The default value is **false**.|
| displayIntent | [DisplayIntentType](#displayintenttype)        | No| Yes  | Rendering mode of the captured HDR image. This does not affect the SDR image effect. The default value is **screenshot.DisplayIntentType.CANONICAL**.<br>**Since**: 26.0.0<br>**Model restriction**: This API can be used only in the stage model.|

## DisplayIntentType 

Enumerates the rendering modes of the captured HDR image.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Window.SessionManager

| Name| Value| Description|
| -------- | -------- | -------- |
| CANONICAL | 0 | The specified screenshot is rendered based on the standard HDR display attribute to optimize the display effect of the screenshot on different HDR displays.|
| LOCAL | 1 | The specified screenshot is rendered based on the current HDR display attribute to ensure that the display effect of the screenshot is consistent with that of the current display from which the screenshot is captured.|

## Size

Describes the size of the screen region to capture.

**System API**: This is a system API.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

| Name                | Type         |  Read-Only|  Optional| Description                                                        |
| ------ | ------ | ---- | ---- | ------------------------------------------------------------ |
| width  | number | No  | No  | Width of the screen region to capture, in px. The value must be an integer.|
| height | number | No  | No  | Height of the screen region to capture, in px. The value must be an integer.|

## screenshot.save

save(options: ScreenshotOptions, callback: AsyncCallback&lt;image.PixelMap&gt;): void

Obtains a screenshot. This API uses an asynchronous callback to return the result.

The returned **PixelMap** object must be manually released. After using the object, you must call [release()](../apis-image-kit/arkts-apis-image-PixelMap.md#release7) to release the memory. Otherwise, memory leakage may occur.

**System API**: This is a system API.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

**Required permissions**:
- API versions 22+: **ohos.permission.CAPTURE_SCREEN** or **ohos.permission.CUSTOM_SCREEN_RECORDING**
- API versions 7-21: **ohos.permission.CAPTURE_SCREEN**

**Parameters**

| Name  | Type                                   | Mandatory| Description                                                        |
| -------- | --------------------------------------- | ---- | ------------------------------------------------------------ |
| options  | [ScreenshotOptions](#screenshotoptions) | Yes  | Information about the snapshot. If the screen to capture is a virtual screen, the snapshot is a white screen.|
| callback | AsyncCallback&lt;[image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)&gt;     | Yes  | Callback used to return a PixelMap object. The size of the PixelMap object is **imageSize**. If **imageSize** is not specified, the size of the logical screen associated with the specified display ID is used.                                  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Display Error Codes](errorcode-display.md).

| ID| Error Message|
| ------- | -------------------------- |
| 201     | Permission verification failed. The application does not have the permission required to call the API. |
| 202     | Permission verification failed. A non-system application calls a system API.<br>Applicable versions: 11+|
| 1400001 | Invalid display or screen.<br>Applicable versions: 11+|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

let screenshotOptions: screenshot.ScreenshotOptions = {
  screenRect: {
    left: 200,
    top: 100,
    width: 200,
    height: 200 },
  imageSize: {
    width: 300,
    height: 300 },
  rotation: 0,
  displayId: 0,
  isNotificationNeeded: true,
  isCaptureFullOfScreen: true
};
// Call the save method to obtain the screenshot.
screenshot.save(screenshotOptions, (err: BusinessError, pixelMap: image.PixelMap) => {
  if (err) {
    console.error(`Failed to save screenshot. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in saving screenshot. Pixel bytes number: ${pixelMap.getPixelBytesNumber()}`);
  pixelMap.release(); // Release the memory in time after the PixelMap is used.
});
```

## screenshot.save

save(callback: AsyncCallback&lt;image.PixelMap&gt;): void

Obtains a screenshot. This API uses an asynchronous callback to return the result.

The returned **PixelMap** object must be manually released. After using the object, you must call [release()](../apis-image-kit/arkts-apis-image-PixelMap.md#release7) to release the memory. Otherwise, memory leakage may occur.

**System API**: This is a system API.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

**Required permissions**:
- API versions 22+: **ohos.permission.CAPTURE_SCREEN** or **ohos.permission.CUSTOM_SCREEN_RECORDING**
- API versions 7-21: **ohos.permission.CAPTURE_SCREEN**

**Parameters**

| Name  | Type                                   | Mandatory| Description                                                        |
| -------- | --------------------------------------- | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback&lt;[image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)&gt;     | Yes  | Callback used to return a PixelMap object.                                  |


**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------- |
| 201     | Permission verification failed. The application does not have the permission required to call the API. |
| 202     | Permission verification failed. A non-system application calls a system API. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

// Call the save method to obtain the screenshot.
screenshot.save((err: BusinessError, pixelMap: image.PixelMap) => {
  if (err) {
    console.error(`Failed to save screenshot. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in saving screenshot. Pixel bytes number: ${pixelMap.getPixelBytesNumber()}`);
  pixelMap.release(); // Release the memory in time after the PixelMap is used.
});
```

## screenshot.save

save(options?: ScreenshotOptions): Promise&lt;image.PixelMap&gt;

Obtains a screenshot. This API uses a promise to return the result.

The returned **PixelMap** object must be manually released. After using the object, you must call [release()](../apis-image-kit/arkts-apis-image-PixelMap.md#release7) to release the memory. Otherwise, memory leakage may occur.

**System API**: This is a system API.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

**Required permissions**:
- API versions 22+: **ohos.permission.CAPTURE_SCREEN** or **ohos.permission.CUSTOM_SCREEN_RECORDING**
- API versions 7-21: **ohos.permission.CAPTURE_SCREEN**

**Parameters**

| Name | Type                                   | Mandatory| Description                                                        |
| ------- | --------------------------------------- | ---- | ------------------------------------------------------------ |
| options | [ScreenshotOptions](#screenshotoptions) | No  | Information about the snapshot. If the screen to capture is a virtual screen, the snapshot is a white screen.|

**Return value**

| Type                         | Description                                           |
| ----------------------------- | ----------------------------------------------- |
| Promise&lt;[image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)&gt; | Promise used to return a PixelMap object. The size is specified by **imageSize**. If **imageSize** is not specified, the size of the logical screen associated with the specified display ID is used by default.|


**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Display Error Codes](errorcode-display.md).

| ID| Error Message|
| ------- | -------------------------- |
| 201     | Permission verification failed. The application does not have the permission required to call the API. |
| 202     | Permission verification failed. A non-system application calls a system API. |
| 1400001 | Invalid display or screen. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

let screenshotOptions: screenshot.ScreenshotOptions = {
  screenRect: {
    left: 200,
    top: 100,
    width: 200,
    height: 200 },
  imageSize: {
    width: 300,
    height: 300 },
  rotation: 0,
  displayId: 0,
  isNotificationNeeded: true,
  isCaptureFullOfScreen: true
};
try {
  let promise = screenshot.save(screenshotOptions);
  promise.then((pixelMap: image.PixelMap) => {
    let pixelBytesNumber = pixelMap.getPixelBytesNumber();
    console.info(`Succeeded in saving screenshot. Pixel bytes number: ${pixelBytesNumber}`);
    pixelMap.release(); // Release the memory in time after the PixelMap is used.
  }).catch((err: BusinessError) => {
    console.error(`Failed to save screenshot. Code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to save screenshot. Code: ${exception.code}, message: ${exception.message}`);
}
```

## screenshot.saveHdrPicture<sup>20+</sup>

saveHdrPicture(options?: HdrScreenshotOptions): Promise&lt;Array&lt;image.PixelMap&gt;&gt;

Obtains a screenshot. This API uses a promise to return the result. SDR stands for Standard Dynamic Range, and HDR stands for High Dynamic Range.
- If the screen contains HDR resources (even if they are partially obscured), this API returns an array with both SDR and HDR PixelMaps, regardless of whether HDR is enabled.
- If there are no HDR resources, it returns an array with a single SDR PixelMap. Unlike the [save](#screenshotsave) API, which returns a single SDR PixelMap, this API always returns an array. Additionally, this API does not support cropping, stretching, or rotating features available in the [save](#screenshotsave) API.

Each **PixelMap** object in the returned object array must be manually released. After using the objects, you must call [release()](../apis-image-kit/arkts-apis-image-PixelMap.md#release7) to release the memory. Otherwise, memory leakage may occur.

**System API**: This is a system API.

**System capability**: SystemCapability.Window.SessionManager

**Required permissions**:
- API versions 22+: **ohos.permission.CAPTURE_SCREEN** or **ohos.permission.CUSTOM_SCREEN_RECORDING**
- API versions 20-21: **ohos.permission.CAPTURE_SCREEN**

**Parameters**

| Name | Type                                   | Mandatory| Description                                                        |
| ------- | --------------------------------------- | ---- | ------------------------------------------------------------ |
| options | [HdrScreenshotOptions](#hdrscreenshotoptions20) | No  | Information about the HDR snapshot. If this parameter is not passed, the default values of the fields are used.|

**Return value**

| Type                         | Description                                           |
| ----------------------------- | ----------------------------------------------- |
| Promise&lt;Array&lt;[image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)&gt;&gt; | Promise used to return an array of PixelMap objects. If the screen contains HDR resources (even if they are partially obscured), the array contains two PixelMaps: the first is an SDR PixelMap, and the second is an HDR PixelMap. If there are no HDR resources, the array contains a single SDR PixelMap.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Display Error Codes](errorcode-display.md).

| ID| Error Message|
| ------- | -------------------------- |
| 201     | Permission verification failed. The application does not have the permission required to call the API. |
| 202     | Permission verification failed. A non-system application calls a system API. |
| 801     | Capability not supported. Failed to call the API due to limited device capabilities. |
| 1400001  | Invalid display or screen. |
| 1400003  | This display manager service works abnormally. |
| 1400004  | Parameter error. Possible cause: 1. Invalid parameter range. |

**Example**

```ts
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
      console.info(`succeeded in saving screenshot ${i}. Pixel bytes number: ${pixelMap.getPixelBytesNumber()}`);
      pixelMap.release();
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to save SDR and HDR screenshot. Code: ${err.code}, message: ${err.message}`);
  });
} catch (exception) {
  console.error(`Failed to save SDR and HDR screenshot. Code: ${exception.code}, message: ${exception.message}`);
}
```
