# InputEventType

```TypeScript
declare type InputEventType = TouchEvent | MouseEvent | AxisEvent
```

[postInputEvent](arkts-arkui-buildernode-c.md#postInputEvent)的参数，定义要发送的输入事件类型。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type InputEventType = TouchEvent | MouseEvent | AxisEvent--><!--Device-unnamed-declare type InputEventType = TouchEvent | MouseEvent | AxisEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型 | 说明 |
| --- | --- |
| TouchEvent | 触摸事件。 |
| MouseEvent | 鼠标事件。 |
| AxisEvent | 轴事件。 |

