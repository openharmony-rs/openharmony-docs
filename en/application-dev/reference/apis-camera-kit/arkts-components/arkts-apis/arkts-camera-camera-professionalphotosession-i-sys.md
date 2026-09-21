# ProfessionalPhotoSession (System API)

```TypeScript
interface ProfessionalPhotoSession extends Session, AutoExposure, ManualExposure, Focus,
    ManualFocus, WhiteBalance, ManualIso, Flash, Zoom, ColorEffect, Aperture
```

ProfessionalPhotoSession extends Session, AutoExposure, ManualExposure, Focus, ManualFocus, WhiteBalance, ManualIso, Flash, Zoom, ColorEffect, Aperture Implements a professional photo session, which sets the parameters of the professional photo mode and saves all [CameraInput](arkts-camera-camera-camerainput-i.md) and [CameraOutput](arkts-camera-camera-cameraoutput-i.md) instances required to run the camera. It inherits from [Session](arkts-camera-camera-session-i.md).

**Inheritance/Implementation:** ProfessionalPhotoSession extends [Session](arkts-camera-camera-session-i.md), [AutoExposure](arkts-camera-camera-autoexposure-i.md), [ManualExposure](arkts-camera-camera-manualexposure-i.md), [Focus](arkts-camera-camera-focus-i.md), [ManualFocus](arkts-camera-camera-manualfocus-i.md), [WhiteBalance](arkts-camera-camera-whitebalance-i.md), [ManualIso](arkts-camera-camera-manualiso-i.md), [Flash](arkts-camera-camera-flash-i.md), [Zoom](arkts-camera-camera-zoom-i.md)<!--Del-->, [ColorEffect](arkts-camera-camera-coloreffect-i-sys.md)<!--DelEnd-->, [Aperture](arkts-camera-camera-aperture-i.md)

**Since:** 12

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## off('error')

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

Unsubscribes from HighResolutionPhotoSession error events.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'error' | Yes | Event type. The value is fixed at **'error'**. The event can be listened for when a session is created. |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | No | Callback used to return the result. This parameter is optional. If this parameter is specified, the subscription to the specified event **on('error')** with the specified callback is canceled. (The callback object cannot be an anonymous function.) |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |

**Examples**

```TypeScript
function unregisterSessionError(professionalPhotoSession: camera.ProfessionalPhotoSession): void {
  professionalPhotoSession.off('error');
}
```

## off('focusStateChange')

```TypeScript
off(type: 'focusStateChange', callback?: AsyncCallback<FocusState>): void
```

Unsubscribes from focus state change events.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'focusStateChange' | Yes | Event type. The value is fixed at **'focusStateChange'**. The event can be listened for when a session is created. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FocusState](arkts-camera-camera-focusstate-e.md)&gt; | No | Callback used to return the result. This parameter is optional. If this parameter is specified, the subscription to the specified event **on('focusStateChange')** with the specified callback is canceled. (The callback object cannot be an anonymous function.) |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |

**Examples**

```TypeScript
function unregisterFocusStateChange(professionalPhotoSession: camera.ProfessionalPhotoSession): void {
  professionalPhotoSession.off('focusStateChange');
}
```

## off('smoothZoomInfoAvailable')

```TypeScript
off(type: 'smoothZoomInfoAvailable', callback?: AsyncCallback<SmoothZoomInfo>): void
```

Unsubscribes from smooth zoom state change events.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'smoothZoomInfoAvailable' | Yes | Event type. The value is fixed at **'smoothZoomInfoAvailable'**. The event can be listened for when a session is created. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[SmoothZoomInfo](arkts-camera-camera-smoothzoominfo-i.md)&gt; | No | Callback used to return the result. This parameter is optional. If this parameter is specified, the subscription to the specified event **on('smoothZoomInfoAvailable')** with the specified callback is canceled. (The callback object cannot be an anonymous function.) |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |

**Examples**

```TypeScript
function unregisterSmoothZoomInfo(professionalPhotoSession: camera.ProfessionalPhotoSession): void {
  professionalPhotoSession.off('smoothZoomInfoAvailable');
}
```

## off('isoInfoChange')

```TypeScript
off(type: 'isoInfoChange', callback?: AsyncCallback<IsoInfo>): void
```

Unsubscribes from automatic ISO change events.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'isoInfoChange' | Yes | Event type. The value is fixed at **'isoInfoChange'**. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[IsoInfo](arkts-camera-camera-isoinfo-i.md)&gt; | No | Callback, which is optional and is used to match **callback** in **on('isoInfoChange')**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |

**Examples**

```TypeScript
function unregisterIsoInfoEvent(professionalPhotoSession: camera.ProfessionalPhotoSession): void {
  professionalPhotoSession.off('isoInfoChange');
}
```

## off('exposureInfoChange')

```TypeScript
off(type: 'exposureInfoChange', callback?: AsyncCallback<ExposureInfo>): void
```

Unsubscribes from exposure information change events.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'exposureInfoChange' | Yes | Event type. The value is fixed at **'exposureInfoChange'**. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ExposureInfo](arkts-camera-camera-exposureinfo-i.md)&gt; | No | Callback, which is optional and is used to match **callback** in **on('exposureInfoChange')**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |

**Examples**

```TypeScript
function unregisterExposureInfoEvent(professionalPhotoSession: camera.ProfessionalPhotoSession): void {
  professionalPhotoSession.off('exposureInfoChange');
}
```

## off('apertureInfoChange')

```TypeScript
off(type: 'apertureInfoChange', callback?: AsyncCallback<ApertureInfo>): void
```

Unsubscribes from aperture change events.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'apertureInfoChange' | Yes | Event type. The value is fixed at **'apertureInfoChange'**. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ApertureInfo](arkts-camera-camera-apertureinfo-i-sys.md)&gt; | No | Callback, which is optional and is used to match **callback** in **on('apertureInfoChange')**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |

**Examples**

```TypeScript
function unregisterApertureInfoEvent(professionalPhotoSession: camera.ProfessionalPhotoSession): void {
  professionalPhotoSession.off('apertureInfoChange');
}
```

## off('luminationInfoChange')

```TypeScript
off(type: 'luminationInfoChange', callback?: AsyncCallback<LuminationInfo>): void
```

Unsubscribes from illumination change events.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'luminationInfoChange' | Yes | Event type. The value is fixed at **'luminationInfoChange'**. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[LuminationInfo](arkts-camera-camera-luminationinfo-i-sys.md)&gt; | No | Callback, which is optional and is used to match **callback** in **on('luminationInfoChange')**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |

**Examples**

```TypeScript
function unregisterLuminationInfoEvent(professionalPhotoSession: camera.ProfessionalPhotoSession): void {
  professionalPhotoSession.off('luminationInfoChange');
}
```

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

Subscribes to HighResolutionPhotoSession error events. This API uses an asynchronous callback to return the result.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'error' | Yes | Event type. The value is fixed at **'error'**. The event can be listened for when a session is created. This event is triggered and the error message is returned when an error occurs during the calling of a session-related API such as [beginConfig](arkts-camera-camera-session-i.md#beginconfig), [commitConfig](arkts-camera-camera-session-i.md#commitconfig), and [addInput](arkts-camera-camera-session-i.md#addinput). |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | Yes | Callback used to return an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function callback(err: BusinessError): void {
  console.error(`Professional photo session error code: ${err.code}`);
}

function registerSessionError(professionalPhotoSession: camera.ProfessionalPhotoSession): void {
  professionalPhotoSession.on('error', callback);
}
```

## on('focusStateChange')

```TypeScript
on(type: 'focusStateChange', callback: AsyncCallback<FocusState>): void
```

Subscribes to focus state change events. This API uses an asynchronous callback to return the result.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'focusStateChange' | Yes | Event type. The value is fixed at **'focusStateChange'**. The event can be listened for when a session is created. This event is triggered only when the camera focus state changes in auto focus mode. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FocusState](arkts-camera-camera-focusstate-e.md)&gt; | Yes | Callback used to return the focus state change. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |

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

function registerFocusStateChange(professionalPhotoSession: camera.ProfessionalPhotoSession): void {
  professionalPhotoSession.on('focusStateChange', callback);
}
```

## on('smoothZoomInfoAvailable')

```TypeScript
on(type: 'smoothZoomInfoAvailable', callback: AsyncCallback<SmoothZoomInfo>): void
```

Subscribes to smooth zoom state change events. This API uses an asynchronous callback to return the result.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'smoothZoomInfoAvailable' | Yes | Event type. The value is fixed at **'smoothZoomInfoAvailable'**. The event can be listened for when a session is created. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[SmoothZoomInfo](arkts-camera-camera-smoothzoominfo-i.md)&gt; | Yes | Callback used to return the smooth zoom state change. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |

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

function registerSmoothZoomInfo(professionalPhotoSession: camera.ProfessionalPhotoSession): void {
  professionalPhotoSession.on('smoothZoomInfoAvailable', callback);
}
```

## on('isoInfoChange')

```TypeScript
on(type: 'isoInfoChange', callback: AsyncCallback<IsoInfo>): void
```

Subscribes to automatic ISO change events to obtain real-time ISO information. This API uses an asynchronous callback to return the result.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'isoInfoChange' | Yes | Event type. The value is fixed at **'isoInfoChange'**. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[IsoInfo](arkts-camera-camera-isoinfo-i.md)&gt; | Yes | Callback used to return the ISO information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function isoInfoCallback(err: BusinessError, info: camera.IsoInfo): void {
  if (err !== undefined && err.code !== 0) {
    console.error(`Callback Error, errorCode: ${err.code}`);
    return;
  }
  console.info(`ISO value: ${info.iso}`);
}

function registerIsoInfoEvent(professionalPhotoSession: camera.ProfessionalPhotoSession): void {
  professionalPhotoSession.on('isoInfoChange', isoInfoCallback);
}
```

## on('exposureInfoChange')

```TypeScript
on(type: 'exposureInfoChange', callback: AsyncCallback<ExposureInfo>): void
```

Subscribes to exposure information change events to obtain the exposure information. This API uses an asynchronous callback to return the result.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'exposureInfoChange' | Yes | Event type. The value is fixed at **'exposureInfoChange'**. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ExposureInfo](arkts-camera-camera-exposureinfo-i.md)&gt; | Yes | Callback used to return the exposure information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function exposureInfoCallback(err: BusinessError, info: camera.ExposureInfo): void {
  if (err !== undefined && err.code !== 0) {
    console.error(`Callback Error, errorCode: ${err.code}`);
    return;
  }
  console.info(`exposureTimeValue: ${info.exposureTime}`);
}

function registerExposureInfoEvent(professionalPhotoSession: camera.ProfessionalPhotoSession): void {
  professionalPhotoSession.on('exposureInfoChange', exposureInfoCallback);
}
```

## on('apertureInfoChange')

```TypeScript
on(type: 'apertureInfoChange', callback: AsyncCallback<ApertureInfo>): void
```

Subscribes to aperture change events to obtain the real-time aperture information. This API uses an asynchronous callback to return the result.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'apertureInfoChange' | Yes | Event type. The value is fixed at **'apertureInfoChange'**. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ApertureInfo](arkts-camera-camera-apertureinfo-i-sys.md)&gt; | Yes | Callback used to return the aperture information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function apertureInfoCallback(err: BusinessError, info: camera.ApertureInfo): void {
  if (err !== undefined && err.code !== 0) {
    console.error(`Callback Error, errorCode: ${err.code}`);
    return;
  }
  console.info(`Aperture value: ${info.aperture}`);
}

function registerApertureInfoEvent(professionalPhotoSession: camera.ProfessionalPhotoSession): void {
  professionalPhotoSession.on('apertureInfoChange', apertureInfoCallback);
}
```

## on('luminationInfoChange')

```TypeScript
on(type: 'luminationInfoChange', callback: AsyncCallback<LuminationInfo>): void
```

Subscribes to illumination change events to obtain real-time illumination information. This API uses an asynchronous callback to return the result.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'luminationInfoChange' | Yes | Event type. The value is fixed at **'luminationInfoChange'**. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[LuminationInfo](arkts-camera-camera-luminationinfo-i-sys.md)&gt; | Yes | Callback used to return the illumination information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System Application. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function luminationInfoCallback(err: BusinessError, info: camera.LuminationInfo): void {
  if (err !== undefined && err.code !== 0) {
    console.error(`Callback Error, errorCode: ${err.code}`);
    return;
  }
  console.info(`Lumination: ${info.lumination}`);
}

function registerLuminationInfoEvent(professionalPhotoSession: camera.ProfessionalPhotoSession): void {
  professionalPhotoSession.on('luminationInfoChange', luminationInfoCallback);
}
```
