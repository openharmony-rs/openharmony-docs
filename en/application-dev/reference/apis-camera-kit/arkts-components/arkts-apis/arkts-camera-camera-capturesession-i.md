# CaptureSession

**CaptureSession** implements a capture session, which saves all [CameraInput](arkts-camera-camera-camerainput-i.md) and [CameraOutput](arkts-camera-camera-cameraoutput-i.md) instances required to run the camera and requests the camera to complete shooting or video recording.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [VideoSession](arkts-camera-camera-videosession-i.md)

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## addInput

```TypeScript
addInput(cameraInput: CameraInput): void
```

Adds a [CameraInput](arkts-camera-camera-camerainput-i.md) instance to this session.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [addInput](arkts-camera-camera-session-i.md#addinput)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cameraInput | [CameraInput](arkts-camera-camera-camerainput-i.md) | Yes | CameraInput instance to add. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-invalid-parameter) | Parameter missing or parameter type incorrect. |
| [7400102](../errorcode-camera.md#7400102-invalid-operation) | Operation not allowed. |

## addOutput

```TypeScript
addOutput(cameraOutput: CameraOutput): void
```

Adds a [CameraOutput](arkts-camera-camera-cameraoutput-i.md) instance to this session.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [addOutput](arkts-camera-camera-session-i.md#addoutput)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cameraOutput | [CameraOutput](arkts-camera-camera-cameraoutput-i.md) | Yes | CameraOutput instance to add. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-invalid-parameter) | Parameter missing or parameter type incorrect. |
| [7400102](../errorcode-camera.md#7400102-invalid-operation) | Operation not allowed. |

## beginConfig

```TypeScript
beginConfig(): void
```

Starts configuration for the session.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [beginConfig](arkts-camera-camera-session-i.md#beginconfig)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400105](../errorcode-camera.md#7400105-session-configuration-locked) | Session config locked. |

## commitConfig

```TypeScript
commitConfig(callback: AsyncCallback<void>): void
```

Commits the configuration for this session. This API uses an asynchronous callback to return the result.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [commitConfig](arkts-camera-camera-session-i.md#commitconfig)(callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the configuration is successfully committed, **err** is **undefined**; otherwise, **err** is an error object with an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-invalid-operation) | Operation not allowed. |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |

## commitConfig

```TypeScript
commitConfig(): Promise<void>
```

Commits the configuration for this session. This API uses a promise to return the result.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [commitConfig](arkts-camera-camera-session-i.md#commitconfig)()

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-invalid-operation) | Operation not allowed. |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |

## getActiveVideoStabilizationMode

```TypeScript
getActiveVideoStabilizationMode(): VideoStabilizationMode
```

Obtains the video stabilization mode in use.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [getActiveVideoStabilizationMode](arkts-camera-camera-stabilization-i.md#getactivevideostabilizationmode)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| [VideoStabilizationMode](arkts-camera-camera-videostabilizationmode-e.md) | Video stabilization mode obtained. If the operation fails, an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

## getExposureBiasRange

```TypeScript
getExposureBiasRange(): Array<number>
```

Obtains the exposure compensation values of the camera device.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [getExposureBiasRange](arkts-camera-camera-autoexposurequery-i.md#getexposurebiasrange)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;number&gt; | Array of compensation values. If the operation fails, an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

## getExposureMode

```TypeScript
getExposureMode(): ExposureMode
```

Obtains the exposure mode in use.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [getExposureMode](arkts-camera-camera-autoexposure-i.md#getexposuremode)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| [ExposureMode](arkts-camera-camera-exposuremode-e.md) | Exposure mode obtained. If the operation fails, an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

## getExposureValue

```TypeScript
getExposureValue(): number
```

Obtains the exposure value in use.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [getExposureValue](arkts-camera-camera-autoexposure-i.md#getexposurevalue)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Exposure value obtained. There is a step for EV. For example, if the step is 0.5 and this parameter is set to 1.2, the EV that takes effect is 1.0. If the operation fails, an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

## getFlashMode

```TypeScript
getFlashMode(): FlashMode
```

Obtains the flash mode in use.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [getFlashMode](arkts-camera-camera-flash-i.md#getflashmode)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| [FlashMode](arkts-camera-camera-flashmode-e.md) | Flash mode obtained. If the operation fails, an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

## getFocalLength

```TypeScript
getFocalLength(): number
```

Obtains the focal length of the camera device.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [getFocalLength](arkts-camera-camera-focus-i.md#getfocallength)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Focal length obtained. If the operation fails, an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

## getFocusMode

```TypeScript
getFocusMode(): FocusMode
```

Obtains the focus mode in use.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [getFocusMode](arkts-camera-camera-focus-i.md#getfocusmode)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| [FocusMode](arkts-camera-camera-focusmode-e.md) | Focus mode obtained. If the operation fails, an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

## getFocusPoint

```TypeScript
getFocusPoint(): Point
```

Obtains the focal point of the camera device.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [getFocusPoint](arkts-camera-camera-focus-i.md#getfocuspoint)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| [Point](arkts-camera-camera-point-i.md) | Focal point obtained. If the operation fails, an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

## getMeteringPoint

```TypeScript
getMeteringPoint(): Point
```

Obtains the metering point of the camera device.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [getMeteringPoint](arkts-camera-camera-autoexposure-i.md#getmeteringpoint)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| [Point](arkts-camera-camera-point-i.md) | Metering point obtained. If the operation fails, an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

## getZoomRatio

```TypeScript
getZoomRatio(): number
```

Obtains the zoom ratio in use.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [getZoomRatio](arkts-camera-camera-zoom-i.md#getzoomratio)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Zoom ratio obtained. If the operation fails, an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

## getZoomRatioRange

```TypeScript
getZoomRatioRange(): Array<number>
```

Obtains the supported zoom ratio range.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [getZoomRatioRange](arkts-camera-camera-zoomquery-i.md#getzoomratiorange)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;number&gt; | Array containing the minimum and maximum zoom ratios. If the operation fails, an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

## hasFlash

```TypeScript
hasFlash(): boolean
```

Checks whether the camera device has flash.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [hasFlash](arkts-camera-camera-flashquery-i.md#hasflash)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for whether the camera device has flash. **true** if it has flash, **false** otherwise. If the operation fails, an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

## isExposureModeSupported

```TypeScript
isExposureModeSupported(aeMode: ExposureMode): boolean
```

Checks whether an exposure mode is supported.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [isExposureModeSupported](arkts-camera-camera-autoexposurequery-i.md#isexposuremodesupported)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| aeMode | [ExposureMode](arkts-camera-camera-exposuremode-e.md) | Yes | Exposure mode. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for the support of the exposure mode. **true** if supported, **false** otherwise. If the operation fails, an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

## isFlashModeSupported

```TypeScript
isFlashModeSupported(flashMode: FlashMode): boolean
```

Checks whether the flash mode is supported.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [isFlashModeSupported](arkts-camera-camera-flashquery-i.md#isflashmodesupported)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| flashMode | [FlashMode](arkts-camera-camera-flashmode-e.md) | Yes | Flash mode. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for the support of the flash mode. **true** if supported, **false** otherwise. If the operation fails, an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

## isFocusModeSupported

```TypeScript
isFocusModeSupported(afMode: FocusMode): boolean
```

Checks whether a focus mode is supported.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [isFocusModeSupported](arkts-camera-camera-focusquery-i.md#isfocusmodesupported)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| afMode | [FocusMode](arkts-camera-camera-focusmode-e.md) | Yes | Focus mode. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for the support of the focus mode. **true** if supported, **false** otherwise. If the operation fails, an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

## isVideoStabilizationModeSupported

```TypeScript
isVideoStabilizationModeSupported(vsMode: VideoStabilizationMode): boolean
```

Checks whether a video stabilization mode is supported.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [isVideoStabilizationModeSupported](arkts-camera-camera-stabilizationquery-i.md#isvideostabilizationmodesupported)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| vsMode | [VideoStabilizationMode](arkts-camera-camera-videostabilizationmode-e.md) | Yes | Video stabilization mode. If the input parameter is null or undefined, it is treated as 0 and video stabilization is disabled. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for the support of the video stabilization mode. **true** if supported, **false** otherwise. If the operation fails, an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

## off('focusStateChange')

```TypeScript
off(type: 'focusStateChange', callback?: AsyncCallback<FocusState>): void
```

Unsubscribes from focus state change events.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [off](arkts-camera-camera-videosession-i.md#offfocusstatechange)(type: 'focusStateChange', callback?: AsyncCallback&lt;FocusState&gt;)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'focusStateChange' | Yes | Event type. The value is fixed at **'focusStateChange'**. The event can be listened for when a session is created. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FocusState](arkts-camera-camera-focusstate-e.md)&gt; | No | Callback used to return the result. If this parameter is specified, the subscription to the specified event with the specified callback is canceled. (The callback object cannot be an anonymous function.) Otherwise, the subscriptions to the specified event with all the callbacks are canceled. |

## off('error')

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

Unsubscribes from CaptureSession error events. This API uses a callback to return the result.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [off](arkts-camera-camera-videosession-i.md#offerror)(type: 'error', callback?: ErrorCallback)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'error' | Yes | Event type. The value is fixed at **'error'**. The event can be listened for when a session is created. |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | No | Callback used to return the result. If this parameter is specified, the subscription to the specified event with the specified callback is canceled. (The callback object cannot be an anonymous function.) Otherwise, the subscriptions to the specified event with all the callbacks are canceled. |

## on('focusStateChange')

```TypeScript
on(type: 'focusStateChange', callback: AsyncCallback<FocusState>): void
```

Subscribes to focus state change events. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> Currently, you cannot use **off()** to unregister the callback in the callback method of **on()**.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [on](arkts-camera-camera-videosession-i.md#onfocusstatechange)(type: 'focusStateChange', callback: AsyncCallback&lt;FocusState&gt;)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'focusStateChange' | Yes | Event type. The value is fixed at **'focusStateChange'**. The event can be listened for when a session is created. This event is triggered only when the camera focus state changes in auto focus mode. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FocusState](arkts-camera-camera-focusstate-e.md)&gt; | Yes | Callback used to return the focus state change. |

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

Subscribes to CaptureSession error events. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> Currently, you cannot use **off()** to unregister the callback in the callback method of **on()**.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [on](arkts-camera-camera-videosession-i.md#onerror)(type: 'error', callback: ErrorCallback)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'error' | Yes | Event type. The value is fixed at **'error'**. The event can be listened for when a session is created. This event is triggered and the error message is returned when an error occurs during the calling of a session-related API such as [beginConfig](#beginconfig), [commitConfig](#commitconfig), and [addInput](#addinput). |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | Yes | Callback used to return an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md). |

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

Releases this session. This API uses an asynchronous callback to return the result.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [release](arkts-camera-camera-session-i.md#release)(callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the session is released successfully, **err** is **undefined**; otherwise, **err** is an error object with an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |

## release

```TypeScript
release(): Promise<void>
```

Releases this session. This API uses a promise to return the result.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [release](arkts-camera-camera-session-i.md#release)()

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |

## removeInput

```TypeScript
removeInput(cameraInput: CameraInput): void
```

Removes a [CameraInput](arkts-camera-camera-camerainput-i.md) instance from this session.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [removeInput](arkts-camera-camera-session-i.md#removeinput)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cameraInput | [CameraInput](arkts-camera-camera-camerainput-i.md) | Yes | CameraInput instance to remove. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-invalid-parameter) | Parameter missing or parameter type incorrect. |
| [7400102](../errorcode-camera.md#7400102-invalid-operation) | Operation not allowed. |

## removeOutput

```TypeScript
removeOutput(cameraOutput: CameraOutput): void
```

Removes a [CameraOutput](arkts-camera-camera-cameraoutput-i.md) instance from this session.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [removeOutput](arkts-camera-camera-session-i.md#removeoutput)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cameraOutput | [CameraOutput](arkts-camera-camera-cameraoutput-i.md) | Yes | CameraOutput instance to remove. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-invalid-parameter) | Parameter missing or parameter type incorrect. |
| [7400102](../errorcode-camera.md#7400102-invalid-operation) | Operation not allowed. |

## setExposureBias

```TypeScript
setExposureBias(exposureBias: number): void
```

Sets an exposure compensation value (EV).

Before the setting, you are advised to use [getExposureBiasRange](#getexposurebiasrange) to obtain the supported values.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [setExposureBias](arkts-camera-camera-autoexposure-i.md#setexposurebias)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| exposureBias | number | Yes | EV. The supported EV range can be obtained by calling [getExposureBiasRange](arkts-camera-camera-autoexposurequery-i.md#getexposurebiasrange). If the value passed is not within the supported range, the nearest critical point is used. There is a step for EV. For example, if the step is 0.5 and this parameter is set to 1.2, the EV that takes effect is 1.0. If the operation fails, an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is returned. If the input parameter is null or undefined, the EV is set to 0. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

## setExposureMode

```TypeScript
setExposureMode(aeMode: ExposureMode): void
```

Sets an exposure mode. Before the setting, call [isExposureModeSupported](#isexposuremodesupported) to check whether the target exposure mode is supported.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [setExposureMode](arkts-camera-camera-autoexposure-i.md#setexposuremode)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| aeMode | [ExposureMode](arkts-camera-camera-exposuremode-e.md) | Yes | Exposure mode. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

## setFlashMode

```TypeScript
setFlashMode(flashMode: FlashMode): void
```

Sets a flash mode.

Before the setting, do the following checks:

1. Use [hasFlash](#hasflash) to check whether the camera device has flash.
2. Use [isFlashModeSupported](#isflashmodesupported) to check whether the camera device supports the flash mode.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [setFlashMode](arkts-camera-camera-flash-i.md#setflashmode)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| flashMode | [FlashMode](arkts-camera-camera-flashmode-e.md) | Yes | Flash mode. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

## setFocusMode

```TypeScript
setFocusMode(afMode: FocusMode): void
```

Sets a focus mode.

Before the setting, call [isFocusModeSupported](#isfocusmodesupported) to check whether the focus mode is supported.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [setFocusMode](arkts-camera-camera-focus-i.md#setfocusmode)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| afMode | [FocusMode](arkts-camera-camera-focusmode-e.md) | Yes | Focus mode. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

## setFocusPoint

```TypeScript
setFocusPoint(point: Point): void
```

Sets the focal point. The focal point must be in the coordinate system (0-1), where the top-left corner is {0, 0} and the bottom-right corner is {1, 1}.

The coordinate system is based on the horizontal device direction with the device's charging port on the right. If the layout of the preview screen of an application is based on the vertical direction with the charging port on the lower side, the layout width and height are {w, h}, and the touch point is {x, y}, then the coordinate point after conversion is {y/h, 1-x/w}.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [setFocusPoint](arkts-camera-camera-focus-i.md#setfocuspoint)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| point | [Point](arkts-camera-camera-point-i.md) | Yes | Focal point. The value range of x and y must be within [0,1]. If a value less than 0 is passed, the value **0** is used. If a value greater than **1** is passed, the value **1** is used. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

## setMeteringPoint

```TypeScript
setMeteringPoint(point: Point): void
```

Sets the metering point, which is the center point of the metering rectangle. The metering point must be in the coordinate system (0-1), where the top-left corner is {0, 0} and the bottom-right corner is {1, 1}.

The coordinate system is based on the horizontal device direction with the device's charging port on the right. If the layout of the preview screen of an application is based on the vertical direction with the charging port on the lower side, the layout width and height are {w, h}, and the touch point is {x, y}, then the coordinate point after conversion is {y/h, 1-x/w}.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [setMeteringPoint](arkts-camera-camera-autoexposure-i.md#setmeteringpoint)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| point | [Point](arkts-camera-camera-point-i.md) | Yes | Metering point. The value range of x and y must be within [0,1]. If a value less than 0 is passed, the value **0** is used. If a value greater than **1** is passed, the value **1** is used. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

## setVideoStabilizationMode

```TypeScript
setVideoStabilizationMode(mode: VideoStabilizationMode): void
```

Sets a video stabilization mode. Before the setting, call [isVideoStabilizationModeSupported](#isvideostabilizationmodesupported) to check whether the target video stabilization mode is supported.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [setVideoStabilizationMode](arkts-camera-camera-stabilization-i.md#setvideostabilizationmode)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [VideoStabilizationMode](arkts-camera-camera-videostabilizationmode-e.md) | Yes | Video stabilization mode. If the input parameter is null or undefined, it is treated as 0 and video stabilization is disabled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

## setZoomRatio

```TypeScript
setZoomRatio(zoomRatio: number): void
```

Sets a zoom ratio, with a maximum precision of two decimal places.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [setZoomRatio](arkts-camera-camera-zoom-i.md#setzoomratio)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| zoomRatio | number | Yes | Zoom ratio. The supported zoom ratio range can be obtained by calling [getZoomRatioRange](arkts-camera-camera-zoomquery-i.md#getzoomratiorange). If the value passed in is not within the supported range, the value within the precision range is retained. If the input parameter is null or undefined, it is treated as 0 and the minimum zoom ratio is used. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |

## start

```TypeScript
start(callback: AsyncCallback<void>): void
```

Starts this session. This API uses an asynchronous callback to return the result.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [start](arkts-camera-camera-session-i.md#start)(callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the session starts successfully, **err** is **undefined**; otherwise, **err** is an error object with an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |

## start

```TypeScript
start(): Promise<void>
```

Starts this session. This API uses a promise to return the result.

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
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |

## stop

```TypeScript
stop(callback: AsyncCallback<void>): void
```

Stops this session. This API uses an asynchronous callback to return the result.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [stop](arkts-camera-camera-session-i.md#stop)(callback: AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the session stops successfully, **err** is **undefined**; otherwise, **err** is an error object with an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |

## stop

```TypeScript
stop(): Promise<void>
```

Stops this session. This API uses a promise to return the result.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [stop](arkts-camera-camera-session-i.md#stop)()

**System capability:** SystemCapability.Multimedia.Camera.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |
