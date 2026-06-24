# TapRecognizer

点击手势识别器对象，继承自[GestureRecognizer](arkts-arkui-tapgesture-gesturerecognizer-c.md#GestureRecognizer)。

**继承/实现关系：** TapRecognizer extends [GestureRecognizer](arkts-arkui-tapgesture-gesturerecognizer-c.md#GestureRecognizer)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getTapCount

```TypeScript
getTapCount(): number
```

返回预设点击手势识别器连续点击次数阈值。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 预设点击手势识别器连续点击次数阈值。<br/>取值范围：[0, +∞) |

