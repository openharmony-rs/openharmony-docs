# Interface (StabilizationQuery)
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @zengyawen-->

> **说明：**
>
> - 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本Interface的起始版本为API version 12。接口在API version 12发生兼容变更，保留了内层元素的起始版本信息，会出现外层元素@since版本号大于内层元素的情况，不影响接口使用。

提供了查询设备在录像模式下是否支持对应的视频防抖模式的能力。

## 导入模块

```ts
import { camera } from '@kit.CameraKit';
```

## isVideoStabilizationModeSupported<sup>11+</sup>

isVideoStabilizationModeSupported(vsMode: VideoStabilizationMode): boolean

查询是否支持指定的视频防抖模式。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名      | 类型                                              | 必填 | 说明                             |
| -------- | ------------------------------------------------- | ---- | ------------------------------ |
| vsMode   | [VideoStabilizationMode](arkts-apis-camera-e.md#videostabilizationmode) | 是   | 视频防抖模式。                    |

**返回值：**

| 类型        | 说明                          |
| ---------- | ----------------------------- |
| boolean    | 返回视频防抖模式是否支持。true表示支持，false表示不支持。接口调用失败会返回相应错误码，错误码类型[CameraErrorCode](arkts-apis-camera-e.md#cameraerrorcode)。 |

**错误码：**

以下错误码的详细介绍请参见[Camera错误码](errorcode-camera.md)。

| 错误码ID         | 错误信息        |
| --------------- | --------------- |
| 7400103                |  Session not config, only throw in session usage.             |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function isVideoStabilizationModeSupported(videoSession: camera.VideoSession): boolean {
  let isSupported: boolean = false;
  try {
    isSupported = videoSession.isVideoStabilizationModeSupported(camera.VideoStabilizationMode.OFF);
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The isVideoStabilizationModeSupported call failed. error code: ${err.code}`);
  }
  return isSupported;
}
```
