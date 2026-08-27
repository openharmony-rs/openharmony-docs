# Flash

Flash继承自[FlashQuery](arkts-camera-camera-flashquery-i.md)。闪光灯类，对设备闪光灯操作。

**继承/实现关系：** Flash extends [FlashQuery](arkts-camera-camera-flashquery-i.md)

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
```

## getFlashMode

```TypeScript
getFlashMode(): FlashMode
```

获取当前设备的闪光灯模式。

**起始版本：** 11

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FlashMode](arkts-camera-camera-flashmode-e.md) | 获取当前设备的闪光灯模式。接口调用失败会抛出相应错误码并返回undefined，错误码类型 [CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getFlashMode(captureSession: camera.CaptureSession): camera.FlashMode | undefined {
  let flashMode: camera.FlashMode | undefined = undefined;
  try {
    flashMode = captureSession.getFlashMode();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The getFlashMode call failed.error code: ${err.code}`);
  }
  return flashMode;
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getFlashMode(photoSession: camera.PhotoSession): camera.FlashMode | undefined {
  let flashMode: camera.FlashMode | undefined = undefined;
  try {
    flashMode = photoSession.getFlashMode();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The getFlashMode call failed.error code: ${err.code}`);
  }
  return flashMode;
}
```

## offFlashStateChange

```TypeScript
offFlashStateChange(callback?: Callback<FlashState>): void
```

取消订阅闪光灯状态变化事件回调。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[FlashState](arkts-camera-camera-flashstate-e.md)&gt; | 否 | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

**示例**

```TypeScript
function offFlashStateChange(photoSession: camera.PhotoSession): void {
  photoSession.offFlashStateChange();
}
```

## onFlashStateChange

```TypeScript
onFlashStateChange(callback: Callback<FlashState>): void
```

订阅闪光灯状态变化事件回调。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[FlashState](arkts-camera-camera-flashstate-e.md)&gt; | 是 | 回调函数，用于获取闪光灯状态变化信息。 |

**示例**

```TypeScript
function onFlashStateChange(photoSession: camera.PhotoSession): void {
  photoSession.onFlashStateChange((flashState: camera.FlashState) => {
    console.info(`Flash state changed: ${flashState}`);
  });
}
```

## setFlashMode

```TypeScript
setFlashMode(flashMode: FlashMode): void
```

设置闪光灯模式。进行设置之前，需要先检查：
1. 设备是否支持闪光灯，可使用方法[hasFlash](arkts-camera-camera-flashquery-i.md#hasflash)。
2. 设备是否支持指定的闪光灯模式，可使用方法[isFlashModeSupported](arkts-camera-camera-flashquery-i.md#isflashmodesupported)。

**起始版本：** 11

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| flashMode | [FlashMode](arkts-camera-camera-flashmode-e.md) | 是 | 指定闪光灯模式。传参为null或者undefined，作为0处理，闪光灯关闭。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function setFlashMode(captureSession: camera.CaptureSession): void {
  try {
    captureSession.setFlashMode(camera.FlashMode.FLASH_MODE_AUTO);
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The setFlashMode call failed. error code: ${err.code}`);
  }
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function setFlashMode(photoSession: camera.PhotoSession): void {
  try {
    photoSession.setFlashMode(camera.FlashMode.FLASH_MODE_AUTO);
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The setFlashMode call failed. error code: ${err.code}`);
  }
}
```
