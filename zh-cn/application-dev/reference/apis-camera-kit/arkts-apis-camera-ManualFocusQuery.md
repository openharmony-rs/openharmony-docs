# Interface (ManualFocusQuery)
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leoqsl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

手动对焦查询对象。

> **说明：**
>
> - 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本Interface首批接口从API version 24开始支持。

## 导入模块

```ts
import { camera } from '@kit.CameraKit';
```

## isFocusDistanceSupported<sup>24+</sup>

isFocusDistanceSupported(): boolean

检测是否支持设置对焦距离。

**原子化服务API：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型        | 说明                          |
| ---------- | ----------------------------- |
| boolean    | 表示是否支持对焦距离。返回true表示支持，返回false表示不支持。 |

**错误码：**

以下错误码的详细介绍请参见[Camera错误码](errorcode-camera.md)。

| 错误码ID         | 错误信息        |
| --------------- | --------------- |
| 7400103 | Session not config, only throw in session usage. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function isFocusDistanceSupported(photoSession: camera.PhotoSession): boolean {
  let isSupported = false;
  try {
    isSupported = photoSession.isFocusDistanceSupported();
  } catch (error) {
    let err = error as BusinessError;
    console.error(`The isFocusDistanceSupported call failed. error code: ${err.code}`);
  }
  return isSupported;
}
```
