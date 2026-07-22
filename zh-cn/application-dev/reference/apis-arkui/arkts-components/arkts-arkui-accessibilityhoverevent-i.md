# AccessibilityHoverEvent

The accessibility hover action triggers this method invocation.

**继承/实现关系：** AccessibilityHoverEvent extends [BaseEvent](arkts-arkui-baseevent-i.md)

**起始版本：** 12

<!--Device-unnamed-declare interface AccessibilityHoverEvent extends BaseEvent--><!--Device-unnamed-declare interface AccessibilityHoverEvent extends BaseEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## displayX

```TypeScript
displayX: number
```

X coordinate of the accessibility hover point relative to the left edge of the device screen.

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AccessibilityHoverEvent-displayX: number--><!--Device-AccessibilityHoverEvent-displayX: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## displayY

```TypeScript
displayY: number
```

Y coordinate of the accessibility hover point relative to the upper edge of the device screen.

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AccessibilityHoverEvent-displayY: number--><!--Device-AccessibilityHoverEvent-displayY: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## globalDisplayX

```TypeScript
globalDisplayX?: number
```

相对于全局显示的点的 Y 坐标。

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-AccessibilityHoverEvent-globalDisplayX?: number--><!--Device-AccessibilityHoverEvent-globalDisplayX?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## globalDisplayY

```TypeScript
globalDisplayY?: number
```

鼠标位置在[全局坐标系](../../../windowmanager/window-terminology.md#全局坐标系)中的Y坐标。

单位：vp

取值范围：[0, +∞)

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-AccessibilityHoverEvent-globalDisplayY?: number--><!--Device-AccessibilityHoverEvent-globalDisplayY?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: AccessibilityHoverType
```

Type of the accessibility hover event.

**类型：** AccessibilityHoverType

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AccessibilityHoverEvent-type: AccessibilityHoverType--><!--Device-AccessibilityHoverEvent-type: AccessibilityHoverType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## windowX

```TypeScript
windowX: number
```

X coordinate of the accessibility hover point relative to the left edge of the current window.

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AccessibilityHoverEvent-windowX: number--><!--Device-AccessibilityHoverEvent-windowX: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## windowY

```TypeScript
windowY: number
```

Y coordinate of the accessibility hover point relative to the upper edge of the current window.

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AccessibilityHoverEvent-windowY: number--><!--Device-AccessibilityHoverEvent-windowY: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## x

```TypeScript
x: number
```

X coordinate of the accessibility hover point relative to the left edge of the event hit element.

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AccessibilityHoverEvent-x: number--><!--Device-AccessibilityHoverEvent-x: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## y

```TypeScript
y: number
```

Y coordinate of the accessibility hover point relative to the upper edge of the event hit element.

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AccessibilityHoverEvent-y: number--><!--Device-AccessibilityHoverEvent-y: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

