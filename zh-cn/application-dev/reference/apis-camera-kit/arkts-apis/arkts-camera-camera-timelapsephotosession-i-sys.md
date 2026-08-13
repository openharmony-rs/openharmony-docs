# TimeLapsePhotoSession（系统接口）

TimeLapsePhotoSession extends Session, Focus, ManualFocus, AutoExposure, ManualExposure, ManualIso, WhiteBalance, Zoom, ColorEffect Implements a time-lapse photo session, which sets the parameters of the time-lapse photo mode and saves all [CameraInput](arkts-camera-camera-camerainput-i.md#CameraInput) and [CameraOutput](arkts-camera-camera-cameraoutput-i.md#CameraOutput) instances required to run the camera. It inherits from [Session](arkts-camera-camera-session-i.md#Session).

**继承/实现关系：** TimeLapsePhotoSession extends [Session](arkts-camera-camera-session-i.md#Session), [Focus](arkts-camera-camera-focus-i.md#Focus), [ManualFocus](arkts-camera-camera-manualfocus-i-sys.md#ManualFocus（系统接口）), [AutoExposure](arkts-camera-camera-autoexposure-i.md#AutoExposure), [ManualExposure](arkts-camera-camera-manualexposure-i.md#ManualExposure（系统接口）), [ManualIso](arkts-camera-camera-manualiso-i-sys.md#ManualIso（系统接口）), [WhiteBalance](arkts-camera-camera-whitebalance-i.md#WhiteBalance（系统接口）), [Zoom](arkts-camera-camera-zoom-i.md#Zoom), [ColorEffect](arkts-camera-camera-coloreffect-i-sys.md#ColorEffect（系统接口）)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-camera-interface TimeLapsePhotoSession--><!--Device-camera-interface TimeLapsePhotoSession-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## getSupportedTimeLapseIntervalRange

```TypeScript
getSupportedTimeLapseIntervalRange(): Array<int>
```

Obtains the supported time-lapse shooting interval range.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-TimeLapsePhotoSession-getSupportedTimeLapseIntervalRange(): Array<int>--><!--Device-TimeLapsePhotoSession-getSupportedTimeLapseIntervalRange(): Array<int>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;int&gt; | Interval range, in ms. The value depends on the underlying capability. If the operation fails, an error code defined in [CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getSupportedTimeLapseIntervalRange(timeLapsePhotoSession: camera.TimeLapsePhotoSession): Array<number> {
  let intervalRange: Array<number> = [];
  try {
    intervalRange = timeLapsePhotoSession.getSupportedTimeLapseIntervalRange();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The getSupportedTimeLapseIntervalRange call failed. error code: ${err.code}`);
  }
  return intervalRange;
}
```

## getTimeLapseInterval

```TypeScript
getTimeLapseInterval(): int
```

Obtains the current time-lapse shooting interval.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-TimeLapsePhotoSession-getTimeLapseInterval(): int--><!--Device-TimeLapsePhotoSession-getTimeLapseInterval(): int-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | Shooting interval, in ms. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getTimeLapseInterval(timeLapsePhotoSession: camera.TimeLapsePhotoSession): number {
  let interval: number = 0;
  try {
    interval = timeLapsePhotoSession.getTimeLapseInterval();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The getTimeLapseInterval call failed. error code: ${err.code}`);
  }
  return interval;
}
```

## getTimeLapsePreviewType

```TypeScript
getTimeLapsePreviewType(): TimeLapsePreviewType
```

Obtains the time-lapse preview type.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-TimeLapsePhotoSession-getTimeLapsePreviewType(): TimeLapsePreviewType--><!--Device-TimeLapsePhotoSession-getTimeLapsePreviewType(): TimeLapsePreviewType-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TimeLapsePreviewType](arkts-camera-camera-timelapsepreviewtype-e-sys.md) | Preview type. If the operation fails, an error code defined in [CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getTimeLapsePreviewType(timeLapsePhotoSession: camera.TimeLapsePhotoSession): camera.TimeLapsePreviewType {
  let type = camera.TimeLapsePreviewType.DARK;
  try {
    type = timeLapsePhotoSession.getTimeLapsePreviewType();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The getTimeLapsePreviewType call failed. error code: ${err.code}`);
  }
  return type;
}
```

## getTimeLapseRecordState

```TypeScript
getTimeLapseRecordState(): TimeLapseRecordState
```

Obtains the time-lapse shooting state.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-TimeLapsePhotoSession-getTimeLapseRecordState(): TimeLapseRecordState--><!--Device-TimeLapsePhotoSession-getTimeLapseRecordState(): TimeLapseRecordState-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TimeLapseRecordState](arkts-camera-camera-timelapserecordstate-e-sys.md) | Shooting state. If the operation fails, an error code defined in [CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getTimeLapseRecordState(timeLapsePhotoSession: camera.TimeLapsePhotoSession): camera.TimeLapseRecordState {
  let state = camera.TimeLapseRecordState.IDLE;
  try {
    state = timeLapsePhotoSession.getTimeLapseRecordState();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The getTimeLapseRecordState call failed. error code: ${err.code}`);
  }
  return state;
}
```

## isTryAENeeded

```TypeScript
isTryAENeeded(): boolean
```

Checks whether Try AE is required.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-TimeLapsePhotoSession-isTryAENeeded(): boolean--><!--Device-TimeLapsePhotoSession-isTryAENeeded(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Check result for whether Try AE is required. **true** if required, **false** otherwise. The error code type is defined in [CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function isTryAENeeded(timeLapsePhotoSession: camera.TimeLapsePhotoSession): boolean {
  let needed = false;
  try {
    needed = timeLapsePhotoSession.isTryAENeeded();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The isTryAENeeded call failed. error code: ${err.code}`);
  }
  return needed;
}
```

## offError

```TypeScript
offError(callback?: ErrorCallback): void
```

Unsubscribes from error events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-TimeLapsePhotoSession-offError(callback?: ErrorCallback): void--><!--Device-TimeLapsePhotoSession-offError(callback?: ErrorCallback): void-End-->

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

<!--Device-TimeLapsePhotoSession-offExposureInfoChange(callback?: AsyncCallback<ExposureInfo>): void--><!--Device-TimeLapsePhotoSession-offExposureInfoChange(callback?: AsyncCallback<ExposureInfo>): void-End-->

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

<!--Device-TimeLapsePhotoSession-offFocusStateChange(callback?: AsyncCallback<FocusState>): void--><!--Device-TimeLapsePhotoSession-offFocusStateChange(callback?: AsyncCallback<FocusState>): void-End-->

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

<!--Device-TimeLapsePhotoSession-offIsoInfoChange(callback?: AsyncCallback<IsoInfo>): void--><!--Device-TimeLapsePhotoSession-offIsoInfoChange(callback?: AsyncCallback<IsoInfo>): void-End-->

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

<!--Device-TimeLapsePhotoSession-offLuminationInfoChange(callback?: AsyncCallback<LuminationInfo>): void--><!--Device-TimeLapsePhotoSession-offLuminationInfoChange(callback?: AsyncCallback<LuminationInfo>): void-End-->

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

## offTryAEInfoChange

```TypeScript
offTryAEInfoChange(callback?: AsyncCallback<TryAEInfo>): void
```

Unsubscribes from try AE info event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-TimeLapsePhotoSession-offTryAEInfoChange(callback?: AsyncCallback<TryAEInfo>): void--><!--Device-TimeLapsePhotoSession-offTryAEInfoChange(callback?: AsyncCallback<TryAEInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[TryAEInfo](arkts-camera-camera-tryaeinfo-i-sys.md)&gt; | 否 | Callback used to get the try AE info. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## off_error

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

Unsubscribes from HighResolutionPhotoSession error events.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-TimeLapsePhotoSession-off(type: 'error', callback?: ErrorCallback): void--><!--Device-TimeLapsePhotoSession-off(type: 'error', callback?: ErrorCallback): void-End-->

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
function unregisterSessionError(timeLapsePhotoSession: camera.TimeLapsePhotoSession): void {
  timeLapsePhotoSession.off('error');
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

<!--Device-TimeLapsePhotoSession-off(type: 'exposureInfoChange', callback?: AsyncCallback<ExposureInfo>): void--><!--Device-TimeLapsePhotoSession-off(type: 'exposureInfoChange', callback?: AsyncCallback<ExposureInfo>): void-End-->

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
function unregisterExposureInfoEvent(timeLapsePhotoSession: camera.TimeLapsePhotoSession): void {
  timeLapsePhotoSession.off('exposureInfoChange');
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

<!--Device-TimeLapsePhotoSession-off(type: 'focusStateChange', callback?: AsyncCallback<FocusState>): void--><!--Device-TimeLapsePhotoSession-off(type: 'focusStateChange', callback?: AsyncCallback<FocusState>): void-End-->

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
function unregisterFocusStateChange(timeLapsePhotoSession: camera.TimeLapsePhotoSession): void {
  timeLapsePhotoSession.off('focusStateChange');
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

<!--Device-TimeLapsePhotoSession-off(type: 'isoInfoChange', callback?: AsyncCallback<IsoInfo>): void--><!--Device-TimeLapsePhotoSession-off(type: 'isoInfoChange', callback?: AsyncCallback<IsoInfo>): void-End-->

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
function unregisterIsoInfoEvent(timeLapsePhotoSession: camera.TimeLapsePhotoSession): void {
  timeLapsePhotoSession.off('isoInfoChange');
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

<!--Device-TimeLapsePhotoSession-off(type: 'luminationInfoChange', callback?: AsyncCallback<LuminationInfo>): void--><!--Device-TimeLapsePhotoSession-off(type: 'luminationInfoChange', callback?: AsyncCallback<LuminationInfo>): void-End-->

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
function unregisterLuminationInfoEvent(timeLapsePhotoSession: camera.TimeLapsePhotoSession): void {
  timeLapsePhotoSession.off('luminationInfoChange');
}
```

## off_tryAEInfoChange

```TypeScript
off(type: 'tryAEInfoChange', callback?: AsyncCallback<TryAEInfo>): void
```

Unsubscribes from Try AE change events.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-TimeLapsePhotoSession-off(type: 'tryAEInfoChange', callback?: AsyncCallback<TryAEInfo>): void--><!--Device-TimeLapsePhotoSession-off(type: 'tryAEInfoChange', callback?: AsyncCallback<TryAEInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'tryAEInfoChange' | 是 | Event type. The value is fixed at **'tryAEInfoChange'**. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[TryAEInfo](arkts-camera-camera-tryaeinfo-i-sys.md)&gt; | 否 | Callback, which is optional and is used to match **callback** in **on('tryAEInfoChange')**. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

```TypeScript
function unregisterTryAEInfoEvent(timeLapsePhotoSession: camera.TimeLapsePhotoSession): void {
  timeLapsePhotoSession.off('tryAEInfoChange');
}
```

## onError

```TypeScript
onError(callback: ErrorCallback): void
```

Subscribes to error events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-TimeLapsePhotoSession-onError(callback: ErrorCallback): void--><!--Device-TimeLapsePhotoSession-onError(callback: ErrorCallback): void-End-->

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

<!--Device-TimeLapsePhotoSession-onExposureInfoChange(callback: AsyncCallback<ExposureInfo>): void--><!--Device-TimeLapsePhotoSession-onExposureInfoChange(callback: AsyncCallback<ExposureInfo>): void-End-->

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

<!--Device-TimeLapsePhotoSession-onFocusStateChange(callback: AsyncCallback<FocusState>): void--><!--Device-TimeLapsePhotoSession-onFocusStateChange(callback: AsyncCallback<FocusState>): void-End-->

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

<!--Device-TimeLapsePhotoSession-onIsoInfoChange(callback: AsyncCallback<IsoInfo>): void--><!--Device-TimeLapsePhotoSession-onIsoInfoChange(callback: AsyncCallback<IsoInfo>): void-End-->

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

<!--Device-TimeLapsePhotoSession-onLuminationInfoChange(callback: AsyncCallback<LuminationInfo>): void--><!--Device-TimeLapsePhotoSession-onLuminationInfoChange(callback: AsyncCallback<LuminationInfo>): void-End-->

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

## onTryAEInfoChange

```TypeScript
onTryAEInfoChange(callback: AsyncCallback<TryAEInfo>): void
```

Subscribes try AE info event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-TimeLapsePhotoSession-onTryAEInfoChange(callback: AsyncCallback<TryAEInfo>): void--><!--Device-TimeLapsePhotoSession-onTryAEInfoChange(callback: AsyncCallback<TryAEInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[TryAEInfo](arkts-camera-camera-tryaeinfo-i-sys.md)&gt; | 是 | Callback used to get the try AE info. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## on_error

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

Subscribes to HighResolutionPhotoSession error events. This API uses an asynchronous callback to return the result.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-TimeLapsePhotoSession-on(type: 'error', callback: ErrorCallback): void--><!--Device-TimeLapsePhotoSession-on(type: 'error', callback: ErrorCallback): void-End-->

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
  console.error(`Time lapse photo session error code: ${err.code}`);
}

function registerSessionError(timeLapsePhotoSession: camera.TimeLapsePhotoSession): void {
  timeLapsePhotoSession.on('error', callback);
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

<!--Device-TimeLapsePhotoSession-on(type: 'exposureInfoChange', callback: AsyncCallback<ExposureInfo>): void--><!--Device-TimeLapsePhotoSession-on(type: 'exposureInfoChange', callback: AsyncCallback<ExposureInfo>): void-End-->

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

function registerExposureInfoEvent(timeLapsePhotoSession: camera.TimeLapsePhotoSession): void {
  timeLapsePhotoSession.on('exposureInfoChange', exposureInfoCallback);
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

<!--Device-TimeLapsePhotoSession-on(type: 'focusStateChange', callback: AsyncCallback<FocusState>): void--><!--Device-TimeLapsePhotoSession-on(type: 'focusStateChange', callback: AsyncCallback<FocusState>): void-End-->

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

function registerFocusStateChange(timeLapsePhotoSession: camera.TimeLapsePhotoSession): void {
  timeLapsePhotoSession.on('focusStateChange', callback);
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

<!--Device-TimeLapsePhotoSession-on(type: 'isoInfoChange', callback: AsyncCallback<IsoInfo>): void--><!--Device-TimeLapsePhotoSession-on(type: 'isoInfoChange', callback: AsyncCallback<IsoInfo>): void-End-->

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

function registerIsoInfoEvent(timeLapsePhotoSession: camera.TimeLapsePhotoSession): void {
  timeLapsePhotoSession.on('isoInfoChange', isoInfoCallback);
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

<!--Device-TimeLapsePhotoSession-on(type: 'luminationInfoChange', callback: AsyncCallback<LuminationInfo>): void--><!--Device-TimeLapsePhotoSession-on(type: 'luminationInfoChange', callback: AsyncCallback<LuminationInfo>): void-End-->

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

function registerLuminationInfoEvent(timeLapsePhotoSession: camera.TimeLapsePhotoSession): void {
  timeLapsePhotoSession.on('luminationInfoChange', luminationInfoCallback);
}
```

## on_tryAEInfoChange

```TypeScript
on(type: 'tryAEInfoChange', callback: AsyncCallback<TryAEInfo>): void
```

Subscribes to Try AE change events to obtain real-time Try AE parameters. This API uses an asynchronous callback to return the result.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-TimeLapsePhotoSession-on(type: 'tryAEInfoChange', callback: AsyncCallback<TryAEInfo>): void--><!--Device-TimeLapsePhotoSession-on(type: 'tryAEInfoChange', callback: AsyncCallback<TryAEInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'tryAEInfoChange' | 是 | Event type. The value is fixed at **'tryAEInfoChange'**. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[TryAEInfo](arkts-camera-camera-tryaeinfo-i-sys.md)&gt; | 是 | Callback used to return the Try AE parameters. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function tryAEInfoCallback(err: BusinessError, info: camera.TryAEInfo): void {
  if (err !== undefined && err.code !== 0) {
    console.error(`Callback Error, errorCode: ${err.code}`);
    return;
  }
  console.info(`TryAEInfo: ${info.isTryAEDone}, ${info.isTryAEHintNeeded}, ${info.previewType}, ${info.captureInterval}`);
}

function registerTryAEInfoEvent(timeLapsePhotoSession: camera.TimeLapsePhotoSession): void {
  timeLapsePhotoSession.on('tryAEInfoChange', tryAEInfoCallback);
}
```

## setTimeLapseInterval

```TypeScript
setTimeLapseInterval(interval: int): void
```

Sets a time-lapse shooting interval.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-TimeLapsePhotoSession-setTimeLapseInterval(interval: int): void--><!--Device-TimeLapsePhotoSession-setTimeLapseInterval(interval: int): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| interval | int | 是 | Shooting interval, in units of ms, the supported range can be obtained by calling [getSupportedTimeLapseIntervalRange](#getSupportedTimeLapseIntervalRange) |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function setTimeLapseInterval(timeLapsePhotoSession: camera.TimeLapsePhotoSession): void {
  try {
    let interval: number = 10000;
    timeLapsePhotoSession.setTimeLapseInterval(interval);
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The setTimeLapseInterval call failed. error code: ${err.code}`);
  }
}
```

## setTimeLapsePreviewType

```TypeScript
setTimeLapsePreviewType(type: TimeLapsePreviewType): void
```

Sets the time-lapse preview type.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-TimeLapsePhotoSession-setTimeLapsePreviewType(type: TimeLapsePreviewType): void--><!--Device-TimeLapsePhotoSession-setTimeLapsePreviewType(type: TimeLapsePreviewType): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [TimeLapsePreviewType](arkts-camera-camera-timelapsepreviewtype-e-sys.md) | 是 | Preview type. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function setTimeLapsePreviewType(timeLapsePhotoSession: camera.TimeLapsePhotoSession): void {
  try {
    timeLapsePhotoSession.setTimeLapsePreviewType(camera.TimeLapsePreviewType.LIGHT);
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The setTimeLapsePreviewType call failed. error code: ${err.code}`);
  }
}
```

## setTimeLapseRecordState

```TypeScript
setTimeLapseRecordState(state: TimeLapseRecordState): void
```

Sets the time-lapse shooting state.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-TimeLapsePhotoSession-setTimeLapseRecordState(state: TimeLapseRecordState): void--><!--Device-TimeLapsePhotoSession-setTimeLapseRecordState(state: TimeLapseRecordState): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| state | [TimeLapseRecordState](arkts-camera-camera-timelapserecordstate-e-sys.md) | 是 | Shooting state. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function setTimeLapseRecordState(timeLapsePhotoSession: camera.TimeLapsePhotoSession): void {
  try {
    timeLapsePhotoSession.setTimeLapseRecordState(camera.TimeLapseRecordState.RECORDING);
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The setTimeLapseRecordState call failed. error code: ${err.code}`);
  }
}
```

## startTryAE

```TypeScript
startTryAE(): void
```

Starts to execute Try AE.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-TimeLapsePhotoSession-startTryAE(): void--><!--Device-TimeLapsePhotoSession-startTryAE(): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function startTryAE(timeLapsePhotoSession: camera.TimeLapsePhotoSession): void {
  try {
    timeLapsePhotoSession.startTryAE();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The startTryAE call failed. error code: ${err.code}`);
  }
}
```

## stopTryAE

```TypeScript
stopTryAE(): void
```

Stops the execution of Try AE.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-TimeLapsePhotoSession-stopTryAE(): void--><!--Device-TimeLapsePhotoSession-stopTryAE(): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function stopTryAE(timeLapsePhotoSession: camera.TimeLapsePhotoSession): void {
  try {
    timeLapsePhotoSession.stopTryAE();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The stopTryAE call failed. error code: ${err.code}`);
  }
}
```

