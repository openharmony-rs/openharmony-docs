# ScaleRingStyleOptions

环形有刻度样式选项。 继承自[CommonProgressStyleOptions](arkts-arkui-commonprogressstyleoptions-i.md)。

**继承/实现关系：** ScaleRingStyleOptions extends [CommonProgressStyleOptions](arkts-arkui-commonprogressstyleoptions-i.md)

**起始版本：** 10

<!--Device-unnamed-declare interface ScaleRingStyleOptions--><!--Device-unnamed-declare interface ScaleRingStyleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## scaleCount

```TypeScript
scaleCount?: number
```

设置环形进度条总刻度数。 默认值：120 取值范围：[2, min(width, height)*π/scaleWidth]，超出取值范围时，样式显示为环形无刻度进度条。 在scaleCount和scaleWidth都与默认值相等的情况下，设置组件宽度或高度小于77vp会显示为环形无刻度进度条。

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScaleRingStyleOptions-scaleCount?: number--><!--Device-ScaleRingStyleOptions-scaleCount?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scaleWidth

```TypeScript
scaleWidth?: Length
```

设置环形进度条刻度粗细（不支持百分比设置）。 默认值：2.0vp 取值范围：大于0的数值。 刻度粗细大于进度条宽度时，使用系统默认粗细。 在scaleCount和scaleWidth都与默认值相等的情况下，设置组件宽度或高度小于77vp会显示为环形无刻度进度条。

**类型：** Length

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScaleRingStyleOptions-scaleWidth?: Length--><!--Device-ScaleRingStyleOptions-scaleWidth?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeWidth

```TypeScript
strokeWidth?: Length
```

设置进度条宽度。 默认值：4.0vp 取值范围：大于0的数值，不支持百分比设置。 超出取值范围或设置非法值时按默认值处理。

**类型：** Length

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScaleRingStyleOptions-strokeWidth?: Length--><!--Device-ScaleRingStyleOptions-strokeWidth?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

