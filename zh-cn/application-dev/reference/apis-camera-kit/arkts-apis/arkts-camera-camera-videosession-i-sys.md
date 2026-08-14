# VideoSession

VideoSession继承自[Session](arkts-camera-camera-session-i.md#Session)、[Flash](arkts-camera-camera-flash-i.md#Flash)、 [AutoExposure](arkts-camera-camera-autoexposure-i.md#AutoExposure)、[WhiteBalance](arkts-camera-camera-whitebalance-i.md#WhiteBalance（系统接口）)、[Focus](arkts-camera-camera-focus-i.md#Focus)、 [Zoom](arkts-camera-camera-zoom-i.md#Zoom)、[Stabilization](arkts-camera-camera-stabilization-i.md#Stabilization)、 [ColorManagement](arkts-camera-camera-colormanagement-i.md#ColorManagement)、[AutoDeviceSwitch](arkts-camera-camera-autodeviceswitch-i.md#AutoDeviceSwitch)、 [Macro](arkts-camera-camera-macro-i-sys.md#Macro（系统接口）)、[ControlCenter](arkts-camera-camera-controlcenter-i.md#ControlCenter)、 [ManualExposure](../../../reference/apis-camera-kit/arkts-apis-camera-ManualExposure.md)、 [ManualFocus](../../../reference/apis-camera-kit/arkts-apis-camera-ManualFocus.md)、 [ManualIso](../../../reference/apis-camera-kit/arkts-apis-camera-ManualIso.md)、 [OIS](../../../reference/apis-camera-kit/arkts-apis-camera-OIS.md)、 [Aperture](../../../reference/apis-camera-kit/arkts-apis-camera-Aperture.md)。 普通录像模式会话类，提供了对闪光灯、曝光、白平衡、对焦、变焦、视频防抖、色彩空间、微距及控制器、手动曝光、手动对焦、手动ISO、光学防抖及光圈的操作。 默认的视频录制模式，适用于一般场景。支持720P、1080p等多种分辨率的录制，可选择不同帧率（如30fps、60fps）。

**继承/实现关系：** VideoSession extends [Session](arkts-camera-camera-session-i.md#Session), [Flash](arkts-camera-camera-flash-i.md#Flash), [AutoExposure](arkts-camera-camera-autoexposure-i.md#AutoExposure), [WhiteBalance](arkts-camera-camera-whitebalance-i.md#WhiteBalance（系统接口）), [Focus](arkts-camera-camera-focus-i.md#Focus), [Zoom](arkts-camera-camera-zoom-i.md#Zoom), [Stabilization](arkts-camera-camera-stabilization-i.md#Stabilization), [ColorManagement](arkts-camera-camera-colormanagement-i.md#ColorManagement), [ControlCenter](arkts-camera-camera-controlcenter-i.md#ControlCenter), [AutoDeviceSwitch](arkts-camera-camera-autodeviceswitch-i.md#AutoDeviceSwitch), [Macro](arkts-camera-camera-macro-i-sys.md#Macro（系统接口）), [ManualExposure](arkts-camera-camera-manualexposure-i.md#ManualExposure（系统接口）), [ManualFocus](arkts-camera-camera-manualfocus-i-sys.md#ManualFocus（系统接口）), [ManualIso](arkts-camera-camera-manualiso-i-sys.md#ManualIso（系统接口）), [OIS](arkts-camera-camera-ois-i.md#OIS), [Aperture](arkts-camera-camera-aperture-i-sys.md#Aperture（系统接口）)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-camera-interface VideoSession--><!--Device-camera-interface VideoSession-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## getSessionConflictFunctions

```TypeScript
getSessionConflictFunctions(): Array<VideoConflictFunctions>
```

Gets session conflict functions.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-VideoSession-getSessionConflictFunctions(): Array<VideoConflictFunctions>--><!--Device-VideoSession-getSessionConflictFunctions(): Array<VideoConflictFunctions>-End-->

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

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-VideoSession-getSessionFunctions(outputCapability: CameraOutputCapability): Array<VideoFunctions>--><!--Device-VideoSession-getSessionFunctions(outputCapability: CameraOutputCapability): Array<VideoFunctions>-End-->

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
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## offApertureInfoChange

```TypeScript
offApertureInfoChange(callback?: Callback<ApertureInfo>): void
```

Unsubscribes from aperture info event callback.

**起始版本：** 26.1.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.1.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VideoSession-offApertureInfoChange(callback?: Callback<ApertureInfo>): void--><!--Device-VideoSession-offApertureInfoChange(callback?: Callback<ApertureInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[ApertureInfo](arkts-camera-camera-apertureinfo-i-sys.md)&gt; | 否 | Callback used to get the aperture info. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## offEffectSuggestionChange

```TypeScript
offEffectSuggestionChange(callback?: AsyncCallback<EffectSuggestionType>): void
```

Unsubscribes from effect suggestion change events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-VideoSession-offEffectSuggestionChange(callback?: AsyncCallback<EffectSuggestionType>): void--><!--Device-VideoSession-offEffectSuggestionChange(callback?: AsyncCallback<EffectSuggestionType>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[EffectSuggestionType](arkts-camera-camera-effectsuggestiontype-e-sys.md)&gt; | 否 | Callback used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## offFocusTrackingInfoAvailable

```TypeScript
offFocusTrackingInfoAvailable(callback?: Callback<FocusTrackingInfo>): void
```

Unsubscribes from focus tracking info event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-VideoSession-offFocusTrackingInfoAvailable(callback?: Callback<FocusTrackingInfo>): void--><!--Device-VideoSession-offFocusTrackingInfoAvailable(callback?: Callback<FocusTrackingInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[FocusTrackingInfo](arkts-camera-camera-focustrackinginfo-i-sys.md)&gt; | 否 | Callback used to get the focus tracking info. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## offLcdFlashStatus

```TypeScript
offLcdFlashStatus(callback?: AsyncCallback<LcdFlashStatus>): void
```

Unsubscribes from lcd flash status.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-VideoSession-offLcdFlashStatus(callback?: AsyncCallback<LcdFlashStatus>): void--><!--Device-VideoSession-offLcdFlashStatus(callback?: AsyncCallback<LcdFlashStatus>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[LcdFlashStatus](arkts-camera-camera-lcdflashstatus-i-sys.md)&gt; | 否 | Callback used to get the lcd flash status. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## offLightStatusChange

```TypeScript
offLightStatusChange(callback?: AsyncCallback<LightStatus>): void
```

Unsubscribes camera light status event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-VideoSession-offLightStatusChange(callback?: AsyncCallback<LightStatus>): void--><!--Device-VideoSession-offLightStatusChange(callback?: AsyncCallback<LightStatus>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[LightStatus](arkts-camera-camera-lightstatus-e-sys.md)&gt; | 否 | Callback used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## off_effectSuggestionChange

```TypeScript
off(type: 'effectSuggestionChange', callback?: AsyncCallback<EffectSuggestionType>): void
```

Unsubscribes from effect suggestion change events.

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

<!--Device-VideoSession-off(type: 'effectSuggestionChange', callback?: AsyncCallback<EffectSuggestionType>): void--><!--Device-VideoSession-off(type: 'effectSuggestionChange', callback?: AsyncCallback<EffectSuggestionType>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'effectSuggestionChange' | 是 | Event type. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[EffectSuggestionType](arkts-camera-camera-effectsuggestiontype-e-sys.md)&gt; | 否 | Callback used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## off_focusTrackingInfoAvailable

```TypeScript
off(type: 'focusTrackingInfoAvailable', callback?: Callback<FocusTrackingInfo>): void
```

Unsubscribes from focus tracking information events.

**起始版本：** 15

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为15。

**废弃版本：** -1

<!--Device-VideoSession-off(type: 'focusTrackingInfoAvailable', callback?: Callback<FocusTrackingInfo>): void--><!--Device-VideoSession-off(type: 'focusTrackingInfoAvailable', callback?: Callback<FocusTrackingInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'focusTrackingInfoAvailable' | 是 | Event type. The value is fixed at **'focusTrackingInfoAvailable'**. The event can be listened for when a VideoSessionForSys object is created. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[FocusTrackingInfo](arkts-camera-camera-focustrackinginfo-i-sys.md)&gt; | 否 | Callback used to return the result. This parameter is optional. If this parameter is specified, the subscription to the specified event **on('focusTrackingInfoAvailable')** with the specified callback is canceled. (The callback object cannot be an anonymous function.) |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

```TypeScript
function unregisterFocusTrackingInfoChanged(session: camera.VideoSessionForSys): void {
  session.off('focusTrackingInfoAvailable');
}
```

## off_lcdFlashStatus

```TypeScript
off(type: 'lcdFlashStatus', callback?: AsyncCallback<LcdFlashStatus>): void
```

Unsubscribes from LCD flash status change events.

**起始版本：** 13

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为13。

**废弃版本：** -1

<!--Device-VideoSession-off(type: 'lcdFlashStatus', callback?: AsyncCallback<LcdFlashStatus>): void--><!--Device-VideoSession-off(type: 'lcdFlashStatus', callback?: AsyncCallback<LcdFlashStatus>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'lcdFlashStatus' | 是 | Event type. The value is fixed at **'lcdFlashStatus'**. The event can be listened for when a session is created. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[LcdFlashStatus](arkts-camera-camera-lcdflashstatus-i-sys.md)&gt; | 否 | Callback used to return the result. This parameter is optional. If this parameter is specified, the subscription to the specified event **on('lcdFlashStatus')** with the specified callback is canceled. (The callback object cannot be an anonymous function.) |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

```TypeScript
function unregisterLcdFlashStatus(videoSession: camera.VideoSession): void {
  videoSession.off('lcdFlashStatus');
}
```

## off_lightStatusChange

```TypeScript
off(type: 'lightStatusChange', callback?: AsyncCallback<LightStatus>): void
```

Unsubscribes from camera light status changes.

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

<!--Device-VideoSession-off(type: 'lightStatusChange', callback?: AsyncCallback<LightStatus>): void--><!--Device-VideoSession-off(type: 'lightStatusChange', callback?: AsyncCallback<LightStatus>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'lightStatusChange' | 是 | Event type. The value is fixed at **'lightStatusChange'**. &lt;br&gt;The event can be listened for when a VideoSessionForSys object is created. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[LightStatus](arkts-camera-camera-lightstatus-e-sys.md)&gt; | 否 | Callback used to return the result. This parameter is optional. If this parameter is specified, the subscription to the specified event **on('lightStatusChange')** with the specified callback is canceled. (The callback object cannot be an anonymous function.) |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

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

## off_macroStatusChanged

```TypeScript
off(type: 'macroStatusChanged', callback?: AsyncCallback<boolean>): void
```

注销相机微距状态变化的监听。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-VideoSession-off(type: 'macroStatusChanged', callback?: AsyncCallback<boolean>): void--><!--Device-VideoSession-off(type: 'macroStatusChanged', callback?: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'macroStatusChanged' | 是 | 注销监听事件，固定为'macroStatusChanged'，session创建成功可触发此事件。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;boolean&gt; | 否 | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否则参数默认为空，取消所有callback, 返 回true表示成功，false表示失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.<br>**适用版本：** 11 - 19 |

## onApertureInfoChange

```TypeScript
onApertureInfoChange(callback: Callback<ApertureInfo>): void
```

Subscribes aperture info event callback.

**起始版本：** 26.1.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.1.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VideoSession-onApertureInfoChange(callback: Callback<ApertureInfo>): void--><!--Device-VideoSession-onApertureInfoChange(callback: Callback<ApertureInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[ApertureInfo](arkts-camera-camera-apertureinfo-i-sys.md)&gt; | 是 | Callback used to get the aperture info. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## onEffectSuggestionChange

```TypeScript
onEffectSuggestionChange(callback: AsyncCallback<EffectSuggestionType>): void
```

Subscribes to effect suggestion change events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-VideoSession-onEffectSuggestionChange(callback: AsyncCallback<EffectSuggestionType>): void--><!--Device-VideoSession-onEffectSuggestionChange(callback: AsyncCallback<EffectSuggestionType>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[EffectSuggestionType](arkts-camera-camera-effectsuggestiontype-e-sys.md)&gt; | 是 | Callback used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## onFocusTrackingInfoAvailable

```TypeScript
onFocusTrackingInfoAvailable(callback: Callback<FocusTrackingInfo>): void
```

Subscribes to focus tracking info event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-VideoSession-onFocusTrackingInfoAvailable(callback: Callback<FocusTrackingInfo>): void--><!--Device-VideoSession-onFocusTrackingInfoAvailable(callback: Callback<FocusTrackingInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[FocusTrackingInfo](arkts-camera-camera-focustrackinginfo-i-sys.md)&gt; | 是 | Callback used to get the focus tracking info. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## onLcdFlashStatus

```TypeScript
onLcdFlashStatus(callback: AsyncCallback<LcdFlashStatus>): void
```

Subscribes to lcd flash status.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-VideoSession-onLcdFlashStatus(callback: AsyncCallback<LcdFlashStatus>): void--><!--Device-VideoSession-onLcdFlashStatus(callback: AsyncCallback<LcdFlashStatus>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[LcdFlashStatus](arkts-camera-camera-lcdflashstatus-i-sys.md)&gt; | 是 | Callback used to get the lcd flash status. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## onLightStatusChange

```TypeScript
onLightStatusChange(callback: AsyncCallback<LightStatus>): void
```

Subscribes camera light status event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-VideoSession-onLightStatusChange(callback: AsyncCallback<LightStatus>): void--><!--Device-VideoSession-onLightStatusChange(callback: AsyncCallback<LightStatus>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[LightStatus](arkts-camera-camera-lightstatus-e-sys.md)&gt; | 是 | Callback used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## on_effectSuggestionChange

```TypeScript
on(type: 'effectSuggestionChange', callback: AsyncCallback<EffectSuggestionType>): void
```

Subscribes to effect suggestion change events.

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

<!--Device-VideoSession-on(type: 'effectSuggestionChange', callback: AsyncCallback<EffectSuggestionType>): void--><!--Device-VideoSession-on(type: 'effectSuggestionChange', callback: AsyncCallback<EffectSuggestionType>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'effectSuggestionChange' | 是 | Event type. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[EffectSuggestionType](arkts-camera-camera-effectsuggestiontype-e-sys.md)&gt; | 是 | Callback used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## on_focusTrackingInfoAvailable

```TypeScript
on(type: 'focusTrackingInfoAvailable', callback: Callback<FocusTrackingInfo>): void
```

Subscribes to focus tracking information events. This API uses an asynchronous callback to return the result.

**起始版本：** 15

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为15。

**废弃版本：** -1

<!--Device-VideoSession-on(type: 'focusTrackingInfoAvailable', callback: Callback<FocusTrackingInfo>): void--><!--Device-VideoSession-on(type: 'focusTrackingInfoAvailable', callback: Callback<FocusTrackingInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'focusTrackingInfoAvailable' | 是 | Event type. The value is fixed at **'focusTrackingInfoAvailable'**. The event can be listened for when a VideoSessionForSys object is created. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[FocusTrackingInfo](arkts-camera-camera-focustrackinginfo-i-sys.md)&gt; | 是 | Callback used to return the focus tracking information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

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

## on_lcdFlashStatus

```TypeScript
on(type: 'lcdFlashStatus', callback: AsyncCallback<LcdFlashStatus>): void
```

Subscribes to LCD flash status change events. This API uses an asynchronous callback to return the result.

**起始版本：** 13

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为13。

**废弃版本：** -1

<!--Device-VideoSession-on(type: 'lcdFlashStatus', callback: AsyncCallback<LcdFlashStatus>): void--><!--Device-VideoSession-on(type: 'lcdFlashStatus', callback: AsyncCallback<LcdFlashStatus>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'lcdFlashStatus' | 是 | Event type. The value is fixed at **'lcdFlashStatus'**. The event can be listened for when a session is created. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[LcdFlashStatus](arkts-camera-camera-lcdflashstatus-i-sys.md)&gt; | 是 | Callback used to return the LCD flash status change. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

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

## on_lightStatusChange

```TypeScript
on(type: 'lightStatusChange', callback: AsyncCallback<LightStatus>): void
```

Subscribes to camera light status changes. This API uses an asynchronous callback to return the result.

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

<!--Device-VideoSession-on(type: 'lightStatusChange', callback: AsyncCallback<LightStatus>): void--><!--Device-VideoSession-on(type: 'lightStatusChange', callback: AsyncCallback<LightStatus>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'lightStatusChange' | 是 | Event type. The value is fixed at **'lightStatusChange'**. &lt;br&gt;The event can be listened for when a VideoSessionForSys object is created. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[LightStatus](arkts-camera-camera-lightstatus-e-sys.md)&gt; | 是 | Callback used to return the light status information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

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

## on_macroStatusChanged

```TypeScript
on(type: 'macroStatusChanged', callback: AsyncCallback<boolean>): void
```

监听相机微距状态变化，通过注册回调函数获取结果。使用callback异步回调。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-VideoSession-on(type: 'macroStatusChanged', callback: AsyncCallback<boolean>): void--><!--Device-VideoSession-on(type: 'macroStatusChanged', callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'macroStatusChanged' | 是 | 监听事件，固定为'macroStatusChanged'，session创建成功可监听。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;boolean&gt; | 是 | 回调函数，用于获取当前微距状态，返回true是开启状态，返回false是禁用状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.<br>**适用版本：** 11 - 19 |

