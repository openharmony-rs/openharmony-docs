# Interface (AVRecorder)
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_dyOv3Sds-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @zzs911-->


The **AVRecorder** class is used to manage the entire audio and video recording process, including audio recording, video recording, and audio-video recording. It can be used to flexibly configure encoding parameters, add watermarks, set metadata, and listen for the recording status and error events. It can be used to record audio and video and saved them to files, including scenarios where recording continuity needs to be maintained when the audio is interrupted and audio amplitude needs to be monitored in real time. Before calling the methods of the AVRecorder class, you need to call the [createAVRecorder](arkts-apis-media-f.md#mediacreateavrecorder9) API to create an **AVRecorder** instance. Typical recording process: [createAVRecorder](arkts-apis-media-f.md#mediacreateavrecorder9) → [prepare](#prepare9) → [getInputSurface](#getinputsurface9) (for video-only or audio and video recording) → [start](#start9) → [pause](#pause9)/[resume](#resume9) → [stop](#stop9) → [release](#release9).

For details about the audio and video recording demo, see [Audio Recording](../../media/media/using-avrecorder-for-recording.md) and [Video Recording](../../media/media/video-recording.md).

> **NOTE**
>
> - The initial APIs of this module are supported since API version 6. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The initial APIs of this interface are supported since API version 9.
> - The camera module is required for video recording. For details about how to use the camera module API, see [Camera Management](../apis-camera-kit/arkts-apis-camera.md).

## Modules to Import

```ts
import { media } from '@kit.MediaKit';
```

## Properties

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

| Name   | Type                                | Read-Only| Optional| Description              |
| ------- | ------------------------------------ | ---- | ---- | ------------------ |
| state<sup>9+</sup> | [AVRecorderState](arkts-apis-media-t.md#avrecorderstate9) | Yes  | No  | AVRecorder state.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|

## prepare<sup>9+</sup>

prepare(config: AVRecorderConfig, callback: AsyncCallback\<void>): void

Prepares for recording. This method can be used to set audio and video recording parameters and initializes the recording context. This API uses an asynchronous callback to return the result.

This API must be called before [start](#start9). After this API is successfully called, the recording enters the prepared state. For audio-only recording, you can directly call [start](#start9) to start recording. For video-only or audio and video recording, you need to call [getInputSurface](#getinputsurface9) to obtain the surface and then call [start](#start9) to start recording.

**Required permissions:** ohos.permission.MICROPHONE

This permission is a user-granted permission. You need to call [requestPermissionsFromUser()](../apis-ability-kit/js-apis-abilityAccessCtrl.md#requestpermissionsfromuser9) to request the permission from the user. If audio recording is not involved, the **ohos.permission.MICROPHONE** permission is not required.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Parameters**

| Name  | Type                                  | Mandatory| Description                                 |
| -------- | -------------------------------------- | ---- | ------------------------------------- |
| config   | [AVRecorderConfig](arkts-apis-media-i.md#avrecorderconfig9) | Yes  | Audio and video recording parameters to set. You need to set **audioSourceType** for audio recording and **videoSourceType** for video recording.|
| callback | AsyncCallback\<void>                   | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Media Error Codes](errorcode-media.md).

| ID| Error Message                               |
| -------- | --------------------------------------- |
| 201      | Permission denied. Return by callback.  |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.    |
| 5400102  | Operation not allowed. Return by callback. |
| 5400105  | Service died. Return by callback.       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// Configure the parameters based on those supported by the hardware device.
let avRecorderProfile: media.AVRecorderProfile = {
  audioBitrate : 48000,
  audioChannels : 2,
  audioCodec : media.CodecMimeType.AUDIO_AAC,
  audioSampleRate : 48000,
  fileFormat : media.ContainerFormatType.CFT_MPEG_4,
  videoBitrate : 2000000,
  videoCodec : media.CodecMimeType.VIDEO_AVC,
  videoFrameWidth : 640,
  videoFrameHeight : 480,
  videoFrameRate : 30
};
let videoMetaData: media.AVMetadata = {
  videoOrientation: '0' // The value can be 0, 90, 180, or 270. If any other value is used, prepare() reports an error.
};
let avRecorderConfig: media.AVRecorderConfig = {
  audioSourceType : media.AudioSourceType.AUDIO_SOURCE_TYPE_MIC,
  videoSourceType : media.VideoSourceType.VIDEO_SOURCE_TYPE_SURFACE_YUV,
  profile : avRecorderProfile,
  url: 'fd://', // Open the file using fs.open(@kit.FileKit) to obtain the file descriptor (FD), assign read and write permissions, and pass the FD to this parameter. For details, see the file management development guideline.
  metadata: videoMetaData,
  location : { latitude : 30, longitude : 130 }
};

avRecorder.prepare(avRecorderConfig, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to prepare and error is: Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in preparing');
  }
});
```

## prepare<sup>9+</sup>

prepare(config: AVRecorderConfig): Promise\<void>

Prepares for recording. This method can be used to set audio and video recording parameters and initializes the recording context. This API uses a promise to return the result.

This API must be called before [start](#start9-1). After this API is successfully called, the recording enters the prepared state. For audio-only recording, you can directly call [start](#start9-1) to start recording. For video-only or audio and video recording, you need to call [getInputSurface](#getinputsurface9-1) to obtain the surface and then call [start](#start9-1) to start recording.

**Required permissions:** ohos.permission.MICROPHONE

This permission is a user-granted permission. You need to call [requestPermissionsFromUser()](../apis-ability-kit/js-apis-abilityAccessCtrl.md#requestpermissionsfromuser9) to request the permission from the user. If audio recording is not involved, the **ohos.permission.MICROPHONE** permission is not required.


**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Parameters**

| Name| Type                                  | Mandatory| Description                      |
| ------ | -------------------------------------- | ---- | -------------------------- |
| config | [AVRecorderConfig](arkts-apis-media-i.md#avrecorderconfig9) | Yes  | Audio and video recording parameters to set. You need to set **audioSourceType** for audio recording and **videoSourceType** for video recording.|

**Return value**

| Type          | Description                                      |
| -------------- | ------------------------------------------ |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Media Error Codes](errorcode-media.md).

| ID| Error Message                              |
| -------- | -------------------------------------- |
| 201      | Permission denied. Return by promise.  |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.    |
| 5400102  | Operation not allowed. Return by promise. |
| 5400105  | Service died. Return by promise.       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// Configure the parameters based on those supported by the hardware device.
let avRecorderProfile: media.AVRecorderProfile = {
  audioBitrate : 48000,
  audioChannels : 2,
  audioCodec : media.CodecMimeType.AUDIO_AAC,
  audioSampleRate : 48000,
  fileFormat : media.ContainerFormatType.CFT_MPEG_4,
  videoBitrate : 2000000,
  videoCodec : media.CodecMimeType.VIDEO_AVC,
  videoFrameWidth : 640,
  videoFrameHeight : 480,
  videoFrameRate : 30
};
let videoMetaData: media.AVMetadata = {
  videoOrientation: '0' // The value can be 0, 90, 180, or 270. If any other value is used, prepare() reports an error.
};
let avRecorderConfig: media.AVRecorderConfig = {
  audioSourceType : media.AudioSourceType.AUDIO_SOURCE_TYPE_MIC,
  videoSourceType : media.VideoSourceType.VIDEO_SOURCE_TYPE_SURFACE_YUV,
  profile : avRecorderProfile,
  url: 'fd://', // Open the file using the fileIo.open API of Core File Kit to obtain the file descriptor (FD), assign read and write permissions, and pass the FD to this parameter.
  metadata : videoMetaData,
  location : { latitude : 30, longitude : 130 }
};

avRecorder.prepare(avRecorderConfig).then(() => {
  console.info('Succeeded in preparing');
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to prepare and error is: Code: ${error.code}, message: ${error.message}`);
});
```

## addWatermark

addWatermark(watermark: image.PixelMap, config: WatermarkConfiguration): Promise\<number>

Adds a custom watermark to a video. This method is applicable to scenarios where watermarks such as brand logos, copyright information, or timestamps need to be embedded into videos. This API uses a promise to return the result.

> **NOTE**
>
> - A maximum of five watermarks can be added to an application.
>
> - This API must be called before [prepare](#prepare9).

**Since**: 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Parameters**

| Name| Type                                  | Mandatory| Description                      |
| ------ | -------------------------------------- | ---- | -------------------------- |
| watermark | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)  | Yes  | Watermark image. The image will be overlaid as a watermark on the video.|
| config | [WatermarkConfiguration](arkts-apis-media-i.md#watermarkconfiguration) | Yes  | Parameters for configuring the watermark of video recording.|

**Return value**

| Type          | Description                                      |
| -------------- | ------------------------------------------ |
| Promise\<number>| Promise used to return the ID of the added watermark. The value range is [1, 5].|

**Error codes**

For details about the error codes, see [Media Error Codes](errorcode-media.md).

| ID| Error Message                              |
| -------- | -------------------------------------- |
| 5400102  | Operation not allowed. Return by promise.  |
| 5400103  | IO error. Return by promise.    |
| 5400105  | Service died. Return by promise. |
| 5400108  | The parameter check failed, parameter value out of range.     |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';
import { media } from '@kit.MediaKit';

let watermark: image.PixelMap | undefined = undefined; // Create an ImageSource object using image.createImageSource and call the createPixelMap API of the Image Kit to obtain a pixel map. The watermark image cannot be empty.
let watermarkConfig: media.WatermarkConfiguration = { top: 100, left: 100, width: 100, height: 100 };

if (watermark) {
    avRecorder.addWatermark(watermark, watermarkConfig).then((num: number) => {
      console.info(`Succeeded in adding watermark, watermarkNum is ${num}`);
    })
    .catch((error: BusinessError) => {
      console.error(`Failed to add watermark and catch error is: Code: ${error.code}, message: ${error.message}`);
    });
}
```

## getInputSurface<sup>9+</sup>

getInputSurface(callback: AsyncCallback\<string>): void

Obtains the surface required for recording. This method is applicable to scenarios where a surface is required to transfer video data during video-only or audio-video recording. The camera module is required for video recording. For details about how to use the camera module API, see [Camera Management](../apis-camera-kit/arkts-apis-camera.md). This API uses an asynchronous callback to return the result.

The caller obtains the surface buffer from this surface and fills in data of the video to be recorded.

The video data must contain the timestamp (in ns) and buffer size. The start time of the timestamp must be based on the system startup time.

This API must be called between [prepare](#prepare9) and [start](#start9).

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Parameters**

| Name  | Type                  | Mandatory| Description                       |
| -------- | ---------------------- | ---- | --------------------------- |
| callback | AsyncCallback\<string> | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the surface ID obtained; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Media Error Codes](errorcode-media.md).

| ID| Error Message                               |
| -------- | --------------------------------------- |
| 5400102  | Operation not allowed. Return by callback. |
| 5400103  | IO error. Return by callback.           |
| 5400105  | Service died. Return by callback.       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let inputSurfaceId: string; // The inputSurfaceId is transferred to the camera API to create a videoOutput instance.

avRecorder.getInputSurface((err: BusinessError, surfaceId: string) => {
  if (err) {
    console.error(`Failed to do getInputSurface and error is: Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in doing getInputSurface');
    inputSurfaceId = surfaceId;
  }
});

```

## getInputSurface<sup>9+</sup>

getInputSurface(): Promise\<string>

Obtains the surface required for recording. This method is applicable to scenarios where a surface is required to transfer video data during video-only or audio-video recording. The camera module is required for video recording. For details about how to use the camera module API, see [Camera Management](../apis-camera-kit/arkts-apis-camera.md). This API uses a promise to return the result.

The caller obtains the surface buffer from this surface and fills in data of the video to be recorded. The video data to be filled must contain the timestamp (in ns) and buffer size. The start time of the timestamp must be based on the system startup time.

This API must be called between [prepare](#prepare9-1) and [start](#start9-1).

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Return value**

| Type            | Description                            |
| ---------------- | -------------------------------- |
| Promise\<string> | Promise used to return the obtained surface ID.|

**Error codes**

For details about the error codes, see [Media Error Codes](errorcode-media.md).

| ID| Error Message                              |
| -------- | -------------------------------------- |
| 5400102  | Operation not allowed. Return by promise. |
| 5400103  | IO error. Return by promise.           |
| 5400105  | Service died. Return by promise.       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let inputSurfaceId: string; // The inputSurfaceId is transferred to the camera API to create a videoOutput instance.

avRecorder.getInputSurface().then((surfaceId: string) => {
  console.info('Succeeded in getting InputSurface');
  inputSurfaceId = surfaceId;
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to get InputSurface and error is: Code: ${error.code}, message: ${error.message}`);
});
```

## updateRotation<sup>12+</sup>

updateRotation(rotation: number): Promise\<void>

Updates the video rotation angle. This API applies to scenarios where the rotation angle of the video to record needs to be dynamically adjusted when the device orientation changes (for example, switching between landscape and portrait modes). This API uses a promise to return the result.

This API must be called between [prepare](#prepare9-1) and [start](#start9-1).

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Parameters**

| Name  | Type                | Mandatory| Description                       |
| -------- | -------------------- | ---- | --------------------------- |
| rotation | number | Yes  | Angle to rotate, in degrees (°), which can only be **0**, **90**, **180**, or **270**. If an invalid value is passed, error code 401 is returned.|

**Return value**

| Type            | Description                            |
| ---------------- | -------------------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Media Error Codes](errorcode-media.md).

| ID| Error Message                              |
| -------- | -------------------------------------- |
|   401    | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.   |
| 5400102  | Operation not allowed. Return by promise. |
| 5400103  | IO error. Return by promise.           |
| 5400105  | Service died. Return by promise.       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let rotation = 90;

avRecorder.updateRotation(rotation).then(() => {
  console.info('Succeeded in doing updateRotation');
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to do updateRotation and error is: Code: ${error.code}, message: ${error.message}`);
});
```

## setMetadata

setMetadata(metadata: Record&lt;string, string&gt;): void

Sets the metadata information to record. This method is applicable to scenarios where you need to embed custom metadata (such as the author, title, and tags) into recorded files. If the **metadata** parameter contains the same key as **config.metadata.customInfo** (refer to [prepare()](#prepare9-1) and [AVRecorderConfig](arkts-apis-media-i.md#avrecorderconfig9)), the value of the former will overwrite that of the latter.

This API must be called after [prepare()](#prepare9-1) and before [stop()](#stop9-1).

**Since**: 26.0.0

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Parameters**

| Name    | Type            | Mandatory  | Description                                                     |
| ---------- |---------------- | ------ |---------------------------------------------------------|
| metadata | Record&lt;string, string&gt; | Yes | Metadata information to record.<br>The value is a string key-value pair. The key must start with **com.openharmony**. If not, the key-value pair will be ignored. The value can contain 0 to 256 bytes. If the value is out of range, error code 5400108 is returned.|

**Error codes**

For details about the error codes, see [Media Error Codes](errorcode-media.md).

| ID| Error Message                              |
| -------- | -------------------------------------- |
| 5400101  | No memory. |
| 5400102  | Operation not allowed. |
| 5400108  | Parameter check failed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let metadata: Record<string, string> = {
  'com.openharmony.userdefine': '10',
  'com.openharmony.userdefine2': '20'
};

try {
  avRecorder.setMetadata(metadata);
  console.info('set metadata successfully');
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to set metadata. Code: ${error.code}, message: ${error.message}`);
}
```

## setWillMuteWhenInterrupted<sup>20+</sup>

setWillMuteWhenInterrupted(muteWhenInterrupted: boolean): Promise&lt;void&gt;

Sets whether to mute the current audio recording stream when an audio interruption occurs. After this function is enabled, the recording will be muted instead of being stopped when the audio recording stream is interrupted by an audio stream with a higher priority. This function is applicable to scenarios where recording continuity needs to be maintained during interruptions, such as conference recording and voice notes. If this function is disabled, the default interruption mode is used, that is, recording stops when the audio stream is interrupted. This API uses a promise to return the result.

This API must be called before [prepare()](#prepare9-1).

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Parameters**

| Name    | Type            | Mandatory  | Description                                                     |
| ---------- |---------------- | ------ |---------------------------------------------------------|
| muteWhenInterrupted | boolean | Yes | Sets whether to mute the current audio recording stream when an audio interruption occurs. The value **true** indicates that the function is enabled, and the recording is muted when the audio stream is interrupted. The value **false** indicates that the function is disabled, and the recording stops when the audio stream is interrupted.|

**Return value**

| Type               | Description                         |
| ------------------- | ----------------------------- |
| Promise&lt;void&gt;| Promise that returns no value.|

**Error codes**

For details about the error codes, see [Media Error Codes](errorcode-media.md).

| ID| Error Message                              |
| -------- | -------------------------------------- |
| 5400102  | Operation not allowed. Return by promise. |
| 5400105  | Service died. Return by promise.       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.setWillMuteWhenInterrupted(true).then(() => {
  console.info('Succeeded in doing setWillMuteWhenInterrupted');
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to do setWillMuteWhenInterrupted and error is: Code: ${error.code}, message: ${error.message}`);
});
```

## start<sup>9+</sup>

start(callback: AsyncCallback\<void>): void

Starts recording. This API uses an asynchronous callback to return the result.

This API must be called after [prepare](#prepare9). After this API is successfully called, the AVRecorder enters the started state. For video recording, this API can be called only after the [getInputSurface](#getinputsurface9) API is successfully called.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Parameters**

| Name  | Type                | Mandatory| Description                        |
| -------- | -------------------- | ---- | ---------------------------- |
| callback | AsyncCallback\<void> | Yes  |Callback used to return the result. If the recording starts successfully, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Media Error Codes](errorcode-media.md).

| ID| Error Message                               |
| -------- | --------------------------------------- |
| 5400102  | Operation not allowed. Return by callback. |
| 5400103  | IO error. Return by callback.           |
| 5400105  | Service died. Return by callback.       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.start((err: BusinessError) => {
  if (err) {
    console.error(`Failed to start AVRecorder and error is: Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in starting AVRecorder');
  }
});
```

## start<sup>9+</sup>

start(): Promise\<void>

Starts recording. This API uses a promise to return the result.

This API must be called after [prepare](#prepare9-1). After this API is successfully called, the AVRecorder enters the started state. For video recording, this API can be called only after the [getInputSurface](#getinputsurface9-1) API is successfully called.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Return value**

| Type          | Description                                 |
| -------------- | ------------------------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Media Error Codes](errorcode-media.md).

| ID| Error Message                              |
| -------- | -------------------------------------- |
| 5400102  | Operation not allowed. Return by promise. |
| 5400103  | IO error. Return by promise.           |
| 5400105  | Service died. Return by promise.       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.start().then(() => {
  console.info('Succeeded in starting AVRecorder');
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to start AVRecorder and error is: Code: ${error.code}, message: ${error.message}`);
});
```

## pause<sup>9+</sup>

pause(callback: AsyncCallback\<void>): void

Pauses recording. This API uses an asynchronous callback to return the result.

This API must be called after [start](#start9). After this API is successfully called, the AVRecorder enters the paused state. You can then call [resume](#resume9) to resume recording.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Parameters**

| Name  | Type                | Mandatory| Description                       |
| -------- | -------------------- | ---- | --------------------------- |
| callback | AsyncCallback\<void> | Yes  | Callback used to return the result. If the recording is paused successfully, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Media Error Codes](errorcode-media.md).

| ID| Error Message                               |
| -------- | --------------------------------------- |
| 5400102  | Operation not allowed. Return by callback. |
| 5400103  | IO error. Return by callback.           |
| 5400105  | Service died. Return by callback.       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.pause((err: BusinessError) => {
  if (err) {
    console.error(`Failed to pause AVRecorder and error is: Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in pausing');
  }
});
```

## pause<sup>9+</sup>

pause(): Promise\<void>

Pauses recording. This API uses a promise to return the result.

This API must be called after [start](#start9-1). After this API is successfully called, the AVRecorder enters the paused state. You can then call resume](#resume9-1) to resume recording.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Return value**

| Type          | Description                                 |
| -------------- | ------------------------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Media Error Codes](errorcode-media.md).

| ID| Error Message                              |
| -------- | -------------------------------------- |
| 5400102  | Operation not allowed. Return by promise. |
| 5400103  | IO error. Return by promise.           |
| 5400105  | Service died. Return by promise.       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.pause().then(() => {
  console.info('Succeeded in pausing');
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to pause AVRecorder and error is: Code: ${error.code}, message: ${error.message}`);
});
```

## resume<sup>9+</sup>

resume(callback: AsyncCallback\<void>): void

Resumes recording. This API uses an asynchronous callback to return the result.

This API must be called after [pause](#pause9). After this API is successfully called, the AVRecorder enters the started state. You can then call [pause](#pause9) again to pause recording or call [stop](#stop9) to stop recording.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Parameters**

| Name  | Type                | Mandatory| Description                        |
| -------- | -------------------- | ---- | ---------------------------- |
| callback | AsyncCallback\<void> | Yes  | Callback used to return the result. If the recording is resumed successfully, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Media Error Codes](errorcode-media.md).

| ID| Error Message                               |
| -------- | --------------------------------------- |
| 5400102  | Operation not allowed. Return by callback. |
| 5400103  | IO error. Return by callback.           |
| 5400105  | Service died. Return by callback.       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.resume((err: BusinessError) => {
  if (err) {
    console.error(`Failed to resume AVRecorder and error is: Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in resuming AVRecorder');
  }
});
```

## resume<sup>9+</sup>

resume(): Promise\<void>

Resumes recording. This API uses a promise to return the result.

This API must be called after [pause](#pause9-1). After this API is successfully called, the AVRecorder enters the started state. You can then call [pause](#pause9-1) again to pause recording or call [stop](#stop9-1) to stop recording.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Return value**

| Type          | Description                                 |
| -------------- | ------------------------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Media Error Codes](errorcode-media.md).

| ID| Error Message                              |
| -------- | -------------------------------------- |
| 5400102  | Operation not allowed. Return by promise. |
| 5400103  | IO error. Return by promise.           |
| 5400105  | Service died. Return by promise.       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.resume().then(() => {
  console.info('Succeeded in resuming AVRecorder');
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to resume AVRecorder and error is: Code: ${error.code}, message: ${error.message}`);
});
```

## stop<sup>9+</sup>

stop(callback: AsyncCallback\<void>): void

Stop recording. This API uses an asynchronous callback to return the result.

This API must be called after [start](#start9) or [pause](#pause9). After this API is successfully called, the AVRecorder enters the stopped state. When **FileGenerationMode** is used during media file creation in the configuration of **prepare()**, the [on('photoAssetAvailable')](#onphotoassetavailable12) callback will be triggered after this API is called.

For audio-only recording, you can call [prepare](#prepare9) again for re-recording. For video-only recording or audio and video recording, you can call [prepare](#prepare9) and [getInputSurface](#getinputsurface9) again for re-recording.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Parameters**

| Name  | Type                | Mandatory| Description                        |
| -------- | -------------------- | ---- | ---------------------------- |
| callback | AsyncCallback\<void> | Yes  | Callback used to return the result. If the recording is stopped successfully, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Media Error Codes](errorcode-media.md).

| ID| Error Message                               |
| -------- | --------------------------------------- |
| 5400102  | Operation not allowed. Return by callback. |
| 5400103  | IO error. Return by callback.           |
| 5400105  | Service died. Return by callback.       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.stop((err: BusinessError) => {
  if (err) {
    console.error(`Failed to stop AVRecorder and error is: Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in stopping AVRecorder');
  }
});
```

## stop<sup>9+</sup>

stop(): Promise\<void>

Stop recording. This API uses a promise to return the result.

This API must be called after [start](#start9-1) or [pause](#pause9-1). After this API is successfully called, the AVRecorder enters the stopped state. When **FileGenerationMode** is used during media file creation in the configuration of **prepare()**, the [on('photoAssetAvailable')](#onphotoassetavailable12) callback will be triggered after this API is called.

For audio-only recording, you can call [prepare](#prepare9-1) again for re-recording. For video-only recording or audio and video recording, you can call [prepare](#prepare9-1) and [getInputSurface](#getinputsurface9-1) again for re-recording.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Return value**

| Type          | Description                                 |
| -------------- | ------------------------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Media Error Codes](errorcode-media.md).

| ID| Error Message                              |
| -------- | -------------------------------------- |
| 5400102  | Operation not allowed. Return by promise. |
| 5400103  | IO error. Return by promise.           |
| 5400105  | Service died. Return by promise.       |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.stop().then(() => {
  console.info('Succeeded in stopping AVRecorder');
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to stop AVRecorder and error is: Code: ${error.code}, message: ${error.message}`);
});
```

## reset<sup>9+</sup>

reset(callback: AsyncCallback\<void>): void

Resets audio and video recording, restoring the recorder to the initial state for reconfiguration of parameters. This API uses an asynchronous callback to return the result.

This API must be called when the AVRecorder is not in the released state. After this API is successfully called, the AVRecorder enters the idle state.

For audio-only recording, you can call [prepare](#prepare9) again for re-recording. For video-only recording or audio and video recording, you can call [prepare](#prepare9) and [getInputSurface](#getinputsurface9) again for re-recording.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Parameters**

| Name  | Type                | Mandatory| Description                          |
| -------- | -------------------- | ---- | ------------------------------ |
| callback | AsyncCallback\<void> | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Media Error Codes](errorcode-media.md).

| ID| Error Message                         |
| -------- | --------------------------------- |
| 5400103  | IO error. Return by callback.     |
| 5400105  | Service died. Return by callback. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.reset((err: BusinessError) => {
  if (err) {
    console.error(`Failed to reset AVRecorder and error is: Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in resetting AVRecorder');
  }
});
```

## reset<sup>9+</sup>

reset(): Promise\<void>

Resets audio and video recording, restoring the recorder to the initial state for reconfiguration of parameters. This API uses a promise to return the result.

This API must be called when the AVRecorder is not in the released state. After this API is successfully called, the AVRecorder enters the idle state.

For audio-only recording, you can call [prepare](#prepare9-1) again for re-recording. For video-only recording or audio and video recording, you can call [prepare](#prepare9-1) and [getInputSurface](#getinputsurface9-1) again for re-recording.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

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

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.reset().then(() => {
  console.info('Succeeded in resetting AVRecorder');
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to reset AVRecorder and error is: Code: ${error.code}, message: ${error.message}`);
});
```

## release<sup>9+</sup>

release(callback: AsyncCallback\<void>): void

Releases the audio and video recording resources. This API uses an asynchronous callback to return the result.

This API must be called when the AVRecorder is not in the released state. After this API is successfully called, the AVRecorder enters the released state.

This API is used together with [createAVRecorder](arkts-apis-media-f.md#mediacreateavrecorder9). After the recording process is complete, call this API to release resources. After the resources are released, you can no longer perform any operation on the AVRecorder instance.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Parameters**

| Name  | Type                | Mandatory| Description                              |
| -------- | -------------------- | ---- | ---------------------------------- |
| callback | AsyncCallback\<void> | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Media Error Codes](errorcode-media.md).

| ID| Error Message                         |
| -------- | --------------------------------- |
| 5400105  | Service died. Return by callback. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.release((err: BusinessError) => {
  if (err) {
    console.error(`Failed to release AVRecorder and error is: Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in releasing AVRecorder');
  }
});
```

## release<sup>9+</sup>

release(): Promise\<void>

Releases the audio and video recording resources. This API uses a promise to return the result.

This API must be called when the AVRecorder is not in the released state. After this API is successfully called, the AVRecorder enters the released state.

This API is used together with [createAVRecorder](arkts-apis-media-f.md#mediacreateavrecorder9). After the recording process is complete, call this API to release resources. After the resources are released, you can no longer perform any operation on the AVRecorder instance.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Return value**

| Type          | Description                                       |
| -------------- | ------------------------------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Media Error Codes](errorcode-media.md).

| ID| Error Message                         |
| -------- | --------------------------------- |
| 5400105  | Service died. Return by promise. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.release().then(() => {
  console.info('Succeeded in releasing AVRecorder');
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to release AVRecorder and error is: Code: ${error.code}, message: ${error.message}`);
});
```

## getCurrentAudioCapturerInfo<sup>11+</sup>

getCurrentAudioCapturerInfo(callback: AsyncCallback\<audio.AudioCapturerChangeInfo>): void

Obtains the information about the current audio capturer. This API is applicable to scenarios where you need to confirm the type of the current audio capture device or verify the audio configuration. This API uses an asynchronous callback to return the result.

This API must be called after [prepare()](#prepare9) and before [stop()](#stop9).

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------ |
| callback | AsyncCallback\<[audio.AudioCapturerChangeInfo](../apis-audio-kit/arkts-apis-audio-i.md#audiocapturerchangeinfo9)> | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the audio.AudioCapturerChangeInfo object obtained; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Media Error Codes](errorcode-media.md).

| ID| Error Message                                  |
| -------- | ------------------------------------------ |
| 5400102  | Operation not allowed. |
| 5400103  | I/O error.             |
| 5400105  | Service died. Return by callback.          |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { audio } from '@kit.AudioKit';

let currentCapturerInfo: audio.AudioCapturerChangeInfo;

avRecorder.getCurrentAudioCapturerInfo((err: BusinessError, capturerInfo: audio.AudioCapturerChangeInfo) => {
  if (err) {
    console.error(`Failed to get CurrentAudioCapturerInfo and error is: Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in getting CurrentAudioCapturerInfo');
    currentCapturerInfo = capturerInfo;
  }
});
```

## getCurrentAudioCapturerInfo<sup>11+</sup>

getCurrentAudioCapturerInfo(): Promise\<audio.AudioCapturerChangeInfo>

Obtains the information about the current audio capturer. This API is applicable to scenarios where you need to confirm the type of the current audio capture device or verify the audio configuration. This API uses a promise to return the result.

This API must be called after [prepare()](#prepare9-1) and before [stop()](#stop9-1).

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Return value**

| Type                                                        | Description                                             |
| ------------------------------------------------------------ | ------------------------------------------------- |
| Promise\<[audio.AudioCapturerChangeInfo](../apis-audio-kit/arkts-apis-audio-i.md#audiocapturerchangeinfo9)> | Promise used to return the audio capturer information.|

**Error codes**

For details about the error codes, see [Media Error Codes](errorcode-media.md).

| ID| Error Message                        |
| -------- | -------------------------------- |
| 5400102  | Operation not allowed.           |
| 5400103  | I/O error.                       |
| 5400105  | Service died. Return by promise. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { audio } from '@kit.AudioKit';

let currentCapturerInfo: audio.AudioCapturerChangeInfo;

avRecorder.getCurrentAudioCapturerInfo().then((capturerInfo: audio.AudioCapturerChangeInfo) => {
  console.info('Succeeded in getting CurrentAudioCapturerInfo');
  currentCapturerInfo = capturerInfo;
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to get CurrentAudioCapturerInfo and error is: Code: ${error.code}, message: ${error.message}`);
});
```

## getAudioCapturerMaxAmplitude<sup>11+</sup>

getAudioCapturerMaxAmplitude(callback: AsyncCallback\<number>): void

Obtains the maximum amplitude of the current audio capturer. This API is applicable to scenarios where the audio amplitude needs to be monitored in real time, such as displaying the recording volume and checking the audio quality. This API uses an asynchronous callback to return the result.

This API must be called after [prepare()](#prepare9) and before [stop()](#stop9).

The return value is the maximum amplitude within the duration from the time the maximum amplitude is obtained last time to the current time. For example, if you have obtained the maximum amplitude at 1s and you call this API again at 2s, then the return value is the maximum amplitude within the duration from 1s to 2s.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Parameters**

| Name  | Type                  | Mandatory| Description                                |
| -------- | ---------------------- | ---- | ------------------------------------ |
| callback | AsyncCallback\<number> | Yes  |  Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the maximum amplitude obtained; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Media Error Codes](errorcode-media.md).

| ID| Error Message                                  |
| -------- | ------------------------------------------ |
| 5400102  | Operation not allowed. |
| 5400105  | Service died. Return by callback.          |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let maxAmplitude: number;

avRecorder.getAudioCapturerMaxAmplitude((err: BusinessError, amplitude: number) => {
  if (err) {
    console.error(`Failed to get AudioCapturerMaxAmplitude and error is: Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in getting AudioCapturerMaxAmplitude');
    maxAmplitude = amplitude;
  }
});
```

## getAudioCapturerMaxAmplitude<sup>11+</sup>

getAudioCapturerMaxAmplitude(): Promise\<number>

Obtains the maximum amplitude of the current audio capturer. This API is applicable to scenarios where the audio amplitude needs to be monitored in real time, such as displaying the recording volume and checking the audio quality. This API uses a promise to return the result.

This API must be called after [prepare()](#prepare9-1) and before [stop()](#stop9-1).

The return value is the maximum amplitude within the duration from the time the maximum amplitude is obtained last time to the current time. For example, if you have obtained the maximum amplitude at 1s and you call this API again at 2s, then the return value is the maximum amplitude within the duration from 1s to 2s.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Return value**

| Type            | Description                                             |
| ---------------- | ------------------------------------------------- |
| Promise\<number>| Promise used to return the maximum amplitude obtained.|

**Error codes**

For details about the error codes, see [Media Error Codes](errorcode-media.md).

| ID| Error Message                        |
| -------- | -------------------------------- |
| 5400102  | Operation not allowed.           |
| 5400105  | Service died. Return by promise. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let maxAmplitude: number;

avRecorder.getAudioCapturerMaxAmplitude().then((amplitude: number) => {
  console.info('Succeeded in getting AudioCapturerMaxAmplitude');
  maxAmplitude = amplitude;
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to get AudioCapturerMaxAmplitude and error is: Code: ${error.code}, message: ${error.message}`);
});
```

## getAvailableEncoder<sup>11+</sup>

getAvailableEncoder(callback: AsyncCallback\<Array\<EncoderInfo>>): void

Obtains available encoders. This method is suitable for scenarios where an appropriate encoder needs to be selected based on the device capability. This API uses an asynchronous callback to return the result.

This API must be called when the AVRecorder is not in the released or error state.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------ |
| callback | AsyncCallback\<Array\<[EncoderInfo](arkts-apis-media-i.md#encoderinfo11)>> | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the available encoders obtained; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Media Error Codes](errorcode-media.md).

| ID| Error Message                                  |
| -------- | ------------------------------------------ |
| 5400102  | Operation not allowed. |
| 5400105  | Service died. Return by callback.          |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let encoderInfo: media.EncoderInfo;

avRecorder.getAvailableEncoder((err: BusinessError, info: media.EncoderInfo[]) => {
  if (err) {
    console.error(`Failed to get AvailableEncoder and error is: Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in getting AvailableEncoder');
    if (info.length > 0) {
      encoderInfo = info[0];
    } else {
      console.error('No available encoder');
    }
  }
});
```

## getAvailableEncoder<sup>11+</sup>

getAvailableEncoder(): Promise\<Array\<EncoderInfo>>

Obtains available encoders. This method is suitable for scenarios where an appropriate encoder needs to be selected based on the device capability. This API uses a promise to return the result.

This API must be called when the AVRecorder is not in the released or error state.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Return value**

| Type                                           | Description                                           |
| ----------------------------------------------- | ----------------------------------------------- |
| Promise\<Array\<[EncoderInfo](arkts-apis-media-i.md#encoderinfo11)>> | Promise used to return the information about the available encoders.|

**Error codes**

For details about the error codes, see [Media Error Codes](errorcode-media.md).

| ID| Error Message                        |
| -------- | -------------------------------- |
| 5400102  | Operation not allowed.           |
| 5400105  | Service died. Return by promise. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let encoderInfo: media.EncoderInfo;

avRecorder.getAvailableEncoder().then((info: media.EncoderInfo[]) => {
  console.info('Succeeded in getting AvailableEncoder');
    if (info.length > 0) {
      encoderInfo = info[0];
    } else {
      console.error('No available encoder');
    }
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to get AvailableEncoder and error is: Code: ${error.code}, message: ${error.message}`);
});
```

## getAVRecorderConfig<sup>11+</sup>

getAVRecorderConfig(callback: AsyncCallback\<AVRecorderConfig>): void

Obtains the real-time configuration of this AVRecorder. This method is applicable to scenarios where you need to check whether the recording configuration is correctly applied, such as debugging recording parameters and verifying whether the configuration takes effect. This API uses an asynchronous callback to return the result.

This API must be called after [prepare](#prepare9).

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Parameters**

| Name  | Type                  | Mandatory| Description                       |
| -------- | ---------------------- | ---- | --------------------------- |
| callback | AsyncCallback\<[AVRecorderConfig](arkts-apis-media-i.md#avrecorderconfig9)> | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the real-time configuration obtained; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Media Error Codes](errorcode-media.md).

| ID| Error Message                                  |
| -------- | ------------------------------------------ |
| 5400102  | Operation not allowed. Return by callback. |
| 5400103  | IO error. Return by callback.             |
| 5400105  | Service died. Return by callback.          |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let avRecorderConfig: media.AVRecorderConfig;

avRecorder.getAVRecorderConfig((err: BusinessError, config: media.AVRecorderConfig) => {
  if (err) {
    console.error(`Failed to get avRecorderConfig and error is: Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in getting AVRecorderConfig');
    avRecorderConfig = config;
  }
});
```

## getAVRecorderConfig<sup>11+</sup>

getAVRecorderConfig(): Promise\<AVRecorderConfig>;

Obtains the real-time configuration of this AVRecorder. This method is applicable to scenarios where you need to check whether the recording configuration is correctly applied, such as debugging recording parameters and verifying whether the configuration takes effect. This API uses a promise to return the result.

This API must be called after [prepare](#prepare9-1).

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Return value**

| Type            | Description                            |
| ---------------- | -------------------------------- |
| Promise\<[AVRecorderConfig](arkts-apis-media-i.md#avrecorderconfig9)> | Promise used to return the real-time configuration.|

**Error codes**

For details about the error codes, see [Media Error Codes](errorcode-media.md).

| ID| Error Message                                 |
| -------- | ----------------------------------------- |
| 5400102  | Operation not allowed. Return by promise. |
| 5400103  | IO error. Return by promise.             |
| 5400105  | Service died. Return by promise.          |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let avRecorderConfig: media.AVRecorderConfig;

avRecorder.getAVRecorderConfig().then((config: media.AVRecorderConfig) => {
  console.info('Succeeded in getting AVRecorderConfig');
  avRecorderConfig = config;
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to get AVRecorderConfig and error is: Code: ${error.code}, message: ${error.message}`);
});
```

## on('stateChange')<sup>9+</sup>

on(type: 'stateChange', callback: OnAVRecorderStateChangeHandler): void

Subscribes to [AVRecorderState](arkts-apis-media-t.md#avrecorderstate9) changes.  An app can subscribe to only one callback. When the app initiates multiple subscriptions, the last subscription is applied. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Parameters**

| Name  | Type    | Mandatory| Description                                                        |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | Yes  | Event type, which is **'stateChange'** in this case. This event can be triggered by both user operations and the system.|
| callback | [OnAVRecorderStateChangeHandler](arkts-apis-media-t.md#onavrecorderstatechangehandler12) | Yes  | Callback used to receive the state change event. The callback parameters include **state** (recording state, which is of the **AVRecorderState** type) and **reason** (state change reason, which is of the **StateChangeReason** type).|

**Error codes**

For details about the error codes, see [Media Error Codes](errorcode-media.md).

| ID| Error Message                         |
| -------- | --------------------------------- |
| 5400103  | IO error. Return by callback.     |
| 5400105  | Service died. Return by callback. |

**Example**

```ts
avRecorder.on('stateChange', (state: media.AVRecorderState, reason: media.StateChangeReason) => {
  console.info('case state has changed, new state is: ' + state + ', and reason is: ' + reason);
});
```

## off('stateChange')<sup>9+</sup>

off(type: 'stateChange', callback?: OnAVRecorderStateChangeHandler): void

Unsubscribes from [AVRecorderState](arkts-apis-media-t.md#avrecorderstate9) changes. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Parameters**

| Name| Type  | Mandatory| Description                                                        |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| type   | string | Yes  | Event type, which is **'stateChange'** in this case. This event can be triggered by both user operations and the system.|
| callback<sup>12+</sup> | [OnAVRecorderStateChangeHandler](arkts-apis-media-t.md#onavrecorderstatechangehandler12) | No  | Callback used to receive the state change event. If this parameter is specified, the subscription to the specified event with the specified callback is canceled. (The callback object cannot be an anonymous function.) Otherwise, the subscriptions to the specified event with all the callbacks are canceled.<br>This parameter is supported since API version 12.|

**Example**

```ts
avRecorder.off('stateChange');
```

## on('error')<sup>9+</sup>

on(type: 'error', callback: ErrorCallback): void

Subscribes to AVRecorder error events. This event is used only for error prompt and does not require the user to stop recording. If the [AVRecorderState](arkts-apis-media-t.md#avrecorderstate9) is also switched to error, call [reset](#reset9) or [release][release()](#release9) to exit the recording. This API uses an asynchronous callback to return the result.

An application can subscribe to only one AVRecorder error event. When the application initiates multiple subscriptions to this event, the last subscription is applied.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Parameters**

| Name  | Type         | Mandatory| Description                                                        |
| -------- | ------------- | ---- | ------------------------------------------------------------ |
| type     | string        | Yes  | Event type, which is **'error'** in this case.|
| callback | [ErrorCallback](../apis-basic-services-kit/js-apis-base.md#errorcallback) | Yes  | Callback used to receive AVRecorder error events. The callback parameter is **err**, which is an object of the **BusinessError** type and contains the error code and error message.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Media Error Codes](errorcode-media.md).

| ID| Error Message                                  |
| -------- | ------------------------------------------ |
| 201      | Permission denied.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| 801      | Capability not supported. |
| 5400101  | No memory.             |
| 5400102  | Operation not allowed. |
| 5400103  | I/O error.             |
| 5400104  | Operation timeout.     |
| 5400105  | Service died.          |
| 5400106  | Unsupported format.    |
| 5400107  | Audio interrupted. <br>Applicable versions: 11+    |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.on('error', (err: BusinessError) => {
  console.error(`Failed to record. Code: ${err.code}, message: ${err.message}`);
});
```

## off('error')<sup>9+</sup>

off(type: 'error', callback?: ErrorCallback): void

Unsubscribes from AVRecorder error events. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Parameters**

| Name| Type  | Mandatory| Description                                                        |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| type   | string | Yes  | Event type, which is **'error'** in this case.|
| callback<sup>12+</sup> | [ErrorCallback](../apis-basic-services-kit/js-apis-base.md#errorcallback) | No  | Callback used to receive AVRecorder error events. If this parameter is specified, the subscription to the specified event with the specified callback is canceled. (The callback object cannot be an anonymous function.) Otherwise, the subscriptions to the specified event with all the callbacks are canceled.<br>This parameter is supported since API version 12.                  |

**Example**

```ts
avRecorder.off('error');
```

## on('audioCapturerChange')<sup>11+</sup>

on(type: 'audioCapturerChange', callback: Callback\<audio.AudioCapturerChangeInfo>): void

Subscribes to audio capturer configuration changes. When the audio capturer configuration changes, the callback is triggered to return the full information about the new configuration. This API uses an asynchronous callback to return the result.

An app can subscribe to only one audio capturer configuration change event. When the app initiates multiple subscriptions to this event, the last subscription is applied.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Parameters**

| Name  | Type    | Mandatory| Description                                                        |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | Yes  | Event type, which is **'audioCapturerChange'** in this case.|
| callback | Callback\<[audio.AudioCapturerChangeInfo](../apis-audio-kit/arkts-apis-audio-i.md#audiocapturerchangeinfo9)> | Yes| Callback used to receive the audio capturer configuration after change. The callback parameter is **audio.AudioCapturerChangeInfo**, which indicates the audio capturer configuration after change.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                  |
| -------- | ------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.      |

**Example**

```ts
import { audio } from '@kit.AudioKit';

let capturerChangeInfo: audio.AudioCapturerChangeInfo;

avRecorder.on('audioCapturerChange', (audioCapturerChangeInfo: audio.AudioCapturerChangeInfo) => {
  console.info('audioCapturerChange called');
  capturerChangeInfo = audioCapturerChangeInfo;
});
```

## off('audioCapturerChange')<sup>11+</sup>

off(type: 'audioCapturerChange', callback?: Callback\<audio.AudioCapturerChangeInfo>): void

Unsubscribes from audio capturer configuration changes. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Parameters**

| Name| Type  | Mandatory| Description                                                        |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| type   | string | Yes  | Event type, which is **'audioCapturerChange'** in this case.|
| callback<sup>12+</sup> | Callback\<[audio.AudioCapturerChangeInfo](../apis-audio-kit/arkts-apis-audio-i.md#audiocapturerchangeinfo9)> | No| Callback used to receive the audio capturer configuration after change. If this parameter is specified, the subscription to the specified event with the specified callback is canceled. (The callback object cannot be an anonymous function.) Otherwise, the subscriptions to the specified event with all the callbacks are canceled.<br>This parameter is supported since API version 12.|

**Example**

```ts
avRecorder.off('audioCapturerChange');
```

## on('photoAssetAvailable')<sup>12+</sup>

on(type: 'photoAssetAvailable', callback: Callback\<photoAccessHelper.PhotoAsset>): void

Subscribes to media asset callback events. When [FileGenerationMode](arkts-apis-media-e.md#filegenerationmode12) is used during media file creation, the [PhotoAsset](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAsset.md) object is called back to the application after the [stop](#stop9) operation is complete. This API uses an asynchronous callback to return the result.

An app can subscribe to only one media asset callback event. When the app initiates multiple subscriptions to this event, the last subscription is applied.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Parameters**

| Name  | Type    | Mandatory| Description                                                        |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | Yes  |Event type, which is **'photoAssetAvailable'** in this case.|
| callback | Callback\<[photoAccessHelper.PhotoAsset](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAsset.md)> | Yes| Callback used to receive the **PhotoAsset** object corresponding to the resource file created by the system. When **FileGenerationMode** is used during media file creation in the configuration of **prepare()**, this callback is triggered only after the **stop** operation is complete.|

**Error codes**

For details about the error codes, see [Media Error Codes](errorcode-media.md).

| ID| Error Message                                  |
| -------- | ------------------------------------------ |
| 5400103  | IO error. Return by callback.             |
| 5400105  | Service died. Return by callback.          |

**Example**

<!--code_no_check-->
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { photoAccessHelper } from '@kit.MediaLibraryKit';
let photoAsset: photoAccessHelper.PhotoAsset;

// Example: Process the photoAsset callback and save the video.
async function saveVideo(context: Context, asset: photoAccessHelper.PhotoAsset) {
  console.info('saveVideo called');
  try {
    let photoHelper = photoAccessHelper.getPhotoAccessHelper(context);
    let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest = new photoAccessHelper.MediaAssetChangeRequest(asset);
    assetChangeRequest.saveCameraPhoto();
    await photoHelper.applyChanges(assetChangeRequest);
    console.info('apply saveVideo successfully');
  } catch (err) {
    let error: BusinessError = err as BusinessError;
    console.error(`Failed to apply saveVideo. Code: ${error.code}, message: ${error.message}`);
  }
}
// Subscribe to the photoAsset event.
avRecorder.on('photoAssetAvailable', (asset: photoAccessHelper.PhotoAsset) => {
  console.info('photoAssetAvailable called');
  if (asset != undefined) {
    photoAsset = asset;
    // Process the photoAsset callback.
    // Example: this.saveVideo(context, asset);
  } else {
    console.error('photoAsset is undefined');
  }
});
```

## off('photoAssetAvailable')<sup>12+</sup>

off(type: 'photoAssetAvailable', callback?: Callback\<photoAccessHelper.PhotoAsset>): void

Unsubscribes from media asset callback events. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.Media.AVRecorder

**Parameters**

| Name| Type  | Mandatory| Description                                                        |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| type   | string | Yes  | Event type, which is **'photoAssetAvailable'** in this case.|
| callback | Callback\<[photoAccessHelper.PhotoAsset](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAsset.md)> | No| Callback used to receive the **PhotoAsset** object corresponding to the resource file created by the system. If this parameter is specified, the subscription to the specified event with the specified callback is canceled. (The callback object cannot be an anonymous function.) Otherwise, the subscriptions to the specified event with all the callbacks are canceled.|

**Example**

```ts
avRecorder.off('photoAssetAvailable');
```