# OIS

OIS (Optical Image Stabilization) interface.

**继承/实现关系：** OIS extends [OISQuery](arkts-camera-camera-oisquery-i.md)

**起始版本：** 24

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
```

## setOISMode

```TypeScript
setOISMode(mode: OISMode): void
```

Sets the OIS mode.

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [OISMode](arkts-camera-camera-oismode-e.md) | 是 | The OIS mode to set. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed, the inputDevice or the session is abnormal. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## setOISModeCustom

```TypeScript
setOISModeCustom(pitch: number, yaw: number): void
```

Sets custom OIS bias values for each axis.

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pitch | number | 是 | Bias value for pitch axis. |
| yaw | number | 是 | Bias value for yaw axis. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed, the inputDevice or the session is abnormal. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
