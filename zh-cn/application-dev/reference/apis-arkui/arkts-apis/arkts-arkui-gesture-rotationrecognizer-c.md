# RotationRecognizer

旋转手势识别器对象，继承于[GestureRecognizer](arkts-arkui-gesture-gesturerecognizer-c.md#GestureRecognizer)。

**继承/实现关系：** RotationRecognizer extends [GestureRecognizer](arkts-arkui-gesture-gesturerecognizer-c.md#GestureRecognizer)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class RotationRecognizer--><!--Device-unnamed-export declare class RotationRecognizer-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getAngle

```TypeScript
getAngle(): double
```

返回预设旋转手势识别器触发旋转手势最小改变度数阈值。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RotationRecognizer-getAngle(): double--><!--Device-RotationRecognizer-getAngle(): double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | 预设旋转手势识别器触发旋转手势最小改变度数阈值，单位为deg。&lt;br/&gt;取值范围： [0, +∞)&lt;br/&gt;**说明：** &lt;br/&gt;当输入的改变度数的值小于等于0或大于360时，会被转化为默认值，默认值为1。 |

