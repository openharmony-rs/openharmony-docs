# MacroVideoSession（系统接口）

Implements a macro video session, which sets the parameters of the macro video mode and saves all [CameraInput](arkts-camera-camera-camerainput-i.md#CameraInput) and [CameraOutput](arkts-camera-camera-cameraoutput-i.md#CameraOutput) instances required to run the camera. It inherits from [Session](arkts-camera-camera-session-i.md#Session).

**继承/实现关系：** MacroVideoSession extends [Session](arkts-camera-camera-session-i.md#Session), [Flash](arkts-camera-camera-flash-i.md#Flash), [AutoExposure](arkts-camera-camera-autoexposure-i.md#AutoExposure), [Focus](arkts-camera-camera-focus-i.md#Focus), [Zoom](arkts-camera-camera-zoom-i.md#Zoom), [ColorEffect](arkts-camera-camera-coloreffect-i-sys.md#ColorEffect（系统接口）), [ManualFocus](arkts-camera-camera-manualfocus-i-sys.md#ManualFocus（系统接口）), [ColorManagement](arkts-camera-camera-colormanagement-i.md#ColorManagement)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-camera-interface MacroVideoSession--><!--Device-camera-interface MacroVideoSession-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## offError

```TypeScript
offError(callback?: ErrorCallback): void
```

Unsubscribes from error events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-MacroVideoSession-offError(callback?: ErrorCallback): void--><!--Device-MacroVideoSession-offError(callback?: ErrorCallback): void-End-->

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

## offFocusStateChange

```TypeScript
offFocusStateChange(callback?: AsyncCallback<FocusState>): void
```

Unsubscribes from focus state change event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-MacroVideoSession-offFocusStateChange(callback?: AsyncCallback<FocusState>): void--><!--Device-MacroVideoSession-offFocusStateChange(callback?: AsyncCallback<FocusState>): void-End-->

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

## offSmoothZoomInfoAvailable

```TypeScript
offSmoothZoomInfoAvailable(callback?: AsyncCallback<SmoothZoomInfo>): void
```

Unsubscribes from zoom info event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-MacroVideoSession-offSmoothZoomInfoAvailable(callback?: AsyncCallback<SmoothZoomInfo>): void--><!--Device-MacroVideoSession-offSmoothZoomInfoAvailable(callback?: AsyncCallback<SmoothZoomInfo>): void-End-->

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

## off_error

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

Unsubscribes from HighResolutionPhotoSession error events.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-MacroVideoSession-off(type: 'error', callback?: ErrorCallback): void--><!--Device-MacroVideoSession-off(type: 'error', callback?: ErrorCallback): void-End-->

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
function unregisterSessionError(macroVideoSession: camera.MacroVideoSession): void {
  macroVideoSession.off('error');
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

<!--Device-MacroVideoSession-off(type: 'focusStateChange', callback?: AsyncCallback<FocusState>): void--><!--Device-MacroVideoSession-off(type: 'focusStateChange', callback?: AsyncCallback<FocusState>): void-End-->

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
function unregisterFocusStateChange(macroVideoSession: camera.MacroVideoSession): void {
  macroVideoSession.off('focusStateChange');
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

<!--Device-MacroVideoSession-off(type: 'smoothZoomInfoAvailable', callback?: AsyncCallback<SmoothZoomInfo>): void--><!--Device-MacroVideoSession-off(type: 'smoothZoomInfoAvailable', callback?: AsyncCallback<SmoothZoomInfo>): void-End-->

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
function unregisterSmoothZoomInfo(macroVideoSession: camera.MacroVideoSession): void {
  macroVideoSession.off('smoothZoomInfoAvailable');
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

<!--Device-MacroVideoSession-onError(callback: ErrorCallback): void--><!--Device-MacroVideoSession-onError(callback: ErrorCallback): void-End-->

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

## onFocusStateChange

```TypeScript
onFocusStateChange(callback: AsyncCallback<FocusState>): void
```

Subscribes focus state change event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-MacroVideoSession-onFocusStateChange(callback: AsyncCallback<FocusState>): void--><!--Device-MacroVideoSession-onFocusStateChange(callback: AsyncCallback<FocusState>): void-End-->

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

## onSmoothZoomInfoAvailable

```TypeScript
onSmoothZoomInfoAvailable(callback: AsyncCallback<SmoothZoomInfo>): void
```

Subscribes zoom info event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-MacroVideoSession-onSmoothZoomInfoAvailable(callback: AsyncCallback<SmoothZoomInfo>): void--><!--Device-MacroVideoSession-onSmoothZoomInfoAvailable(callback: AsyncCallback<SmoothZoomInfo>): void-End-->

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

## on_error

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

Subscribes to HighResolutionPhotoSession error events. This API uses an asynchronous callback to return the result.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-MacroVideoSession-on(type: 'error', callback: ErrorCallback): void--><!--Device-MacroVideoSession-on(type: 'error', callback: ErrorCallback): void-End-->

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
  console.error(`MacroPhotoSession error code: ${err.code}`);
}

function registerSessionError(macroVideoSession: camera.MacroVideoSession): void {
  macroVideoSession.on('error', callback);
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

<!--Device-MacroVideoSession-on(type: 'focusStateChange', callback: AsyncCallback<FocusState>): void--><!--Device-MacroVideoSession-on(type: 'focusStateChange', callback: AsyncCallback<FocusState>): void-End-->

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

function registerFocusStateChange(macroVideoSession: camera.MacroVideoSession): void {
  macroVideoSession.on('focusStateChange', callback);
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

<!--Device-MacroVideoSession-on(type: 'smoothZoomInfoAvailable', callback: AsyncCallback<SmoothZoomInfo>): void--><!--Device-MacroVideoSession-on(type: 'smoothZoomInfoAvailable', callback: AsyncCallback<SmoothZoomInfo>): void-End-->

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

function registerSmoothZoomInfo(macroVideoSession: camera.MacroVideoSession): void {
  macroVideoSession.on('smoothZoomInfoAvailable', callback);
}
```

