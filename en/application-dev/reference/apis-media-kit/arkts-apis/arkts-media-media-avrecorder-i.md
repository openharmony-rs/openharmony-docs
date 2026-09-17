# AVRecorder

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

## state

```TypeScript
readonly state: AVRecorderState
```

AVRecorder state.

**Type:** [AVRecorderState](arkts-media-media-avrecorderstate-t.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Media.AVRecorder
