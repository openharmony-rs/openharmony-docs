# ScaleRingStyleOptions

环形有刻度样式选项。

继承自[CommonProgressStyleOptions](arkts-arkui-progress-commonprogressstyleoptions-i.md)。

**继承/实现关系：** ScaleRingStyleOptions extends [CommonProgressStyleOptions](arkts-arkui-progress-commonprogressstyleoptions-i.md)

**起始版本：** 10

<!--Device-unnamed-declare interface ScaleRingStyleOptions extends CommonProgressStyleOptions--><!--Device-unnamed-declare interface ScaleRingStyleOptions extends CommonProgressStyleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scaleCount

```TypeScript
scaleCount?: number
```

设置环形进度条总刻度数。

默认值：120

取值范围：[2, min(width, height)/scaleWidth/2/π]，超出取值范围时，样式显示为环形无刻度进度条。默认情况下宽高最小为77vp。

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

设置环形进度条刻度粗细（不支持百分比设置）。刻度粗细大于进度条宽度时，为系统默认粗细。

默认值：2.0vp

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

设置进度条宽度（不支持百分比设置）。当宽度大于等于半径时，宽度默认修改为半径值的二分之一。

默认值：4.0vp

**类型：** Length

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScaleRingStyleOptions-strokeWidth?: Length--><!--Device-ScaleRingStyleOptions-strokeWidth?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

