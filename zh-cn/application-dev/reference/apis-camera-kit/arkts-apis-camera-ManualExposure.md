# Interface (ManualExposure)
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leoqsl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

ManualExposure继承自[ManualExposureQuery](arkts-apis-camera-ManualExposureQuery.md)。

手动曝光对象。

> **说明：**
>
> - 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本Interface首批接口从API version 24开始支持。

## 导入模块

```ts
import { camera } from '@kit.CameraKit';
```

## getExposureDuration<sup>24+</sup>

getExposureDuration(): number

获取当前曝光时长值。

**原子化服务API：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型        | 说明                          |
| ---------- | ----------------------------- |
| number    | 当前曝光时长值。单位：微秒。 |

**错误码：**

以下错误码的详细介绍请参见[Camera错误码](errorcode-camera.md)。

| 错误码ID         | 错误信息        |
| --------------- | --------------- |
| 7400102                |  Operation not allowed, session or inputdevice maybe abnormal.                                   |
| 7400103                |  Session not config.                                   |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function getExposureDuration(photoSession: camera.PhotoSession): number {
  let exposureDuration: number = 0;
  try {
    exposureDuration = photoSession.getExposureDuration();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The getExposureDuration call failed. error code: ${err.code}`);
  }
  return exposureDuration;
}
```

## setExposureDuration<sup>24+</sup>

setExposureDuration(exposureDuration: number): void

设置曝光时长值。

**原子化服务API：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名      | 类型                           | 必填  | 说明                           |
| -------- | -------------------------------| ---- | ----------------------------- |
| exposureDuration   | number  | 是   | 曝光时长值。单位：微秒。                 |

**错误码：**

以下错误码的详细介绍请参见[Camera错误码](errorcode-camera.md)。

| 错误码ID         | 错误信息        |
| --------------- | --------------- |
| 7400103                |  Session not config.                                   |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function setExposureDuration(photoSession: camera.PhotoSession, exposureDuration: number): void {
  try {
    photoSession.setExposureDuration(exposureDuration);
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The setExposureDuration call failed. error code: ${err.code}`);
  }
}
```

## onExposureInfoChange<sup>24+</sup>

onExposureInfoChange(callback: Callback\<ExposureInfo\>): void

订阅曝光信息变化事件回调。曝光参数更改后，系统将返回更新后的曝光信息。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名     | 类型            | 必填 | 说明       |
| -------- | -----------------| ---- | --------- |
| callback | Callback\<[ExposureInfo](arkts-apis-camera-i.md#exposureinfo24)\> | 是   | 回调函数，用于获取曝光值变化信息。 |

**示例：**

```ts
function onExposureInfoChange(photoSession: camera.PhotoSession): void {
  photoSession.onExposureInfoChange((exposureInfo: camera.ExposureInfo) => {
    console.info(`Exposure info changed, exposureTime: ${exposureInfo.exposureTime}`);
  });
}
```

## offExposureInfoChange<sup>24+</sup>

offExposureInfoChange(callback?: Callback\<ExposureInfo\>): void

取消订阅曝光信息变化事件回调。如果订阅了曝光信息，请在释放相机前取消订阅。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名     | 类型            | 必填 | 说明       |
| -------- | -----------------| ---- | --------- |
| callback | Callback\<[ExposureInfo](arkts-apis-camera-i.md#exposureinfo24)\> | 否   | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

**示例：**

```ts
function offExposureInfoChange(photoSession: camera.PhotoSession): void {
  photoSession.offExposureInfoChange();
}
```
