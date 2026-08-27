# ProfessionalVideoSession（系统接口）

ProfessionalVideoSession extends Session, AutoExposure, ManualExposure, Focus, ManualFocus, WhiteBalance, ManualIso, Flash, Zoom, ColorEffect, Aperture Implements a professional video session, which sets the parameters of the professional video mode and saves all [CameraInput](arkts-camera-camera-camerainput-i.md) and [CameraOutput](arkts-camera-camera-cameraoutput-i.md) instances required to run the camera. It inherits from [Session](arkts-camera-camera-session-i.md).

**继承/实现关系：** ProfessionalVideoSession extends [Session](arkts-camera-camera-session-i.md), [AutoExposure](arkts-camera-camera-autoexposure-i.md), [ManualExposure](arkts-camera-camera-manualexposure-i.md), [Focus](arkts-camera-camera-focus-i.md), [ManualFocus](arkts-camera-camera-manualfocus-i.md), [WhiteBalance](arkts-camera-camera-whitebalance-i.md), [ManualIso](arkts-camera-camera-manualiso-i.md), [Flash](arkts-camera-camera-flash-i.md), [Zoom](arkts-camera-camera-zoom-i.md), [ColorEffect](arkts-camera-camera-coloreffect-i-sys.md), [Aperture](arkts-camera-camera-aperture-i.md)

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
```

## off('error')

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

Unsubscribes from HighResolutionPhotoSession error events.

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | Event type. The value is fixed at **'error'**. The event can be listened for when a session is created. |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | 否 | Callback used to return the result. This parameter is optional. If this parameter is specified, the subscription to the specified event **on('error')** with the specified callback is canceled. (The callback object cannot be an anonymous function.) |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

**示例**

```TypeScript
function unregisterSessionError(professionalVideoSession: camera.ProfessionalVideoSession): void {
  professionalVideoSession.off('error');
}
```

## off('focusStateChange')

```TypeScript
off(type: 'focusStateChange', callback?: AsyncCallback<FocusState>): void
```

Unsubscribes from focus state change events.

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'focusStateChange' | 是 | Event type. The value is fixed at **'focusStateChange'**. The event can be listened for when a session is created. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FocusState](arkts-camera-camera-focusstate-e.md)&gt; | 否 | Callback used to return the result. This parameter is optional. If this parameter is specified, the subscription to the specified event **on('focusStateChange')** with the specified callback is canceled. (The callback object cannot be an anonymous function.) |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

**示例**

```TypeScript
function unregisterFocusStateChange(professionalVideoSession: camera.ProfessionalVideoSession): void {
  professionalVideoSession.off('focusStateChange');
}
```

## off('smoothZoomInfoAvailable')

```TypeScript
off(type: 'smoothZoomInfoAvailable', callback?: AsyncCallback<SmoothZoomInfo>): void
```

Unsubscribes from smooth zoom state change events.

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'smoothZoomInfoAvailable' | 是 | Event type. The value is fixed at **'smoothZoomInfoAvailable'**. The event can be listened for when a session is created. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[SmoothZoomInfo](arkts-camera-camera-smoothzoominfo-i.md)&gt; | 否 | Callback used to return the result. This parameter is optional. If this parameter is specified, the subscription to the specified event **on('smoothZoomInfoAvailable')** with the specified callback is canceled. (The callback object cannot be an anonymous function.) |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

**示例**

```TypeScript
function unregisterSmoothZoomInfo(professionalVideoSession: camera.ProfessionalVideoSession): void {
  professionalVideoSession.off('smoothZoomInfoAvailable');
}
```

## off('isoInfoChange')

```TypeScript
off(type: 'isoInfoChange', callback?: AsyncCallback<IsoInfo>): void
```

Unsubscribes from automatic ISO change events.

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'isoInfoChange' | 是 | Event type. The value is fixed at **'isoInfoChange'**. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[IsoInfo](arkts-camera-camera-isoinfo-i.md)&gt; | 否 | Callback, which is optional and is used to match **callback** in **on('isoInfoChange')**. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

**示例**

```TypeScript
function unregisterIsoInfoEvent(professionalVideoSession: camera.ProfessionalVideoSession): void {
  professionalVideoSession.off('isoInfoChange');
}
```

## off('exposureInfoChange')

```TypeScript
off(type: 'exposureInfoChange', callback?: AsyncCallback<ExposureInfo>): void
```

Unsubscribes from exposure information change events.

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'exposureInfoChange' | 是 | Event type. The value is fixed at **'exposureInfoChange'**. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ExposureInfo](arkts-camera-camera-exposureinfo-i.md)&gt; | 否 | Callback, which is optional and is used to match **callback** in **on('exposureInfoChange')**. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

**示例**

```TypeScript
function unregisterExposureInfoEvent(professionalVideoSession: camera.ProfessionalVideoSession): void {
  professionalVideoSession.off('exposureInfoChange');
}
```

## off('apertureInfoChange')

```TypeScript
off(type: 'apertureInfoChange', callback?: AsyncCallback<ApertureInfo>): void
```

Unsubscribes from aperture change events.

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'apertureInfoChange' | 是 | Event type. The value is fixed at **'apertureInfoChange'**. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ApertureInfo](arkts-camera-camera-apertureinfo-i-sys.md)&gt; | 否 | Callback, which is optional and is used to match **callback** in **on('apertureInfoChange')**. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

**示例**

```TypeScript
function unregisterApertureInfoEvent(professionalVideoSession: camera.ProfessionalVideoSession): void {
  professionalVideoSession.off('apertureInfoChange');
}
```

## off('luminationInfoChange')

```TypeScript
off(type: 'luminationInfoChange', callback?: AsyncCallback<LuminationInfo>): void
```

Unsubscribes from illumination change events.

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'luminationInfoChange' | 是 | Event type. The value is fixed at **'luminationInfoChange'**. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[LuminationInfo](arkts-camera-camera-luminationinfo-i-sys.md)&gt; | 否 | Callback, which is optional and is used to match **callback** in **on('luminationInfoChange')**. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

**示例**

```TypeScript
function unregisterLuminationInfoEvent(professionalVideoSession: camera.ProfessionalVideoSession): void {
  professionalVideoSession.off('luminationInfoChange');
}
```

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

Subscribes to HighResolutionPhotoSession error events. This API uses an asynchronous callback to return the result.

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | Event type. The value is fixed at **'error'**. The event can be listened for when a session is created. This event is triggered and the error message is returned when an error occurs during the calling of a session-related API such as [beginConfig](arkts-camera-camera-session-i.md#beginconfig), [commitConfig](arkts-camera-camera-session-i.md#commitconfig), and [addInput](arkts-camera-camera-session-i.md#addinput). |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | 是 | Callback used to return an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md). |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function callback(err: BusinessError): void {
  console.error(`Professional video session error code: ${err.code}`);
}

function registerSessionError(professionalVideoSession: camera.ProfessionalVideoSession): void {
  professionalVideoSession.on('error', callback);
}
```

## on('focusStateChange')

```TypeScript
on(type: 'focusStateChange', callback: AsyncCallback<FocusState>): void
```

Subscribes to focus state change events. This API uses an asynchronous callback to return the result.

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'focusStateChange' | 是 | Event type. The value is fixed at **'focusStateChange'**. The event can be listened for when a session is created. This event is triggered only when the camera focus state changes in auto focus mode. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FocusState](arkts-camera-camera-focusstate-e.md)&gt; | 是 | Callback used to return the focus state change. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function callback(err: BusinessError, focusState: camera.FocusState): void {
  if (err !== undefined && err.code !== 0) {
    console.error(`Callback Error, errorCode: ${err.code}`);
    return;
  }
  console.info(`Focus state: ${focusState}`);
}

function registerFocusStateChange(professionalVideoSession: camera.ProfessionalVideoSession): void {
  professionalVideoSession.on('focusStateChange', callback);
}
```

## on('smoothZoomInfoAvailable')

```TypeScript
on(type: 'smoothZoomInfoAvailable', callback: AsyncCallback<SmoothZoomInfo>): void
```

Subscribes to smooth zoom state change events. This API uses an asynchronous callback to return the result.

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'smoothZoomInfoAvailable' | 是 | Event type. The value is fixed at **'smoothZoomInfoAvailable'**. The event can be listened for when a session is created. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[SmoothZoomInfo](arkts-camera-camera-smoothzoominfo-i.md)&gt; | 是 | Callback used to return the smooth zoom state change. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function callback(err: BusinessError, smoothZoomInfo: camera.SmoothZoomInfo): void {
  if (err !== undefined && err.code !== 0) {
    console.error(`Callback Error, errorCode: ${err.code}`);
    return;
  }
  console.info(`The duration of smooth zoom: ${smoothZoomInfo.duration}`);
}

function registerSmoothZoomInfo(professionalVideoSession: camera.ProfessionalVideoSession): void {
  professionalVideoSession.on('smoothZoomInfoAvailable', callback);
}
```

## on('isoInfoChange')

```TypeScript
on(type: 'isoInfoChange', callback: AsyncCallback<IsoInfo>): void
```

Subscribes to automatic ISO change events to obtain real-time ISO information. This API uses an asynchronous callback to return the result.

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'isoInfoChange' | 是 | Event type. The value is fixed at **'isoInfoChange'**. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[IsoInfo](arkts-camera-camera-isoinfo-i.md)&gt; | 是 | Callback used to return the ISO information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function isoInfoCallback(err: BusinessError, info: camera.IsoInfo): void {
  if (err !== undefined && err.code !== 0) {
    console.error(`Callback Error, errorCode: ${err.code}`);
    return;
  }
  console.info(`ISO value: ${info.iso}`);
}

function registerIsoInfoEvent(professionalVideoSession: camera.ProfessionalVideoSession): void {
  professionalVideoSession.on('isoInfoChange', isoInfoCallback);
}
```

## on('exposureInfoChange')

```TypeScript
on(type: 'exposureInfoChange', callback: AsyncCallback<ExposureInfo>): void
```

Subscribes to exposure information change events to obtain the exposure information. This API uses an asynchronous callback to return the result.

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'exposureInfoChange' | 是 | Event type. The value is fixed at **'exposureInfoChange'**. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ExposureInfo](arkts-camera-camera-exposureinfo-i.md)&gt; | 是 | Callback used to return the exposure information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function exposureInfoCallback(err: BusinessError, info: camera.ExposureInfo): void {
  if (err !== undefined && err.code !== 0) {
    console.error(`Callback Error, errorCode: ${err.code}`);
    return;
  }
  console.info(`exposureTimeValue: ${info.exposureTime}`);
}

function registerExposureInfoEvent(professionalVideoSession: camera.ProfessionalVideoSession): void {
  professionalVideoSession.on('exposureInfoChange', exposureInfoCallback);
}
```

## on('apertureInfoChange')

```TypeScript
on(type: 'apertureInfoChange', callback: AsyncCallback<ApertureInfo>): void
```

Subscribes to aperture change events to obtain the real-time aperture information. This API uses an asynchronous callback to return the result.

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'apertureInfoChange' | 是 | Event type. The value is fixed at **'apertureInfoChange'**. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ApertureInfo](arkts-camera-camera-apertureinfo-i-sys.md)&gt; | 是 | Callback used to return the aperture information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function apertureInfoCallback(err: BusinessError, info: camera.ApertureInfo): void {
  if (err !== undefined && err.code !== 0) {
    console.error(`Callback Error, errorCode: ${err.code}`);
    return;
  }
  console.info(`Aperture value: ${info.aperture}`);
}

function registerApertureInfoEvent(professionalVideoSession: camera.ProfessionalVideoSession): void {
  professionalVideoSession.on('apertureInfoChange', apertureInfoCallback);
}
```

## on('luminationInfoChange')

```TypeScript
on(type: 'luminationInfoChange', callback: AsyncCallback<LuminationInfo>): void
```

Subscribes to illumination change events to obtain real-time illumination information. This API uses an asynchronous callback to return the result.

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'luminationInfoChange' | 是 | Event type. The value is fixed at **'luminationInfoChange'**. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[LuminationInfo](arkts-camera-camera-luminationinfo-i-sys.md)&gt; | 是 | Callback used to return the illumination information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function luminationInfoCallback(err: BusinessError, info: camera.LuminationInfo): void {
  if (err !== undefined && err.code !== 0) {
    console.error(`Callback Error, errorCode: ${err.code}`);
    return;
  }
  console.info(`Lumination: ${info.lumination}`);
}

function registerLuminationInfoEvent(professionalVideoSession: camera.ProfessionalVideoSession): void {
  professionalVideoSession.on('luminationInfoChange', luminationInfoCallback);
}
```
