# VideoSession

VideoSession inherits from [Session](arkts-camera-camera-session-i.md), [Flash](arkts-camera-camera-flash-i.md), [AutoExposure](arkts-camera-camera-autoexposure-i.md), [WhiteBalance](arkts-camera-camera-whitebalance-i.md), [Focus](arkts-camera-camera-focus-i.md), [Zoom](arkts-camera-camera-zoom-i.md), [Stabilization](arkts-camera-camera-stabilization-i.md), [ColorManagement](arkts-camera-camera-colormanagement-i.md), [AutoDeviceSwitch](arkts-camera-camera-autodeviceswitch-i.md), [Macro](arkts-camera-camera-macro-i.md), [ControlCenter](arkts-camera-camera-controlcenter-i.md), [ManualExposure](arkts-camera-camera-manualexposure-i.md), [ManualFocus](arkts-camera-camera-manualfocus-i.md), [ManualIso](arkts-camera-camera-manualiso-i.md), [OIS](arkts-camera-camera-ois-i.md), and [Aperture](arkts-camera-camera-aperture-i.md).

It implements a video session, which provides operations on the flash, exposure, white balance, focus, zoom, video stabilization, color space, macro mode and controller, manual exposure, manual focus, manual ISO, optical image stabilization, and aperture.

**VideoSession** is provided for the default video recording mode. It applies to common scenarios. It supports recording at various resolutions (such as 720p and 1080p) and frame rates (such as 30 fps and 60 fps).

@extends Session, Flash, AutoExposure, Focus, Zoom, Stabilization, ColorManagement [since 11 - 12] @extends AutoDeviceSwitch [since 13 - 18] @extends Session, Flash, AutoExposure, Focus, Zoom, Stabilization, ColorManagement, AutoDeviceSwitch, Macro [since 19 - 19] @extends Session, Flash, AutoExposure, WhiteBalance, Focus, Zoom, Stabilization, ColorManagement, ControlCenter, AutoDeviceSwitch, Macro [since 20 - 24] @extends Session, Flash, AutoExposure, WhiteBalance, Focus, Zoom, Stabilization, ColorManagement, ControlCenter, AutoDeviceSwitch, Macro, ManualExposure, ManualFocus, ManualIso, OIS, Aperture [since 26.0.0] @extends Session, Flash, AutoExposure, WhiteBalance, Focus, Zoom, Stabilization, ColorManagement, ControlCenter, AutoDeviceSwitch, Macro, ManualExposure, ManualFocus, ManualIso, OIS, Aperture, ColorControls [since 26.1.0]

**Inheritance/Implementation:** VideoSession extends [Session](arkts-camera-camera-session-i.md), [Flash](arkts-camera-camera-flash-i.md), [AutoExposure](arkts-camera-camera-autoexposure-i.md), [WhiteBalance](arkts-camera-camera-whitebalance-i.md), [Focus](arkts-camera-camera-focus-i.md), [Zoom](arkts-camera-camera-zoom-i.md), [Stabilization](arkts-camera-camera-stabilization-i.md), [ColorManagement](arkts-camera-camera-colormanagement-i.md), [ControlCenter](arkts-camera-camera-controlcenter-i.md), [AutoDeviceSwitch](arkts-camera-camera-autodeviceswitch-i.md), [Macro](arkts-camera-camera-macro-i.md), [ManualExposure](arkts-camera-camera-manualexposure-i.md), [ManualFocus](arkts-camera-camera-manualfocus-i.md), [ManualIso](arkts-camera-camera-manualiso-i.md), [OIS](arkts-camera-camera-ois-i.md), [Aperture](arkts-camera-camera-aperture-i.md)<!--Del-->, [ColorControls](arkts-camera-camera-colorcontrols-i-sys.md)<!--DelEnd-->

**Since:** 11

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## canPreconfig

```TypeScript
canPreconfig(preconfigType: PreconfigType, preconfigRatio?: PreconfigRatio): boolean
```

Checks whether this session supports a preconfigured resolution.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| preconfigType | [PreconfigType](arkts-camera-camera-preconfigtype-e.md) | Yes | Resolution type. |
| preconfigRatio | [PreconfigRatio](arkts-camera-camera-preconfigratio-e.md) | No | Aspect ratio. The default value is 16:9. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | **true**: The preconfigured resolution is supported.<br>**false**: The preconfigured resolution is not supported. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |

## off('error')

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

Unsubscribes from **VideoSession** error events. This API uses a callback to return the result.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'error' | Yes | Event type. The value is fixed at **'error'**. The event can be listened for when a session is created. |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | No | Callback used to return the result. If this parameter is specified, the subscription to the specified event with the specified callback is canceled. (The callback object cannot be an anonymous function.) Otherwise, the subscriptions to the specified event with all the callbacks are canceled. |

## off('focusStateChange')

```TypeScript
off(type: 'focusStateChange', callback?: AsyncCallback<FocusState>): void
```

Unsubscribes from focus state change events.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'focusStateChange' | Yes | Event type. The value is fixed at **'focusStateChange'**. The event can be listened for when a session is created. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FocusState](arkts-camera-camera-focusstate-e.md)&gt; | No | Callback used to return the result. If this parameter is specified, the subscription to the specified event with the specified callback is canceled. (The callback object cannot be an anonymous function.) Otherwise, the subscriptions to the specified event with all the callbacks are canceled. |

## off('smoothZoomInfoAvailable')

```TypeScript
off(type: 'smoothZoomInfoAvailable', callback?: AsyncCallback<SmoothZoomInfo>): void
```

Unsubscribes from smooth zoom state change events.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'smoothZoomInfoAvailable' | Yes | Event type. The value is fixed at **'smoothZoomInfoAvailable'**. The event can be listened for when a session is created. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[SmoothZoomInfo](arkts-camera-camera-smoothzoominfo-i.md)&gt; | No | Callback used to return the result. If this parameter is specified, the subscription to the specified event with the specified callback is canceled. (The callback object cannot be an anonymous function.) Otherwise, the subscriptions to the specified event with all the callbacks are canceled. |

## off('controlCenterEffectStatusChange')

```TypeScript
off(type: 'controlCenterEffectStatusChange', callback?: AsyncCallback<ControlCenterStatusInfo>): void
```

Unsubscribes from events indicating that the camera controller effect status changes.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'controlCenterEffectStatusChange' | Yes | Event type. The value is fixed at **'controlCenterEffectStatusChange'**. The event can be listened for when a session is created. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ControlCenterStatusInfo](arkts-camera-camera-controlcenterstatusinfo-i.md)&gt; | No | Callback used to return the result. If this parameter is specified, the subscription to the specified event with the specified callback is canceled. (The callback object cannot be an anonymous function.) Otherwise, the subscriptions to the specified event with all the callbacks are canceled. |

## off('macroStatusChanged')

```TypeScript
off(type: 'macroStatusChanged', callback?: AsyncCallback<boolean>): void
```

Unsubscribes from macro state change events.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'macroStatusChanged' | Yes | Event type. The value is fixed at **'macroStatusChanged'**. The event can be listened for when a session is created. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | No | Callback used to return the result. If this parameter is specified, the subscription to the specified event with the specified callback is canceled. (The callback object cannot be an anonymous function.) Otherwise, the subscriptions to the specified event with all the callbacks are canceled. If **true** is returned, the unsubscription is successful. If **false** is returned, the unsubscription fails. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application.<br>**Applicable version:** 11 - 19 |

## off('autoDeviceSwitchStatusChange')

```TypeScript
off(type: 'autoDeviceSwitchStatusChange', callback?: AsyncCallback<AutoDeviceSwitchStatus>): void
```

Unsubscribes from automatic camera switch status change events.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'autoDeviceSwitchStatusChange' | Yes | Event type. The value is fixed at **'autoDeviceSwitchStatusChange'**. The event can be listened for when a session is created. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AutoDeviceSwitchStatus](arkts-camera-camera-autodeviceswitchstatus-i.md)&gt; | No | Callback used to return the result. If this parameter is specified, the subscription to the specified event with the specified callback is canceled. (The callback object cannot be an anonymous function.) Otherwise, the subscriptions to the specified event with all the callbacks are canceled. |

## off('systemPressureLevelChange')

```TypeScript
off(type: 'systemPressureLevelChange', callback?: AsyncCallback<SystemPressureLevel>): void
```

Unsubscribes from system pressure level change events.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'systemPressureLevelChange' | Yes | Event type. The value is fixed at **'systemPressureLevelChange'**. The event can be listened for when a session is created. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[SystemPressureLevel](arkts-camera-camera-systempressurelevel-e.md)&gt; | No | Callback used to return the result. If this parameter is specified, the subscription to the specified event with the specified callback is canceled. (The callback object cannot be an anonymous function.) Otherwise, the subscriptions to the specified event with all the callbacks are canceled. |

## offExposureInfoChange

```TypeScript
offExposureInfoChange(callback?: Callback<ExposureInfo>): void
```

Unsubscribes from exposure information change events. If you have subscribed to exposure information, cancel the subscription before releasing the camera. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ExposureInfo](arkts-camera-camera-exposureinfo-i.md)&gt; | No | Callback used to return the result. If this parameter is specified, the subscription to the specified event with the specified callback is canceled. (The callback object cannot be an anonymous function.) Otherwise, the subscriptions to the specified event with all the callbacks are canceled. |

## offIsoInfoChange

```TypeScript
offIsoInfoChange(callback?: Callback<IsoInfo>): void
```

Unsubscribes from ISO state change events.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[IsoInfo](arkts-camera-camera-isoinfo-i.md)&gt; | No | Callback used for unsubscription.<br>If this parameter is specified, the subscription to the specified event with the specified callback is canceled. (The callback object cannot be an anonymous function.) <br>Otherwise, the subscriptions to the specified event with all the callbacks are canceled. |

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

Subscribes to **VideoSession** error events. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> Currently, you cannot use **off()** to unregister the callback in the callback method of **on()**.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'error' | Yes | Event type. The value is fixed at **'error'**. The event can be listened for when a session is created. This event is triggered and the error message is returned when an error occurs during the calling of a session-related API such as [beginConfig](arkts-camera-camera-session-i.md#beginconfig), [commitConfig](arkts-camera-camera-session-i.md#commitconfig), and [addInput](arkts-camera-camera-session-i.md#addinput). |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | Yes | Callback used to return an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md). |

## on('focusStateChange')

```TypeScript
on(type: 'focusStateChange', callback: AsyncCallback<FocusState>): void
```

Subscribes to focus state change events. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> Currently, you cannot use **off()** to unregister the callback in the callback method of **on()**.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'focusStateChange' | Yes | Event type. The value is fixed at **'focusStateChange'**. The event can be listened for when a session is created. This event is triggered only when the camera focus state changes in auto focus mode. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FocusState](arkts-camera-camera-focusstate-e.md)&gt; | Yes | Callback used to return the focus state change. |

## on('smoothZoomInfoAvailable')

```TypeScript
on(type: 'smoothZoomInfoAvailable', callback: AsyncCallback<SmoothZoomInfo>): void
```

Subscribes to smooth zoom state change events. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> Currently, you cannot use **off()** to unregister the callback in the callback method of **on()**.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'smoothZoomInfoAvailable' | Yes | Event type. The value is fixed at **'smoothZoomInfoAvailable'**. The event can be listened for when a session is created. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[SmoothZoomInfo](arkts-camera-camera-smoothzoominfo-i.md)&gt; | Yes | Callback used to return the smooth zoom state change. |

## on('controlCenterEffectStatusChange')

```TypeScript
on(type: 'controlCenterEffectStatusChange', callback: AsyncCallback<ControlCenterStatusInfo>): void
```

Subscribes to events indicating that the camera controller effect status changes. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> Currently, you cannot use **off()** to unregister the callback in the callback method of **on()**.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'controlCenterEffectStatusChange' | Yes | Event type. The value is fixed at **'controlCenterEffectStatusChange'**. The event can be listened for when a session is created. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ControlCenterStatusInfo](arkts-camera-camera-controlcenterstatusinfo-i.md)&gt; | Yes | Callback used to return the effect status of the current controller. |

## on('macroStatusChanged')

```TypeScript
on(type: 'macroStatusChanged', callback: AsyncCallback<boolean>): void
```

Subscribes to macro state change events. This API uses an asynchronous callback to return the result.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'macroStatusChanged' | Yes | Event type. The value is fixed at **'macroStatusChanged'**. The event can be listened for when a session is created. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the macro state. **true** if enabled, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application.<br>**Applicable version:** 11 - 19 |

## on('autoDeviceSwitchStatusChange')

```TypeScript
on(type: 'autoDeviceSwitchStatusChange', callback: AsyncCallback<AutoDeviceSwitchStatus>): void
```

Subscribes to automatic camera switch status change events. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> Currently, you cannot use **off()** to unregister the callback in the callback method of **on()**.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'autoDeviceSwitchStatusChange' | Yes | Event type. The value is fixed at **'autoDeviceSwitchStatusChange'**. The event can be listened for when a session is created. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AutoDeviceSwitchStatus](arkts-camera-camera-autodeviceswitchstatus-i.md)&gt; | Yes | Callback used to obtain the status of automatic camera switch. |

## on('systemPressureLevelChange')

```TypeScript
on(type: 'systemPressureLevelChange', callback: AsyncCallback<SystemPressureLevel>): void
```

Subscribes to system pressure level change events. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> Currently, you cannot use **off()** to unregister the callback in the callback method of **on()**.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'systemPressureLevelChange' | Yes | Event type. The value is fixed at **'systemPressureLevelChange'**. The event can be listened for when a session is created. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[SystemPressureLevel](arkts-camera-camera-systempressurelevel-e.md)&gt; | Yes | Callback used to return the current system pressure level. |

## onExposureInfoChange

```TypeScript
onExposureInfoChange(callback: Callback<ExposureInfo>): void
```

Subscribes to exposure information change events. After the exposure parameters are changed, the system returns the updated exposure information. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ExposureInfo](arkts-camera-camera-exposureinfo-i.md)&gt; | Yes | Callback used to obtain the exposure information. |

## onIsoInfoChange

```TypeScript
onIsoInfoChange(callback: Callback<IsoInfo>): void
```

Subscribes to sensitivity (ISO) state change events and obtains the latest ISO value through a callback.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[IsoInfo](arkts-camera-camera-isoinfo-i.md)&gt; | Yes | Callback used to obtain the current ISO value of the camera. |

## preconfig

```TypeScript
preconfig(preconfigType: PreconfigType, preconfigRatio?: PreconfigRatio): void
```

Preconfigures this session.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| preconfigType | [PreconfigType](arkts-camera-camera-preconfigtype-e.md) | Yes | Resolution type. |
| preconfigRatio | [PreconfigRatio](arkts-camera-camera-preconfigratio-e.md) | No | Aspect ratio. The default value is 16:9. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |

## setQualityPrioritization

```TypeScript
setQualityPrioritization(quality: QualityPrioritization): void
```

Sets the priority level for video recording quality.

> **NOTE:** 
> 
> - The default value is **HIGH_QUALITY**. Switching to **POWER_BALANCE** will compromise video recording quality to achieve lower power usage. The extent of power conservation achieved varies depending on the platform.
> 
> - It is recommended that this API be called between [commitConfig](arkts-camera-camera-session-i.md#commitconfig) and [start](arkts-camera-camera-session-i.md#start).

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| quality | [QualityPrioritization](arkts-camera-camera-qualityprioritization-e.md) | Yes | Priority level to set. The default value is **HIGH_QUALITY**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [7400103](../errorcode-camera.md#7400103-session-not-configured) | Session not config. The session has not been committed or configured. |
