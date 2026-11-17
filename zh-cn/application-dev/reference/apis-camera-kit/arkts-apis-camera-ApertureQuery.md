# Interface (ApertureQuery)
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leoqsl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

物理光圈查询对象。

> **说明：**
>
> - 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本Interface首批接口从API version 24开始支持。

## 导入模块

```ts
import { camera } from '@kit.CameraKit';
```

## getSupportedPhysicalApertures<sup>24+</sup>

getSupportedPhysicalApertures(): Array\<PhysicalAperture\>

获取支持的物理光圈。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型        | 说明                          |
| ---------- | ----------------------------- |
| Array\<[PhysicalAperture](arkts-apis-camera-i.md#physicalaperture24)\>     | 支持的物理光圈数组。 |

**错误码：**

以下错误码的详细介绍请参见[Camera错误码](errorcode-camera.md)。

| 错误码ID         | 错误信息        |
| --------------- | --------------- |
| 7400102                |  Operation not allowed, the inputDevice or the session is abnormal.                                   |
| 7400103                |  Session not config.                                   |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function getSupportedPhysicalApertures(photoSession: camera.PhotoSession): Array<camera.PhysicalAperture> {
  let apertures: Array<camera.PhysicalAperture> = [];
  try {
    apertures = photoSession.getSupportedPhysicalApertures();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The getSupportedPhysicalApertures call failed. error code: ${err.code}`);
  }
  return apertures;
}
```