# PreviewOutput

PreviewOutput implements preview output. It inherits from [CameraOutput](arkts-camera-camera-cameraoutput-i.md).

**Inheritance/Implementation:** PreviewOutput extends [CameraOutput](arkts-camera-camera-cameraoutput-i.md)

**Since:** 10

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## addDeferredSurface

```TypeScript
addDeferredSurface(surfaceId: string): void
```

Adds a surface for delayed preview. This API can run after [commitConfig](arkts-camera-camera-session-i.md#commitconfig) or [start](arkts-camera-camera-session-i.md#start) is called.

**Since:** 24

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| surfaceId | string | Yes | Surface ID, which is obtained from XComponent. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-invalid-parameter) | Parameter missing or parameter type incorrect. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 13 - 23 |

## enableBandwidthCompression

```TypeScript
enableBandwidthCompression(enabled: boolean): void
```

Enables preview bandwidth compression.

Before enabling this feature, you can call [isBandwidthCompressionSupported](#isbandwidthcompressionsupported) to check whether the device supports preview bandwidth compression.

> **NOTE:** 
> 
> This function must be called prior to
> [Session.commitConfig](arkts-camera-camera-session-i.md#commitconfig). Otherwise, the
> preview output stream format will be affected.

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether to enable preview bandwidth compression. **true** to enable, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-invalid-operation) | Operation not allowed. |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |

## getActiveFrameRate

```TypeScript
getActiveFrameRate(): FrameRateRange
```

Obtains the configured frame rate range.

This API is valid only after [setFrameRate](#setframerate) is called to set a frame rate range for preview streams.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| [FrameRateRange](arkts-camera-camera-frameraterange-i.md) | Frame rate range. |

## getActiveProfile

```TypeScript
getActiveProfile(): Profile
```

Obtains the profile that takes effect currently.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| [Profile](arkts-camera-camera-profile-i.md) | Profile obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |

## getPreviewRotation

```TypeScript
getPreviewRotation(displayRotation?: number): ImageRotation
```

Obtains the preview rotation angle.

- Device' natural orientation: the default orientation for using a device. For example, the default orientation  
of the bar-type phone is in portrait mode, with the charging port facing downward.  
- Camera lens angle: equivalent to the angle at which the camera is rotated clockwise to match the device's  
natural orientation. For example, the rear camera sensor of a bar-type phone is installed in landscape mode. Therefore, it needs to be rotated by 90 degrees clockwise to match the device's natural orientation. - [Screen Rotation](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-multi-device-window-direction): indicates the clockwise rotation angle of the device screen.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| displayRotation | number | No | Screen rotation angle of the display. It is obtained by calling [display.getDefaultDisplaySync](../../apis-arkui/arkts-apis/arkts-arkui-display-getdefaultdisplaysync-f.md). <br> Since API version 23, the input parameter **displayRotation** is optional. If no parameter is passed, the system obtains the **displayRotation** value to calculate rotation angle of a video. <br> The value ranges from 0 to 360, in degrees.<br>**Since:** 23 |

**Return value:**

| Type | Description |
| --- | --- |
| [ImageRotation](arkts-camera-camera-imagerotation-e.md) | The preview rotation angle obtained. If the API call fails, undefined is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-invalid-parameter) | Parameter missing or parameter type incorrect.<br>**Applicable version:** 12 - 22 |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |

## getSupportedFrameRates

```TypeScript
getSupportedFrameRates(): Array<FrameRateRange>
```

Obtains the supported frame rates.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[FrameRateRange](arkts-camera-camera-frameraterange-i.md)&gt; | Array of supported frame rates. If the API call fails, undefined is returned. |

## isBandwidthCompressionSupported

```TypeScript
isBandwidthCompressionSupported(): boolean
```

Checks whether preview bandwidth compression is supported. This involves reducing data volume through encoding to minimize bandwidth usage during transmission.

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for the support of preview bandwidth compression. **true** if supported, **false** otherwise. |

## isLogViewAssistSupported

```TypeScript
isLogViewAssistSupported(): boolean
```

Checks whether log video view assistance is supported.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for the support of log video view assistance. **true** if supported, **false** otherwise. |

## off('frameStart')

```TypeScript
off(type: 'frameStart', callback?: AsyncCallback<void>): void
```

Unsubscribes from preview frame start events.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'frameStart' | Yes | Event type. The value is fixed at **'frameStart'**. The event can be listened for when a previewOutput instance is created. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | No | Callback used to return the result. If this parameter is specified, the subscription to the specified event with the specified callback is canceled. (The callback object cannot be an anonymous function.) Otherwise, the subscriptions to the specified event with all the callbacks are canceled. |

## off('frameEnd')

```TypeScript
off(type: 'frameEnd', callback?: AsyncCallback<void>): void
```

Unsubscribes from preview frame end events.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'frameEnd' | Yes | Event type. The value is fixed at **'frameEnd'**. The event can be listened for when a previewOutput instance is created. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | No | Callback used to return the result. If this parameter is specified, the subscription to the specified event with the specified callback is canceled. (The callback object cannot be an anonymous function.) Otherwise, the subscriptions to the specified event with all the callbacks are canceled. |

## off('error')

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

Unsubscribes from PreviewOutput error events.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'error' | Yes | Event type. The value is fixed at **'error'**. The event can be listened for when a previewOutput instance is created. |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | No | Callback used to return the result. If this parameter is specified, the subscription to the specified event with the specified callback is canceled. (The callback object cannot be an anonymous function.) Otherwise, the subscriptions to the specified event with all the callbacks are canceled. |

## on('frameStart')

```TypeScript
on(type: 'frameStart', callback: AsyncCallback<void>): void
```

Subscribes to preview frame start events. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> Currently, you cannot use **off()** to unregister the callback in the callback method of **on()**.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'frameStart' | Yes | Event type. The value is fixed at **'frameStart'**. The event can be listened for when a previewOutput instance is created. This event is triggered and returned when the bottom layer starts exposure for the first time. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. The preview starts as long as this event is returned. |

## on('frameEnd')

```TypeScript
on(type: 'frameEnd', callback: AsyncCallback<void>): void
```

Subscribes to preview frame end events. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> Currently, you cannot use **off()** to unregister the callback in the callback method of **on()**.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'frameEnd' | Yes | Event type. The value is fixed at **'frameEnd'**. The event can be listened for when a previewOutput instance is created. This event is triggered and returned when the last frame of preview ends. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. The preview ends as long as this event is returned. |

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

Subscribes to PreviewOutput error events. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> Currently, you cannot use **off()** to unregister the callback in the callback method of **on()**.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'error' | Yes | Event type. The value is fixed at **'error'**. The event can be listened for when a previewOutput instance is created. This event is triggered and the corresponding error message is returned when an error occurs during the use of a preview-related API such as [Session.start](arkts-camera-camera-session-i.md#start) or [CameraOutput.release](arkts-camera-camera-cameraoutput-i.md#release). |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | Yes | Callback used to return an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md). |

## setFrameRate

```TypeScript
setFrameRate(minFps: number, maxFps: number): void
```

Sets a frame rate range for preview streams. The range must be within the supported frame rate range,

which can be obtained by calling [getSupportedFrameRates](#getsupportedframerates).

> **NOTE:** 
> 
> This API is valid only in [PhotoSession](arkts-camera-camera-photosession-i.md) or
> [VideoSession](arkts-camera-camera-videosession-i.md) mode.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| minFps | number | Yes | Minimum frame rate, in fps. When the maximum value is less than the minimum value, the API does not take effect. |
| maxFps | number | Yes | Maximum frame rate, in fps. When the minimum value is greater than the maximum value, the API does not take effect. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-invalid-parameter) | Parameter missing or parameter type incorrect. |
| [7400110](../errorcode-camera.md#7400110-configuration-conflicts) | Unresolved conflicts with current configurations. |

## setLogViewAssistEnable

```TypeScript
setLogViewAssistEnable(enable: boolean): void
```

Log video view assistance toggle. Before enabling this feature, you can call [isLogViewAssistSupported](#islogviewassistsupported) to check whether the device supports log video view assistance.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to enable log video view assistance, **true** to enable, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |

## setPreviewRotation

```TypeScript
setPreviewRotation(previewRotation: ImageRotation, isDisplayLocked?: boolean): void
```

Sets the preview rotation angle.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| previewRotation | [ImageRotation](arkts-camera-camera-imagerotation-e.md) | Yes | Preview rotation angle. |
| isDisplayLocked | boolean | No | Whether the orientation of the surface is locked when the screen rotates. If this parameter is not set, the default value **false** is used, indicating that the orientation is not locked. **true** if locked, **false** otherwise. For details, see [SurfaceRotationOptions](../../apis-arkui/arkts-components/arkts-arkui-surfacerotationoptions-i.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-invalid-parameter) | Parameter missing or parameter type incorrect. |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |

## start

```TypeScript
start(callback: AsyncCallback<void>): void
```

Starts to output preview streams. This API uses an asynchronous callback to return the result.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [start](arkts-camera-camera-session-i.md#start)(callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the preview stream output starts successfully, **err** is **undefined**; otherwise, **err** is an error object with an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

## start

```TypeScript
start(): Promise<void>
```

Starts to output preview streams. This API uses a promise to return the result.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [start](arkts-camera-camera-session-i.md#start)()

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

## stop

```TypeScript
stop(callback: AsyncCallback<void>): void
```

Stops outputting preview streams. This API uses an asynchronous callback to return the result.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [stop](arkts-camera-camera-session-i.md#stop)(callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the preview stream output stops successfully, **err** is **undefined**; otherwise, **err** is an error object. |

## stop

```TypeScript
stop(): Promise<void>
```

Stops outputting preview streams. This API uses a promise to return the result.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [stop](arkts-camera-camera-session-i.md#stop)()

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |
