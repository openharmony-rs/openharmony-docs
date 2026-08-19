# Zoom

Zoom继承自[ZoomQuery](arkts-camera-camera-zoomquery-i.md)。 变焦类，对设备变焦操作。

**继承/实现关系：** Zoom extends [ZoomQuery](arkts-camera-camera-zoomquery-i.md)

**起始版本：** 23

<!--Device-camera-interface Zoom--><!--Device-camera-interface Zoom-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
import { cameraPicker } from '@kit.CameraKit';
```

## getZoomCenterPoint

```TypeScript
getZoomCenterPoint(): Point
```

Gets zoom center point.

**起始版本：** 23

<!--Device-Zoom-getZoomCenterPoint(): Point--><!--Device-Zoom-getZoomCenterPoint(): Point-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Point | The current zoom center point. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## prepareZoom

```TypeScript
prepareZoom(): void
```

Instructs the bottom layer to prepare for zooming, for example, powering on the sensor.

**起始版本：** 23

<!--Device-Zoom-prepareZoom(): void--><!--Device-Zoom-prepareZoom(): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function prepareZoom(sessionExtendsZoom: camera.Zoom): void {
  try {
    sessionExtendsZoom.prepareZoom();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The prepareZoom call failed. error code: ${err.code}`);
  }
}
```

## setZoomCenterPoint

```TypeScript
setZoomCenterPoint(point: Point): void
```

Sets zoom center point.

**起始版本：** 23

<!--Device-Zoom-setZoomCenterPoint(point: Point): void--><!--Device-Zoom-setZoomCenterPoint(point: Point): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| point | Point | 是 | Target zoom center point. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## unprepareZoom

```TypeScript
unprepareZoom(): void
```

Instructs the bottom layer to unprepare for zooming.

**起始版本：** 23

<!--Device-Zoom-unprepareZoom(): void--><!--Device-Zoom-unprepareZoom(): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function unprepareZoom(sessionExtendsZoom: camera.Zoom): void {
  try {
    sessionExtendsZoom.unprepareZoom();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The unprepareZoom call failed. error code: ${err.code}`);
  }
}
```

