# Interface (Aperture)
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leoqsl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

Aperture继承自[ApertureQuery](arkts-apis-camera-ApertureQuery.md)。

物理光圈对象。

> **说明：**
>
> - 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本Interface首批接口从API version 24开始支持。

## 导入模块

```ts
import { camera } from '@kit.CameraKit';
```

## getPhysicalAperture<sup>24+</sup>

getPhysicalAperture(): number

获取当前物理光圈值。

**原子化服务API：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型        | 说明                          |
| ---------- | ----------------------------- |
| number    | 当前物理光圈值。 |

**错误码：**

以下错误码的详细介绍请参见[Camera错误码](errorcode-camera.md)。

| 错误码ID         | 错误信息        |
| --------------- | --------------- |
| 7400102                |  Operation not allowed, the inputDevice or the session is abnormal.                                   |
| 7400103                |  Session not config.                                   |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function getPhysicalAperture(photoSession: camera.PhotoSession): number {
  let aperture = 0.0;
  try {
    aperture = photoSession.getPhysicalAperture();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The getPhysicalAperture call failed. error code: ${err.code}`);
  }
  return aperture;
}
```

## setPhysicalAperture<sup>24+</sup>

setPhysicalAperture(aperture: number): void

设置物理光圈值。需要先通过[getSupportedPhysicalApertures](arkts-apis-camera-ApertureQuery.md#getsupportedphysicalapertures24)接口获取不同焦段支持的可设置光圈值，再通过调整焦段范围，设置支持的物理光圈值。

例如，"zoomRange":[1, 4]支持可设置物理光圈列表为2.6，需要通过[setZoomRatio](arkts-apis-camera-Zoom.md#setzoomratio11)设置焦段在[1, 4]之间，才可成功设置物理光圈值2.6。


**原子化服务API：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名      | 类型                           | 必填  | 说明                           |
| -------- | -------------------------------| ---- | ----------------------------- |
| aperture   | number  | 是   | 物理光圈值。                 |

**错误码：**

以下错误码的详细介绍请参见[Camera错误码](errorcode-camera.md)。

| 错误码ID         | 错误信息        |
| --------------- | --------------- |
| 7400102                |  Operation not allowed, the inputDevice or the session is abnormal.                                   |
| 7400103                |  Session not config.                                   |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function setPhysicalAperture(photoSession: camera.PhotoSession, aperture: number): void {
  try {
    photoSession.setPhysicalAperture(aperture);
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The setPhysicalAperture call failed. error code: ${err.code}`);
  }
}
```