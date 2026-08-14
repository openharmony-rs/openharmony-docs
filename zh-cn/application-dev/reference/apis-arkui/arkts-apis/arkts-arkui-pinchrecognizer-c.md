# PinchRecognizer

捏合手势识别器对象，继承于[GestureRecognizer](arkts-arkui-gesturerecognizer-c.md#GestureRecognizer)。

**继承/实现关系：** PinchRecognizer extends [GestureRecognizer](arkts-arkui-gesturerecognizer-c.md#GestureRecognizer)

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

<!--Device-unnamed-declare class PinchRecognizer--><!--Device-unnamed-declare class PinchRecognizer-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getDistance

```TypeScript
getDistance(): number
```

返回预设捏合手势识别器最小识别距离阈值。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PinchRecognizer-getDistance(): number--><!--Device-PinchRecognizer-getDistance(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 预设捏合手势识别器最小识别距离阈值，单位为vp。&lt;br/&gt;取值范围：[0, +∞) |

