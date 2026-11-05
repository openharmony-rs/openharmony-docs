# AVRecorder (System API)

```TypeScript
interface AVRecorder
```

The **AVRecorder** class is used to manage the entire audio and video recording process, including audio recording, video recording, and audio-video recording. It can be used to flexibly configure encoding parameters, add watermarks, set metadata, and listen for the recording status and error events. It can be used to record audio and video and saved them to files, including scenarios where recording continuity needs to be maintained when the audio is interrupted and audio amplitude needs to be monitored in real time. Before calling the methods of the AVRecorder class, you need to call the [createAVRecorder](arkts-media-media-createavrecorder-f.md) API to create an **AVRecorder** instance. Typical recording process: [createAVRecorder](arkts-media-media-createavrecorder-f.md) → [prepare](arkts-media-media-avrecorder-i.md#prepare-2) → [getInputSurface](arkts-media-media-avrecorder-i.md#getinputsurface) (for video-only or audio and video recording) → [start](arkts-media-media-avrecorder-i.md#start) → [pause](arkts-media-media-avrecorder-i.md#pause)/[resume](arkts-media-media-avrecorder-i.md#resume) → [stop](arkts-media-media-avrecorder-i.md#stop) → [release](arkts-media-media-avrecorder-i.md#release).

For details about the audio and video recording demo, see [Audio Recording](../../../media/media/using-avrecorder-for-recording.md) and [Video Recording](../../../media/media/video-recording.md).

> **NOTE:** 
> 
> To use the camera to record videos, the camera module is required. For details about how to use the APIs
> provided by the camera module, see [Camera Management](../../apis-camera-kit/arkts-apis/arkts-camera-multimedia-camera.md).

**Since:** 9

<!--Device-media-interface AVRecorder--><!--Device-media-interface AVRecorder-End-->

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## getInputMetaSurface

```TypeScript
getInputMetaSurface(type: MetaSourceType): Promise<string>
```

Get input meta surface for specified meta source type. it must be called between prepare completed and start.

**Since:** 12

<!--Device-AVRecorder-getInputMetaSurface(type: MetaSourceType): Promise<string>--><!--Device-AVRecorder-getInputMetaSurface(type: MetaSourceType): Promise<string>-End-->

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [MetaSourceType](arkts-media-media-metasourcetype-e-sys.md) | Yes | Meta source type. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | A Promise instance used to return the input surface id in string. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called from Non-System applications. Return by promise. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3. Parameter verification failed. |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Return by promise. |
| [5400103](../errorcode-media.md#5400103-io-error) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-play-service-dead) | Service died. Return by promise. |

## isWatermarkSupported

```TypeScript
isWatermarkSupported(): Promise<boolean>
```

Checks whether the device supports the hardware digital watermark. This API uses a promise to return the result.

This API can be called after the prepare(), start(), or pause() event is triggered.

**Since:** 13

<!--Device-AVRecorder-isWatermarkSupported(): Promise<boolean>--><!--Device-AVRecorder-isWatermarkSupported(): Promise<boolean>-End-->

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the check result. The value **true** means that the device supports the hardware digital watermark, and **false** means the opposite. |

<!--Del-->
**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.isWatermarkSupported().then((isWatermarkSupported: boolean) => {
  console.info(`Succeeded in get, isWatermarkSupported: ${isWatermarkSupported}`);
}).catch((error: BusinessError) => {
  console.error(`Failed to get and catch error is ${error.message}`);
});
```

<!--DelEnd-->

## setWatermark

```TypeScript
setWatermark(watermark: image.PixelMap, config: WatermarkConfig): Promise<void>
```

Sets a watermark for the AVRecorder. This API uses a promise to return the result.

This API can be called only after the prepare() event is triggered and before the start() event is triggered.

**Since:** 13

<!--Device-AVRecorder-setWatermark(watermark: image.PixelMap, config: WatermarkConfig): Promise<void>--><!--Device-AVRecorder-setWatermark(watermark: image.PixelMap, config: WatermarkConfig): Promise<void>-End-->

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| watermark | [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) | Yes | : Watermark image. |
| config | [WatermarkConfig](arkts-media-media-watermarkconfig-i-sys.md) | Yes | : Configures of the watermark. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:         1. Mandatory parameters are left unspecified.         2. Incorrect parameter types.         3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |

<!--Del-->
**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

let watermark: image.PixelMap|undefined = undefined; // need data.
let watermarkConfig: media.WatermarkConfig = { top: 100, left: 100 }

avRecorder.setWatermark(watermark, watermarkConfig).then(() => {
  console.info('Succeeded in setWatermark');
}).catch((error: BusinessError) => {
  console.error(`Failed to setWatermark and catch error is ${error.message}`);
});
```

<!--DelEnd-->
