# FingerInfo

手指信息类型。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface FingerInfo--><!--Device-unnamed-export declare interface FingerInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getCurrentLocalPosition

```TypeScript
getCurrentLocalPosition(): Coordinate2D
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-FingerInfo-getCurrentLocalPosition(): Coordinate2D--><!--Device-FingerInfo-getCurrentLocalPosition(): Coordinate2D-End-->

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Coordinate2D](arkts-arkui-coordinate2d-i.md) |  |

## default

```TypeScript
default
```

获取手指位置相对于当前组件实时位置的左上角坐标。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FingerInfo-default--><!--Device-FingerInfo-default-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## displayX

```TypeScript
displayX: double
```

相对于屏幕左上角的x轴坐标，单位为vp。 取值范围：[0, +∞)

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FingerInfo-displayX: double--><!--Device-FingerInfo-displayX: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## displayY

```TypeScript
displayY: double
```

相对于屏幕左上角的y轴坐标，单位为vp。 取值范围：[0, +∞)

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FingerInfo-displayY: double--><!--Device-FingerInfo-displayY: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## globalDisplayX

```TypeScript
globalDisplayX?: double
```

相对于全局屏幕的左上角的X坐标，单位为vp。 取值范围：[0, +∞)

**类型：** double

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FingerInfo-globalDisplayX?: double--><!--Device-FingerInfo-globalDisplayX?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## globalDisplayY

```TypeScript
globalDisplayY?: double
```

相对于全局屏幕的左上角的Y坐标，单位为vp。 取值范围：[0, +∞)

**类型：** double

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FingerInfo-globalDisplayY?: double--><!--Device-FingerInfo-globalDisplayY?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## globalX

```TypeScript
globalX: double
```

相对于应用窗口左上角的x轴坐标，单位为vp。 取值范围：[0, +∞)

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FingerInfo-globalX: double--><!--Device-FingerInfo-globalX: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## globalY

```TypeScript
globalY: double
```

相对于应用窗口左上角的y轴坐标，单位为vp。 取值范围：[0, +∞)

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FingerInfo-globalY: double--><!--Device-FingerInfo-globalY: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## hand

```TypeScript
hand?: InteractionHand
```

表示事件是由左手点击还是右手点击触发。

**类型：** [InteractionHand](arkts-arkui-interactionhand-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FingerInfo-hand?: InteractionHand--><!--Device-FingerInfo-hand?: InteractionHand-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id: int
```

手指的索引编号，由按下手指的数量决定，按下一根手指为0，之后每按下1根手指索引编号加一。 **说明：** 鼠标（索引编号为1001）、手写笔（索引编号为102）、鼠标滚轮（索引编号为0）、触摸板双指滑动（索引编号为0）的索引编号也会被转化为手指的索引编号。 取值范围：[0, 9)

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FingerInfo-id: int--><!--Device-FingerInfo-id: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## localX

```TypeScript
localX: double
```

相对于当前组件元素原始区域左上角的x轴坐标，单位为vp。 取值范围：[0, +∞)

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FingerInfo-localX: double--><!--Device-FingerInfo-localX: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## localY

```TypeScript
localY: double
```

相对于当前组件元素原始区域左上角的y轴坐标，单位为vp。 取值范围：[0, +∞)

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FingerInfo-localY: double--><!--Device-FingerInfo-localY: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

