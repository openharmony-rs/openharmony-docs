# TapRecognizer

点击手势识别器对象，继承自[GestureRecognizer](arkts-arkui-gesture-gesturerecognizer-c.md)。

**继承/实现关系：** TapRecognizer extends [GestureRecognizer](arkts-arkui-gesture-gesturerecognizer-c.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class TapRecognizer--><!--Device-unnamed-export declare class TapRecognizer-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getTapCount

```TypeScript
getTapCount(): int
```

返回预设点击手势识别器连续点击次数阈值。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TapRecognizer-getTapCount(): int--><!--Device-TapRecognizer-getTapCount(): int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 预设点击手势识别器连续点击次数阈值。<br/>取值范围：[0, +∞) |

