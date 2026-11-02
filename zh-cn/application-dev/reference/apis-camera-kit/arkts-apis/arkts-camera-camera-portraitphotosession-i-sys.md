# PortraitPhotoSession（系统接口）

```TypeScript
interface PortraitPhotoSession extends Session, Flash, AutoExposure, Focus, Zoom, Beauty, ColorEffect, ColorManagement, Portrait, Aperture
```

人像拍照会话类。用于设置人像拍照模式的参数，并保存运行相机所需的[CameraInput](arkts-camera-camera-camerainput-i.md) 和 [CameraOutput](arkts-camera-camera-cameraoutput-i.md)实例。继承自 [Session](arkts-camera-camera-session-i.md)。

**继承/实现关系：** PortraitPhotoSession extends [Session](arkts-camera-camera-session-i.md), [Flash](arkts-camera-camera-flash-i.md), [AutoExposure](arkts-camera-camera-autoexposure-i.md), [Focus](arkts-camera-camera-focus-i.md), [Zoom](arkts-camera-camera-zoom-i.md)<!--Del-->, [Beauty](arkts-camera-camera-beauty-i-sys.md)<!--DelEnd--><!--Del-->, [ColorEffect](arkts-camera-camera-coloreffect-i-sys.md)<!--DelEnd-->, [ColorManagement](arkts-camera-camera-colormanagement-i.md)<!--Del-->, [Portrait](arkts-camera-camera-portrait-i-sys.md)<!--DelEnd-->, [Aperture](arkts-camera-camera-aperture-i.md)

**起始版本：** 11

<!--Device-camera-interface PortraitPhotoSession extends Session, Flash, AutoExposure, Focus, Zoom, Beauty, ColorEffect, ColorManagement, Portrait, Aperture--><!--Device-camera-interface PortraitPhotoSession extends Session, Flash, AutoExposure, Focus, Zoom, Beauty, ColorEffect, ColorManagement, Portrait, Aperture-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## getSessionConflictFunctions

```TypeScript
getSessionConflictFunctions(): Array<PortraitPhotoConflictFunctions>
```

获取会话冲突功能。

**起始版本：** 13

<!--Device-PortraitPhotoSession-getSessionConflictFunctions(): Array<PortraitPhotoConflictFunctions>--><!--Device-PortraitPhotoSession-getSessionConflictFunctions(): Array<PortraitPhotoConflictFunctions>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[PortraitPhotoConflictFunctions](arkts-camera-camera-portraitphotoconflictfunctions-i-sys.md)&gt; | 会话冲突功能列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

## getSessionFunctions

```TypeScript
getSessionFunctions(outputCapability: CameraOutputCapability): Array<PortraitPhotoFunctions>
```

获取会话功能。

**起始版本：** 13

<!--Device-PortraitPhotoSession-getSessionFunctions(outputCapability: CameraOutputCapability): Array<PortraitPhotoFunctions>--><!--Device-PortraitPhotoSession-getSessionFunctions(outputCapability: CameraOutputCapability): Array<PortraitPhotoFunctions>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| outputCapability | [CameraOutputCapability](arkts-camera-camera-cameraoutputcapability-i.md) | 是 | 待设置的 CameraOutputCapability。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[PortraitPhotoFunctions](arkts-camera-camera-portraitphotofunctions-i-sys.md)&gt; | 会话功能列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

## off('error')

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

取消订阅人像会话错误事件。

**起始版本：** 11

<!--Device-PortraitPhotoSession-off(type: 'error', callback?: ErrorCallback): void--><!--Device-PortraitPhotoSession-off(type: 'error', callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 事件类型。取值固定为**'error'**。该事件可在创建会话时监听。 |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | 否 | 用于返回结果的回调。该参数为可选参数。若指定该参数，则取消对指定事件 **on('error')** 中指定回调的订阅。（回调对象不能是匿名函数。） |

<!--Del-->
**示例**

```TypeScript
function unregisterSessionError(portraitPhotoSession: camera.PortraitPhotoSession): void {
  portraitPhotoSession.off('error');
}
```

<!--DelEnd-->

## off('focusStateChange')

```TypeScript
off(type: 'focusStateChange', callback?: AsyncCallback<FocusState>): void
```

取消订阅对焦状态变化事件。

**起始版本：** 11

<!--Device-PortraitPhotoSession-off(type: 'focusStateChange', callback?: AsyncCallback<FocusState>): void--><!--Device-PortraitPhotoSession-off(type: 'focusStateChange', callback?: AsyncCallback<FocusState>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'focusStateChange' | 是 | 事件类型。取值固定为**'focusStateChange'**。该事件可在创建会话时监听。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FocusState](arkts-camera-camera-focusstate-e.md)&gt; | 否 | 用于返回结果的回调。该参数为可选参数。若指定该参数，则取消对指定事件 **on('focusStateChange')** 中指定回调的订阅。（回调对象不能是匿名函数。） |

<!--Del-->
**示例**

```TypeScript
function unregisterFocusStateChange(portraitPhotoSession: camera.PortraitPhotoSession): void {
  portraitPhotoSession.off('focusStateChange');
}
```

<!--DelEnd-->

## off('smoothZoomInfoAvailable')

```TypeScript
off(type: 'smoothZoomInfoAvailable', callback?: AsyncCallback<SmoothZoomInfo>): void
```

取消订阅平滑变焦状态变化事件。

**起始版本：** 11

<!--Device-PortraitPhotoSession-off(type: 'smoothZoomInfoAvailable', callback?: AsyncCallback<SmoothZoomInfo>): void--><!--Device-PortraitPhotoSession-off(type: 'smoothZoomInfoAvailable', callback?: AsyncCallback<SmoothZoomInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'smoothZoomInfoAvailable' | 是 | 事件类型。取值固定为**'smoothZoomInfoAvailable'**。该事件可在创建会话时监听。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[SmoothZoomInfo](arkts-camera-camera-smoothzoominfo-i.md)&gt; | 否 | 用于返回结果的回调。该参数为可选参数。若指定该参数，则取消对指定事件**on('smoothZoomInfoAvailable')** 中指定回调的订阅。（回调对象不能是匿名函数。） |

<!--Del-->
**示例**

```TypeScript
function unregisterSmoothZoomInfo(portraitPhotoSession: camera.PortraitPhotoSession): void {
  portraitPhotoSession.off('smoothZoomInfoAvailable');
}
```

<!--DelEnd-->

## off('lcdFlashStatus')

```TypeScript
off(type: 'lcdFlashStatus', callback?: AsyncCallback<LcdFlashStatus>): void
```

取消订阅 LCD 闪光灯状态变化事件。

**起始版本：** 13

<!--Device-PortraitPhotoSession-off(type: 'lcdFlashStatus', callback?: AsyncCallback<LcdFlashStatus>): void--><!--Device-PortraitPhotoSession-off(type: 'lcdFlashStatus', callback?: AsyncCallback<LcdFlashStatus>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'lcdFlashStatus' | 是 | 事件类型。取值固定为**'lcdFlashStatus'**。该事件可在创建会话时监听。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[LcdFlashStatus](arkts-camera-camera-lcdflashstatus-i-sys.md)&gt; | 否 | 用于返回结果的回调。该参数为可选参数。若指定该参数，则取消对指定事件 **on('lcdFlashStatus')**中指定回调的订阅。（回调对象不能是匿名函数。） |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

<!--Del-->
**示例**

```TypeScript
function unregisterLcdFlashStatus(portraitPhotoSession: camera.PortraitPhotoSession): void {
  portraitPhotoSession.off('lcdFlashStatus');
}
```

<!--DelEnd-->

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

订阅人像会话错误事件。该接口使用异步回调返回结果。

**起始版本：** 11

<!--Device-PortraitPhotoSession-on(type: 'error', callback: ErrorCallback): void--><!--Device-PortraitPhotoSession-on(type: 'error', callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 事件类型。取值固定为**'error'**。该事件可在创建会话时监听。当调用会话相关接口（例如[beginConfig](arkts-camera-camera-session-i.md#beginconfig)、[commitConfig](arkts-camera-camera-session-i.md#commitconfig) 和[addInput](arkts-camera-camera-session-i.md#addinput)）过程中发生错误时，会触发该事件并返回错误信息。 |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | 是 | 用于返回错误码的回调，错误码定义见[CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md)。 |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function callback(err: BusinessError): void {
  console.error(`Portrait photo session error code: ${err.code}`);
}

function registerSessionError(portraitPhotoSession: camera.PortraitPhotoSession): void {
  portraitPhotoSession.on('error', callback);
}
```

<!--DelEnd-->

## on('focusStateChange')

```TypeScript
on(type: 'focusStateChange', callback: AsyncCallback<FocusState>): void
```

订阅对焦状态变化事件。该接口使用异步回调返回结果。

**起始版本：** 11

<!--Device-PortraitPhotoSession-on(type: 'focusStateChange', callback: AsyncCallback<FocusState>): void--><!--Device-PortraitPhotoSession-on(type: 'focusStateChange', callback: AsyncCallback<FocusState>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'focusStateChange' | 是 | 事件类型。取值固定为**'focusStateChange'**。该事件可在创建会话时监听。该事件仅在自动对焦模式下相机对焦状态发生变化时触发。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FocusState](arkts-camera-camera-focusstate-e.md)&gt; | 是 | 用于返回对焦状态变化的回调。 |

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

function registerFocusStateChange(portraitPhotoSession: camera.PortraitPhotoSession): void {
  portraitPhotoSession.on('focusStateChange', callback);
}
```

<!--DelEnd-->

## on('smoothZoomInfoAvailable')

```TypeScript
on(type: 'smoothZoomInfoAvailable', callback: AsyncCallback<SmoothZoomInfo>): void
```

订阅平滑变焦状态变化事件。该接口使用异步回调返回结果。

**起始版本：** 11

<!--Device-PortraitPhotoSession-on(type: 'smoothZoomInfoAvailable', callback: AsyncCallback<SmoothZoomInfo>): void--><!--Device-PortraitPhotoSession-on(type: 'smoothZoomInfoAvailable', callback: AsyncCallback<SmoothZoomInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'smoothZoomInfoAvailable' | 是 | 事件类型。取值固定为**'smoothZoomInfoAvailable'**。该事件可在创建会话时监听。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[SmoothZoomInfo](arkts-camera-camera-smoothzoominfo-i.md)&gt; | 是 | 用于返回平滑变焦状态变化的回调。 |

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

function registerSmoothZoomInfo(portraitPhotoSession: camera.PortraitPhotoSession): void {
  portraitPhotoSession.on('smoothZoomInfoAvailable', callback);
}
```

<!--DelEnd-->

## on('lcdFlashStatus')

```TypeScript
on(type: 'lcdFlashStatus', callback: AsyncCallback<LcdFlashStatus>): void
```

订阅 LCD 闪光灯状态变化事件。该接口使用异步回调返回结果。

**起始版本：** 13

<!--Device-PortraitPhotoSession-on(type: 'lcdFlashStatus', callback: AsyncCallback<LcdFlashStatus>): void--><!--Device-PortraitPhotoSession-on(type: 'lcdFlashStatus', callback: AsyncCallback<LcdFlashStatus>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'lcdFlashStatus' | 是 | 事件类型。取值固定为**'lcdFlashStatus'**。该事件可在创建会话时监听。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[LcdFlashStatus](arkts-camera-camera-lcdflashstatus-i-sys.md)&gt; | 是 | 用于返回 LCD 闪光灯状态变化的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

<!--Del-->
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

function registerLcdFlashStatus(portraitPhotoSession: camera.PortraitPhotoSession): void {
  portraitPhotoSession.on('lcdFlashStatus', callback);
}
```

<!--DelEnd-->
