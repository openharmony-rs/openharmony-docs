# Interface (OIS)
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leoqsl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

OIS继承自[OISQuery](arkts-apis-camera-OISQuery.md)。

光学防抖（Optical Image Stabilization）对象。

> **说明：**
>
> - 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本Interface首批接口从API version 24开始支持。

## 导入模块

```ts
import { camera } from '@kit.CameraKit';
```

## setOISMode<sup>24+</sup>

setOISMode(mode: OISMode): void

设置OIS模式。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名     | 类型             | 必填 | 说明       |
| -------- | --------------- | ---- | --------- |
| mode | [OISMode](arkts-apis-camera-e.md#oismode24) | 是 | 设置的OIS模式。 |

**错误码：**

以下错误码的详细介绍请参见[Camera错误码](errorcode-camera.md)。

| 错误码ID         | 错误信息        |
| --------------- | --------------- |
| 7400102 | Operation not allowed, the inputDevice or the session is abnormal. |
| 7400103 | Session not config. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function setOISMode(photoSession: camera.PhotoSession, mode: camera.OISMode): void {
  try {
    photoSession.setOISMode(mode);
  } catch (error) {
    let err = error as BusinessError;
    console.error(`The setOISMode call failed. error code: ${err.code}`);
  }
}
```

## setOISModeCustom<sup>24+</sup>

setOISModeCustom(pitch: number, yaw: number): void

设置各轴向的自定义OIS偏置值，仅在[OISMode](arkts-apis-camera-e.md#oismode24)为CUSTOM模式时支持调用。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名     | 类型             | 必填 | 说明       |
| -------- | --------------- | ---- | --------- |
| pitch | number | 是 | 俯仰轴偏置值。 |
| yaw | number | 是 | 偏航轴偏置值。 |

**错误码：**

以下错误码的详细介绍请参见[Camera错误码](errorcode-camera.md)。

| 错误码ID         | 错误信息        |
| --------------- | --------------- |
| 7400102 | Operation not allowed, the inputDevice or the session is abnormal. |
| 7400103 | Session not config. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function setOISModeCustom(photoSession: camera.PhotoSession, pitch: number, yaw: number): void {
  try {
    photoSession.setOISModeCustom(pitch, yaw);
  } catch (error) {
    let err = error as BusinessError;
    console.error(`The setOISModeCustom call failed. error code: ${err.code}`);
  }
}
```