# ProfessionalVideoSession（系统接口）

ProfessionalVideoSession extends Session, AutoExposure, ManualExposure, Focus, ManualFocus, WhiteBalance, ManualIso , Flash, Zoom, ColorEffect, Aperture Implements a professional video session, which sets the parameters of the professional video mode and saves all [CameraInput](arkts-camera-camera-camerainput-i.md#CameraInput) and [CameraOutput](arkts-camera-camera-cameraoutput-i.md#CameraOutput) instances required to run the camera. It inherits from [Session](arkts-camera-camera-session-i.md#Session).

**继承/实现关系：** ProfessionalVideoSession extends [Session](arkts-camera-camera-session-i.md#Session), [AutoExposure](arkts-camera-camera-autoexposure-i.md#AutoExposure), [ManualExposure](arkts-camera-camera-manualexposure-i.md#ManualExposure（系统接口）), [Focus](arkts-camera-camera-focus-i.md#Focus), [ManualFocus](arkts-camera-camera-manualfocus-i-sys.md#ManualFocus（系统接口）), [WhiteBalance](arkts-camera-camera-whitebalance-i.md#WhiteBalance（系统接口）), [ManualIso](arkts-camera-camera-manualiso-i-sys.md#ManualIso（系统接口）), [Flash](arkts-camera-camera-flash-i.md#Flash), [Zoom](arkts-camera-camera-zoom-i.md#Zoom), [ColorEffect](arkts-camera-camera-coloreffect-i-sys.md#ColorEffect（系统接口）), [Aperture](arkts-camera-camera-aperture-i-sys.md#Aperture（系统接口）)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-camera-interface ProfessionalVideoSession--><!--Device-camera-interface ProfessionalVideoSession-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## offApertureInfoChange

```TypeScript
offApertureInfoChange(callback?: AsyncCallback<ApertureInfo>): void
```

Unsubscribes from aperture info event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ProfessionalVideoSession-offApertureInfoChange(callback?: AsyncCallback<ApertureInfo>): void--><!--Device-ProfessionalVideoSession-offApertureInfoChange(callback?: AsyncCallback<ApertureInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[ApertureInfo](arkts-camera-camera-apertureinfo-i-sys.md)&gt; | 否 | Callback used to get the aperture info. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## offError

```TypeScript
offError(callback?: ErrorCallback): void
```

Unsubscribes from error events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ProfessionalVideoSession-offError(callback?: ErrorCallback): void--><!--Device-ProfessionalVideoSession-offError(callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ErrorCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-errorcallback-t.md) | 否 | Callback used to get the capture session errors. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## offExposureInfoChange

```TypeScript
offExposureInfoChange(callback?: AsyncCallback<ExposureInfo>): void
```

Unsubscribes from exposure info event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ProfessionalVideoSession-offExposureInfoChange(callback?: AsyncCallback<ExposureInfo>): void--><!--Device-ProfessionalVideoSession-offExposureInfoChange(callback?: AsyncCallback<ExposureInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[ExposureInfo](arkts-camera-camera-exposureinfo-i-sys.md)&gt; | 否 | Callback used to get the exposure info. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## offFocusStateChange

```TypeScript
offFocusStateChange(callback?: AsyncCallback<FocusState>): void
```

Unsubscribes from focus state change event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ProfessionalVideoSession-offFocusStateChange(callback?: AsyncCallback<FocusState>): void--><!--Device-ProfessionalVideoSession-offFocusStateChange(callback?: AsyncCallback<FocusState>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[FocusState](arkts-camera-camera-focusstate-e.md)&gt; | 否 | Callback used to get the focus state change. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## offIsoInfoChange

```TypeScript
offIsoInfoChange(callback?: AsyncCallback<IsoInfo>): void
```

Unsubscribes from ISO info event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ProfessionalVideoSession-offIsoInfoChange(callback?: AsyncCallback<IsoInfo>): void--><!--Device-ProfessionalVideoSession-offIsoInfoChange(callback?: AsyncCallback<IsoInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[IsoInfo](arkts-camera-camera-isoinfo-i-sys.md)&gt; | 否 | Callback used to get the ISO info. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## offLuminationInfoChange

```TypeScript
offLuminationInfoChange(callback?: AsyncCallback<LuminationInfo>): void
```

Unsubscribes from lumination info event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ProfessionalVideoSession-offLuminationInfoChange(callback?: AsyncCallback<LuminationInfo>): void--><!--Device-ProfessionalVideoSession-offLuminationInfoChange(callback?: AsyncCallback<LuminationInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[LuminationInfo](arkts-camera-camera-luminationinfo-i-sys.md)&gt; | 否 | Callback used to get the lumination info. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## offSmoothZoomInfoAvailable

```TypeScript
offSmoothZoomInfoAvailable(callback?: AsyncCallback<SmoothZoomInfo>): void
```

Unsubscribes from zoom info event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ProfessionalVideoSession-offSmoothZoomInfoAvailable(callback?: AsyncCallback<SmoothZoomInfo>): void--><!--Device-ProfessionalVideoSession-offSmoothZoomInfoAvailable(callback?: AsyncCallback<SmoothZoomInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[SmoothZoomInfo](arkts-camera-camera-smoothzoominfo-i.md)&gt; | 否 | Callback used to get the zoom info. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## off_apertureInfoChange

```TypeScript
off(type: 'apertureInfoChange', callback?: AsyncCallback<ApertureInfo>): void
```

Unsubscribes from aperture change events.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-ProfessionalVideoSession-off(type: 'apertureInfoChange', callback?: AsyncCallback<ApertureInfo>): void--><!--Device-ProfessionalVideoSession-off(type: 'apertureInfoChange', callback?: AsyncCallback<ApertureInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'apertureInfoChange' | 是 | Event type. The value is fixed at **'apertureInfoChange'**. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[ApertureInfo](arkts-camera-camera-apertureinfo-i-sys.md)&gt; | 否 | Callback, which is optional and is used to match **callback** in **on('apertureInfoChange')**. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

```TypeScript
function unregisterApertureInfoEvent(professionalVideoSession: camera.ProfessionalVideoSession): void {
  professionalVideoSession.off('apertureInfoChange');
}
```

## off_error

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

Unsubscribes from HighResolutionPhotoSession error events.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-ProfessionalVideoSession-off(type: 'error', callback?: ErrorCallback): void--><!--Device-ProfessionalVideoSession-off(type: 'error', callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | Event type. The value is fixed at **'error'**. The event can be listened for when a session is created. |
| callback | [ErrorCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-errorcallback-t.md) | 否 | Callback used to return the result. This parameter is optional. If this parameter is specified, the subscription to the specified event **on('error')** with the specified callback is canceled. (The callback object cannot be an anonymous function.) |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

```TypeScript
function unregisterSessionError(professionalVideoSession: camera.ProfessionalVideoSession): void {
  professionalVideoSession.off('error');
}
```

## off_exposureInfoChange

```TypeScript
off(type: 'exposureInfoChange', callback?: AsyncCallback<ExposureInfo>): void
```

Unsubscribes from exposure information change events.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-ProfessionalVideoSession-off(type: 'exposureInfoChange', callback?: AsyncCallback<ExposureInfo>): void--><!--Device-ProfessionalVideoSession-off(type: 'exposureInfoChange', callback?: AsyncCallback<ExposureInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'exposureInfoChange' | 是 | Event type. The value is fixed at **'exposureInfoChange'**. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[ExposureInfo](arkts-camera-camera-exposureinfo-i-sys.md)&gt; | 否 | Callback, which is optional and is used to match **callback** in **on('exposureInfoChange')**. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

```TypeScript
function unregisterExposureInfoEvent(professionalVideoSession: camera.ProfessionalVideoSession): void {
  professionalVideoSession.off('exposureInfoChange');
}
```

## off_focusStateChange

```TypeScript
off(type: 'focusStateChange', callback?: AsyncCallback<FocusState>): void
```

Unsubscribes from focus state change events.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-ProfessionalVideoSession-off(type: 'focusStateChange', callback?: AsyncCallback<FocusState>): void--><!--Device-ProfessionalVideoSession-off(type: 'focusStateChange', callback?: AsyncCallback<FocusState>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'focusStateChange' | 是 | Event type. The value is fixed at **'focusStateChange'**. The event can be listened for when a session is created. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[FocusState](arkts-camera-camera-focusstate-e.md)&gt; | 否 | Callback used to return the result. This parameter is optional. If this parameter is specified, the subscription to the specified event **on('focusStateChange')** with the specified callback is canceled. (The callback object cannot be an anonymous function.) |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

```TypeScript
function unregisterFocusStateChange(professionalVideoSession: camera.ProfessionalVideoSession): void {
  professionalVideoSession.off('focusStateChange');
}
```

## off_isoInfoChange

```TypeScript
off(type: 'isoInfoChange', callback?: AsyncCallback<IsoInfo>): void
```

Unsubscribes from automatic ISO change events.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-ProfessionalVideoSession-off(type: 'isoInfoChange', callback?: AsyncCallback<IsoInfo>): void--><!--Device-ProfessionalVideoSession-off(type: 'isoInfoChange', callback?: AsyncCallback<IsoInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'isoInfoChange' | 是 | Event type. The value is fixed at **'isoInfoChange'**. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[IsoInfo](arkts-camera-camera-isoinfo-i-sys.md)&gt; | 否 | Callback, which is optional and is used to match **callback** in **on('isoInfoChange')**. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

```TypeScript
function unregisterIsoInfoEvent(professionalVideoSession: camera.ProfessionalVideoSession): void {
  professionalVideoSession.off('isoInfoChange');
}
```

## off_luminationInfoChange

```TypeScript
off(type: 'luminationInfoChange', callback?: AsyncCallback<LuminationInfo>): void
```

Unsubscribes from illumination change events.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-ProfessionalVideoSession-off(type: 'luminationInfoChange', callback?: AsyncCallback<LuminationInfo>): void--><!--Device-ProfessionalVideoSession-off(type: 'luminationInfoChange', callback?: AsyncCallback<LuminationInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'luminationInfoChange' | 是 | Event type. The value is fixed at **'luminationInfoChange'**. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[LuminationInfo](arkts-camera-camera-luminationinfo-i-sys.md)&gt; | 否 | Callback, which is optional and is used to match **callback** in **on('luminationInfoChange')**. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

```TypeScript
function unregisterLuminationInfoEvent(professionalVideoSession: camera.ProfessionalVideoSession): void {
  professionalVideoSession.off('luminationInfoChange');
}
```

## off_smoothZoomInfoAvailable

```TypeScript
off(type: 'smoothZoomInfoAvailable', callback?: AsyncCallback<SmoothZoomInfo>): void
```

Unsubscribes from smooth zoom state change events.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-ProfessionalVideoSession-off(type: 'smoothZoomInfoAvailable', callback?: AsyncCallback<SmoothZoomInfo>): void--><!--Device-ProfessionalVideoSession-off(type: 'smoothZoomInfoAvailable', callback?: AsyncCallback<SmoothZoomInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'smoothZoomInfoAvailable' | 是 | Event type. The value is fixed at **'smoothZoomInfoAvailable'**. The event can be listened for when a session is created. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[SmoothZoomInfo](arkts-camera-camera-smoothzoominfo-i.md)&gt; | 否 | Callback used to return the result. This parameter is optional. If this parameter is specified, the subscription to the specified event **on('smoothZoomInfoAvailable')** with the specified callback is canceled. (The callback object cannot be an anonymous function.) |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

```TypeScript
function unregisterSmoothZoomInfo(professionalVideoSession: camera.ProfessionalVideoSession): void {
  professionalVideoSession.off('smoothZoomInfoAvailable');
}
```

## onApertureInfoChange

```TypeScript
onApertureInfoChange(callback: AsyncCallback<ApertureInfo>): void
```

Subscribes aperture info event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ProfessionalVideoSession-onApertureInfoChange(callback: AsyncCallback<ApertureInfo>): void--><!--Device-ProfessionalVideoSession-onApertureInfoChange(callback: AsyncCallback<ApertureInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[ApertureInfo](arkts-camera-camera-apertureinfo-i-sys.md)&gt; | 是 | Callback used to get the aperture info. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## onError

```TypeScript
onError(callback: ErrorCallback): void
```

Subscribes to error events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ProfessionalVideoSession-onError(callback: ErrorCallback): void--><!--Device-ProfessionalVideoSession-onError(callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ErrorCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-errorcallback-t.md) | 是 | Callback used to get the capture session errors. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## onExposureInfoChange

```TypeScript
onExposureInfoChange(callback: AsyncCallback<ExposureInfo>): void
```

Subscribes exposure info event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ProfessionalVideoSession-onExposureInfoChange(callback: AsyncCallback<ExposureInfo>): void--><!--Device-ProfessionalVideoSession-onExposureInfoChange(callback: AsyncCallback<ExposureInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[ExposureInfo](arkts-camera-camera-exposureinfo-i-sys.md)&gt; | 是 | Callback used to get the exposure info. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## onFocusStateChange

```TypeScript
onFocusStateChange(callback: AsyncCallback<FocusState>): void
```

Subscribes focus state change event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ProfessionalVideoSession-onFocusStateChange(callback: AsyncCallback<FocusState>): void--><!--Device-ProfessionalVideoSession-onFocusStateChange(callback: AsyncCallback<FocusState>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[FocusState](arkts-camera-camera-focusstate-e.md)&gt; | 是 | Callback used to get the focus state change. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## onIsoInfoChange

```TypeScript
onIsoInfoChange(callback: AsyncCallback<IsoInfo>): void
```

Subscribes ISO info event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ProfessionalVideoSession-onIsoInfoChange(callback: AsyncCallback<IsoInfo>): void--><!--Device-ProfessionalVideoSession-onIsoInfoChange(callback: AsyncCallback<IsoInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[IsoInfo](arkts-camera-camera-isoinfo-i-sys.md)&gt; | 是 | Callback used to get the ISO info. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## onLuminationInfoChange

```TypeScript
onLuminationInfoChange(callback: AsyncCallback<LuminationInfo>): void
```

Subscribes lumination info event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ProfessionalVideoSession-onLuminationInfoChange(callback: AsyncCallback<LuminationInfo>): void--><!--Device-ProfessionalVideoSession-onLuminationInfoChange(callback: AsyncCallback<LuminationInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[LuminationInfo](arkts-camera-camera-luminationinfo-i-sys.md)&gt; | 是 | Callback used to get the lumination info. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## onSmoothZoomInfoAvailable

```TypeScript
onSmoothZoomInfoAvailable(callback: AsyncCallback<SmoothZoomInfo>): void
```

Subscribes zoom info event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ProfessionalVideoSession-onSmoothZoomInfoAvailable(callback: AsyncCallback<SmoothZoomInfo>): void--><!--Device-ProfessionalVideoSession-onSmoothZoomInfoAvailable(callback: AsyncCallback<SmoothZoomInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[SmoothZoomInfo](arkts-camera-camera-smoothzoominfo-i.md)&gt; | 是 | Callback used to get the zoom info. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## on_apertureInfoChange

```TypeScript
on(type: 'apertureInfoChange', callback: AsyncCallback<ApertureInfo>): void
```

Subscribes to aperture change events to obtain the real-time aperture information. This API uses an asynchronous callback to return the result.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-ProfessionalVideoSession-on(type: 'apertureInfoChange', callback: AsyncCallback<ApertureInfo>): void--><!--Device-ProfessionalVideoSession-on(type: 'apertureInfoChange', callback: AsyncCallback<ApertureInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'apertureInfoChange' | 是 | Event type. The value is fixed at **'apertureInfoChange'**. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[ApertureInfo](arkts-camera-camera-apertureinfo-i-sys.md)&gt; | 是 | Callback used to return the aperture information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

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

## on_error

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

Subscribes to HighResolutionPhotoSession error events. This API uses an asynchronous callback to return the result.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-ProfessionalVideoSession-on(type: 'error', callback: ErrorCallback): void--><!--Device-ProfessionalVideoSession-on(type: 'error', callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | Event type. The value is fixed at **'error'**. The event can be listened for when a session is created. This event is triggered and the error message is returned when an error occurs during the calling of a session-related API such as [beginConfig](arkts-camera-camera-session-i.md#beginConfig), [commitConfig](arkts-camera-camera-session-i.md#commitConfig), and [addInput](arkts-camera-camera-session-i.md#addInput). |
| callback | [ErrorCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-errorcallback-t.md) | 是 | Callback used to return an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md#CameraErrorCode). |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function callback(err: BusinessError): void {
  console.error(`Professional video session error code: ${err.code}`);
}

function registerSessionError(professionalVideoSession: camera.ProfessionalVideoSession): void {
  professionalVideoSession.on('error', callback);
}
```

## on_exposureInfoChange

```TypeScript
on(type: 'exposureInfoChange', callback: AsyncCallback<ExposureInfo>): void
```

Subscribes to exposure information change events to obtain the exposure information. This API uses an asynchronous callback to return the result.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-ProfessionalVideoSession-on(type: 'exposureInfoChange', callback: AsyncCallback<ExposureInfo>): void--><!--Device-ProfessionalVideoSession-on(type: 'exposureInfoChange', callback: AsyncCallback<ExposureInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'exposureInfoChange' | 是 | Event type. The value is fixed at **'exposureInfoChange'**. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[ExposureInfo](arkts-camera-camera-exposureinfo-i-sys.md)&gt; | 是 | Callback used to return the exposure information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

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

## on_focusStateChange

```TypeScript
on(type: 'focusStateChange', callback: AsyncCallback<FocusState>): void
```

Subscribes to focus state change events. This API uses an asynchronous callback to return the result.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-ProfessionalVideoSession-on(type: 'focusStateChange', callback: AsyncCallback<FocusState>): void--><!--Device-ProfessionalVideoSession-on(type: 'focusStateChange', callback: AsyncCallback<FocusState>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'focusStateChange' | 是 | Event type. The value is fixed at **'focusStateChange'**. The event can be listened for when a session is created. This event is triggered only when the camera focus state changes in auto focus mode. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[FocusState](arkts-camera-camera-focusstate-e.md)&gt; | 是 | Callback used to return the focus state change. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

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

## on_isoInfoChange

```TypeScript
on(type: 'isoInfoChange', callback: AsyncCallback<IsoInfo>): void
```

Subscribes to automatic ISO change events to obtain real-time ISO information. This API uses an asynchronous callback to return the result.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-ProfessionalVideoSession-on(type: 'isoInfoChange', callback: AsyncCallback<IsoInfo>): void--><!--Device-ProfessionalVideoSession-on(type: 'isoInfoChange', callback: AsyncCallback<IsoInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'isoInfoChange' | 是 | Event type. The value is fixed at **'isoInfoChange'**. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[IsoInfo](arkts-camera-camera-isoinfo-i-sys.md)&gt; | 是 | Callback used to return the ISO information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

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

## on_luminationInfoChange

```TypeScript
on(type: 'luminationInfoChange', callback: AsyncCallback<LuminationInfo>): void
```

Subscribes to illumination change events to obtain real-time illumination information. This API uses an asynchronous callback to return the result.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-ProfessionalVideoSession-on(type: 'luminationInfoChange', callback: AsyncCallback<LuminationInfo>): void--><!--Device-ProfessionalVideoSession-on(type: 'luminationInfoChange', callback: AsyncCallback<LuminationInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'luminationInfoChange' | 是 | Event type. The value is fixed at **'luminationInfoChange'**. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[LuminationInfo](arkts-camera-camera-luminationinfo-i-sys.md)&gt; | 是 | Callback used to return the illumination information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

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

## on_smoothZoomInfoAvailable

```TypeScript
on(type: 'smoothZoomInfoAvailable', callback: AsyncCallback<SmoothZoomInfo>): void
```

Subscribes to smooth zoom state change events. This API uses an asynchronous callback to return the result.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-ProfessionalVideoSession-on(type: 'smoothZoomInfoAvailable', callback: AsyncCallback<SmoothZoomInfo>): void--><!--Device-ProfessionalVideoSession-on(type: 'smoothZoomInfoAvailable', callback: AsyncCallback<SmoothZoomInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'smoothZoomInfoAvailable' | 是 | Event type. The value is fixed at **'smoothZoomInfoAvailable'**. The event can be listened for when a session is created. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[SmoothZoomInfo](arkts-camera-camera-smoothzoominfo-i.md)&gt; | 是 | Callback used to return the smooth zoom state change. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

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

