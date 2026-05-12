# Interface (Flash)
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

Flash继承自[FlashQuery](arkts-apis-camera-FlashQuery.md)。

闪光灯类，对设备闪光灯操作。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本Interface首批接口从API version 11开始支持。

## 导入模块

```ts
import { camera } from '@kit.CameraKit';
```

## setFlashMode<sup>11+</sup>

setFlashMode(flashMode: FlashMode): void

设置闪光灯模式。

进行设置之前，需要先检查：

1. 设备是否支持闪光灯，可使用方法[hasFlash](arkts-apis-camera-FlashQuery.md#hasflash11)。
2. 设备是否支持指定的闪光灯模式，可使用方法[isFlashModeSupported](arkts-apis-camera-FlashQuery.md#isflashmodesupported11)。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名       | 类型                     | 必填 | 说明                  |
| --------- | ----------------------- | ---- | --------------------- |
| flashMode | [FlashMode](arkts-apis-camera-e.md#flashmode) | 是   | ArtTS-Dyn： 指定闪光灯模式。传参为null或者undefined，作为0处理，闪光灯关闭。<br/>ArkTS-Sta： 指定闪光灯模式。目前不支持传参null或者undefined。 |

**错误码：**

以下错误码的详细介绍请参见[Camera错误码](errorcode-camera.md)。

| 错误码ID         | 错误信息        |
| --------------- | --------------- |
| 7400103                |  Session not config.                                   |

**示例：**

```ts
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

## getFlashMode<sup>11+</sup>

getFlashMode(): FlashMode

获取当前设备的闪光灯模式。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 22

**返回值：**

| 类型        | 说明                          |
| ---------- | ----------------------------- |
| [FlashMode](arkts-apis-camera-e.md#flashmode)    | 获取当前设备的闪光灯模式。接口调用失败会抛出相应错误码并返回undefined，错误码类型[CameraErrorCode](arkts-apis-camera-e.md#cameraerrorcode)。 |

**错误码：**

以下错误码的详细介绍请参见[Camera错误码](errorcode-camera.md)。

| 错误码ID         | 错误信息        |
| --------------- | --------------- |
| 7400103                |  Session not config.                                   |

**示例：**

```ts
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

## onFlashStateChange<sup>24+</sup>

onFlashStateChange(callback: Callback\<FlashState\>): void

订阅闪光灯状态变化事件回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名     | 类型            | 必填 | 说明       |
| -------- | -----------------| ---- | --------- |
| callback | Callback\<[FlashState](arkts-apis-camera-e.md#flashstate24)\> | 是   | 回调函数，用于获取闪光灯状态变化信息。 |

**示例：**

```ts
function onFlashStateChange(photoSession: camera.PhotoSession): void {
  photoSession.onFlashStateChange((flashState: camera.FlashState) => {
    console.info(`Flash state changed: ${flashState}`);
  });
}
```

## offFlashStateChange<sup>24+</sup>

offFlashStateChange(callback?: Callback\<FlashState\>): void

取消订阅闪光灯状态变化事件回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名     | 类型            | 必填 | 说明       |
| -------- | -----------------| ---- | --------- |
| callback | Callback\<[FlashState](arkts-apis-camera-e.md#flashstate24)\> | 否   | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

**示例：**

```ts
function offFlashStateChange(photoSession: camera.PhotoSession): void {
  photoSession.offFlashStateChange();
}
```
