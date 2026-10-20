# TimeLapsePhotoSession（系统接口）

```TypeScript
interface TimeLapsePhotoSession extends Session, Focus, ManualFocus, AutoExposure, ManualExposure, ManualIso, WhiteBalance, Zoom, ColorEffect
```

TimeLapsePhotoSession 继承 Session, Focus, ManualFocus, AutoExposure, ManualExposure, ManualIso, WhiteBalance, Zoom, ColorEffect实现延时拍照会话，用于设置延时拍照模式的参数，并保存运行相机所需的所有[CameraInput](arkts-camera-camera-camerainput-i.md) 和 [CameraOutput](arkts-camera-camera-cameraoutput-i.md)实例。继承自 [Session](arkts-camera-camera-session-i.md)。

**继承/实现关系：** TimeLapsePhotoSession extends [Session](arkts-camera-camera-session-i.md), [Focus](arkts-camera-camera-focus-i.md), [ManualFocus](arkts-camera-camera-manualfocus-i.md), [AutoExposure](arkts-camera-camera-autoexposure-i.md), [ManualExposure](arkts-camera-camera-manualexposure-i.md), [ManualIso](arkts-camera-camera-manualiso-i.md), [WhiteBalance](arkts-camera-camera-whitebalance-i.md), [Zoom](arkts-camera-camera-zoom-i.md)<!--Del-->, [ColorEffect](arkts-camera-camera-coloreffect-i-sys.md)<!--DelEnd-->

**起始版本：** 12

<!--Device-camera-interface TimeLapsePhotoSession extends Session, Focus, ManualFocus, AutoExposure, ManualExposure, ManualIso, WhiteBalance, Zoom, ColorEffect--><!--Device-camera-interface TimeLapsePhotoSession extends Session, Focus, ManualFocus, AutoExposure, ManualExposure, ManualIso, WhiteBalance, Zoom, ColorEffect-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## getSupportedTimeLapseIntervalRange

```TypeScript
getSupportedTimeLapseIntervalRange(): Array<number>
```

获取支持的延时拍摄间隔范围。

**起始版本：** 12

<!--Device-TimeLapsePhotoSession-getSupportedTimeLapseIntervalRange(): Array<int>--><!--Device-TimeLapsePhotoSession-getSupportedTimeLapseIntervalRange(): Array<int>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;number&gt; | 间隔范围，单位为毫秒。具体值取决于底层能力。如果操作失败，返回 [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) 中定义的错误码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |

<!--Del-->
**示例**

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

<!--DelEnd-->

## getTimeLapseInterval

```TypeScript
getTimeLapseInterval(): number
```

获取当前延时拍摄间隔。

**起始版本：** 12

<!--Device-TimeLapsePhotoSession-getTimeLapseInterval(): int--><!--Device-TimeLapsePhotoSession-getTimeLapseInterval(): int-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 拍摄间隔，单位为毫秒。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

<!--Del-->
**示例**

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

<!--DelEnd-->

## getTimeLapsePreviewType

```TypeScript
getTimeLapsePreviewType(): TimeLapsePreviewType
```

获取延时摄影预览类型。

**起始版本：** 12

<!--Device-TimeLapsePhotoSession-getTimeLapsePreviewType(): TimeLapsePreviewType--><!--Device-TimeLapsePhotoSession-getTimeLapsePreviewType(): TimeLapsePreviewType-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TimeLapsePreviewType](arkts-camera-camera-timelapsepreviewtype-e-sys.md) | 预览类型。如果操作失败，返回[CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) 中定义的错误码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

<!--Del-->
**示例**

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

<!--DelEnd-->

## getTimeLapseRecordState

```TypeScript
getTimeLapseRecordState(): TimeLapseRecordState
```

获取延时拍摄状态。

**起始版本：** 12

<!--Device-TimeLapsePhotoSession-getTimeLapseRecordState(): TimeLapseRecordState--><!--Device-TimeLapsePhotoSession-getTimeLapseRecordState(): TimeLapseRecordState-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TimeLapseRecordState](arkts-camera-camera-timelapserecordstate-e-sys.md) | 拍摄状态。如果操作失败，返回[CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) 中定义的错误码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

<!--Del-->
**示例**

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

<!--DelEnd-->

## isTryAENeeded

```TypeScript
isTryAENeeded(): boolean
```

查询是否需要执行 Try AE。

**起始版本：** 12

<!--Device-TimeLapsePhotoSession-isTryAENeeded(): boolean--><!--Device-TimeLapsePhotoSession-isTryAENeeded(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 查询是否需要执行 Try AE 的结果。**true** 表示需要，**false** 表示不需要。错误码类型定义在 [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) 中。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |

<!--Del-->
**示例**

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

<!--DelEnd-->

## off('error')

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

取消订阅TimeLapsePhotoSession错误事件。

**起始版本：** 12

<!--Device-TimeLapsePhotoSession-off(type: 'error', callback?: ErrorCallback): void--><!--Device-TimeLapsePhotoSession-off(type: 'error', callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 事件类型。值固定为 **'error'**。创建会话后即可监听此事件。 |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | 否 | 用于返回结果的回调。此参数为可选参数。如果指定此参数将取消订阅指定回调的 **on('error')** 事件。（回调对象不能为匿名函数。） |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

<!--Del-->
**示例**

```TypeScript
function unregisterSessionError(timeLapsePhotoSession: camera.TimeLapsePhotoSession): void {
  timeLapsePhotoSession.off('error');
}
```

<!--DelEnd-->

## off('focusStateChange')

```TypeScript
off(type: 'focusStateChange', callback?: AsyncCallback<FocusState>): void
```

取消订阅对焦状态变更事件。

**起始版本：** 12

<!--Device-TimeLapsePhotoSession-off(type: 'focusStateChange', callback?: AsyncCallback<FocusState>): void--><!--Device-TimeLapsePhotoSession-off(type: 'focusStateChange', callback?: AsyncCallback<FocusState>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'focusStateChange' | 是 | 事件类型。值固定为 **'focusStateChange'**。创建会话后即可监听此事件。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FocusState](arkts-camera-camera-focusstate-e.md)&gt; | 否 | 用于返回结果的回调。此参数为可选参数。如果指定此参数，将取消订阅指定回调的 **on('focusStateChange')** 事件。（回调对象不能为匿名函数。） |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

<!--Del-->
**示例**

```TypeScript
function unregisterFocusStateChange(timeLapsePhotoSession: camera.TimeLapsePhotoSession): void {
  timeLapsePhotoSession.off('focusStateChange');
}
```

<!--DelEnd-->

## off('isoInfoChange')

```TypeScript
off(type: 'isoInfoChange', callback?: AsyncCallback<IsoInfo>): void
```

取消订阅自动 ISO 变更事件。

**起始版本：** 12

<!--Device-TimeLapsePhotoSession-off(type: 'isoInfoChange', callback?: AsyncCallback<IsoInfo>): void--><!--Device-TimeLapsePhotoSession-off(type: 'isoInfoChange', callback?: AsyncCallback<IsoInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'isoInfoChange' | 是 | 事件类型。值固定为 **'isoInfoChange'**。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[IsoInfo](arkts-camera-camera-isoinfo-i.md)&gt; | 否 | 回调，为可选参数，用于匹配 **on('isoInfoChange')** 中的 **callback**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

<!--Del-->
**示例**

```TypeScript
function unregisterIsoInfoEvent(timeLapsePhotoSession: camera.TimeLapsePhotoSession): void {
  timeLapsePhotoSession.off('isoInfoChange');
}
```

<!--DelEnd-->

## off('exposureInfoChange')

```TypeScript
off(type: 'exposureInfoChange', callback?: AsyncCallback<ExposureInfo>): void
```

取消订阅曝光信息变更事件。

**起始版本：** 12

<!--Device-TimeLapsePhotoSession-off(type: 'exposureInfoChange', callback?: AsyncCallback<ExposureInfo>): void--><!--Device-TimeLapsePhotoSession-off(type: 'exposureInfoChange', callback?: AsyncCallback<ExposureInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'exposureInfoChange' | 是 | 事件类型。值固定为 **'exposureInfoChange'**。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ExposureInfo](arkts-camera-camera-exposureinfo-i.md)&gt; | 否 | 回调，为可选参数，用于匹配 **on('exposureInfoChange')** 中的 **callback**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

<!--Del-->
**示例**

```TypeScript
function unregisterExposureInfoEvent(timeLapsePhotoSession: camera.TimeLapsePhotoSession): void {
  timeLapsePhotoSession.off('exposureInfoChange');
}
```

<!--DelEnd-->

## off('luminationInfoChange')

```TypeScript
off(type: 'luminationInfoChange', callback?: AsyncCallback<LuminationInfo>): void
```

取消订阅光照变更事件。

**起始版本：** 12

<!--Device-TimeLapsePhotoSession-off(type: 'luminationInfoChange', callback?: AsyncCallback<LuminationInfo>): void--><!--Device-TimeLapsePhotoSession-off(type: 'luminationInfoChange', callback?: AsyncCallback<LuminationInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'luminationInfoChange' | 是 | 事件类型。值固定为 **'luminationInfoChange'** |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[LuminationInfo](arkts-camera-camera-luminationinfo-i-sys.md)&gt; | 否 | 回调，为可选参数，用于匹配 **on('luminationInfoChange')** 中的 **callback**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

<!--Del-->
**示例**

```TypeScript
function unregisterLuminationInfoEvent(timeLapsePhotoSession: camera.TimeLapsePhotoSession): void {
  timeLapsePhotoSession.off('luminationInfoChange');
}
```

<!--DelEnd-->

## off('tryAEInfoChange')

```TypeScript
off(type: 'tryAEInfoChange', callback?: AsyncCallback<TryAEInfo>): void
```

取消订阅 Try AE 变更事件。

**起始版本：** 12

<!--Device-TimeLapsePhotoSession-off(type: 'tryAEInfoChange', callback?: AsyncCallback<TryAEInfo>): void--><!--Device-TimeLapsePhotoSession-off(type: 'tryAEInfoChange', callback?: AsyncCallback<TryAEInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'tryAEInfoChange' | 是 | 事件类型。值固定为 **'tryAEInfoChange'**。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[TryAEInfo](arkts-camera-camera-tryaeinfo-i-sys.md)&gt; | 否 | 回调，为可选参数，用于匹配 **on('tryAEInfoChange')** 中的 **callback**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

<!--Del-->
**示例**

```TypeScript
function unregisterTryAEInfoEvent(timeLapsePhotoSession: camera.TimeLapsePhotoSession): void {
  timeLapsePhotoSession.off('tryAEInfoChange');
}
```

<!--DelEnd-->

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

订阅TimeLapsePhotoSession错误事件。此接口使用异步回调返回结果。

**起始版本：** 12

<!--Device-TimeLapsePhotoSession-on(type: 'error', callback: ErrorCallback): void--><!--Device-TimeLapsePhotoSession-on(type: 'error', callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 事件类型。值固定为 **'error'**。创建会话后即可监听此事件。当调用会话相关 API 如[beginConfig](arkts-camera-camera-session-i.md#beginconfig)、[commitConfig](arkts-camera-camera-session-i.md#commitconfig) 和[addInput](arkts-camera-camera-session-i.md#addinput) 时发生错误，将触发此事件并返回错误信息。 |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | 是 | 用于返回 [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) 中定义的错误码的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function callback(err: BusinessError): void {
  console.error(`Time lapse photo session error code: ${err.code}`);
}

function registerSessionError(timeLapsePhotoSession: camera.TimeLapsePhotoSession): void {
  timeLapsePhotoSession.on('error', callback);
}
```

<!--DelEnd-->

## on('focusStateChange')

```TypeScript
on(type: 'focusStateChange', callback: AsyncCallback<FocusState>): void
```

订阅对焦状态变更事件。此接口使用异步回调返回结果。

**起始版本：** 12

<!--Device-TimeLapsePhotoSession-on(type: 'focusStateChange', callback: AsyncCallback<FocusState>): void--><!--Device-TimeLapsePhotoSession-on(type: 'focusStateChange', callback: AsyncCallback<FocusState>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'focusStateChange' | 是 | 事件类型。值固定为 **'focusStateChange'**。创建会话后即可监听此事件。仅在自动对焦模式下相机对焦状态变更时触发此事件。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FocusState](arkts-camera-camera-focusstate-e.md)&gt; | 是 | 用于返回对焦状态变更的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

<!--Del-->
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

function registerFocusStateChange(timeLapsePhotoSession: camera.TimeLapsePhotoSession): void {
  timeLapsePhotoSession.on('focusStateChange', callback);
}
```

<!--DelEnd-->

## on('isoInfoChange')

```TypeScript
on(type: 'isoInfoChange', callback: AsyncCallback<IsoInfo>): void
```

订阅自动 ISO 变更事件以获取实时 ISO 信息。此接口使用异步回调返回结果。

**起始版本：** 12

<!--Device-TimeLapsePhotoSession-on(type: 'isoInfoChange', callback: AsyncCallback<IsoInfo>): void--><!--Device-TimeLapsePhotoSession-on(type: 'isoInfoChange', callback: AsyncCallback<IsoInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'isoInfoChange' | 是 | 事件类型。值固定为 **'isoInfoChange'**。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[IsoInfo](arkts-camera-camera-isoinfo-i.md)&gt; | 是 | 用于返回 ISO 信息的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

<!--Del-->
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

function registerIsoInfoEvent(timeLapsePhotoSession: camera.TimeLapsePhotoSession): void {
  timeLapsePhotoSession.on('isoInfoChange', isoInfoCallback);
}
```

<!--DelEnd-->

## on('exposureInfoChange')

```TypeScript
on(type: 'exposureInfoChange', callback: AsyncCallback<ExposureInfo>): void
```

订阅曝光信息变更事件以获取曝光信息。此接口使用异步回调返回结果。

**起始版本：** 12

<!--Device-TimeLapsePhotoSession-on(type: 'exposureInfoChange', callback: AsyncCallback<ExposureInfo>): void--><!--Device-TimeLapsePhotoSession-on(type: 'exposureInfoChange', callback: AsyncCallback<ExposureInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'exposureInfoChange' | 是 | 事件类型。值固定为 **'exposureInfoChange'**。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ExposureInfo](arkts-camera-camera-exposureinfo-i.md)&gt; | 是 | 用于返回曝光信息的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

<!--Del-->
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

function registerExposureInfoEvent(timeLapsePhotoSession: camera.TimeLapsePhotoSession): void {
  timeLapsePhotoSession.on('exposureInfoChange', exposureInfoCallback);
}
```

<!--DelEnd-->

## on('luminationInfoChange')

```TypeScript
on(type: 'luminationInfoChange', callback: AsyncCallback<LuminationInfo>): void
```

订阅光照变更事件以获取实时光照信息。此接口使用异步回调返回结果。

**起始版本：** 12

<!--Device-TimeLapsePhotoSession-on(type: 'luminationInfoChange', callback: AsyncCallback<LuminationInfo>): void--><!--Device-TimeLapsePhotoSession-on(type: 'luminationInfoChange', callback: AsyncCallback<LuminationInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'luminationInfoChange' | 是 | 事件类型。值固定为 **'luminationInfoChange'**。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[LuminationInfo](arkts-camera-camera-luminationinfo-i-sys.md)&gt; | 是 | 用于返回光照信息的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

<!--Del-->
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

function registerLuminationInfoEvent(timeLapsePhotoSession: camera.TimeLapsePhotoSession): void {
  timeLapsePhotoSession.on('luminationInfoChange', luminationInfoCallback);
}
```

<!--DelEnd-->

## on('tryAEInfoChange')

```TypeScript
on(type: 'tryAEInfoChange', callback: AsyncCallback<TryAEInfo>): void
```

订阅 Try AE 变更事件以获取实时 Try AE 参数。此接口使用异步回调返回结果。

**起始版本：** 12

<!--Device-TimeLapsePhotoSession-on(type: 'tryAEInfoChange', callback: AsyncCallback<TryAEInfo>): void--><!--Device-TimeLapsePhotoSession-on(type: 'tryAEInfoChange', callback: AsyncCallback<TryAEInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'tryAEInfoChange' | 是 | 事件类型。值固定为 **'tryAEInfoChange'**。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[TryAEInfo](arkts-camera-camera-tryaeinfo-i-sys.md)&gt; | 是 | 用于返回 Try AE 参数的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

<!--Del-->
**示例**

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

<!--DelEnd-->

## setTimeLapseInterval

```TypeScript
setTimeLapseInterval(interval: number): void
```

设置延时拍摄间隔。

**起始版本：** 12

<!--Device-TimeLapsePhotoSession-setTimeLapseInterval(interval: int): void--><!--Device-TimeLapsePhotoSession-setTimeLapseInterval(interval: int): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| interval | number | 是 | 拍摄间隔，单位为毫秒，支持的范围可通过调用[getSupportedTimeLapseIntervalRange](#getsupportedtimelapseintervalrange) 获取。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

<!--Del-->
**示例**

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

<!--DelEnd-->

## setTimeLapsePreviewType

```TypeScript
setTimeLapsePreviewType(type: TimeLapsePreviewType): void
```

设置延时摄影预览类型。

**起始版本：** 12

<!--Device-TimeLapsePhotoSession-setTimeLapsePreviewType(type: TimeLapsePreviewType): void--><!--Device-TimeLapsePhotoSession-setTimeLapsePreviewType(type: TimeLapsePreviewType): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [TimeLapsePreviewType](arkts-camera-camera-timelapsepreviewtype-e-sys.md) | 是 | 预览类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

<!--Del-->
**示例**

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

<!--DelEnd-->

## setTimeLapseRecordState

```TypeScript
setTimeLapseRecordState(state: TimeLapseRecordState): void
```

设置延时拍摄状态。

**起始版本：** 12

<!--Device-TimeLapsePhotoSession-setTimeLapseRecordState(state: TimeLapseRecordState): void--><!--Device-TimeLapsePhotoSession-setTimeLapseRecordState(state: TimeLapseRecordState): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| state | [TimeLapseRecordState](arkts-camera-camera-timelapserecordstate-e-sys.md) | 是 | 拍摄状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

<!--Del-->
**示例**

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

<!--DelEnd-->

## startTryAE

```TypeScript
startTryAE(): void
```

开始执行 Try AE。

**起始版本：** 12

<!--Device-TimeLapsePhotoSession-startTryAE(): void--><!--Device-TimeLapsePhotoSession-startTryAE(): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

<!--Del-->
**示例**

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

<!--DelEnd-->

## stopTryAE

```TypeScript
stopTryAE(): void
```

停止执行 Try AE。

**起始版本：** 12

<!--Device-TimeLapsePhotoSession-stopTryAE(): void--><!--Device-TimeLapsePhotoSession-stopTryAE(): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

<!--Del-->
**示例**

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

<!--DelEnd-->
