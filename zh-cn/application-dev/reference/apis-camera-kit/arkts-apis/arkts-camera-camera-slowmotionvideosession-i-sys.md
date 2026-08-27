# SlowMotionVideoSession（系统接口）

SlowMotionVideoSession extends Session, Flash, AutoExposure, Focus, Zoom, ColorEffect Implements a slow-motion video session, which sets the parameters of the slow-motion video mode and saves all [CameraInput](arkts-camera-camera-camerainput-i.md) and [CameraOutput](arkts-camera-camera-cameraoutput-i.md) instances required to run the camera. It inherits from [Session](arkts-camera-camera-session-i.md).

**继承/实现关系：** SlowMotionVideoSession extends [Session](arkts-camera-camera-session-i.md), [Flash](arkts-camera-camera-flash-i.md), [AutoExposure](arkts-camera-camera-autoexposure-i.md), [Focus](arkts-camera-camera-focus-i.md), [Zoom](arkts-camera-camera-zoom-i.md), [ColorEffect](arkts-camera-camera-coloreffect-i-sys.md)

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
```

## isSlowMotionDetectionSupported

```TypeScript
isSlowMotionDetectionSupported(): boolean
```

Checks whether the device supports slow-motion detection.

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Check result for the support of slow-motion detection. **true** if supported, **false** otherwise. If the operation fails, an error code defined in [CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config.<br>**适用版本：** 12 - 18 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function isSlowMotionDetectionSupported(slowMotionVideoSession: camera.SlowMotionVideoSession): boolean {
  let isSupported: boolean = false;
  try {
    isSupported = slowMotionVideoSession.isSlowMotionDetectionSupported();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The isFocusModeSupported call failed. error code: ${err.code}`);
  }
  return isSupported;
}
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
function unregisterSessionError(slowMotionVideoSession: camera.SlowMotionVideoSession): void {
  slowMotionVideoSession.off('error');
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
function unregisterFocusStateChange(slowMotionVideoSession: camera.SlowMotionVideoSession): void {
  slowMotionVideoSession.off('focusStateChange');
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
function unregisterSmoothZoomInfo(slowMotionVideoSession: camera.SlowMotionVideoSession): void {
  slowMotionVideoSession.off('smoothZoomInfoAvailable');
}
```

## off('slowMotionStatus')

```TypeScript
off(type: 'slowMotionStatus', callback?: AsyncCallback<SlowMotionStatus>): void
```

Unsubscribes from slow-motion status change events.

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'slowMotionStatus' | 是 | Event type. The value is fixed at **'slowMotionStatus'**. The event can be listened for when a session is created. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[SlowMotionStatus](arkts-camera-camera-slowmotionstatus-e-sys.md)&gt; | 否 | Callback used to return the result. This parameter is optional. If this parameter is specified, the subscription to the specified event **on('slowMotionStatus')** with the specified callback is canceled. (The callback object cannot be an anonymous function.) If the operation fails, an error code defined in [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) is returned. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

**示例**

```TypeScript
function unregisterSlowMotionStatus(slowMotionVideoSession: camera.SlowMotionVideoSession): void {
  slowMotionVideoSession.off('slowMotionStatus');
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
  console.error(`Portrait photo session error code: ${err.code}`);
}

function registerSessionError(slowMotionVideoSession: camera.SlowMotionVideoSession): void {
  slowMotionVideoSession.on('error', callback);
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

function registerFocusStateChange(slowMotionVideoSession: camera.SlowMotionVideoSession): void {
  slowMotionVideoSession.on('focusStateChange', callback);
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

function registerSmoothZoomInfo(slowMotionVideoSession: camera.SlowMotionVideoSession): void {
  slowMotionVideoSession.on('smoothZoomInfoAvailable', callback);
}
```

## on('slowMotionStatus')

```TypeScript
on(type: 'slowMotionStatus', callback: AsyncCallback<SlowMotionStatus>): void
```

Subscribes to slow-motion status change events. This API uses an asynchronous callback to return the result.

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'slowMotionStatus' | 是 | Event type. The value is fixed at **'slowMotionStatus'**. The event can be listened for when a session is created. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[SlowMotionStatus](arkts-camera-camera-slowmotionstatus-e-sys.md)&gt; | 是 | Callback used to return the slow-motion status change. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function callback(err: BusinessError, slowMotionStatus: camera.SlowMotionStatus): void {
  if (err !== undefined && err.code !== 0) {
    console.error(`Callback Error, errorCode: ${err.code}`);
    return;
  }
  console.info(`The slow motion status: ${slowMotionStatus}`);
}

function registerSlowMotionStatus(slowMotionVideoSession: camera.SlowMotionVideoSession): void {
  slowMotionVideoSession.on('slowMotionStatus', callback);
}
```

## setSlowMotionDetectionArea

```TypeScript
setSlowMotionDetectionArea(area: Rect): void
```

Sets an area for slow-motion detection.

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| area | Rect | 是 | Area. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect.<br>**适用版本：** 12 - 18 |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config.<br>**适用版本：** 12 - 18 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function setSlowMotionDetectionArea(slowMotionVideoSession: camera.SlowMotionVideoSession): void {
  try {
    slowMotionVideoSession.setSlowMotionDetectionArea({topLeftX: 0.1, topLeftY: 0.1, width: 0.8, height: 0.8});
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The setSlowMotionDetectionArea call failed. error code: ${err.code}`);
  }
}
```
