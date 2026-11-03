# PanoramaPhotoSession（系统接口）

```TypeScript
interface PanoramaPhotoSession extends Session, Focus, AutoExposure, WhiteBalance, ColorEffect
```

全景拍照会话类。用于设置全景拍照模式的参数，并保存运行相机所需的全部[CameraInput](arkts-camera-camera-camerainput-i.md) 和 [CameraOutput](arkts-camera-camera-cameraoutput-i.md)实例。继承自 [Session](arkts-camera-camera-session-i.md)。

**继承/实现关系：** PanoramaPhotoSession extends [Session](arkts-camera-camera-session-i.md), [Focus](arkts-camera-camera-focus-i.md), [AutoExposure](arkts-camera-camera-autoexposure-i.md), [WhiteBalance](arkts-camera-camera-whitebalance-i.md)<!--Del-->, [ColorEffect](arkts-camera-camera-coloreffect-i-sys.md)<!--DelEnd-->

**起始版本：** 12

<!--Device-camera-interface PanoramaPhotoSession extends Session, Focus, AutoExposure, WhiteBalance, ColorEffect--><!--Device-camera-interface PanoramaPhotoSession extends Session, Focus, AutoExposure, WhiteBalance, ColorEffect-End-->

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

取消订阅高分辨率拍照会话错误事件。

**起始版本：** 12

<!--Device-PanoramaPhotoSession-off(type: 'error', callback?: ErrorCallback): void--><!--Device-PanoramaPhotoSession-off(type: 'error', callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 事件类型。取值固定为**'error'**。该事件可在创建会话时监听。 |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | 否 | 用于返回结果的回调。该参数为可选参数。若指定该参数，则取消对指定事件 **on('error')** 中指定回调的订阅。（回调对象不能是匿名函数。） |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

<!--Del-->
**示例**

```TypeScript
function unregisterSessionError(panoramaPhotoSession: camera.PanoramaPhotoSession): void {
  panoramaPhotoSession.off('error');
}
```

<!--DelEnd-->

## off('focusStateChange')

```TypeScript
off(type: 'focusStateChange', callback?: AsyncCallback<FocusState>): void
```

取消订阅对焦状态变化事件。

**起始版本：** 12

<!--Device-PanoramaPhotoSession-off(type: 'focusStateChange', callback?: AsyncCallback<FocusState>): void--><!--Device-PanoramaPhotoSession-off(type: 'focusStateChange', callback?: AsyncCallback<FocusState>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'focusStateChange' | 是 | 事件类型。取值固定为**'focusStateChange'**。该事件可在创建会话时监听。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FocusState](arkts-camera-camera-focusstate-e.md)&gt; | 否 | 用于返回结果的回调。该参数为可选参数。若指定该参数，则取消对指定事件 **on('focusStateChange')** 中指定回调的订阅。（回调对象不能是匿名函数。） |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

<!--Del-->
**示例**

```TypeScript
function unregisterFocusStateChange(panoramaPhotoSession: camera.PanoramaPhotoSession): void {
  panoramaPhotoSession.off('focusStateChange');
}
```

<!--DelEnd-->

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

订阅高分辨率拍照会话错误事件。该接口使用异步回调返回结果。

**起始版本：** 12

<!--Device-PanoramaPhotoSession-on(type: 'error', callback: ErrorCallback): void--><!--Device-PanoramaPhotoSession-on(type: 'error', callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 事件类型。取值固定为**'error'**。该事件可在创建会话时监听。当调用会话相关接口（例如[beginConfig](arkts-camera-camera-session-i.md#beginconfig)、[commitConfig](arkts-camera-camera-session-i.md#commitconfig) 和[addInput](arkts-camera-camera-session-i.md#addinput)）过程中发生错误时，会触发该事件并返回错误信息。 |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | 是 | 用于返回错误码的回调，错误码定义见[CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function callback(err: BusinessError): void {
  console.error(`Panorama photo session error code: ${err.code}`);
}

function registerSessionError(panoramaPhotoSession: camera.PanoramaPhotoSession): void {
  panoramaPhotoSession.on('error', callback);
}
```

<!--DelEnd-->

## on('focusStateChange')

```TypeScript
on(type: 'focusStateChange', callback: AsyncCallback<FocusState>): void
```

订阅对焦状态变化事件。该接口使用异步回调返回结果。

**起始版本：** 12

<!--Device-PanoramaPhotoSession-on(type: 'focusStateChange', callback: AsyncCallback<FocusState>): void--><!--Device-PanoramaPhotoSession-on(type: 'focusStateChange', callback: AsyncCallback<FocusState>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'focusStateChange' | 是 | 事件类型。取值固定为**'focusStateChange'**。该事件可在创建会话时监听。该事件仅在自动对焦模式下相机对焦状态发生变化时触发。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FocusState](arkts-camera-camera-focusstate-e.md)&gt; | 是 | 用于返回对焦状态变化的回调。 |

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

function registerFocusStateChange(panoramaPhotoSession: camera.PanoramaPhotoSession): void {
  panoramaPhotoSession.on('focusStateChange', callback);
}
```

<!--DelEnd-->
