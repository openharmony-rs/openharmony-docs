# Interface (AVScreenCaptureRecorder)
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @zzs911-->
<!-- md-trans-meta sourceCommit=e333368a624b8bc7050f7aac484dab3786ec6aed translatedAt=2026-09-15T14:49:23.168Z pushedAt=2026-09-18T03:45:03.077Z -->

**AVScreenCaptureRecorder** is a class for screen capture management. It provides APIs for screen capture, such as screen capture initialization, starting, pausing, resuming, or stopping recording, adding watermarks, privacy window exemption, microphone switch control, picker mode selection, and content auto-rotation. It is applicable to scenarios where the screen capture process needs to be controlled within an app, helping you flexibly manage the screen capture lifecycle, protect user privacy, and customize the recording output. Before calling any API in AVScreenCaptureRecorder, you must use [createAVScreenCaptureRecorder()](arkts-apis-media-f.md#mediacreateavscreencapturerecorder12) to create an AVScreenCaptureRecorder instance.

Typical usage process: **createAVScreenCaptureRecorder** → **init** → **startRecording** → **pauseRecording**/**resumeRecording** → **stopRecording** → **release**.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 6. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The initial APIs of this interface are supported since API version 12.


## Modules to Import

``` TypeScript
import { media } from '@kit.MediaKit';
```

## init<sup>12+</sup>

init(config: AVScreenCaptureRecordConfig): Promise\<void>

Initializes screen capture and sets screen capture parameters. This API uses a promise to return the result.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Parameters**

| Name| Type                                                        | Mandatory| Description                    |
| ------ | ------------------------------------------------------------ | ---- | ------------------------ |
| config | [AVScreenCaptureRecordConfig](arkts-apis-media-i.md#avscreencapturerecordconfig12) | Yes | Screen capture parameters. Key configuration items include **fd**, **frameWidth**, and **frameHeight**. For details, see [AVScreenCaptureRecordConfig](arkts-apis-media-i.md#avscreencapturerecordconfig12). You need to create file (usually an MP4 file) first, grant the write permission, and then pass in the file descriptor to this parameter. |

**Return value**

| Type          | Description                               |
| -------------- | ----------------------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Media Error Codes](errorcode-media.md).

| ID| Error Message                                      |
| -------- | ---------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. Return by promise. |
| 5400103  | IO error. Return by promise.                   |
| 5400105  | Service died. Return by promise.               |

**Example**

``` TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';
import { fileIo } from '@kit.CoreFileKit';

async function testInit() {
  // Create a screen capture instance.
  let avScreenCaptureRecorder = await media.createAVScreenCaptureRecorder();

  // Create a file.
  let filesDir = '/data/storage/el2/base/haps';
  let file = fileIo.openSync(filesDir + '/screenCapture.mp4', fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);

  let avCaptureConfig: media.AVScreenCaptureRecordConfig = {
      fd: file.fd, // Before passing in an FD to this parameter, the file (generally an MP4 file) must be created by the caller and granted with the write permissions.
      frameWidth: 640,
      frameHeight: 480
      // Add other parameters.
  };

  // Call the init method.
  if (avScreenCaptureRecorder) {
    avScreenCaptureRecorder.init(avCaptureConfig).then(() => {
      console.info('Succeeded in initializing avScreenCaptureRecorder');
    }).catch((err: BusinessError) => {
      console.error(`Failed to init avScreenCaptureRecorder. Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```

## startRecording<sup>12+</sup>

startRecording(): Promise\<void>

Starts screen recording. Before using this API, you must call [init](#init12). This API uses a promise to return the result.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Return value**

| Type          | Description                            |
| -------------- | -------------------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Media Error Codes](errorcode-media.md).

| ID| Error Message                        |
| -------- | -------------------------------- |
| 5400103  | IO error. Return by promise.     |
| 5400105  | Service died. Return by promise. |

**Example**

``` TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

async function testStartRecording() {
  // Create a screen capture instance.
  let avScreenCaptureRecorder = await media.createAVScreenCaptureRecorder();

  // Other processes

  // Call the startRecording method.
  if (avScreenCaptureRecorder) {
    avScreenCaptureRecorder.startRecording().then(() => {
      console.info('Succeeded in starting avScreenCaptureRecorder');
    }).catch((err: BusinessError) => {
      console.error(`Failed to start avScreenCaptureRecorder. Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```

## stopRecording<sup>12+</sup>

stopRecording(): Promise\<void>

Stops screen recording. This API uses a promise to return the result.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Return value**

| Type          | Description                             |
| -------------- | --------------------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Media Error Codes](errorcode-media.md).

| ID| Error Message                        |
| -------- | -------------------------------- |
| 5400103  | IO error. Return by promise.     |
| 5400105  | Service died. Return by promise. |

**Example**

``` TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

async function testStopRecording() {
  // Create a screen capture instance.
  let avScreenCaptureRecorder = await media.createAVScreenCaptureRecorder();

  // Other processes

  // Call the stopRecording method.
  if (avScreenCaptureRecorder) {
    avScreenCaptureRecorder.stopRecording().then(() => {
      console.info('Succeeded in stopping avScreenCaptureRecorder');
    }).catch((err: BusinessError) => {
      console.error(`Failed to stop avScreenCaptureRecorder. Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```

## pauseRecording

pauseRecording(): Promise\<void>

Pauses screen recording. This API uses a promise to return the result. Call this API to temporarily pause screen recording, for example, when you need to leave temporarily or switch to another app.

Before using this API, call [startRecording](#startrecording12) and ensure that screen recording is in progress.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the Stage model.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Return value**

| Type          | Description                            |
| -------------- | --------------------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Media Error Codes](errorcode-media.md).

| ID| Error Message                       |
| -------- | -------------------------------- |
| 5400102  | Operation not allowed. Return by promise. |
| 5400103  | IO error. Return by promise.     |
| 5400105  | Service died. Return by promise. |

**Example**

``` TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

async function testPauseRecording() {
  // Create a screen capture instance.
  let avScreenCaptureRecorder = await media.createAVScreenCaptureRecorder();

  // Other processes

  // Call the pauseRecording method.
  if (avScreenCaptureRecorder) {
    avScreenCaptureRecorder.pauseRecording().then(() => {
      console.info('Succeeded in pausing avScreenCaptureRecorder');
    }).catch((err: BusinessError) => {
      console.error(`Failed to pause avScreenCaptureRecorder. Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```

## resumeRecording

resumeRecording(): Promise\<void>

Resumes screen recording. This API uses a promise to return the result.

Before using this API, call [pauseRecording](arkts-apis-media-AVScreenCaptureRecorder.md#pauserecording) and ensure that screen recording is paused.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the Stage model.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Return value**

| Type         | Description                            |
| -------------- | --------------------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Media Error Codes](errorcode-media.md).

| ID| Error Message                       |
| -------- | -------------------------------- |
| 5400102  | Operation not allowed. Return by promise. |
| 5400103  | IO error. Return by promise.     |
| 5400105  | Service died. Return by promise. |

**Example**

``` TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

async function testResumeRecording() {
  // Create a screen capture instance.
  let avScreenCaptureRecorder = await media.createAVScreenCaptureRecorder();

  // Other processes

  // Call the resumeRecording method.
  if (avScreenCaptureRecorder) {
    avScreenCaptureRecorder.resumeRecording().then(() => {
      console.info('Succeeded in resuming avScreenCaptureRecorder');
    }).catch((err: BusinessError) => {
      console.error(`Failed to resume avScreenCaptureRecorder. Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```

## addWatermark

addWatermark(watermark: image.PixelMap, config: WatermarkConfiguration): Promise\<number>

Adds a custom watermark image during video recording. This API uses a promise to return the result.

> **NOTE**
>
> - A maximum of five watermarks can be added to an app.
>
> - The **addWatermark** API must be called before the [startRecording](#startrecording12) API.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the Stage model.

**System capability:** SystemCapability.Multimedia.Media.AVScreenCapture

**Parameters**

| Name | Type                                   | Mandatory | Description                       |
| ------ | -------------------------------------- | ---- | -------------------------- |
| watermark | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)  | Yes   | Watermark image. The **PixelMap** object cannot be null. Opacity settings are supported. For details about the image format and dimensions, see [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md). |
| config | [WatermarkConfiguration](arkts-apis-media-i.md#watermarkconfiguration) | Yes   | Parameters for configuring the watermark of video recording. For details about the value range of each field, see the definition of **WatermarkConfiguration**. This parameter must be set before the **startRecording** API is called. |

**Return value**

| Type           | Description                                       |
| -------------- | ------------------------------------------ |
| Promise\<number> | Promise used to return the ID of the added watermark. If the watermark is added successfully, the ID is returned. If the operation fails, an error code is returned. |

**Error codes**

For details about the error codes, see [Media Error Codes](errorcode-media.md).

| ID | Error Message                               |
| -------- | -------------------------------------- |
| 5400102  | Operation not allowed. Return by promise.  |
| 5400103  | IO error. Return by promise.    |
| 5400105  | Service died. Return by promise. |
| 5400108  | The parameter check failed, parameter value out of range.     |

**Example**

``` TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';
import { media } from '@kit.MediaKit';

async function testAddWaterMark() {
  // Create a screen capture instance.
  let avScreenCaptureRecorder = await media.createAVScreenCaptureRecorder();

  // Other processes

  let watermark: image.PixelMap | undefined = undefined; // You can obtain a local resource file and convert it to a PixelMap. The watermark image cannot be empty.
  let watermarkConfig: media.WatermarkConfiguration = { top: 100, left: 100, width: 100, height: 100 };

  if (watermark && avScreenCaptureRecorder) {
    avScreenCaptureRecorder.addWatermark(watermark, watermarkConfig).then((num: number) => {
      console.info(`Succeeded in adding watermark, watermarkNum is ${num}`);
    })
    .catch((error: BusinessError) => {
      console.error(`Failed to add watermark and catch error is: Code: ${error.code}, message: ${error.message}`);
    });
  }
}
```

## skipPrivacyMode<sup>12+</sup>

skipPrivacyMode(windowIDs: Array\<number>): Promise\<void>

During screen capture, the application can grant a security exemption for its own privacy window. This API uses a promise to return the result.

For example, if a user enters a password in this application during screen capture, the application will not display a black screen.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Parameters**

| Name| Type   | Mandatory| Description                                                     |
| ------ | ------- | ---- | --------------------------------------------------------- |
| windowIDs | Array\<number> | Yes  | IDs of windows that require privacy exemption, including the main window ID and subwindow ID. For details about how to obtain window attributes, see [getWindowProperties](../apis-arkui/arkts-apis-window-Window.md#getwindowproperties9).|

**Return value**

| Type          | Description                            |
| -------------- | -------------------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Media Error Codes](errorcode-media.md).

| ID| Error Message                        |
| -------- | -------------------------------- |
| 5400103  | IO error. Return by promise.     |
| 5400105  | Service died. Return by promise. |

**Example**

``` TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

async function testSkipPrivacyMode() {
  // Create a screen capture instance.
  let avScreenCaptureRecorder = await media.createAVScreenCaptureRecorder();

  // Other processes

  // Call the skipPrivacyMode method.
  if (avScreenCaptureRecorder) {
    let windowIDs = [];
    avScreenCaptureRecorder.skipPrivacyMode(windowIDs).then(() => {
      console.info('Succeeded in skipping privacy mode');
    }).catch((err: BusinessError) => {
      console.error(`Failed to skip privacy mode. Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```

## setMicEnabled<sup>12+</sup>

setMicEnabled(enable: boolean): Promise\<void>

Enables or disables the microphone. This API uses a promise to return the result.

> **NOTE**
>
> - Call this API when you need to record or mute the microphone audio, for example, when you need to temporarily disable the microphone or re-enable the microphone for recording.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Parameters**

| Name| Type   | Mandatory| Description                                                     |
| ------ | ------- | ---- | --------------------------------------------------------- |
| enable | boolean | Yes  | Whether to enable the microphone. **true** to enable, **false** otherwise.|

**Return value**

| Type          | Description                                   |
| -------------- | --------------------------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Media Error Codes](errorcode-media.md).

| ID| Error Message                        |
| -------- | -------------------------------- |
| 5400103  | IO error. Return by promise.     |
| 5400105  | Service died. Return by promise. |

**Example**

``` TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

async function testSetMicEnable() {
  // Create a screen capture instance.
  let avScreenCaptureRecorder = await media.createAVScreenCaptureRecorder();

  // Other processes

  // Call the setMicEnabled method.
  if (avScreenCaptureRecorder) {
    avScreenCaptureRecorder.setMicEnabled(true).then(() => {
      console.info('Succeeded in setting microphone enabled.');
    }).catch((err: BusinessError) => {
      console.error(`Failed to set microphone enabled. Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```

## setPickerMode<sup>22+</sup>

setPickerMode(pickerMode: PickerMode): Promise\<void>

Sets the display mode of the picker. The setting takes effect the next time the picker is displayed. This API uses a promise to return the result.

You can select a mode based on the recording requirements.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Parameters**

| Name| Type   | Mandatory| Description                                                     |
| ------ | ------- | ---- | --------------------------------------------------------- |
| pickerMode | [PickerMode](arkts-apis-media-e.md#pickermode22) | Yes | Picker mode. |

**Return value**

| Type          | Description                                   |
| -------------- | --------------------------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Media Error Codes](errorcode-media.md).

| ID| Error Message                        |
| -------- | -------------------------------- |
| 5400102  | Operation not allowed. Return by promise. |
| 5400103  | IO error. Return by promise.     |
| 5400105  | Service died. Return by promise. |

**Example**

``` TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

async function testSetPickerMode() {
  // Create a screen capture instance.
  let avScreenCaptureRecorder = await media.createAVScreenCaptureRecorder();

  // Other processes

  // Call the setPickerMode method.
  if (avScreenCaptureRecorder) {
    avScreenCaptureRecorder.setPickerMode(media.PickerMode.WINDOW_ONLY).then(() => {
      console.info('Succeeded in setting picker mode.');
    }).catch((err: BusinessError) => {
      console.error(`Failed to set picker mode. Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```

## excludePickerWindows<sup>22+</sup>

excludePickerWindows(excludedWindows: Array\<number>): Promise\<void>

Sets the list of windows to be hidden in the picker. The setting takes effect the next time the picker is displayed. This API uses a promise to return the result.

Call this API when you need to hide specific windows from users, such as the app window, privacy window, or irrelevant background window.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Parameters**

| Name| Type   | Mandatory| Description                                                     |
| ------ | ------- | ---- | --------------------------------------------------------- |
| excludedWindows | Array\<number> | Yes  | List of windows to be hidden in the picker. For details about how to obtain window attributes, see [getWindowProperties](../apis-arkui/arkts-apis-window-Window.md#getwindowproperties9).|

**Return value**

| Type          | Description                                   |
| -------------- | --------------------------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Media Error Codes](errorcode-media.md).

| ID| Error Message                        |
| -------- | -------------------------------- |
| 5400102  | Operation not allowed. Return by promise. |
| 5400103  | IO error. Return by promise.     |
| 5400105  | Service died. Return by promise. |

**Example**

``` TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

async function testExcludePickerWindows() {
  let excludedWindows: number[] = [101, 102, 103];

  // Create a screen capture instance.
  let avScreenCaptureRecorder = await media.createAVScreenCaptureRecorder();

  // Other processes

  // Call the excludePickerWindows method.
  if (avScreenCaptureRecorder) {
    avScreenCaptureRecorder.excludePickerWindows(excludedWindows).then(() => {
      console.info('Succeeded in excluding picker windows.');
    }).catch((err: BusinessError) => {
      console.error(`Failed to exclude picker windows. Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```

## presentPicker<sup>22+</sup>

presentPicker(): Promise\<void>

Displays the Picker once more after the screen capture starts, allowing for dynamic updates to the recording source, such as changing the window or screen being recorded. This API uses a promise to return the result.

This API must be called after [startRecording](#startrecording12).

> **NOTE**
>
> - The ongoing capture process remains uninterrupted while updating the recording source.
> - Following the dynamic update of the recording source through the Picker, the capture proceeds with the newly selected source.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Return value**

| Type          | Description                             |
| -------------- | --------------------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Media Error Codes](errorcode-media.md).

| ID| Error Message                        |
| -------- | -------------------------------- |
| 5400102  | Operation not allowed. Return by promise. |
| 5400103  | IO error. Return by promise.     |
| 5400105  | Service died. Return by promise. |

**Example**

``` TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

async function testPresentPicker() {
  // Create a screen capture instance.
  let avScreenCaptureRecorder = await media.createAVScreenCaptureRecorder();

  // Other processes

  // Call the presentPicker method.
  if (avScreenCaptureRecorder) {
    avScreenCaptureRecorder.presentPicker().then(() => {
      console.info('Succeeded in presenting picker avScreenCaptureRecorder.');
    }).catch((err: BusinessError) => {
      console.error(`Failed to present picker avScreenCaptureRecorder. Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```
## setContentAutoRotation

setContentAutoRotation(enable: boolean): Promise\<void>

Sets whether to enable auto-rotation for the captured screen content to keep the image upright. This API uses a promise to return the result.

> **NOTE**
>
> This API must be called before [startRecording](#startrecording12).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.AVScreenCapture

**Parameters**

| Name | Type                                   | Mandatory | Description                       |
| ------ | -------------------------------------- | ---- | -------------------------- |
| enable | boolean | Yes | Whether to enable auto-rotation. The default value is **false**. **true**: enables auto-rotation. The image content in the output frame will automatically remain upright. **false**: disables auto-rotation. The image content in the output frame will not automatically remain upright. |

**Return value**

| Type           | Description                                       |
| -------------- | ------------------------------------------ |
| Promise\<void> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Media Error Codes](errorcode-media.md).

| ID | Error Message                               |
| -------- | -------------------------------------- |
| 5400102  | Operation not allowed. Return by promise.    |
| 5400105  | Service died. Return by promise. |

**Example**

``` TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

async function testSetContentAutoRotation() {
  // Create the screen capture instance.
  let avScreenCaptureRecorder = await media.createAVScreenCaptureRecorder();

  // Other processes

  // Call the setContentAutoRotation method.
  if (avScreenCaptureRecorder) {
    avScreenCaptureRecorder.setContentAutoRotation(true).then(() => {
      console.info('Succeeded in enabling setContentAutoRotation.');
    }).catch((err: BusinessError) => {
      console.error(`Failed to enable setContentAutoRotation. Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```

## release<sup>12+</sup>

release(): Promise\<void>

Releases this AVScreenCaptureRecorder instance. This API uses a promise to return the result.

Call this API to release resources when the screen capture function is no longer used, for example, when the app exits or the screen recording module is uninstalled.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Return value**

| Type          | Description                             |
| -------------- | --------------------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Media Error Codes](errorcode-media.md).

| ID| Error Message                        |
| -------- | -------------------------------- |
| 5400103  | IO error. Return by promise.     |
| 5400105  | Service died. Return by promise. |

**Example**

``` TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

async function testRelease() {
  // Create a screen capture instance.
  let avScreenCaptureRecorder = await media.createAVScreenCaptureRecorder();

  // Other processes

  // Call the release method.
  if (avScreenCaptureRecorder) {
    avScreenCaptureRecorder.release().then(() => {
      console.info('Succeeded in releasing avScreenCaptureRecorder');
    }).catch((err: BusinessError) => {
      console.error(`Failed to release avScreenCaptureRecorder. Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```

## on('stateChange')<sup>12+</sup>

on(type: 'stateChange', callback: Callback\<AVScreenCaptureStateCode>): void

Subscribes to screen capture state changes. An application can subscribe to only one screen capture state change event. When the application initiates multiple subscriptions to this event, the last subscription is applied.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Parameters**

| Name  | Type    | Mandatory| Description                                                        |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | Yes  | Event type, which is **'stateChange'** in this case.           |
| callback | Callback\<[AVScreenCaptureStateCode](arkts-apis-media-e.md#avscreencapturestatecode12)> | Yes  | Callback invoked when the event is triggered. [AVScreenCaptureStateCode](arkts-apis-media-e.md#avscreencapturestatecode12) indicates the new state.|

**Example**

``` TypeScript
import { media } from '@kit.MediaKit';

async function testOnStateChange() {
  // Create a screen capture instance.
  let avScreenCaptureRecorder = await media.createAVScreenCaptureRecorder();

  // Other processes

  // Call the on method.
  if (avScreenCaptureRecorder) {
    avScreenCaptureRecorder.on('stateChange', (state: media.AVScreenCaptureStateCode) => {
        console.info('avScreenCaptureRecorder stateChange to ' + state);
    });
  }
}
```

## on('error')<sup>12+</sup>

on(type: 'error', callback: ErrorCallback): void

Subscribes to **AVScreenCaptureRecorder** errors. You can handle the errors based on the application logic. An application can subscribe to only one AVScreenCaptureRecorder error event. When the application initiates multiple subscriptions to this event, the last subscription is applied.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Parameters**

| Name  | Type         | Mandatory| Description                                   |
| -------- | ------------- | ---- | --------------------------------------- |
| type     | string        | Yes  | Error event callback type. Supported event: 'error'.|
| callback | [ErrorCallback](../apis-basic-services-kit/js-apis-base.md#errorcallback) | Yes  | Callback for screen capture error events.                 |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Media Error Codes](errorcode-media.md).

| ID| Error Message                        |
| -------- | -------------------------------- |
| 201      | permission denied.     |
| 5400103  | IO error. Return by ErrorCallback. |
| 5400105  | Service died. Return by ErrorCallback. |

**Example**

``` TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

async function testOnError() {
  // Create a screen capture instance.
  let avScreenCaptureRecorder = await media.createAVScreenCaptureRecorder();

  // Other processes

  // Call the on method.
  if (avScreenCaptureRecorder) {
    avScreenCaptureRecorder.on('error', (err: BusinessError) => {
      console.error(`avScreenCaptureRecorder error: Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```

## off('stateChange')<sup>12+</sup>

 off(type: 'stateChange', callback?: Callback\<AVScreenCaptureStateCode>): void

Unsubscribes from state change callback events. You can specify a state change callback to unsubscribe.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Parameters**

| Name  | Type    | Mandatory| Description                                                        |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | Yes  | Event type, which is **'stateChange'** in this case.           |
| callback | Callback\<[AVScreenCaptureStateCode](arkts-apis-media-e.md#avscreencapturestatecode12)> | No  | Callback for the state change event. [AVScreenCaptureStateCode](arkts-apis-media-e.md#avscreencapturestatecode12) indicates the new state. If this parameter is not specified, the last subscription is canceled.|

**Example**

``` TypeScript
import { media } from '@kit.MediaKit';

async function testOffStateChange() {
  // Create a screen capture instance.
  let avScreenCaptureRecorder = await media.createAVScreenCaptureRecorder();

  // Other processes

  // Call the off method.
  if (avScreenCaptureRecorder) {
    avScreenCaptureRecorder.off('stateChange');
  }
}
```

## off('error')<sup>12+</sup>

off(type: 'error', callback?: ErrorCallback): void

Unsubscribes from error callback events. You can specify an error callback to cancel the subscription.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Parameters**

| Name  | Type    | Mandatory| Description                                                      |
| -------- | -------- | ---- | ---------------------------------------------------------- |
| type     | string   | Yes   | Event type, which is **'error'** in this case.                |
| callback | [ErrorCallback](../apis-basic-services-kit/js-apis-base.md#errorcallback) | No  | Callback used for unsubscription. If this parameter is not specified, the last subscription is canceled.|

**Example**

``` TypeScript
import { media } from '@kit.MediaKit';

async function testOffError() {
  // Create a screen capture instance.
  let avScreenCaptureRecorder = await media.createAVScreenCaptureRecorder();

  // Other processes

  // Call the off method.
  if (avScreenCaptureRecorder) {
    avScreenCaptureRecorder.off('error');
  }
}
```