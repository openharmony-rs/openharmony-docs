# WhiteBalance（系统接口）

WhiteBalance继承自[WhiteBalanceQuery](arkts-camera-camera-whitebalancequery-i.md#WhiteBalanceQuery（系统接口）)。 提供了处理设备白平衡的相关功能，包括获取和设置白平衡模式以及白平衡值。

**继承/实现关系：** WhiteBalance extends [WhiteBalanceQuery](arkts-camera-camera-whitebalancequery-i.md#WhiteBalanceQuery（系统接口）)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-camera-interface WhiteBalance--><!--Device-camera-interface WhiteBalance-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## getColorTint

```TypeScript
getColorTint(): int
```

获取当前白平衡的色调调节值。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-WhiteBalance-getColorTint(): int--><!--Device-WhiteBalance-getColorTint(): int-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回当前白平衡色调调节值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## setColorTint

```TypeScript
setColorTint(colorTint: int): void
```

设置白平衡的色调调节值。 设置之前需要先检查设备支持配置的白平衡色调调节范围，具体方法请参考[getColorTintRange](arkts-camera-camera-whitebalancequery-i.md#getColorTintRange)。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-WhiteBalance-setColorTint(colorTint: int): void--><!--Device-WhiteBalance-setColorTint(colorTint: int): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| colorTint | int | 是 | 设置手动白平衡色调调节值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

