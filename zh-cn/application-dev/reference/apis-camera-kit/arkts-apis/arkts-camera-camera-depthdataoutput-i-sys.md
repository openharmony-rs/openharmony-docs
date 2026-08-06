# DepthDataOutput（系统接口）

Implements depth data output. It inherits from [CameraOutput]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_.

**继承/实现关系：** DepthDataOutput extends [CameraOutput](arkts-camera-camera-cameraoutput-i.md)

**起始版本：** 13

**ArkTS模式：** ArkTS-Dyn起始版本为13；ArkTS-Sta起始版本为23。

<!--Device-camera-interface DepthDataOutput extends CameraOutput--><!--Device-camera-interface DepthDataOutput extends CameraOutput-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## off('depthDataAvailable')

```TypeScript
off(type: 'depthDataAvailable', callback?: AsyncCallback<DepthData>): void
```

Unsubscribes from depth data availability events.

**起始版本：** 13

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为13。

<!--Device-DepthDataOutput-off(type: 'depthDataAvailable', callback?: AsyncCallback<DepthData>): void--><!--Device-DepthDataOutput-off(type: 'depthDataAvailable', callback?: AsyncCallback<DepthData>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'depthDataAvailable' | 是 | Event type. The value is fixed at **'depthDataAvailable'**. The event can be listened for when a depthDataOutput instance is created. |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;DepthData&gt; | 否 | Callback used to return the result. If this parameter is specified, the subscription to the specified event with the specified callback is canceled. (The callback object cannot be an anonymous function.) Otherwise, the subscriptions to the specified event with all the callbacks are canceled. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

**示例：**

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

## off('error')

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

Unsubscribes from DepthDataOutput error events.

**起始版本：** 13

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为13。

<!--Device-DepthDataOutput-off(type: 'error', callback?: ErrorCallback): void--><!--Device-DepthDataOutput-off(type: 'error', callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | Event type. The value is fixed at **'error'**. The event can be listened for when a depthDataOutput instance is created. |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Callback used to return the result. If this parameter is specified, the subscription to the specified event with the specified callback is canceled. (The callback object cannot be an anonymous function.) Otherwise, the subscriptions to the specified event with all the callbacks are canceled. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

**示例：**

```TypeScript
function unregisterDepthDataOutputError(depthDataOutput: camera.DepthDataOutput): void {
  depthDataOutput.off('error');
}
```

## offDepthDataAvailable

```TypeScript
offDepthDataAvailable(callback?: AsyncCallback<DepthData>): void
```

Unsubscribes from depth data objects available event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-DepthDataOutput-offDepthDataAvailable(callback?: AsyncCallback<DepthData>): void--><!--Device-DepthDataOutput-offDepthDataAvailable(callback?: AsyncCallback<DepthData>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;DepthData&gt; | 否 | Callback used to get the available DepthData objects. |

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

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-DepthDataOutput-offError(callback?: ErrorCallback): void--><!--Device-DepthDataOutput-offError(callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Callback used to get the depth data output errors. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## on('depthDataAvailable')

```TypeScript
on(type: 'depthDataAvailable', callback: AsyncCallback<DepthData>): void
```

Subscribes to depth data availability events. This API uses an asynchronous callback to return the result. > **NOTE** > > Currently, you cannot use **off()** to unregister the callback in the callback method of **on()**.

**起始版本：** 13

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为13。

<!--Device-DepthDataOutput-on(type: 'depthDataAvailable', callback: AsyncCallback<DepthData>): void--><!--Device-DepthDataOutput-on(type: 'depthDataAvailable', callback: AsyncCallback<DepthData>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'depthDataAvailable' | 是 | Event type. The value is fixed at **'depthDataAvailable'**. The event can be listened for when a depthDataOutput instance is created. |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;DepthData&gt; | 是 | Callback used to listen for depth data. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

**示例：**

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

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

Subscribes to DepthDataOutput error events. This API uses an asynchronous callback to return the result. > **NOTE** > > Currently, you cannot use **off()** to unregister the callback in the callback method of **on()**.

**起始版本：** 13

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为13。

<!--Device-DepthDataOutput-on(type: 'error', callback: ErrorCallback): void--><!--Device-DepthDataOutput-on(type: 'error', callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | Event type. The value is fixed at **'error'**. The event can be listened for when a depthDataOutput instance is created. |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Callback used to return an error code defined in [CameraErrorCode]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function callback(depthDataOutputError: BusinessError): void {
  console.error(`Depth data output error code: ${depthDataOutputError.code}`);
}

function registerDepthDataOutputError(depthDataOutput: camera.DepthDataOutput): void {
  depthDataOutput.on('error', callback);
}
```

## onDepthDataAvailable

```TypeScript
onDepthDataAvailable(callback: AsyncCallback<DepthData>): void
```

Subscribes to depth data objects available event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-DepthDataOutput-onDepthDataAvailable(callback: AsyncCallback<DepthData>): void--><!--Device-DepthDataOutput-onDepthDataAvailable(callback: AsyncCallback<DepthData>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;DepthData&gt; | 是 | Callback used to get the available DepthData objects. |

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

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-DepthDataOutput-onError(callback: ErrorCallback): void--><!--Device-DepthDataOutput-onError(callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Callback used to get the depth data output errors. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## start

```TypeScript
start(): Promise<void>
```

Starts depth data output. This API uses a promise to return the result.

**起始版本：** 13

**ArkTS模式：** ArkTS-Dyn起始版本为13；ArkTS-Sta起始版本为23。

<!--Device-DepthDataOutput-start(): Promise<void>--><!--Device-DepthDataOutput-start(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

**示例：**

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

## stop

```TypeScript
stop(): Promise<void>
```

Stops depth data output. This API uses a promise to return the result.

**起始版本：** 13

**ArkTS模式：** ArkTS-Dyn起始版本为13；ArkTS-Sta起始版本为23。

<!--Device-DepthDataOutput-stop(): Promise<void>--><!--Device-DepthDataOutput-stop(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

**示例：**

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

