# MacroPhotoSession（系统接口）

```TypeScript
interface MacroPhotoSession extends Session, Flash, AutoExposure, Focus, Zoom, ColorEffect, ManualFocus,
      DepthFusion, ColorManagement
```

实现微距拍照会话，用于设置微距拍照模式的参数，并保存运行相机所需的[CameraInput](arkts-camera-camera-camerainput-i.md)和[CameraOutput](arkts-camera-camera-cameraoutput-i.md)实例。继承自[Session](arkts-camera-camera-session-i.md)。

**继承/实现关系：** MacroPhotoSession extends [Session](arkts-camera-camera-session-i.md), [Flash](arkts-camera-camera-flash-i.md), [AutoExposure](arkts-camera-camera-autoexposure-i.md), [Focus](arkts-camera-camera-focus-i.md), [Zoom](arkts-camera-camera-zoom-i.md)<!--Del-->, [ColorEffect](arkts-camera-camera-coloreffect-i-sys.md)<!--DelEnd-->, [ManualFocus](arkts-camera-camera-manualfocus-i.md)<!--Del-->, [DepthFusion](arkts-camera-camera-depthfusion-i-sys.md)<!--DelEnd-->, [ColorManagement](arkts-camera-camera-colormanagement-i.md)

**起始版本：** 12

<!--Device-camera-interface MacroPhotoSession extends Session, Flash, AutoExposure, Focus, Zoom, ColorEffect, ManualFocus,      DepthFusion, ColorManagement--><!--Device-camera-interface MacroPhotoSession extends Session, Flash, AutoExposure, Focus, Zoom, ColorEffect, ManualFocus,      DepthFusion, ColorManagement-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## off('error')

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

注销监听微距拍照会话的错误事件。

**起始版本：** 12

<!--Device-MacroPhotoSession-off(type: 'error', callback?: ErrorCallback): void--><!--Device-MacroPhotoSession-off(type: 'error', callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 监听事件，固定为'error'，session创建成功之后可监听该接口。 |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | 否 | 回调函数，本参数可选。如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

<!--Del-->
**示例**

```TypeScript
function unregisterSessionError(macroPhotoSession: camera.MacroPhotoSession): void {
  macroPhotoSession.off('error');
}
```

<!--DelEnd-->

## off('focusStateChange')

```TypeScript
off(type: 'focusStateChange', callback?: AsyncCallback<FocusState>): void
```

注销监听相机聚焦的状态变化。

**起始版本：** 12

<!--Device-MacroPhotoSession-off(type: 'focusStateChange', callback?: AsyncCallback<FocusState>): void--><!--Device-MacroPhotoSession-off(type: 'focusStateChange', callback?: AsyncCallback<FocusState>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'focusStateChange' | 是 | 监听事件，固定为'focusStateChange'，session创建成功可监听。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FocusState](arkts-camera-camera-focusstate-e.md)&gt; | 否 | 回调函数，本参数可选。如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

<!--Del-->
**示例**

```TypeScript
function unregisterFocusStateChange(macroPhotoSession: camera.MacroPhotoSession): void {
  macroPhotoSession.off('focusStateChange');
}
```

<!--DelEnd-->

## off('smoothZoomInfoAvailable')

```TypeScript
off(type: 'smoothZoomInfoAvailable', callback?: AsyncCallback<SmoothZoomInfo>): void
```

注销监听平滑变焦状态变化事件。

**起始版本：** 12

<!--Device-MacroPhotoSession-off(type: 'smoothZoomInfoAvailable', callback?: AsyncCallback<SmoothZoomInfo>): void--><!--Device-MacroPhotoSession-off(type: 'smoothZoomInfoAvailable', callback?: AsyncCallback<SmoothZoomInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'smoothZoomInfoAvailable' | 是 | 监听事件，固定为'smoothZoomInfoAvailable'，session创建成功之后可监听该接口。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[SmoothZoomInfo](arkts-camera-camera-smoothzoominfo-i.md)&gt; | 否 | 回调函数，本参数可选。如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

<!--Del-->
**示例**

```TypeScript
function unregisterSmoothZoomInfo(macroPhotoSession: camera.MacroPhotoSession): void {
  macroPhotoSession.off('smoothZoomInfoAvailable');
}
```

<!--DelEnd-->

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

监听微距拍照会话的错误事件，通过注册回调函数获取结果。使用callback异步回调。

**起始版本：** 12

<!--Device-MacroPhotoSession-on(type: 'error', callback: ErrorCallback): void--><!--Device-MacroPhotoSession-on(type: 'error', callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 监听事件，固定为'error'，session创建成功之后可监听该接口。session调用相关接口出现错误时会触发该事件，比如调用[beginConfig](arkts-camera-camera-session-i.md#beginconfig)，[commitConfig](arkts-camera-camera-session-i.md#commitconfig)，[addInput](arkts-camera-camera-session-i.md#addinput)等接口发生错误时返回错误信息。 |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | 是 | 回调函数，用于获取错误信息。返回错误码，错误码见[CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function callback(err: BusinessError): void {
  console.error(`MacroPhotoSession error code: ${err.code}`);
}

function registerSessionError(macroPhotoSession: camera.MacroPhotoSession): void {
  macroPhotoSession.on('error', callback);
}
```

<!--DelEnd-->

## on('focusStateChange')

```TypeScript
on(type: 'focusStateChange', callback: AsyncCallback<FocusState>): void
```

监听相机聚焦的状态变化，通过注册回调函数获取结果。使用callback异步回调。

**起始版本：** 12

<!--Device-MacroPhotoSession-on(type: 'focusStateChange', callback: AsyncCallback<FocusState>): void--><!--Device-MacroPhotoSession-on(type: 'focusStateChange', callback: AsyncCallback<FocusState>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'focusStateChange' | 是 | 监听事件，固定为'focusStateChange'，session创建成功可监听。仅当自动对焦模式时，且相机对焦状态发生改变时可触发该事件。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FocusState](arkts-camera-camera-focusstate-e.md)&gt; | 是 | 回调函数，用于获取当前对焦状态。 |

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

function registerFocusStateChange(macroPhotoSession: camera.MacroPhotoSession): void {
  macroPhotoSession.on('focusStateChange', callback);
}
```

<!--DelEnd-->

## on('smoothZoomInfoAvailable')

```TypeScript
on(type: 'smoothZoomInfoAvailable', callback: AsyncCallback<SmoothZoomInfo>): void
```

监听平滑变焦状态变化事件，通过注册回调函数获取结果。使用callback异步回调。

**起始版本：** 12

<!--Device-MacroPhotoSession-on(type: 'smoothZoomInfoAvailable', callback: AsyncCallback<SmoothZoomInfo>): void--><!--Device-MacroPhotoSession-on(type: 'smoothZoomInfoAvailable', callback: AsyncCallback<SmoothZoomInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'smoothZoomInfoAvailable' | 是 | 监听事件，固定为'smoothZoomInfoAvailable'，session创建成功之后可监听该接口。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[SmoothZoomInfo](arkts-camera-camera-smoothzoominfo-i.md)&gt; | 是 | 回调函数，用于获取平滑变焦状态变化。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

<!--Del-->
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

function registerSmoothZoomInfo(macroPhotoSession: camera.MacroPhotoSession): void {
  macroPhotoSession.on('smoothZoomInfoAvailable', callback);
}
```

<!--DelEnd-->
