# FingerInfo

手指信息类型。

**起始版本：** 8

<!--Device-unnamed-interface FingerInfo--><!--Device-unnamed-interface FingerInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getCurrentLocalPosition

```TypeScript
getCurrentLocalPosition?(): Coordinate2D
```

获取点击位置相对于当前组件实时位置的左上角坐标。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-FingerInfo-getCurrentLocalPosition?(): Coordinate2D--><!--Device-FingerInfo-getCurrentLocalPosition?(): Coordinate2D-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Coordinate2D](arkts-arkui-units-coordinate2d-i.md) | - 点击位置相对于当前组件实时位置的左上角坐标。 |

## displayX

```TypeScript
displayX: number
```

相对于屏幕左上角的x轴坐标，单位为vp。

取值范围：[0, +∞)

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FingerInfo-displayX: number--><!--Device-FingerInfo-displayX: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## displayY

```TypeScript
displayY: number
```

相对于屏幕左上角的y轴坐标，单位为vp。

取值范围：[0, +∞)

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FingerInfo-displayY: number--><!--Device-FingerInfo-displayY: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## globalDisplayX

```TypeScript
globalDisplayX?: number
```

相对于全局屏幕的左上角的X坐标，单位为vp。

取值范围：[0, +∞)

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-FingerInfo-globalDisplayX?: number--><!--Device-FingerInfo-globalDisplayX?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## globalDisplayY

```TypeScript
globalDisplayY?: number
```

相对于全局屏幕的左上角的Y坐标，单位为vp。

取值范围：[0, +∞)

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-FingerInfo-globalDisplayY?: number--><!--Device-FingerInfo-globalDisplayY?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## globalX

```TypeScript
globalX: number
```

相对于应用窗口左上角的x轴坐标，单位为vp。

取值范围：[0, +∞)

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FingerInfo-globalX: number--><!--Device-FingerInfo-globalX: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## globalY

```TypeScript
globalY: number
```

相对于应用窗口左上角的y轴坐标，单位为vp。

取值范围：[0, +∞)

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FingerInfo-globalY: number--><!--Device-FingerInfo-globalY: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## hand

```TypeScript
hand?: InteractionHand
```

表示事件是由左手点击还是右手点击触发。

**类型：** InteractionHand

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-FingerInfo-hand?: InteractionHand--><!--Device-FingerInfo-hand?: InteractionHand-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id: number
```

手指的索引编号，由按下手指的数量决定，按下一根手指为0，之后每按下1根手指索引编号加一。

**说明：**

鼠标（索引编号为1001）、手写笔（索引编号为102）、鼠标滚轮（索引编号为0）、触摸板双指滑动（索引编号为0）的索引编号也会被转化为手指的索引编号。

取值范围：[0, 9)

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FingerInfo-id: number--><!--Device-FingerInfo-id: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## localX

```TypeScript
localX: number
```

相对于当前组件元素原始区域左上角的x轴坐标，单位为vp。

取值范围：[0, +∞)

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FingerInfo-localX: number--><!--Device-FingerInfo-localX: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## localY

```TypeScript
localY: number
```

相对于当前组件元素原始区域左上角的y轴坐标，单位为vp。

取值范围：[0, +∞)

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FingerInfo-localY: number--><!--Device-FingerInfo-localY: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

