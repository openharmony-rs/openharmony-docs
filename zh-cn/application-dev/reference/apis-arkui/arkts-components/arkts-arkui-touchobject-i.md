# TouchObject

触摸事件类型。

**起始版本：** 7

<!--Device-unnamed-declare interface TouchObject--><!--Device-unnamed-declare interface TouchObject-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getCurrentLocalPosition

```TypeScript
getCurrentLocalPosition?(): Coordinate2D
```

获取点击位置相对于当前组件实时位置的左上角坐标。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TouchObject-getCurrentLocalPosition?(): Coordinate2D--><!--Device-TouchObject-getCurrentLocalPosition?(): Coordinate2D-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Coordinate2D](../arkts-apis/arkts-arkui-coordinate2d-i.md) | - 点击位置相对于当前组件实时位置的左上角坐标。 |

## displayX

```TypeScript
displayX: number
```

触摸点在当前应用屏幕坐标系中的X坐标。

单位：vp

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TouchObject-displayX: number--><!--Device-TouchObject-displayX: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## displayY

```TypeScript
displayY: number
```

触摸点在当前应用屏幕坐标系中的Y坐标。

单位：vp

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TouchObject-displayY: number--><!--Device-TouchObject-displayY: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## globalDisplayX

```TypeScript
globalDisplayX?: number
```

触摸点在[全局坐标系](../../../windowmanager/window-terminology.md#全局坐标系)中的X坐标。

单位：vp

取值范围：[0, +∞)

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-TouchObject-globalDisplayX?: number--><!--Device-TouchObject-globalDisplayX?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## globalDisplayY

```TypeScript
globalDisplayY?: number
```

点击位置在[全局坐标系](../../../windowmanager/window-terminology.md#全局坐标系)中的Y坐标。

单位：vp

取值范围：[0, +∞)

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-TouchObject-globalDisplayY?: number--><!--Device-TouchObject-globalDisplayY?: number-End-->

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

<!--Device-TouchObject-hand?: InteractionHand--><!--Device-TouchObject-hand?: InteractionHand-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height?: number
```

当前手指按压区域的高度。

单位：vp

**类型：** number

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-TouchObject-height?: number--><!--Device-TouchObject-height?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id: number
```

手指唯一标识符。

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TouchObject-id: number--><!--Device-TouchObject-id: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## pressedTime

```TypeScript
pressedTime?: number
```

当前手指按下的时间。

单位：ns

**类型：** number

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-TouchObject-pressedTime?: number--><!--Device-TouchObject-pressedTime?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## pressure

```TypeScript
pressure?: number
```

当前手指按压的压力值。

取值范围：[0,65535)，压力越大，值越大。

**类型：** number

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-TouchObject-pressure?: number--><!--Device-TouchObject-pressure?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## screenX

```TypeScript
screenX: number
```

触摸点在当前应用窗口坐标系中的X坐标。

单位：vp

**类型：** number

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [windowX](arkts-arkui-touchobject-i.md#windowx)

<!--Device-TouchObject-screenX: number--><!--Device-TouchObject-screenX: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## screenY

```TypeScript
screenY: number
```

触摸点在当前应用窗口坐标系中的Y坐标。

单位：vp

**类型：** number

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [windowY](arkts-arkui-touchobject-i.md#windowy)

<!--Device-TouchObject-screenY: number--><!--Device-TouchObject-screenY: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: TouchType
```

触摸事件的类型。

**类型：** TouchType

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TouchObject-type: TouchType--><!--Device-TouchObject-type: TouchType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: number
```

当前手指按压区域的宽度。

单位：vp

**类型：** number

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-TouchObject-width?: number--><!--Device-TouchObject-width?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## windowX

```TypeScript
windowX: number
```

触摸点在当前应用窗口坐标系中的X坐标。

单位：vp

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TouchObject-windowX: number--><!--Device-TouchObject-windowX: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## windowY

```TypeScript
windowY: number
```

触摸点在当前应用窗口坐标系中的Y坐标。

单位：vp

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TouchObject-windowY: number--><!--Device-TouchObject-windowY: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## x

```TypeScript
x: number
```

触摸点在事件响应组件为基准的[组件坐标系](../../../ui/arkui-glossary.md#组件坐标系)中的X坐标。

单位：vp

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TouchObject-x: number--><!--Device-TouchObject-x: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## y

```TypeScript
y: number
```

触摸点在事件响应组件为基准的[组件坐标系](../../../ui/arkui-glossary.md#组件坐标系)中的Y坐标。

单位：vp

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TouchObject-y: number--><!--Device-TouchObject-y: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

