# HoverEvent

继承于[BaseEvent](arkts-arkui-common-baseevent-i.md)。

**继承/实现关系：** HoverEvent extends [BaseEvent](arkts-arkui-common-baseevent-i.md)

**起始版本：** 10

<!--Device-unnamed-declare interface HoverEvent extends BaseEvent--><!--Device-unnamed-declare interface HoverEvent extends BaseEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## displayX

```TypeScript
displayX?: number
```

鼠标光标或手写笔位置在当前应用屏幕坐标系中的X坐标。

单位：vp

取值范围：[0, +∞)

**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。

**类型：** number

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-HoverEvent-displayX?: number--><!--Device-HoverEvent-displayX?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## displayY

```TypeScript
displayY?: number
```

鼠标光标或手写笔位置在当前应用屏幕坐标系中的Y坐标。

单位：vp

取值范围：[0, +∞)

**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。

**类型：** number

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-HoverEvent-displayY?: number--><!--Device-HoverEvent-displayY?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## globalDisplayX

```TypeScript
globalDisplayX?: number
```

鼠标光标或手写笔位置在[全局坐标系](../../../../windowmanager/window-terminology.md#全局坐标系)中的X坐标。

单位：vp

取值范围：[0, +∞)

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-HoverEvent-globalDisplayX?: number--><!--Device-HoverEvent-globalDisplayX?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## globalDisplayY

```TypeScript
globalDisplayY?: number
```

相对于全局显示的点的 Y 坐标。

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-HoverEvent-globalDisplayY?: number--><!--Device-HoverEvent-globalDisplayY?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## stopPropagation

```TypeScript
stopPropagation: () => void
```

阻塞[事件冒泡](../../../../ui/arkts-interaction-basic-principles.md#事件冒泡)。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** () => void

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HoverEvent-stopPropagation: () => void--><!--Device-HoverEvent-stopPropagation: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## windowX

```TypeScript
windowX?: number
```

鼠标光标或手写笔位置在当前应用窗口坐标系中的X坐标。

单位：vp

取值范围：[0, +∞)

**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。

**类型：** number

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-HoverEvent-windowX?: number--><!--Device-HoverEvent-windowX?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## windowY

```TypeScript
windowY?: number
```

鼠标光标或手写笔位置在当前应用窗口坐标系中的Y坐标。

单位：vp

取值范围：[0, +∞)

**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。

**类型：** number

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-HoverEvent-windowY?: number--><!--Device-HoverEvent-windowY?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## x

```TypeScript
x?: number
```

鼠标光标或手写笔位置在当前组件为基准的[组件坐标系](../../../../ui/arkui-glossary.md#组件坐标系)中的X坐标。

单位：vp

取值范围：[0, +∞)

**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。

**类型：** number

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-HoverEvent-x?: number--><!--Device-HoverEvent-x?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## y

```TypeScript
y?: number
```

鼠标光标或手写笔位置在当前组件为基准的[组件坐标系](../../../../ui/arkui-glossary.md#组件坐标系)中的Y坐标。

单位：vp

取值范围：[0, +∞)

**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。

**类型：** number

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-HoverEvent-y?: number--><!--Device-HoverEvent-y?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

