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

## getZoomRatio

```TypeScript
getZoomRatio(): double
```

获取当前的变焦比。

**起始版本：** 23

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-Zoom-getZoomRatio(): double--><!--Device-Zoom-getZoomRatio(): double-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | 获取当前的变焦比结果。接口调用失败会返回相应错误码，错误码类型[CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error.<br>**适用版本：** 12+ |

## setSmoothZoom

```TypeScript
setSmoothZoom(targetRatio: double, mode?: SmoothZoomMode): void
```

触发平滑变焦。

**起始版本：** 23

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-Zoom-setSmoothZoom(targetRatio: double, mode?: SmoothZoomMode): void--><!--Device-Zoom-setSmoothZoom(targetRatio: double, mode?: SmoothZoomMode): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| targetRatio | double | 是 | 目标值。通过[getZoomRatioRange](arkts-camera-camera-zoomquery-i.md#getzoomratiorange)获取支持的变焦范围，如果设置 超过支持范围的值，则只保留精度范围内数值。 |
| mode | [SmoothZoomMode](arkts-camera-camera-smoothzoommode-e.md) | 否 | 平滑变焦模式。默认为0。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config.<br>**适用版本：** 11 - 17 |

## setZoomRatio

```TypeScript
setZoomRatio(zoomRatio: double): void
```

设置变焦比，变焦精度最高为小数点后两位，如果设置超过支持的精度范围，则只保留精度范围内数值。

**起始版本：** 23

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-Zoom-setZoomRatio(zoomRatio: double): void--><!--Device-Zoom-setZoomRatio(zoomRatio: double): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| zoomRatio | double | 是 | 可变焦距比，通过[getZoomRatioRange](arkts-camera-camera-zoomquery-i.md#getzoomratiorange)获取支持的变焦范围，如果设置 超过支持范围的值，则只保留精度范围内数值。 <br>设置可变焦距比到底层生效需要一定时间，获取正确设置的可变焦距比需要等待1~2帧的时间。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

