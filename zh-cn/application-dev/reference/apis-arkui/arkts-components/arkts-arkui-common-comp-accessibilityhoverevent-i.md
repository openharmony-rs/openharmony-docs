# AccessibilityHoverEvent

```TypeScript
declare interface AccessibilityHoverEvent extends BaseEvent
```

无障碍悬浮事件对象，用于获取触发无障碍悬浮事件时的详细信息，包括无障碍悬浮动作类型（type）、手指相对于组件/窗口/屏幕的坐标（x、y、windowX、windowY、displayX、displayY、globalDisplayX、globalDisplayY）等属性。

**继承/实现关系：** AccessibilityHoverEvent extends [BaseEvent](arkts-arkui-common-comp-baseevent-i.md)

**起始版本：** 12

<!--Device-unnamed-declare interface AccessibilityHoverEvent extends BaseEvent--><!--Device-unnamed-declare interface AccessibilityHoverEvent extends BaseEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## displayX

```TypeScript
displayX: number
```

手指位置相对于应用屏幕左上角的x轴坐标。单位：vp取值范围：[0, +∞)

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-AccessibilityHoverEvent-displayX: number--><!--Device-AccessibilityHoverEvent-displayX: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## displayY

```TypeScript
displayY: number
```

手指位置相对于应用屏幕左上角的y轴坐标。单位：vp取值范围：[0, +∞)

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-AccessibilityHoverEvent-displayY: number--><!--Device-AccessibilityHoverEvent-displayY: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## globalDisplayX

```TypeScript
globalDisplayX?: number
```

点相对于全局显示的 X 坐标。

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

<!--Device-AccessibilityHoverEvent-globalDisplayX?: number--><!--Device-AccessibilityHoverEvent-globalDisplayX?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## globalDisplayY

```TypeScript
globalDisplayY?: number
```

相对于全局显示的点的 Y 坐标。

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

<!--Device-AccessibilityHoverEvent-globalDisplayY?: number--><!--Device-AccessibilityHoverEvent-globalDisplayY?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: AccessibilityHoverType
```

无障碍悬浮动作类型，包括HOVER_ENTER（手指按下时触发）、HOVER_MOVE（触摸移动时触发）、HOVER_EXIT（手指抬起时触发）和HOVER_CANCEL（打断取消当前触发的事件）。

**类型：** [AccessibilityHoverType](../arkts-apis/arkts-arkui-accessibilityhovertype-e.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-AccessibilityHoverEvent-type: AccessibilityHoverType--><!--Device-AccessibilityHoverEvent-type: AccessibilityHoverType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## windowX

```TypeScript
windowX: number
```

手指位置相对于应用窗口左上角的x轴坐标。单位：vp取值范围：[0, +∞)

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-AccessibilityHoverEvent-windowX: number--><!--Device-AccessibilityHoverEvent-windowX: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## windowY

```TypeScript
windowY: number
```

手指位置相对于应用窗口左上角的y轴坐标。单位：vp取值范围：[0, +∞)

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-AccessibilityHoverEvent-windowY: number--><!--Device-AccessibilityHoverEvent-windowY: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## x

```TypeScript
x: number
```

手指位置相对于当前组件左上角的x轴坐标。单位：vp取值范围：[0, +∞)

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-AccessibilityHoverEvent-x: number--><!--Device-AccessibilityHoverEvent-x: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## y

```TypeScript
y: number
```

手指位置相对于当前组件左上角的y轴坐标。单位：vp取值范围：[0, +∞)

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-AccessibilityHoverEvent-y: number--><!--Device-AccessibilityHoverEvent-y: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
