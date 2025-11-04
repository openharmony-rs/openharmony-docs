# Interface (CameraInput)

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

相机设备输入对象。

会话中[Session](arkts-apis-camera-Session.md)使用的相机信息。

## 导入模块

```ts
import { camera } from '@kit.CameraKit';
```

## open

open(callback: AsyncCallback\<void\>): void

打开相机，通过注册回调函数获取状态。使用callback异步回调。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名     | 类型                  | 必填 | 说明                  |
| -------- | -------------------- | ---- | ------------------- |
| callback | AsyncCallback\<void\> | 是   | 回调函数，用于获取结果。接口调用失败会返回相应错误码，错误码类型[CameraErrorCode](arkts-apis-camera-e.md#cameraerrorcode)。 |

**错误码：**

以下错误码的详细介绍请参见[Camera错误码](errorcode-camera.md)。

| 错误码ID         | 错误信息        |
| --------------- | --------------- |
| 7400107                |  Can not use camera cause of conflict.               |
| 7400108                |  Camera disabled cause of security reason.                                  |
| 7400201                |  Camera service fatal error.                                  |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function openCameraInput(cameraInput: camera.CameraInput): void {
  cameraInput.open((err: BusinessError) => {
    if (err) {
      console.error(`Failed to open the camera, error code: ${err.code}.`);
      return;
    }
    console.info('Callback returned with camera opened.');
  });
}
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function openCameraInput(cameraInput: camera.CameraInput): void {
  cameraInput.open((err: BusinessError | null , data:undefined) => {
    if (err && err!.code !== 0) {
      console.error(`Failed to open the camera, error code: ${err.code}.`);
      return;
    }
    console.info('Callback returned with camera opened.');
  });
}
```



## open

open(): Promise\<void\>

打开相机，通过Promise获取相机的状态。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 20

**返回值：**

| 类型           | 说明                      |
| -------------- | ----------------------- |
| Promise\<void\> | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[Camera错误码](errorcode-camera.md)。

| 错误码ID   | 错误信息                                      |
|---------|-------------------------------------------|
| 7400102 | Operation not allowed.                    |
| 7400107 | Can not use camera cause of conflict.     |
| 7400108 | Camera disabled cause of security reason. |
| 7400201 | Camera service fatal error.               |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function openCameraInput(cameraInput: camera.CameraInput): void {
  cameraInput.open().then(() => {
    console.info('Promise returned with camera opened.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to open the camera, error code: ${error.code}.`);
  });
}
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function openCameraInput(cameraInput: camera.CameraInput): void {
  cameraInput.open().then(() => {
    console.info('Promise returned with camera opened.');
  }).catch((error) => {
    let err = error as BusinessError;
    console.error(`Failed to open the camera, error code: ${err.code}.`);
  });
}
```

## open<sup>12+</sup>

open(isSecureEnabled: boolean): Promise\<bigint\>

打开相机，获取安全相机的句柄。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名     | 类型                  | 必填 | 说明                                                                      |
| -------- | -------------------- | ---- |-------------------------------------------------------------------------|
| isSecureEnabled | boolean | 是   | 设置true为使能以安全的方式打开相机，设置false则反之。接口调用失败会返回相应错误码，错误码类型[CameraErrorCode](arkts-apis-camera-e.md#cameraerrorcode)。 |

**返回值：**

| 类型           | 说明                      |
| -------------- | ----------------------- |
| Promise\<bigint\> | 使用Promise的方式获取打开相机句柄。 |

**错误码：**

以下错误码的详细介绍请参见[Camera错误码](errorcode-camera.md)。

| 错误码ID         | 错误信息        |
| --------------- | --------------- |
| 7400107                |  Can not use camera cause of conflict.               |
| 7400108                |  Camera disabled cause of security reason.                                  |
| 7400201                |  Camera service fatal error.                                  |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function openCameraInput(cameraInput: camera.CameraInput): void {
  cameraInput.open(true).then(() => {
    console.info('Promise returned with camera opened.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to open the camera, error code: ${error.code}.`);
  });
}
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function openCameraInput(cameraInput: camera.CameraInput): void {
  cameraInput.open(true).then(() => {
    console.info('Promise returned with camera opened.');
  }).catch((error) => {
    let err = error as BusinessError;
    console.error(`Failed to open the camera, error code: ${err.code}.`);
  });
}
```

## open<sup>18+</sup>

open(type: CameraConcurrentType): Promise\<void\>

以指定的并发类型打开相机。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**ArkTS-Dyn起始版本：** 18

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名     | 类型                  | 必填 | 说明                                                                      |
| -------- | -------------------- | ---- |-------------------------------------------------------------------------|
| type | [CameraConcurrentType](arkts-apis-camera-e.md#cameraconcurrenttype18) | 是   | 以指定的并发类型打开相机。接口调用失败会返回相应错误码。|

**返回值：**

| 类型           | 说明                      |
| -------------- | ----------------------- |
| Promise\<void\> | Promise对象。无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[Camera错误码](errorcode-camera.md)。

| 错误码ID   | 错误信息                                      |
|---------|-------------------------------------------|
| 7400102 | Operation not allowed.                    |
| 7400107 | Can not use camera cause of conflict.     |
| 7400108 | Camera disabled cause of security reason. |
| 7400201 | Camera service fatal error.               |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function openCameraInput(cameraInput: camera.CameraInput): void {
  cameraInput.open(0).then(() => {
    console.info('Promise returned with camera opened.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to open the camera, error code: ${error.code}.`);
  });
}
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function openCameraInput(cameraInput: camera.CameraInput): void {
  let type: camera.CameraConcurrentType = camera.CameraConcurrentType.CAMERA_LIMITED_CAPABILITY;
  cameraInput.open(type).then(() => {
    console.info('Promise returned with camera opened.');
  }).catch((error) => {
    let err = error as BusinessError;
    console.error(`Failed to open the camera, error code: ${err.code}.`);
  });
}
```

## close

close(callback: AsyncCallback\<void\>\): void

关闭相机，通过注册回调函数获取状态。使用callback异步回调。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名     | 类型                   | 必填 | 说明                  |
| -------- | -------------------- | ---- | -------------------- |
| callback | AsyncCallback\<void\> | 是   | 回调函数，用于获取结果。接口调用失败会返回相应错误码，错误码类型[CameraErrorCode](arkts-apis-camera-e.md#cameraerrorcode)。 |

**错误码：**

以下错误码的详细介绍请参见[Camera错误码](errorcode-camera.md)。

| 错误码ID         | 错误信息        |
| --------------- | --------------- |
| 7400201                |  Camera service fatal error.                                  |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function closeCameraInput(cameraInput: camera.CameraInput): void {
  cameraInput.close((err: BusinessError) => {
    if (err) {
      console.error(`Failed to close the cameras, error code: ${err.code}.`);
      return;
    }
    console.info('Callback returned with camera closed.');
  });
}
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function closeCameraInput(cameraInput: camera.CameraInput): void {
  cameraInput.close((err: BusinessError | null, data:undefined) => {
    if (err && err!.code !== 0) {
      console.error(`Failed to close the cameras, error code: ${err.code}.`);
      return;
    }
    console.info('Callback returned with camera closed.');
  });
}
```

## close

close(): Promise\<void\>

关闭相机，通过Promise获取状态。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 20

**返回值：**

| 类型           | 说明                      |
| -------------- | ----------------------- |
| Promise\<void\> | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[Camera错误码](errorcode-camera.md)。

| 错误码ID         | 错误信息        |
| --------------- | --------------- |
| 7400201                |  Camera service fatal error.                                  |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function closeCameraInput(cameraInput: camera.CameraInput): void {
  cameraInput.close().then(() => {
    console.info('Promise returned with camera closed.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to close the cameras, error code: ${error.code}.`);
  });
}
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function closeCameraInput(cameraInput: camera.CameraInput): void {
  cameraInput.close().then(() => {
    console.info('Promise returned with camera closed.');
  }).catch((error) => {
    let err = error as BusinessError;
    console.error(`Failed to close the cameras, error code: ${err.code}.`);
  });
}
```

## on('error')

on(type: 'error', camera: CameraDevice, callback: ErrorCallback): void

监听CameraInput的错误事件，通过注册回调函数获取结果。使用callback异步回调。

> **说明：**
>
> 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onError](#onerror22)。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名     | 类型                              | 必填 | 说明                                          |
| -------- | -------------------------------- | --- | ------------------------------------------- |
| type     | string                           | 是   | 监听事件，固定为'error'，CameraInput对象创建成功可监听。相机设备出错情况下可触发该事件并返回结果，比如设备不可用或者冲突等返回对应错误信息。 |
| camera   | [CameraDevice](arkts-apis-camera-i.md#cameradevice)    | 是   | CameraDevice对象。 |
| callback | [ErrorCallback](../apis-basic-services-kit/js-apis-base.md#errorcallback) | 是   | 回调函数，用于获取结果。返回错误码，错误码类型[CameraErrorCode](arkts-apis-camera-e.md#cameraerrorcode)。  |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function callback(err: BusinessError): void {
  console.error(`Camera input error code: ${err.code}`);
}

function registerCameraInputError(cameraInput: camera.CameraInput, camera: camera.CameraDevice): void {
  cameraInput.on('error', camera, callback);
}
```

## onError<sup>22+</sup>

onError(camera: CameraDevice, callback: ErrorCallback): void

监听CameraInput的错误事件，通过注册回调函数获取结果。使用callback异步回调。

> **说明：**
>
> 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**ArkTS模式：**该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('error')](#onerror)。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| camera   | [CameraDevice](arkts-apis-camera-i.md#cameradevice)          | 是   | CameraDevice对象。                                           |
| callback | [ErrorCallback](../apis-basic-services-kit/js-apis-base.md#errorcallback) | 是   | 回调函数，用于获取结果。返回错误码，错误码类型[CameraErrorCode](arkts-apis-camera-e.md#cameraerrorcode)。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function callback(err: BusinessError): void {
  console.error(`Camera input error code: ${err.code}`);
}

function registerCameraInputError(cameraInput: camera.CameraInput, camera: camera.CameraDevice): void {
  cameraInput.onError(camera, callback);
}
```

## off('error')

off(type: 'error', camera: CameraDevice, callback?: ErrorCallback): void

注销监听CameraInput的错误事件。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offError](#offerror22)。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名     | 类型                              | 必填 | 说明                                          |
| -------- | -------------------------------- | --- | ------------------------------------------- |
| type     | string                           | 是   | 监听事件，固定为'error'，CameraInput对象创建成功可监听。相机设备出错情况下可触发该事件并返回结果，比如设备不可用或者冲突等返回对应错误信息。 |
| camera   | [CameraDevice](arkts-apis-camera-i.md#cameradevice)    | 是   | CameraDevice对象。 |
| callback | [ErrorCallback](../apis-basic-services-kit/js-apis-base.md#errorcallback) | 否   | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

**示例：**

```ts
function unregisterCameraInputError(cameraInput: camera.CameraInput, camera: camera.CameraDevice): void {
  cameraInput.off('error', camera);
}
```

## offError<sup>22+</sup>

offError(camera: CameraDevice, callback?: ErrorCallback): void

注销监听CameraInput的错误事件。

**ArkTS模式：**该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('error')](#offerror)。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| camera   | [CameraDevice](arkts-apis-camera-i.md#cameradevice)          | 是   | CameraDevice对象。                                           |
| callback | [ErrorCallback](../apis-basic-services-kit/js-apis-base.md#errorcallback) | 否   | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

**示例：**

```ts
function unregisterCameraInputError(cameraInput: camera.CameraInput, camera: camera.CameraDevice): void {
  cameraInput.offError(camera);
}
```

