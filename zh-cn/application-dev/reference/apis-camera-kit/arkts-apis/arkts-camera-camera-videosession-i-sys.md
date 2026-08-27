# VideoSession

VideoSession继承自[Session](arkts-camera-camera-session-i.md)、[Flash](arkts-camera-camera-flash-i.md)、 [AutoExposure](arkts-camera-camera-autoexposure-i.md)、[WhiteBalance](arkts-camera-camera-whitebalance-i.md)、[Focus](arkts-camera-camera-focus-i.md)、 [Zoom](arkts-camera-camera-zoom-i.md)、[Stabilization](arkts-camera-camera-stabilization-i.md)、 [ColorManagement](arkts-camera-camera-colormanagement-i.md)、[AutoDeviceSwitch](arkts-camera-camera-autodeviceswitch-i.md)、 [Macro](arkts-camera-camera-macro-i.md)、[ControlCenter](arkts-camera-camera-controlcenter-i.md)、 [ManualExposure](../../../reference/apis-camera-kit/arkts-apis-camera-ManualExposure.md)、 [ManualFocus](../../../reference/apis-camera-kit/arkts-apis-camera-ManualFocus.md)、 [ManualIso](../../../reference/apis-camera-kit/arkts-apis-camera-ManualIso.md)、 [OIS](../../../reference/apis-camera-kit/arkts-apis-camera-OIS.md)、 [Aperture](../../../reference/apis-camera-kit/arkts-apis-camera-Aperture.md)。普通录像模式会话类，提供了对闪光灯、曝光、白平衡、对焦、变焦、视频防抖、色彩空间、微距及控制器、手动曝光、手动对焦、手动ISO、光学防抖及光圈的操作。默认的视频录制模式，适用于一般场景。支持720P、1080p等多种分辨率的录制，可选择不同帧率（如30fps、60fps）。@extends Session, Flash, AutoExposure, Focus, Zoom, Stabilization, ColorManagement [since 11 - 12] @extends AutoDeviceSwitch [since 13 - 18] @extends Session, Flash, AutoExposure, Focus, Zoom, Stabilization, ColorManagement, AutoDeviceSwitch, Macro [since 19 - 19] @extends Session, Flash, AutoExposure, WhiteBalance, Focus, Zoom, Stabilization, ColorManagement, ControlCenter, AutoDeviceSwitch, Macro [since 20 - 24] @extends Session, Flash, AutoExposure, WhiteBalance, Focus, Zoom, Stabilization, ColorManagement, ControlCenter, AutoDeviceSwitch, Macro, ManualExposure, ManualFocus, ManualIso, OIS, Aperture [since 26.0.0]

**继承/实现关系：** VideoSession extends [Session](arkts-camera-camera-session-i.md), [Flash](arkts-camera-camera-flash-i.md), [AutoExposure](arkts-camera-camera-autoexposure-i.md), [WhiteBalance](arkts-camera-camera-whitebalance-i.md), [Focus](arkts-camera-camera-focus-i.md), [Zoom](arkts-camera-camera-zoom-i.md), [Stabilization](arkts-camera-camera-stabilization-i.md), [ColorManagement](arkts-camera-camera-colormanagement-i.md), [ControlCenter](arkts-camera-camera-controlcenter-i.md), [AutoDeviceSwitch](arkts-camera-camera-autodeviceswitch-i.md), [Macro](arkts-camera-camera-macro-i.md), [ManualExposure](arkts-camera-camera-manualexposure-i.md), [ManualFocus](arkts-camera-camera-manualfocus-i.md), [ManualIso](arkts-camera-camera-manualiso-i.md), [OIS](arkts-camera-camera-ois-i.md), [Aperture](arkts-camera-camera-aperture-i.md)

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
```

## getSessionConflictFunctions

```TypeScript
getSessionConflictFunctions(): Array<VideoConflictFunctions>
```

Gets session conflict functions.

**起始版本：** 13

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[VideoConflictFunctions](arkts-camera-camera-videoconflictfunctions-i.md)&gt; | List of session conflict functions. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## getSessionFunctions

```TypeScript
getSessionFunctions(outputCapability: CameraOutputCapability): Array<VideoFunctions>
```

Gets session functions.

**起始版本：** 13

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| outputCapability | [CameraOutputCapability](arkts-camera-camera-cameraoutputcapability-i.md) | 是 | CameraOutputCapability to set. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[VideoFunctions](arkts-camera-camera-videofunctions-i.md)&gt; | List of session functions. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

## off('lcdFlashStatus')

```TypeScript
off(type: 'lcdFlashStatus', callback?: AsyncCallback<LcdFlashStatus>): void
```

Unsubscribes from LCD flash status change events.

**起始版本：** 13

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'lcdFlashStatus' | 是 | Event type. The value is fixed at **'lcdFlashStatus'**. The event can be listened for when a session is created. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[LcdFlashStatus](arkts-camera-camera-lcdflashstatus-i-sys.md)&gt; | 否 | Callback used to return the result. This parameter is optional. If this parameter is specified, the subscription to the specified event **on('lcdFlashStatus')** with the specified callback is canceled. (The callback object cannot be an anonymous function.) |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

**示例**

```TypeScript
function unregisterLcdFlashStatus(videoSession: camera.VideoSession): void {
  videoSession.off('lcdFlashStatus');
}
```

## off('focusTrackingInfoAvailable')

```TypeScript
off(type: 'focusTrackingInfoAvailable', callback?: Callback<FocusTrackingInfo>): void
```

Unsubscribes from focus tracking information events.

**起始版本：** 15

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'focusTrackingInfoAvailable' | 是 | Event type. The value is fixed at **'focusTrackingInfoAvailable'**. The event can be listened for when a VideoSessionForSys object is created. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[FocusTrackingInfo](arkts-camera-camera-focustrackinginfo-i-sys.md)&gt; | 否 | Callback used to return the result. This parameter is optional. If this parameter is specified, the subscription to the specified event **on('focusTrackingInfoAvailable')** with the specified callback is canceled. (The callback object cannot be an anonymous function.) |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

**示例**

```TypeScript
function unregisterFocusTrackingInfoChanged(session: camera.VideoSessionForSys): void {
  session.off('focusTrackingInfoAvailable');
}
```

## off('effectSuggestionChange')

```TypeScript
off(type: 'effectSuggestionChange', callback?: AsyncCallback<EffectSuggestionType>): void
```

Unsubscribes from effect suggestion change events.

**起始版本：** 18

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'effectSuggestionChange' | 是 | Event type. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[EffectSuggestionType](arkts-camera-camera-effectsuggestiontype-e-sys.md)&gt; | 否 | Callback used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## off('lightStatusChange')

```TypeScript
off(type: 'lightStatusChange', callback?: AsyncCallback<LightStatus>): void
```

Unsubscribes from camera light status changes.

**起始版本：** 18

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'lightStatusChange' | 是 | Event type. The value is fixed at **'lightStatusChange'**. The event can be listened for when a VideoSessionForSys object is created. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[LightStatus](arkts-camera-camera-lightstatus-e-sys.md)&gt; | 否 | Callback used to return the result. This parameter is optional. If this parameter is specified, the subscription to the specified event **on('lightStatusChange')** with the specified callback is canceled. (The callback object cannot be an anonymous function.) |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function LightStatusCallback(err: BusinessError, lightStatus: camera.LightStatus) : void {
  if (err !== undefined && err.code !== 0) {
    console.error(`Callback Error, errorCode: ${err.code}`);
    return;
  }
  console.info(`lightStatus: ${lightStatus}`);
}

function handleLightStatusOff(mSession: camera.VideoSessionForSys): void {
  console.info('handleLightStatusOff');
  try {
    mSession.on('lightStatusChange', LightStatusCallback);
  } catch (error) {
    let err = error as BusinessError;
    console.error(`handleLightStatusOff err:${err}`);
  }
}
```

## offApertureInfoChange

```TypeScript
offApertureInfoChange(callback?: Callback<ApertureInfo>): void
```

Unsubscribes from aperture info event callback.

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ApertureInfo](arkts-camera-camera-apertureinfo-i-sys.md)&gt; | 否 | Callback used to get the aperture info. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## on('lcdFlashStatus')

```TypeScript
on(type: 'lcdFlashStatus', callback: AsyncCallback<LcdFlashStatus>): void
```

Subscribes to LCD flash status change events. This API uses an asynchronous callback to return the result.

**起始版本：** 13

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'lcdFlashStatus' | 是 | Event type. The value is fixed at **'lcdFlashStatus'**. The event can be listened for when a session is created. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[LcdFlashStatus](arkts-camera-camera-lcdflashstatus-i-sys.md)&gt; | 是 | Callback used to return the LCD flash status change. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function callback(err: BusinessError, lcdFlashStatus: camera.LcdFlashStatus): void {
  if (err !== undefined && err.code !== 0) {
    console.error(`Callback Error, errorCode: ${err.code}`);
    return;
  }
  console.info(`isLcdFlashNeeded: ${lcdFlashStatus.isLcdFlashNeeded}`);
  console.info(`lcdCompensation: ${lcdFlashStatus.lcdCompensation}`);
}

function registerLcdFlashStatus(videoSession: camera.VideoSession): void {
  videoSession.on('lcdFlashStatus', callback);
}
```

## on('focusTrackingInfoAvailable')

```TypeScript
on(type: 'focusTrackingInfoAvailable', callback: Callback<FocusTrackingInfo>): void
```

Subscribes to focus tracking information events. This API uses an asynchronous callback to return the result.

**起始版本：** 15

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'focusTrackingInfoAvailable' | 是 | Event type. The value is fixed at **'focusTrackingInfoAvailable'**. The event can be listened for when a VideoSessionForSys object is created. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[FocusTrackingInfo](arkts-camera-camera-focustrackinginfo-i-sys.md)&gt; | 是 | Callback used to return the focus tracking information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

**示例**

```TypeScript
function callback(focusTrackingInfo: camera.FocusTrackingInfo): void {
  console.info(`Focus tracking mode: ${focusTrackingInfo.trackingMode}`);
  console.info(`Focus tracking Region: topLeftX ${focusTrackingInfo.trackingRegion.topLeftX}
                                       topLeftY ${focusTrackingInfo.trackingRegion.topLeftY}
                                       width ${focusTrackingInfo.trackingRegion.width}
                                       height ${focusTrackingInfo.trackingRegion.height}`);
}

function registerFocusTrackingInfoChanged(session: camera.VideoSessionForSys): void {
  session.on('focusTrackingInfoAvailable', callback);
}
```

## on('effectSuggestionChange')

```TypeScript
on(type: 'effectSuggestionChange', callback: AsyncCallback<EffectSuggestionType>): void
```

Subscribes to effect suggestion change events.

**起始版本：** 18

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'effectSuggestionChange' | 是 | Event type. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[EffectSuggestionType](arkts-camera-camera-effectsuggestiontype-e-sys.md)&gt; | 是 | Callback used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## on('lightStatusChange')

```TypeScript
on(type: 'lightStatusChange', callback: AsyncCallback<LightStatus>): void
```

Subscribes to camera light status changes. This API uses an asynchronous callback to return the result.

**起始版本：** 18

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'lightStatusChange' | 是 | Event type. The value is fixed at **'lightStatusChange'**. The event can be listened for when a VideoSessionForSys object is created. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[LightStatus](arkts-camera-camera-lightstatus-e-sys.md)&gt; | 是 | Callback used to return the light status information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function handleLightStatusCallback(err: BusinessError, lightStatus: camera.LightStatus) : void {
  if (err !== undefined && err.code !== 0) {
    console.error(`Callback Error, errorCode: ${err.code}`);
    return;
  }
  console.info(`lightStatus: ${lightStatus}`);
}

function handleLightStatusOn(mSession: camera.VideoSessionForSys): void {
  console.info('handleLightStatusOn');
  try {
    mSession.on('lightStatusChange', handleLightStatusCallback);
  } catch (error) {
    let err = error as BusinessError;
    console.error(`handleLightStatusOn err:${err}`);
  }
}
```

## onApertureInfoChange

```TypeScript
onApertureInfoChange(callback: Callback<ApertureInfo>): void
```

Subscribes aperture info event callback.

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ApertureInfo](arkts-camera-camera-apertureinfo-i-sys.md)&gt; | 是 | Callback used to get the aperture info. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |
