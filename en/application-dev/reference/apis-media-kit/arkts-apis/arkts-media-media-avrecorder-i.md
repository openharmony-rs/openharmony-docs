# AVRecorder

```TypeScript
interface AVRecorder
```

AVRecorder is a class for audio and video recording management. It provides APIs to record media assets. Before calling any API in AVRecorder, you must use [createAVRecorder()](arkts-media-media-createavrecorder-f.md) to create an AVRecorder instance.

For details about the audio and video recording demo, see [Audio Recording](../../../media/media/using-avrecorder-for-recording.md) and [Video Recording](../../../media/media/video-recording.md).

> **NOTE:** 
> 
> 
> To use the camera to record videos, the camera module is required. For details about how to use the APIs
> provided by the camera module, see [Camera Management](../../apis-camera-kit/arkts-apis/arkts-camera-multimedia-camera.md).

**Since:** 9

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## addWatermark

```TypeScript
addWatermark(watermark: image.PixelMap, config: WatermarkConfiguration): Promise<number>
```

add a watermark for the AVRecorder. This API uses a promise to return the result. App can add up to 5 watermarks. This API can be called only before the prepared state.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| watermark | [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) | Yes | : Watermark image. |
| config | [WatermarkConfiguration](arkts-media-media-watermarkconfiguration-i.md) | Yes | : Configuration of the watermark. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise that returns the watermark id. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Return by promise. |
| [5400103](../errorcode-media.md#5400103-io-error) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-play-service-dead) | Service died. Return by promise. |
| [5400108](../errorcode-media.md#5400108-parameter-value-out-of-range) | The parameter check failed, parameter value out of range. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';
import { media } from '@kit.MediaKit';

let watermark: image.PixelMap | undefined = undefined; // You can obtain a local resource file and convert it into a pixel map. The watermark image cannot be empty.
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

## getAudioCapturerMaxAmplitude

```TypeScript
getAudioCapturerMaxAmplitude(callback: AsyncCallback<number>): void
```

Obtains the maximum amplitude of the current audio capturer. This API uses an asynchronous callback to return the result.

This API can be called only after the [prepare()](#prepare) API is called. If this API is called after [stop()](#stop) is successfully called, an error is reported.

The return value is the maximum amplitude within the duration from the time the maximum amplitude is obtained last time to the current time. For example, if you have obtained the maximum amplitude at 1s and you call this API again at 2s, then the return value is the maximum amplitude within the duration from 1s to 2s.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the maximum amplitude obtained; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. |
| [5400105](../errorcode-media.md#5400105-play-service-dead) | Service died. Return by callback. |

**Examples**

```TypeScript
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

<a id="getaudiocapturermaxamplitude-1"></a>

## getAudioCapturerMaxAmplitude

```TypeScript
getAudioCapturerMaxAmplitude(): Promise<number>
```

Obtains the maximum amplitude of the current audio capturer. This API uses a promise to return the result.

This API can be called only after the [prepare()](#prepare) API is called. If this API is called after [stop()](#stop) is successfully called, an error is reported.

The return value is the maximum amplitude within the duration from the time the maximum amplitude is obtained last time to the current time. For example, if you have obtained the maximum amplitude at 1s and you call this API again at 2s, then the return value is the maximum amplitude within the duration from 1s to 2s.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the maximum amplitude obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. |
| [5400105](../errorcode-media.md#5400105-play-service-dead) | Service died. Return by promise. |

**Examples**

```TypeScript
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

## getAvailableEncoder

```TypeScript
getAvailableEncoder(callback: AsyncCallback<Array<EncoderInfo>>): void
```

Obtains available encoders. This API uses an asynchronous callback to return the result.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[EncoderInfo](arkts-media-media-encoderinfo-i.md)&gt;&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the available encoders obtained; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. |
| [5400105](../errorcode-media.md#5400105-play-service-dead) | Service died. Return by callback. |

**Examples**

```TypeScript
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

<a id="getavailableencoder-1"></a>

## getAvailableEncoder

```TypeScript
getAvailableEncoder(): Promise<Array<EncoderInfo>>
```

Obtains available encoders. This API uses a promise to return the result.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[EncoderInfo](arkts-media-media-encoderinfo-i.md)&gt;&gt; | Promise used to return the information about the available encoders. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. |
| [5400105](../errorcode-media.md#5400105-play-service-dead) | Service died. Return by promise. |

**Examples**

```TypeScript
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

## getAVRecorderConfig

```TypeScript
getAVRecorderConfig(callback: AsyncCallback<AVRecorderConfig>): void
```

Obtains the real-time configuration of this AVRecorder. This API uses an asynchronous callback to return the result.

This API can be called only after [prepare()](#prepare) is called.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AVRecorderConfig](arkts-media-media-avrecorderconfig-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the real-time configuration obtained; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operate not permit. Return by callback. |
| [5400103](../errorcode-media.md#5400103-io-error) | IO error. Return by callback. |
| [5400105](../errorcode-media.md#5400105-play-service-dead) | Service died. Return by callback. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let avConfig: media.AVRecorderConfig;

avRecorder.getAVRecorderConfig((err: BusinessError, config: media.AVRecorderConfig) => {
  if (err) {
    console.error(`Failed to get avConfig and error is: Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in getting AVRecorderConfig');
    avConfig = config;
  }
});
```

<a id="getavrecorderconfig-2"></a>

## getAVRecorderConfig

```TypeScript
getAVRecorderConfig(): Promise<AVRecorderConfig>
```

Obtains the real-time configuration of this AVRecorder. This API uses a promise to return the result.

This API can be called only after [prepare()](#prepare-1) is called.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AVRecorderConfig](arkts-media-media-avrecorderconfig-i.md)&gt; | Promise used to return the real-time configuration. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operate not permit. Return by promise. |
| [5400103](../errorcode-media.md#5400103-io-error) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-play-service-dead) | Service died. Return by promise. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let avConfig: media.AVRecorderConfig;

avRecorder.getAVRecorderConfig().then((config: media.AVRecorderConfig) => {
  console.info('Succeeded in getting AVRecorderConfig');
  avConfig = config;
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to get AVRecorderConfig and error is: Code: ${error.code}, message: ${error.message}`);
});
```

## getCurrentAudioCapturerInfo

```TypeScript
getCurrentAudioCapturerInfo(callback: AsyncCallback<audio.AudioCapturerChangeInfo>): void
```

Obtains the information about the current audio capturer. This API uses an asynchronous callback to return the result.

This API can be called only after the [prepare()](#prepare) API is called. If this API is called after [stop()](#stop) is successfully called, an error is reported.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[audio.AudioCapturerChangeInfo](../../apis-audio-kit/arkts-apis/arkts-audio-audio-audiocapturerchangeinfo-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the audio.AudioCapturerChangeInfo object obtained; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. |
| [5400103](../errorcode-media.md#5400103-io-error) | I/O error. |
| [5400105](../errorcode-media.md#5400105-play-service-dead) | Service died. Return by callback. |

**Examples**

```TypeScript
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

<a id="getcurrentaudiocapturerinfo-2"></a>

## getCurrentAudioCapturerInfo

```TypeScript
getCurrentAudioCapturerInfo(): Promise<audio.AudioCapturerChangeInfo>
```

Obtains the information about the current audio capturer. This API uses a promise to return the result.

This API can be called only after the [prepare()](#prepare) API is called. If this API is called after [stop()](#stop) is successfully called, an error is reported.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[audio.AudioCapturerChangeInfo](../../apis-audio-kit/arkts-apis/arkts-audio-audio-audiocapturerchangeinfo-i.md)&gt; | Promise used to return the audio capturer information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. |
| [5400103](../errorcode-media.md#5400103-io-error) | I/O error. |
| [5400105](../errorcode-media.md#5400105-play-service-dead) | Service died. Return by promise. |

**Examples**

```TypeScript
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

## getInputSurface

```TypeScript
getInputSurface(callback: AsyncCallback<string>): void
```

Obtains the surface required for recording. This API uses an asynchronous callback to return the result.

The caller obtains the surface buffer from this surface and fills in the corresponding video data.

Note that the video data must carry the timestamp (in ns) and buffer size, and the start time of the timestamp must be based on the system startup time.

This API can be called only after the [prepare()](#prepare) API is called.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the surface ID obtained; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operate not permit. Return by callback. |
| [5400103](../errorcode-media.md#5400103-io-error) | IO error. Return by callback. |
| [5400105](../errorcode-media.md#5400105-play-service-dead) | Service died. Return by callback. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let surfaceID: string; // The surfaceID is transferred to the camera API to create a videoOutput instance.

avRecorder.getInputSurface((err: BusinessError, surfaceId: string) => {
  if (err) {
    console.error(`Failed to do getInputSurface and error is: Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in doing getInputSurface');
    surfaceID = surfaceId;
  }
});
```

<a id="getinputsurface-2"></a>

## getInputSurface

```TypeScript
getInputSurface(): Promise<string>
```

Obtains the surface required for recording. This API uses a promise to return the result.

The caller obtains the surface buffer from this surface and fills in the corresponding video data.

Note that the video data must carry the timestamp (in ns) and buffer size, and the start time of the timestamp must be based on the system startup time.

This API can be called only after the [prepare()](#prepare-1) API is called.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the surface buffer obtained from the surface. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operate not permit. Return by promise. |
| [5400103](../errorcode-media.md#5400103-io-error) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-play-service-dead) | Service died. Return by promise. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let surfaceID: string; // The surfaceID is transferred to the camera API to create a videoOutput instance.

avRecorder.getInputSurface().then((surfaceId: string) => {
  console.info('Succeeded in getting InputSurface');
  surfaceID = surfaceId;
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to get InputSurface and error is: Code: ${error.code}, message: ${error.message}`);
});
```

## off('stateChange')

```TypeScript
off(type: 'stateChange', callback?: OnAVRecorderStateChangeHandler): void
```

Unsubscribes from AVRecorder state changes. This API uses an asynchronous callback to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'stateChange' | Yes | Event type, which is **'stateChange'** in this case. This event can be triggered by both user operations and the system. |
| callback | [OnAVRecorderStateChangeHandler](arkts-media-media-onavrecorderstatechangehandler-t.md) | No | Callback used to return the state change event. If this parameter is specified, the subscription to the specified event with the specified callback is canceled. (The callback object cannot be an anonymous function.) Otherwise, the subscriptions to the specified event with all the callbacks are canceled.<br>This parameter is supported since API version 12.<br>**Since:** 12 |

**Examples**

```TypeScript
avRecorder.off('stateChange');
```

## off('error')

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

Unsubscribes from AVRecorder errors. After the unsubscription, your application can no longer receive AVRecorder errors. This API uses an asynchronous callback to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'error' | Yes | Event type, which is **'error'** in this case.<br>This event is triggered when an error occurs during recording. |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | No | Callback used to return the recording error event. If this parameter is specified, the subscription to the specified event with the specified callback is canceled. (The callback object cannot be an anonymous function.) Otherwise, the subscriptions to the specified event with all the callbacks are canceled.<br>This parameter is supported since API version 12.<br>**Since:** 12 |

**Examples**

```TypeScript
avRecorder.off('error');
```

## off('audioCapturerChange')

```TypeScript
off(type: 'audioCapturerChange', callback?: Callback<audio.AudioCapturerChangeInfo>): void
```

Subscribes to audio capturer configuration changes. This API uses an asynchronous callback to return the result.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'audioCapturerChange' | Yes | Event type, which is **'audioCapturerChange'** in this case. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[audio.AudioCapturerChangeInfo](../../apis-audio-kit/arkts-apis/arkts-audio-audio-audiocapturerchangeinfo-i.md)&gt; | No | Callback used to return the changed audio capturer configuration. If this parameter is specified, the subscription to the specified event with the specified callback is canceled. (The callback object cannot be an anonymous function.) Otherwise, the subscriptions to the specified event with all the callbacks are canceled.<br>This parameter is supported since API version 12.<br>**Since:** 12 |

**Examples**

```TypeScript
avRecorder.off('audioCapturerChange');
```

## off('photoAssetAvailable')

```TypeScript
off(type: 'photoAssetAvailable', callback?: Callback<photoAccessHelper.PhotoAsset>): void
```

Unsubscribes from media asset callback events. This API uses an asynchronous callback to return the result.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'photoAssetAvailable' | Yes | Event type, which is **'photoAssetAvailable'** in this case. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[photoAccessHelper.PhotoAsset](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoasset-i.md)&gt; | No | Callback used to return the PhotoAsset object corresponding to the resource file created by the system. If this parameter is specified, the subscription to the specified event with the specified callback is canceled. (The callback object cannot be an anonymous function.) Otherwise, the subscriptions to the specified event with all the callbacks are canceled. |

**Examples**

```TypeScript
avRecorder.off('photoAssetAvailable');
```

## on('audioCapturerChange')

```TypeScript
on(type: 'audioCapturerChange', callback: Callback<audio.AudioCapturerChangeInfo>): void
```

Subscribes to audio capturer configuration changes. Any configuration change triggers the callback that returns the entire configuration information. This API uses an asynchronous callback to return the result.

When the application initiates multiple subscriptions to this event, the last subscription is applied.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'audioCapturerChange' | Yes | Event type, which is **'audioCapturerChange'** in this case. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[audio.AudioCapturerChangeInfo](../../apis-audio-kit/arkts-apis/arkts-audio-audio-audiocapturerchangeinfo-i.md)&gt; | Yes | Callback used to return the changed audio capturer configuration. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit'

let capturerChangeInfo: audio.AudioCapturerChangeInfo;

avRecorder.on('audioCapturerChange',  (audioCapturerChangeInfo: audio.AudioCapturerChangeInfo) => {
  console.info('audioCapturerChange called');
  capturerChangeInfo = audioCapturerChangeInfo;
});
```

## on('photoAssetAvailable')

```TypeScript
on(type: 'photoAssetAvailable', callback: Callback<photoAccessHelper.PhotoAsset>): void
```

Subscribes to media asset callback events. When [FileGenerationMode](arkts-media-media-filegenerationmode-e.md) is used during media file creation, the [PhotoAsset](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-file-photoaccesshelper.md) object is called back to the application after the [stop](#stop) operation is complete. This API uses an asynchronous callback to return the result.

When the application initiates multiple subscriptions to this event, the last subscription is applied.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'photoAssetAvailable' | Yes | Event type, which is **'photoAssetAvailable'** in this case. The event is triggered when a photo asset is available. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[photoAccessHelper.PhotoAsset](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoasset-i.md)&gt; | Yes | Callback used to return the PhotoAsset object corresponding to the resource file created by the system. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400103](../errorcode-media.md#5400103-io-error) | IO error. Return by callback. |
| [5400105](../errorcode-media.md#5400105-play-service-dead) | Service died. Return by callback. |

**Examples**

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
let photoAsset: photoAccessHelper.PhotoAsset;

// Example: Process the photoAsset callback and save the video.
async function saveVideo(context: Context, asset: photoAccessHelper.PhotoAsset) {
  console.info("saveVideo called");
  try {
    let phAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);
    let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest = new photoAccessHelper.MediaAssetChangeRequest(asset);
    assetChangeRequest.saveCameraPhoto();
    await phAccessHelper.applyChanges(assetChangeRequest);
    console.info('apply saveVideo successfully');
  } catch (err) {
    console.error(`apply saveVideo failed with error: ${err.code}, ${err.message}`);
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

## on('stateChange')

```TypeScript
on(type: 'stateChange', callback: OnAVRecorderStateChangeHandler): void
```

Subscribes to AVRecorder state changes. An application can subscribe to only one AVRecorder state change event. When the application initiates multiple subscriptions to this event, the last subscription is applied. This API uses an asynchronous callback to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'stateChange' | Yes | Event type, which is **'stateChange'** in this case. This event can be triggered by both user operations and the system. |
| callback | [OnAVRecorderStateChangeHandler](arkts-media-media-onavrecorderstatechangehandler-t.md) | Yes | Callback used to return the state change event.<br>**Since:** 12 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400103](../errorcode-media.md#5400103-io-error) | IO error. Return by callback. |
| [5400105](../errorcode-media.md#5400105-play-service-dead) | Service died. Return by callback. |

**Examples**

```TypeScript
avRecorder.on('stateChange', async (state: media.AVRecorderState, reason: media.StateChangeReason) => {
  console.info('case state has changed, new state is: ' + state + ', and reason is: ' + reason);
});
```

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

Subscribes to AVRecorder errors. This event is used only for error prompt and does not require the user to stop recording control. If the [AVRecorderState](arkts-media-media-avrecorderstate-t.md) is also switched to error, call [reset()](#reset) or [release()] [release()](#release) to exit the recording. This API uses an asynchronous callback to return the result.

An application can subscribe to only one AVRecorder error event. When the application initiates multiple subscriptions to this event, the last subscription is applied.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'error' | Yes | Event type, which is **'error'** in this case.<br>This event is triggered when an error occurs during recording. |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | Yes | Callback used to return the recording error event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [5400101](../errorcode-media.md#5400101-memory-allocation-failed) | No memory. |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. |
| [5400103](../errorcode-media.md#5400103-io-error) | I/O error. |
| [5400104](../errorcode-media.md#5400104-operation-timeout) | Time out. |
| [5400105](../errorcode-media.md#5400105-play-service-dead) | Service died. |
| [5400106](../errorcode-media.md#5400106-format-not-supported) | Unsupported format. |
| [5400107](../errorcode-media.md#5400107-audio-focus-conflict) | Audio interrupted.<br>**Applicable version:** 11 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.on('error', (err: BusinessError) => {
  console.error(`case avRecorder.on(error) called. Code: ${err.code}, message: ${err.message}`);
});
```

## pause

```TypeScript
pause(callback: AsyncCallback<void>): void
```

Pauses video recording. This API uses an asynchronous callback to return the result.

This API can be called only after the [start()](#start) API is called. You can call [resume()](#resume) to resume recording.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operate not permit. Return by callback. |
| [5400103](../errorcode-media.md#5400103-io-error) | IO error. Return by callback. |
| [5400105](../errorcode-media.md#5400105-play-service-dead) | Service died. Return by callback. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.pause((err: BusinessError) => {
  if (err) {
    console.error(`Failed to pause AVRecorder and error is: Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in pausing');
  }
});
```

<a id="pause-1"></a>

## pause

```TypeScript
pause(): Promise<void>
```

Pauses video recording. This API uses a promise to return the result.

This API can be called only after the [start()](#start) API is called. You can call [resume()](#resume) to resume recording.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operate not permit. Return by promise. |
| [5400103](../errorcode-media.md#5400103-io-error) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-play-service-dead) | Service died. Return by promise. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.pause().then(() => {
  console.info('Succeeded in pausing');
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to pause AVRecorder and error is: Code: ${error.code}, message: ${error.message}`);
});
```

## prepare

```TypeScript
prepare(config: AVRecorderConfig, callback: AsyncCallback<void>): void
```

Sets audio and video recording parameters. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.MICROPHONE

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [AVRecorderConfig](arkts-media-media-avrecorderconfig-i.md) | Yes | Audio and video recording parameters to set. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. Return by callback. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operate not permit. Return by callback. |
| [5400105](../errorcode-media.md#5400105-play-service-dead) | Service died. Return by callback. |

**Examples**

```TypeScript
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
  url : 'fd://', // Before passing an FD to this parameter, the file must be created by the caller and granted with the read and write permissions.
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

<a id="prepare-1"></a>

## prepare

```TypeScript
prepare(config: AVRecorderConfig): Promise<void>
```

Sets audio and video recording parameters. This API uses a promise to return the result. The MICROPHONE permission is required only if audio recording is involved.

**Since:** 9

**Required permissions:** ohos.permission.MICROPHONE

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [AVRecorderConfig](arkts-media-media-avrecorderconfig-i.md) | Yes | Audio and video recording parameters to set. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. Return by promise. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operate not permit. Return by promise. |
| [5400105](../errorcode-media.md#5400105-play-service-dead) | Service died. Return by promise. |

**Examples**

```TypeScript
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
  url : 'fd://',  // Before passing an FD to this parameter, the file must be created by the caller and granted with the read and write permissions.
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

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

Releases the audio and video recording resources. This API uses an asynchronous callback to return the result.

After the resources are released, you can no longer perform any operation on the AVRecorder instance.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400105](../errorcode-media.md#5400105-play-service-dead) | Service died. Return by callback. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.release((err: BusinessError) => {
  if (err) {
    console.error(`Failed to release AVRecorder and error is: Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in releasing AVRecorder');
  }
});
```

<a id="release-1"></a>

## release

```TypeScript
release(): Promise<void>
```

Releases the audio and video recording resources. This API uses a promise to return the result.

After the resources are released, you can no longer perform any operation on the AVRecorder instance.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400105](../errorcode-media.md#5400105-play-service-dead) | Service died. Return by callback. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.release().then(() => {
  console.info('Succeeded in releasing AVRecorder');
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to release AVRecorder and error is: Code: ${error.code}, message: ${error.message}`);
});
```

## reset

```TypeScript
reset(callback: AsyncCallback<void>): void
```

Resets audio and video recording. This API uses an asynchronous callback to return the result.

For audio-only recording, you can call [prepare()](#prepare) again for re -recording. For video-only recording or audio and video recording, you can call [prepare()](#prepare) and [getInputSurface()](#getinputsurface) again for re- recording.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400103](../errorcode-media.md#5400103-io-error) | IO error. Return by callback. |
| [5400105](../errorcode-media.md#5400105-play-service-dead) | Service died. Return by callback. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.reset((err: BusinessError) => {
  if (err) {
    console.error(`Failed to reset AVRecorder and error is: Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in resetting AVRecorder');
  }
});
```

<a id="reset-1"></a>

## reset

```TypeScript
reset(): Promise<void>
```

Resets audio and video recording. This API uses a promise to return the result.

For audio-only recording, you can call [prepare()](#prepare-1) again for re-recording. For video-only recording or audio and video recording, you can call [prepare()](#prepare-1) and [getInputSurface()](#getinputsurface) again for re-recording.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400103](../errorcode-media.md#5400103-io-error) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-play-service-dead) | Service died. Return by promise. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.reset().then(() => {
  console.info('Succeeded in resetting AVRecorder');
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to reset AVRecorder and error is: Code: ${error.code}, message: ${error.message}`);
});
```

## resume

```TypeScript
resume(callback: AsyncCallback<void>): void
```

Resumes video recording. This API uses an asynchronous callback to return the result.

This API can be called only after the [pause()](#pause) API is called.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operate not permit. Return by callback. |
| [5400103](../errorcode-media.md#5400103-io-error) | IO error. Return by callback. |
| [5400105](../errorcode-media.md#5400105-play-service-dead) | Service died. Return by callback. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.resume((err: BusinessError) => {
  if (err) {
    console.error(`Failed to resume AVRecorder and error is: Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in resuming AVRecorder');
  }
});
```

<a id="resume-1"></a>

## resume

```TypeScript
resume(): Promise<void>
```

Resumes video recording. This API uses a promise to return the result.

This API can be called only after the [pause()](#pause) API is called.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operate not permit. Return by promise. |
| [5400103](../errorcode-media.md#5400103-io-error) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-play-service-dead) | Service died. Return by promise. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.resume().then(() => {
  console.info('Succeeded in resuming AVRecorder');
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to resume AVRecorder and error is: Code: ${error.code}, message: ${error.message}`);
});
```

## setMetadata

```TypeScript
setMetadata(metadata: Record<string, string>): void
```

Set metadata (key-value pairs) for the recording file of the recorder. This metadata overwrites the value in config.metadata.customInfo (see {prepare()} and {AVRecorderConfig}) if they have same key.

This API can be called only after the prepare() event is successfully triggered and before the stop() API is called.

**Since:** 26.0.0

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| metadata | Record&lt;string, string&gt; | Yes | Tag and value of the metadata in key-value pairs.<br>- The first string is the key.<br>- The second string is the value. <br> The key string should start with "com.openharmony.", the length of value can't be more than 256 bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System App.<br>**Applicable version:** 19 - 24 |
| [5400101](../errorcode-media.md#5400101-memory-allocation-failed) | No memory.<br>**Applicable version:** 26.0.0 and later |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed.<br>**Applicable version:** 26.0.0 and later |
| [5400108](../errorcode-media.md#5400108-parameter-value-out-of-range) | Parameter check failed.<br>**Applicable version:** 26.0.0 and later |

**Examples**

```TypeScript
let metadata: Record<string, string> = {
  'com.openharmony.userdefine': '10',
  'com.openharmony.userdefine2': '20'
};

try {
  avRecorder.setMetadata(metadata);
  console.info('set metadata successfully');
} catch (err) {
  console.error(`set metadata failed with error: ${err.code}, ${err.message}`);
}
```

## setWillMuteWhenInterrupted

```TypeScript
setWillMuteWhenInterrupted(muteWhenInterrupted: boolean): Promise<void>
```

Sets whether to mute the current audio recording stream when an audio interruption occurs. This API uses a promise to return the result.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| muteWhenInterrupted | boolean | Yes | Whether to mute the current audio recording stream during an audio interruption. **true** to mute, **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Return by promise. |
| [5400105](../errorcode-media.md#5400105-play-service-dead) | Service died. Return by promise. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.setWillMuteWhenInterrupted(true).then(() => {
  console.info('Succeeded in doing setWillMuteWhenInterrupted');
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to do setWillMuteWhenInterrupted and error is: Code: ${error.code}, message: ${error.message}`);
});
```

## start

```TypeScript
start(callback: AsyncCallback<void>): void
```

Starts video recording. This API uses an asynchronous callback to return the result.

For audio-only recording, this API can be called only after the [prepare()](#prepare) API is called. For video-only recording, this API can be called only after the [getInputSurface()](#getinputsurface) API is called.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operate not permit. Return by callback. |
| [5400103](../errorcode-media.md#5400103-io-error) | IO error. Return by callback. |
| [5400105](../errorcode-media.md#5400105-play-service-dead) | Service died. Return by callback. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.start((err: BusinessError) => {
  if (err) {
    console.error(`Failed to start AVRecorder and error is: Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in starting AVRecorder');
  }
});
```

<a id="start-1"></a>

## start

```TypeScript
start(): Promise<void>
```

Starts video recording. This API uses a promise to return the result.

For audio-only recording, this API can be called only after the [prepare()](#prepare-1) API is called. For video-only recording, this API can be called only after the [getInputSurface()](#getinputsurface) API is called.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operate not permit. Return by promise. |
| [5400103](../errorcode-media.md#5400103-io-error) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-play-service-dead) | Service died. Return by promise. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.start().then(() => {
  console.info('Succeeded in starting AVRecorder');
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to start AVRecorder and error is: Code: ${error.code}, message: ${error.message}`);
});
```

## stop

```TypeScript
stop(callback: AsyncCallback<void>): void
```

Stops video recording. This API uses an asynchronous callback to return the result.

This API can be called only after the [start()](#start) or [pause()](#pause) API is called.

For audio-only recording, you can call [prepare()](#prepare) again for re -recording. For video-only recording or audio and video recording, you can call [prepare()](#prepare) and [getInputSurface()](#getinputsurface) again for re- recording.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operate not permit. Return by callback. |
| [5400103](../errorcode-media.md#5400103-io-error) | IO error. Return by callback. |
| [5400105](../errorcode-media.md#5400105-play-service-dead) | Service died. Return by callback. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.stop((err: BusinessError) => {
  if (err) {
    console.error(`Failed to stop AVRecorder and error is: Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Succeeded in stopping AVRecorder');
  }
});
```

<a id="stop-1"></a>

## stop

```TypeScript
stop(): Promise<void>
```

Stops video recording. This API uses a promise to return the result.

This API can be called only after the [start()](#start) or [pause()](#pause) API is called.

For audio-only recording, you can call [prepare()](#prepare-1) again for re-recording. For video-only recording or audio and video recording, you can call [prepare()](#prepare-1) and [getInputSurface()](#getinputsurface) again for re-recording.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operate not permit. Return by promise. |
| [5400103](../errorcode-media.md#5400103-io-error) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-play-service-dead) | Service died. Return by promise. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avRecorder.stop().then(() => {
  console.info('Succeeded in stopping AVRecorder');
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to stop AVRecorder and error is: Code: ${error.code}, message: ${error.message}`);
});
```

## updateRotation

```TypeScript
updateRotation(rotation: number): Promise<void>
```

Updates the video rotation angle, in degrees. This API uses a promise to return the result.

This API can be called only after the [prepare()](#prepare-1) event is triggered and before the [start()](#start) API is called.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Media.AVRecorder

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rotation | number | Yes | Rotation angle, which can only be 0, 90, 180, or 270 degrees. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
| [5400102](../errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. Return by promise. |
| [5400103](../errorcode-media.md#5400103-io-error) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-play-service-dead) | Service died. Return by promise. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let rotation = 90;

avRecorder.updateRotation(rotation).then(() => {
  console.info('Succeeded in doing updateRotation');
}).catch((err: Error) => {
  let error: BusinessError = err as BusinessError;
  console.error(`Failed to do updateRotation and error is: Code: ${error.code}, message: ${error.message}`);
});
```

## state

```TypeScript
readonly state: AVRecorderState
```

AVRecorder state.

**Type:** [AVRecorderState](arkts-media-media-avrecorderstate-t.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVRecorder
