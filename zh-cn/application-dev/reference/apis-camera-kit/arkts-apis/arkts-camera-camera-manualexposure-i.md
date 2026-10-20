# ManualExposure

```TypeScript
interface ManualExposure extends ManualExposureQuery
```

ManualExposure继承自[ManualExposureQuery](arkts-camera-camera-manualexposurequery-i.md)。提供了获取和设置曝光时长的方法。

**继承/实现关系：** ManualExposure extends [ManualExposureQuery](arkts-camera-camera-manualexposurequery-i.md)

**起始版本：** 24

<!--Device-camera-interface ManualExposure extends ManualExposureQuery--><!--Device-camera-interface ManualExposure extends ManualExposureQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## getExposureDuration

```TypeScript
getExposureDuration(): number
```

获取当前曝光值。

**起始版本：** 24

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务中使用。

<!--Device-ManualExposure-getExposureDuration(): int--><!--Device-ManualExposure-getExposureDuration(): int-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 当前的曝光值，单位为微秒。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed, session or inputdevice maybe abnormal. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## setExposureDuration

```TypeScript
setExposureDuration(exposureDuration: number): void
```

设置曝光时长值，单位：微秒。此设置仅在曝光模式设置为EXPOSURE_MODE_MANUAL时生效。

**起始版本：** 24

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务中使用。

<!--Device-ManualExposure-setExposureDuration(exposureDuration: int): void--><!--Device-ManualExposure-setExposureDuration(exposureDuration: int): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| exposureDuration | number | 是 | 曝光时长值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
