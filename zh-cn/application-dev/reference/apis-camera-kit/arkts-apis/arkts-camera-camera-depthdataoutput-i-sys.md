# DepthDataOutput（系统接口）

```TypeScript
interface DepthDataOutput extends CameraOutput
```

实现深度数据输出。继承自 [CameraOutput](arkts-camera-camera-cameraoutput-i.md)。

**继承/实现关系：** DepthDataOutput extends [CameraOutput](arkts-camera-camera-cameraoutput-i.md)

**起始版本：** 13

<!--Device-camera-interface DepthDataOutput extends CameraOutput--><!--Device-camera-interface DepthDataOutput extends CameraOutput-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## off('depthDataAvailable')

```TypeScript
off(type: 'depthDataAvailable', callback?: AsyncCallback<DepthData>): void
```

取消订阅深度数据可用事件。

**起始版本：** 13

<!--Device-DepthDataOutput-off(type: 'depthDataAvailable', callback?: AsyncCallback<DepthData>): void--><!--Device-DepthDataOutput-off(type: 'depthDataAvailable', callback?: AsyncCallback<DepthData>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'depthDataAvailable' | 是 | 事件类型。值固定为 **'depthDataAvailable'**。创建 depthDataOutput 实例后即可监听此事件。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[DepthData](arkts-camera-camera-depthdata-i-sys.md)&gt; | 否 | 用于返回结果的回调。如果指定此参数，将取消订阅指定回调的指定事件。（回调对象不能为匿名函数。）否则，将取消订阅指定事件的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function callback(err: BusinessError, depthData: camera.DepthData): void {
  if (err !== undefined && err.code !== 0) {
    console.error(`Callback Error, errorCode: ${err.code}`);
    return;
  }
}

function unRegisterDepthDataAvailable(depthDataOutput: camera.DepthDataOutput): void {
  depthDataOutput.off('depthDataAvailable', callback);
}
```

<!--DelEnd-->

## off('error')

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

取消订阅 DepthDataOutput 错误事件。

**起始版本：** 13

<!--Device-DepthDataOutput-off(type: 'error', callback?: ErrorCallback): void--><!--Device-DepthDataOutput-off(type: 'error', callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 事件类型。值固定为 **'error'**。创建 depthDataOutput 实例后即可监听此事件。 |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | 否 | 用于返回结果的回调。如果指定此参数，将取消订阅指定回调的指定事件。（回调对象不能为匿名函数。）否则，将取消订阅指定事件的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

<!--Del-->
**示例**

```TypeScript
function unregisterDepthDataOutputError(depthDataOutput: camera.DepthDataOutput): void {
  depthDataOutput.off('error');
}
```

<!--DelEnd-->

## on('depthDataAvailable')

```TypeScript
on(type: 'depthDataAvailable', callback: AsyncCallback<DepthData>): void
```

订阅深度数据可用事件。此接口使用异步回调返回结果。

> **注意**
> 
> 当前不支持在 **on()** 的回调方法中使用 **off()** 取消注册回调。

**起始版本：** 13

<!--Device-DepthDataOutput-on(type: 'depthDataAvailable', callback: AsyncCallback<DepthData>): void--><!--Device-DepthDataOutput-on(type: 'depthDataAvailable', callback: AsyncCallback<DepthData>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'depthDataAvailable' | 是 | 事件类型。值固定为 **'depthDataAvailable'**。创建 depthDataOutput 实例后即可监听此事件。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[DepthData](arkts-camera-camera-depthdata-i-sys.md)&gt; | 是 | 用于监听深度数据的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function callback(err: BusinessError, depthData: camera.DepthData): void {
  if (err !== undefined && err.code !== 0) {
    console.error(`Callback Error, errorCode: ${err.code}`);
    return;
  }
}

function registerDepthDataAvailable(depthDataOutput: camera.DepthDataOutput): void {
  depthDataOutput.on('depthDataAvailable', callback);
}
```

<!--DelEnd-->

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

订阅 DepthDataOutput 错误事件。此接口使用异步回调返回结果。

> **注意**
> 
> 当前不支持在 **on()** 的回调方法中使用 **off()** 取消注册回调。

**起始版本：** 13

<!--Device-DepthDataOutput-on(type: 'error', callback: ErrorCallback): void--><!--Device-DepthDataOutput-on(type: 'error', callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 事件类型。值固定为 **'error'**。创建 depthDataOutput 实例后即可监听此事件。 |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | 是 | 用于返回 [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md) 中定义的错误码的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function callback(depthDataOutputError: BusinessError): void {
  console.error(`Depth data output error code: ${depthDataOutputError.code}`);
}

function registerDepthDataOutputError(depthDataOutput: camera.DepthDataOutput): void {
  depthDataOutput.on('error', callback);
}
```

<!--DelEnd-->

## start

```TypeScript
start(): Promise<void>
```

启动深度数据输出。此接口使用 Promise 返回结果。

**起始版本：** 13

<!--Device-DepthDataOutput-start(): Promise<void>--><!--Device-DepthDataOutput-start(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 不返回值的 Promise。 |

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

function startDepthDataOutput(depthDataOutput: camera.DepthDataOutput): void {
  depthDataOutput.start().then(() => {
    console.info('Promise returned to indicate that start method execution success.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to depth data output start, error code: ${error.code}.`);
  });
}
```

<!--DelEnd-->

## stop

```TypeScript
stop(): Promise<void>
```

停止深度数据输出。此接口使用 Promise 返回结果。

**起始版本：** 13

<!--Device-DepthDataOutput-stop(): Promise<void>--><!--Device-DepthDataOutput-stop(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 不返回值的 Promise。 |

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

function stopDepthDataOutput(depthDataOutput: camera.DepthDataOutput): void {
  depthDataOutput.stop().then(() => {
    console.info('Promise returned to indicate that stop method execution success.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to depth data output stop, error code: ${error.code}.`);
  });
}
```

<!--DelEnd-->
