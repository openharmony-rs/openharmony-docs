# PhotoSession

```TypeScript
interface PhotoSession extends Session, Flash, AutoExposure, WhiteBalance, Focus, Zoom, ColorManagement,
      AutoDeviceSwitch, Macro, ManualExposure, ManualFocus, ManualIso, OIS, Aperture
```

**PhotoSession** inherits from [Session](arkts-camera-camera-session-i.md), [Flash](arkts-camera-camera-flash-i.md), [AutoExposure](arkts-camera-camera-autoexposure-i.md), [WhiteBalance](arkts-camera-camera-whitebalance-i.md), [Focus](arkts-camera-camera-focus-i.md), [Zoom](arkts-camera-camera-zoom-i.md), [ColorManagement](arkts-camera-camera-colormanagement-i.md), [AutoDeviceSwitch](arkts-camera-camera-autodeviceswitch-i.md), [Macro](arkts-camera-camera-macro-i.md), [ManualExposure](arkts-camera-camera-manualexposure-i.md), [ManualFocus](arkts-camera-camera-manualfocus-i.md), [ManualIso](arkts-camera-camera-manualiso-i.md), [OIS](arkts-camera-camera-ois-i.md), and [Aperture](arkts-camera-camera-aperture-i.md).

It implements a photo session, which provides operations on the flash, exposure, white balance, focus, zoom, color space, macro mode, manual exposure, manual focus, manual ISO setting, optical image stabilization (OIS), and aperture.

**PhotoSession** is provided for the default photo mode. It is used to take standard photos. It supports multiple photo formats and resolutions, which are suitable for most daily photo capture scenarios.

@extends Session, Flash, AutoExposure, Focus, Zoom, ColorManagement [since 11 - 12] @extends Session, Flash, AutoExposure, Focus, Zoom, ColorManagement, AutoDeviceSwitch [since 13 - 18] @extends Session, Flash, AutoExposure, Focus, Zoom, ColorManagement, AutoDeviceSwitch, Macro [since 19 - 19] @extends Session, Flash, AutoExposure, WhiteBalance, Focus, Zoom, ColorManagement, AutoDeviceSwitch, Macro [since 20 - 23] @extends Session, Flash, AutoExposure, WhiteBalance, Focus, Zoom, ColorManagement, AutoDeviceSwitch, Macro, ManualExposure, ManualFocus, ManualIso, OIS, Aperture [since 24]

**Inheritance/Implementation:** PhotoSession extends [Session](arkts-camera-camera-session-i.md), [Flash](arkts-camera-camera-flash-i.md), [AutoExposure](arkts-camera-camera-autoexposure-i.md), [WhiteBalance](arkts-camera-camera-whitebalance-i.md), [Focus](arkts-camera-camera-focus-i.md), [Zoom](arkts-camera-camera-zoom-i.md), [ColorManagement](arkts-camera-camera-colormanagement-i.md), [AutoDeviceSwitch](arkts-camera-camera-autodeviceswitch-i.md), [Macro](arkts-camera-camera-macro-i.md), [ManualExposure](arkts-camera-camera-manualexposure-i.md), [ManualFocus](arkts-camera-camera-manualfocus-i.md), [ManualIso](arkts-camera-camera-manualiso-i.md), [OIS](arkts-camera-camera-ois-i.md), [Aperture](arkts-camera-camera-aperture-i.md)

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
| preconfigRatio | [PreconfigRatio](arkts-camera-camera-preconfigratio-e.md) | No | Aspect ratio. The default value is 4:3. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether a preconfigured resolution is supported. **true** if supported, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function testCanPreconfig(photoSession: camera.PhotoSession, preconfigType: camera.PreconfigType,
  preconfigRatio: camera.PreconfigRatio): void {
  try {
    let result = photoSession.canPreconfig(preconfigType, preconfigRatio);
    console.info(`canPreconfig ${preconfigType} ${preconfigRatio} result is : ${result}`);
  } catch (error) {
    let err = error as BusinessError;
    console.error(`The canPreconfig call failed. error code: ${err.code}`);
  }
}
```

## off('error')

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

Unsubscribes from **PhotoSession** error events. This API uses a callback to return the result.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'error' | Yes | Event type. The value is fixed at **'error'**. The event can be listened for when a session is created. |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | No | Callback used to return the result. If this parameter is specified, the subscription to the specified event with the specified callback is canceled. (The callback object cannot be an anonymous function.) Otherwise, the subscriptions to the specified event with all the callbacks are canceled. |

**Examples**

```TypeScript
function unregisterSessionError(photoSession: camera.PhotoSession): void {
  photoSession.off('error');
}
```

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

**Examples**

```TypeScript
function unregisterFocusStateChange(photoSession: camera.PhotoSession): void {
  photoSession.off('focusStateChange');
}
```

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

**Examples**

```TypeScript
function unregisterSmoothZoomInfo(photoSession: camera.PhotoSession): void {
  photoSession.off('smoothZoomInfoAvailable');
}
```

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
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | No | Callback used to return the result. If this parameter is specified, the subscription to the specified event with the specified callback is canceled. (The callback object cannot be an anonymous function.) Otherwise, the subscriptions to the specified event with all the callbacks are canceled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application.<br>**Applicable version:** 11 - 19 |

**Examples**

```TypeScript
function unregisterMacroStatusChanged(photoSession: camera.PhotoSession): void {
  photoSession.off('macroStatusChanged');
}
```

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

**Examples**

```TypeScript
function unregisterSmoothZoomInfo(photoSession: camera.PhotoSession): void {
  photoSession.off('autoDeviceSwitchStatusChange');
}
```

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

**Examples**

```TypeScript
function unregisterSystemPressureLevelChangeCallback(photoSession: camera.PhotoSession): void {
  photoSession.off('systemPressureLevelChange');
}
```

## offCameraSwitchRequest

```TypeScript
offCameraSwitchRequest(callback?: Callback<CameraDevice>): void
```

Unsubscribes camera switch request event callback.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[CameraDevice](arkts-camera-camera-cameradevice-i.md)&gt; | No | Callback used to get the target camera device. |

## offExposureInfoChange

```TypeScript
offExposureInfoChange(callback?: Callback<ExposureInfo>): void
```

Unsubscribes from exposure information change events. If you have subscribed to exposure information change events, cancel the subscription before releasing the camera object. This API uses an asynchronous callback to return the result.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ExposureInfo](arkts-camera-camera-exposureinfo-i.md)&gt; | No | Callback used to return the result. If this parameter is specified, the subscription to the specified event with the specified callback is canceled. (The callback object cannot be an anonymous function.) Otherwise, the subscriptions to the specified event with all the callbacks are canceled. |

**Examples**

```TypeScript
function offExposureInfoChange(photoSession: camera.PhotoSession): void {
  photoSession.offExposureInfoChange();
}
```

## offIsoInfoChange

```TypeScript
offIsoInfoChange(callback?: Callback<IsoInfo>): void
```

Unsubscribes from ISO information change events.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[IsoInfo](arkts-camera-camera-isoinfo-i.md)&gt; | No | Callback used to return the result. If this parameter is specified, the subscription to the specified event with the specified callback is canceled. (The callback object cannot be an anonymous function.) Otherwise, the subscriptions to the specified event with all the callbacks are canceled. |

**Examples**

```TypeScript
function offIsoInfoChange(photoSession: camera.PhotoSession): void {
  photoSession.offIsoInfoChange();
}
```

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

Subscribes to **PhotoSession** error events. This API uses an asynchronous callback to return the result.

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

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function callback(err: BusinessError): void {
  console.error(`Photo session error code: ${err.code}`);
}

function registerSessionError(photoSession: camera.PhotoSession): void {
  photoSession.on('error', callback);
}
```

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
| type | 'focusStateChange' | Yes | Event type. The value is fixed at **'focusStateChange'**. The event can be listened for when a session is created. This event is triggered only when the camera focus state changes in autofocus mode. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FocusState](arkts-camera-camera-focusstate-e.md)&gt; | Yes | Callback used to return the focus state change. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function callback(err: BusinessError, focusState: camera.FocusState): void {
  if (err !== undefined && err.code !== 0) {
    console.error(`Callback Error, errorCode: ${err.code}`);
    return;
  }
  console.info(`Focus state: ${focusState}`);
}

function registerFocusStateChange(photoSession: camera.PhotoSession): void {
  photoSession.on('focusStateChange', callback);
}
```

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

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function callback(err: BusinessError, smoothZoomInfo: camera.SmoothZoomInfo): void {
  if (err !== undefined && err.code !== 0) {
    console.error(`Callback Error, errorCode: ${err.code}`);
    return;
  }
  console.info(`The duration of smooth zoom: ${smoothZoomInfo.duration}`);
}

function registerSmoothZoomInfo(photoSession: camera.PhotoSession): void {
  photoSession.on('smoothZoomInfoAvailable', callback);
}
```

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

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function callback(err: BusinessError, macroStatus: boolean): void {
  if (err !== undefined && err.code !== 0) {
    console.error(`Callback Error, errorCode: ${err.code}`);
    return;
  }
  console.info(`Macro state: ${macroStatus}`);
}

function registerMacroStatusChanged(photoSession: camera.PhotoSession): void {
  photoSession.on('macroStatusChanged', callback);
}
```

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
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AutoDeviceSwitchStatus](arkts-camera-camera-autodeviceswitchstatus-i.md)&gt; | Yes | Callback function, which is used to obtain the status of automatic camera switch. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function callback(err: BusinessError, autoDeviceSwitchStatus: camera.AutoDeviceSwitchStatus): void {
  if (err !== undefined && err.code !== 0) {
    console.error(`Callback Error, errorCode: ${err.code}`);
    return;
  }
  console.info(`isDeviceSwitched: ${autoDeviceSwitchStatus.isDeviceSwitched}, isDeviceCapabilityChanged: ${autoDeviceSwitchStatus.isDeviceCapabilityChanged}`);
}

function registerAutoDeviceSwitchStatus(photoSession: camera.PhotoSession): void {
  photoSession.on('autoDeviceSwitchStatusChange', callback);
}
```

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

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function callback(err: BusinessError, systemPressureLevel: camera.SystemPressureLevel): void {
  if (err !== undefined && err.code !== 0) {
    console.error(`Callback Error, errorCode: ${err.code}`);
    return;
  }
  console.info(`systemPressureLevel: ${systemPressureLevel}`);
}

function registerSystemPressureLevelChangeCallback(photoSession: camera.PhotoSession): void {
    photoSession.on('systemPressureLevelChange', callback);
}
```

## onCameraSwitchRequest

```TypeScript
onCameraSwitchRequest(callback: Callback<CameraDevice>): void
```

Subscribes camera switch request event callback.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[CameraDevice](arkts-camera-camera-cameradevice-i.md)&gt; | Yes | Callback used to get the target camera device. |

## onExposureInfoChange

```TypeScript
onExposureInfoChange(callback: Callback<ExposureInfo>): void
```

Subscribes to exposure information change events. After the exposure parameters are modified, the system returns the updated exposure information. This API uses an asynchronous callback to return the result.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ExposureInfo](arkts-camera-camera-exposureinfo-i.md)&gt; | Yes | Callback used to obtain the exposure information. |

**Examples**

```TypeScript
function onExposureInfoChange(photoSession: camera.PhotoSession): void {
  photoSession.onExposureInfoChange((exposureInfo: camera.ExposureInfo) => {
    console.info(`Exposure info changed, exposureTime: ${exposureInfo.exposureTime}`);
  });
}
```

## onIsoInfoChange

```TypeScript
onIsoInfoChange(callback: Callback<IsoInfo>): void
```

Subscribes to ISO information change events.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Multimedia.Camera.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[IsoInfo](arkts-camera-camera-isoinfo-i.md)&gt; | Yes | Callback used to obtain the ISO information. |

**Examples**

```TypeScript
function onIsoInfoChange(photoSession: camera.PhotoSession): void {
  photoSession.onIsoInfoChange((isoInfo: camera.IsoInfo) => {
    console.info(`ISO info changed, iso: ${isoInfo.iso}`);
  });
}
```

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
| preconfigRatio | [PreconfigRatio](arkts-camera-camera-preconfigratio-e.md) | No | Aspect ratio. The default value is 4:3. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-camera-service-error) | Camera service fatal error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function testPreconfig(photoSession: camera.PhotoSession, preconfigType: camera.PreconfigType,
  preconfigRatio: camera.PreconfigRatio): void {
  try {
    photoSession.preconfig(preconfigType, preconfigRatio);
    console.info(`preconfig success preconfigType: ${preconfigType}, preconfigRatio: ${preconfigRatio}`);
  } catch (error) {
    let err = error as BusinessError;
    console.error(`The preconfig call failed. error code: ${err.code}`);
  }
}
```
