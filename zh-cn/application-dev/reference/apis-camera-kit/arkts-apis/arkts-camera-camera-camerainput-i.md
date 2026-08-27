# CameraInput

相机设备输入对象。会话中[Session](arkts-camera-camera-session-i.md)使用的相机信息。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
```

## close

```TypeScript
close(callback: AsyncCallback<void>): void
```

关闭相机，通过注册回调函数获取状态。使用callback异步回调。

**起始版本：** 10

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当关闭相机成功，err为undefined，否则为错误对象。错误码类型 [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

**示例**

```TypeScript
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

## close

```TypeScript
close(): Promise<void>
```

关闭相机，使用Promise异步回调。

**起始版本：** 10

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function closeCameraInput(cameraInput: camera.CameraInput): void {
  cameraInput.close().then(() => {
    console.info('Promise returned with camera closed.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to close the cameras, error code: ${error.code}.`);
  }); 
}
```

## getPhysicalCameraOrientation

```TypeScript
getPhysicalCameraOrientation(): number
```

获取设备当前折叠状态下的物理镜头角度。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回设备当前折叠状态下的物理镜头角度。 |

**示例**

```TypeScript
function getPhysicalCameraOrientation(cameraInput: camera.CameraInput): number {
  let physicalCameraOrientation: number = cameraInput.getPhysicalCameraOrientation();
  return physicalCameraOrientation;
}
```

## isPhysicalCameraOrientationVariable

```TypeScript
isPhysicalCameraOrientationVariable(): boolean
```

查询设备不同折叠状态下，相机物理镜头角度是否可变。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 查询设备不同折叠状态下，相机物理镜头角度是否可变。true表示可变，false表示不可变。若接口调用失败，返回undefined。 |

**示例**

```TypeScript
function isPhysicalCameraOrientationVariable(cameraInput: camera.CameraInput): boolean {
  let isVariable: boolean = cameraInput.isPhysicalCameraOrientationVariable();
  return isVariable;
}
```

## off('error')

```TypeScript
off(type: 'error', camera: CameraDevice, callback?: ErrorCallback): void
```

注销监听CameraInput的错误事件。

**起始版本：** 10

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 监听事件，固定为'error'，CameraInput对象创建成功可监听。相机设备出错情况下可触发该事件并返回结果，比如设备不可用或者冲突等返回对应错误信息。 |
| camera | [CameraDevice](arkts-camera-camera-cameradevice-i.md) | 是 | CameraDevice对象。 |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | 否 | 回调函数，如果指定参数则取消对应callback（callback对象不能是匿名函数），否则取消所有callback。 |

## off('cameraOcclusionDetection')

```TypeScript
off(type: 'cameraOcclusionDetection', callback?: AsyncCallback<CameraOcclusionDetectionResult>): void
```

注销监听CameraInput的镜头遮挡或脏污事件。使用callback异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'cameraOcclusionDetection' | 是 | 监听事件，固定为'cameraOcclusionDetection'，CameraInput对象创建成功可监听。相机镜头被遮挡或有脏污可 触发该事件并返回结果。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[CameraOcclusionDetectionResult](arkts-camera-camera-cameraocclusiondetectionresult-i.md)&gt; | 否 | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否 则取消所有callback。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.<br>**适用版本：** 12 - 22 |

## on('error')

```TypeScript
on(type: 'error', camera: CameraDevice, callback: ErrorCallback): void
```

监听CameraInput的错误事件，通过注册回调函数获取结果。使用callback异步回调。

> **说明：**
> 
> 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**起始版本：** 10

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 监听事件，固定为'error'，CameraInput对象创建成功可监听。相机设备出错情况下可触发该事件并返回结果，比如设备不可用或者冲突等返回对应错误信息。 |
| camera | [CameraDevice](arkts-camera-camera-cameradevice-i.md) | 是 | CameraDevice对象。 |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | 是 | 回调函数，用于获取结果。返回错误码，错误码类型[CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md)。 |

## on('cameraOcclusionDetection')

```TypeScript
on(type: 'cameraOcclusionDetection', callback: AsyncCallback<CameraOcclusionDetectionResult>): void
```

监听CameraInput的镜头遮挡或脏污事件，通过注册回调函数获取结果。使用callback异步回调。

> **说明：**
> 
> 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'cameraOcclusionDetection' | 是 | 监听事件，固定为'cameraOcclusionDetection'，CameraInput对象创建成功可监听。相机镜头被遮挡或有脏污可 触发该事件并返回结果。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[CameraOcclusionDetectionResult](arkts-camera-camera-cameraocclusiondetectionresult-i.md)&gt; | 是 | 回调函数，用于获取结果。返回遮挡状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.<br>**适用版本：** 12 - 22 |

## open

```TypeScript
open(callback: AsyncCallback<void>): void
```

打开相机，通过注册回调函数获取状态。使用callback异步回调。

**起始版本：** 10

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当打开相机成功，err为undefined，否则为错误对象，错误码类型 [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400107](../errorcode-camera.md#7400107-相机冲突) | Can not use camera cause of conflict. |
| [7400108](../errorcode-camera.md#7400108-安全策略无法使用相机) | Camera disabled cause of security reason. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function openCameraInput(cameraInput: camera.CameraInput): void {
  cameraInput.open((err: BusinessError) => {
    if (err) {
      console.error(`Failed to open camera, error code: ${err.code}.`);
      return;
    }
    console.info('Callback returned with camera opened.');
  });
}
```

## open

```TypeScript
open(): Promise<void>
```

打开相机，使用Promise异步回调。

**起始版本：** 10

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed. |
| [7400107](../errorcode-camera.md#7400107-相机冲突) | Can not use camera cause of conflict. |
| [7400108](../errorcode-camera.md#7400108-安全策略无法使用相机) | Camera disabled cause of security reason. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function openCameraInput(cameraInput: camera.CameraInput): void {
  cameraInput.open().then(() => {
    console.info('Promise returned with camera opened.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to open camera, error code: ${error.code}.`);
  });
}
```

## open

```TypeScript
open(isSecureEnabled: boolean): Promise<bigint>
```

打开相机。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isSecureEnabled | boolean | 是 | 设置true为使能以安全的方式打开相机，设置false则反之。接口调用失败会返回相应错误码，错误码类型 [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;bigint & gt; | Promise对象，返回安全相机的句柄。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400107](../errorcode-camera.md#7400107-相机冲突) | Can not use camera cause of conflict. |
| [7400108](../errorcode-camera.md#7400108-安全策略无法使用相机) | Camera disabled cause of security reason. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function openCameraInput(cameraInput: camera.CameraInput): void {
  cameraInput.open(true).then(() => {
    console.info('Promise returned with camera opened.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to open camera, error code: ${error.code}.`);
  });
}
```

## open

```TypeScript
open(type: CameraConcurrentType): Promise<void>
```

以指定的并发类型打开相机。使用Promise异步回调。

**起始版本：** 18

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [CameraConcurrentType](arkts-camera-camera-cameraconcurrenttype-e.md) | 是 | 以指定的并发类型打开相机。接口调用失败会返回相应错误码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed. |
| [7400107](../errorcode-camera.md#7400107-相机冲突) | Can not use camera cause of conflict. |
| [7400108](../errorcode-camera.md#7400108-安全策略无法使用相机) | Camera disabled cause of security reason. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function openCameraInput(cameraInput: camera.CameraInput): void {
  cameraInput.open(0).then(() => {
    console.info('Promise returned with camera opened.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to open camera, error code: ${error.code}.`);
  });
}
```

## usePhysicalCameraOrientation

```TypeScript
usePhysicalCameraOrientation(isUsed: boolean): void
```

选择是否使用物理镜头角度。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isUsed | boolean | 是 | 选择是否使用物理镜头角度。true表示使用，false表示不使用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function usePhysicalCameraOrientation(cameraInput: camera.CameraInput, isUsed: boolean): void {
  try {
    cameraInput.usePhysicalCameraOrientation(isUsed);
  } catch (error) {
    let err = error as BusinessError;
    console.error(`The usePhysicalCameraOrientation call failed. error code: ${err.code}`);
  }
}
```
