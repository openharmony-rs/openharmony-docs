# OIS

```TypeScript
interface OIS extends OISQuery
```

提供了与光学防抖（OIS）相关的操作能力。

**继承/实现关系：** OIS extends [OISQuery](arkts-camera-camera-oisquery-i.md)

**起始版本：** 24

<!--Device-camera-interface OIS extends OISQuery--><!--Device-camera-interface OIS extends OISQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## setOISMode

```TypeScript
setOISMode(mode: OISMode): void
```

设置光学防抖模式。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务中使用。

<!--Device-OIS-setOISMode(mode: OISMode): void--><!--Device-OIS-setOISMode(mode: OISMode): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [OISMode](arkts-camera-camera-oismode-e.md) | 是 | 待设置的光学防抖模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed, the inputDevice or the session is abnormal. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## setOISModeCustom

```TypeScript
setOISModeCustom(pitch: number, yaw: number): void
```

设置各轴的自定义光学防抖偏置值。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务中使用。

<!--Device-OIS-setOISModeCustom(pitch: double, yaw: double): void--><!--Device-OIS-setOISModeCustom(pitch: double, yaw: double): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pitch | number | 是 | pitch 轴偏置值。 |
| yaw | number | 是 | yaw 轴偏置值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed, the inputDevice or the session is abnormal. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
