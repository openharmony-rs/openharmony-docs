# Interface (MetadataOutput)
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--SE: @leo_ysl-->
<!--TSE: @xchaosioda-->

> **说明：**
>
> 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

metadata流。继承[CameraOutput](arkts-apis-camera-CameraOutput.md)。

## 导入模块

```ts
import { camera } from '@kit.CameraKit';
```

## start

start(callback: AsyncCallback\<void\>): void

开始输出metadata，通过注册回调函数获取结果。使用callback异步回调。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名     | 类型                                                         | 必填 | 说明                 |
| -------- | -------------------------- | ---- | ------------------- |
| callback | AsyncCallback\<void\>       | 是   | 回调函数，用于获取结果。接口调用失败会返回相应错误码，错误码类型[CameraErrorCode](arkts-apis-camera-e.md#cameraerrorcode)。 |

**错误码：**

以下错误码的详细介绍请参见[Camera错误码](errorcode-camera.md)。

| 错误码ID         | 错误信息        |
| --------------- | --------------- |
| 7400103                |  Session not config.                                   |
| 7400201                |  Camera service fatal error.                           |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function startMetadataOutput(metadataOutput: camera.MetadataOutput): void {
  metadataOutput.start((err: BusinessError) => {
    if (err) {
      console.error(`Failed to start metadata output, error code: ${err.code}.`);
      return;
    }
    console.info('Callback returned with metadata output started.');
  });
}
```

## start

start(): Promise\<void\>

开始输出metadata，通过Promise获取结果。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型                     | 说明                     |
| ----------------------  | ------------------------ |
| Promise\<void\>          | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[Camera错误码](errorcode-camera.md)。

| 错误码ID         | 错误信息        |
| --------------- | --------------- |
| 7400103                |  Session not config.                                   |
| 7400201                |  Camera service fatal error.                           |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function startMetadataOutput(metadataOutput: camera.MetadataOutput): void {
  metadataOutput.start().then(() => {
    console.info('Callback returned with metadata output started.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to metadata output stop, error code: ${error.code}`);
  });
}
```

## stop

stop(callback: AsyncCallback\<void\>): void

停止输出metadata，通过注册回调函数获取结果。使用callback异步回调。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名     | 类型                         | 必填 | 说明                  |
| -------- | -------------------------- | ---- | ------------------- |
| callback | AsyncCallback\<void\>       | 是   | 回调函数，用于获取结果。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function stopMetadataOutput(metadataOutput: camera.MetadataOutput): void {
  metadataOutput.stop((err: BusinessError) => {
    if (err) {
      console.error(`Failed to stop the metadata output, error code: ${err.code}.`);
      return;
    }
    console.info('Callback returned with metadata output stopped.');
  })
}
```

## stop

stop(): Promise\<void\>

停止输出metadata，通过Promise获取结果。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型                    | 说明                        |
| ----------------------  | --------------------------- |
| Promise\<void\>         | 无返回结果的Promise对象。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function stopMetadataOutput(metadataOutput: camera.MetadataOutput): void {
  metadataOutput.stop().then(() => {
    console.info('Callback returned with metadata output stopped.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to metadata output stop, error code: ${error.code}`);
  });
}
```

## on('metadataObjectsAvailable')

on(type: 'metadataObjectsAvailable', callback: AsyncCallback\<Array\<MetadataObject\>\>): void

监听检测到的metadata对象，通过注册回调函数获取结果。使用callback异步回调。

> **说明：**
>
> 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名      | 类型         | 必填 | 说明                                  |
| -------- | -------------- | ---- | ------------------------------------ |
| type     | string         | 是   | 监听事件，固定为'metadataObjectsAvailable'，metadataOutput创建成功后可监听。检测到有效的metadata数据时触发该事件发生并返回相应的metadata数据。 |
| callback | AsyncCallback\<Array\<[MetadataObject](arkts-apis-camera-i.md#metadataobject)\>\> | 是   | 回调函数，用于获取metadata数据。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function callback(err: BusinessError, metadataObjectArr: Array<camera.MetadataObject>): void {
  if (err !== undefined && err.code !== 0) {
    console.error(`Callback Error, errorCode: ${err.code}`);
    return;
  }
  console.info('metadata output metadataObjectsAvailable');
}

function registerMetadataObjectsAvailable(metadataOutput: camera.MetadataOutput): void {
  metadataOutput.on('metadataObjectsAvailable', callback);
}
```

## off('metadataObjectsAvailable')

off(type: 'metadataObjectsAvailable', callback?: AsyncCallback\<Array\<MetadataObject\>\>): void

注销监听检测到的metadata对象。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名      | 类型         | 必填 | 说明                                  |
| -------- | -------------- | ---- | ------------------------------------ |
| type     | string         | 是   | 监听事件，固定为'metadataObjectsAvailable'，metadataOutput创建成功后可监听。 |
| callback | AsyncCallback\<Array\<[MetadataObject](arkts-apis-camera-i.md#metadataobject)\>\> | 否   | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

**示例：**

```ts
function unregisterMetadataObjectsAvailable(metadataOutput: camera.MetadataOutput): void {
  metadataOutput.off('metadataObjectsAvailable');
}
```

## on('error')

on(type: 'error', callback: ErrorCallback): void

监听metadata流的错误，通过注册回调函数获取结果。使用callback异步回调。

> **说明：**
>
> 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名     | 类型         | 必填 | 说明                                     |
| -------- | ------------- | ---- | --------------------------------------- |
| type     | string        | 是   | 监听事件，固定为'error'，metadataOutput创建成功后可监听。metadata接口使用错误时触发该事件并返回对应错误码，比如调用[start](#start-1)，[CameraOutput.release](arkts-apis-camera-CameraOutput.md#release-1)接口时发生错误返回对应错误信息。 |
| callback | [ErrorCallback](../apis-basic-services-kit/js-apis-base.md#errorcallback) | 是   | 回调函数，用于获取错误信息。返回错误码，错误码类型[CameraErrorCode](arkts-apis-camera-e.md#cameraerrorcode)。            |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function callback(metadataOutputError: BusinessError): void {
  console.error(`Metadata output error code: ${metadataOutputError.code}`);
}

function registerMetadataOutputError(metadataOutput: camera.MetadataOutput): void {
  metadataOutput.on('error', callback);
}
```

## off('error')

off(type: 'error', callback?: ErrorCallback): void

注销监听metadata流的错误。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名     | 类型         | 必填 | 说明                                     |
| -------- | ------------- | ---- | --------------------------------------- |
| type     | string        | 是   | 监听事件，固定为'error'，metadataOutput创建成功后可监听。 |
| callback | [ErrorCallback](../apis-basic-services-kit/js-apis-base.md#errorcallback) | 否   | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

**示例：**

```ts
function unregisterMetadataOutputError(metadataOutput: camera.MetadataOutput): void {
  metadataOutput.off('error');
}
```
