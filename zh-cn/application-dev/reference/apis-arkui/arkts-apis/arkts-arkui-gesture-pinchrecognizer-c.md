# PinchRecognizer

捏合手势识别器对象，继承于[GestureRecognizer](arkts-arkui-gesture-gesturerecognizer-c.md)。

**继承/实现关系：** PinchRecognizer extends [GestureRecognizer](arkts-arkui-gesture-gesturerecognizer-c.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class PinchRecognizer--><!--Device-unnamed-export declare class PinchRecognizer-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getDistance

```TypeScript
getDistance(): double
```

返回预设捏合手势识别器最小识别距离阈值。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PinchRecognizer-getDistance(): double--><!--Device-PinchRecognizer-getDistance(): double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | 预设捏合手势识别器最小识别距离阈值，单位为vp。<br/>取值范围：[0, +∞) |

