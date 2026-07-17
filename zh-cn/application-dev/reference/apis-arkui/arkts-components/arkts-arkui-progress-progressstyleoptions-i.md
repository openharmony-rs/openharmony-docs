# ProgressStyleOptions

进度条样式选项。

继承自[CommonProgressStyleOptions](arkts-arkui-progress-commonprogressstyleoptions-i.md)。

**继承/实现关系：** ProgressStyleOptions extends [CommonProgressStyleOptions](arkts-arkui-progress-commonprogressstyleoptions-i.md)

**起始版本：** 8

<!--Device-unnamed-declare interface ProgressStyleOptions extends CommonProgressStyleOptions--><!--Device-unnamed-declare interface ProgressStyleOptions extends CommonProgressStyleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scaleCount

```TypeScript
scaleCount?: number
```

设置环形进度条总刻度数。

默认值：120

取值范围：[2, min(width, height)/scaleWidth/2/π]，超出取值范围时，样式显示为环形无刻度进度条。默认情况下宽高最小为77vp。

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ProgressStyleOptions-scaleCount?: number--><!--Device-ProgressStyleOptions-scaleCount?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scaleWidth

```TypeScript
scaleWidth?: Length
```

设置环形进度条刻度粗细（不支持百分比设置）。刻度粗细大于进度条宽度时，为系统默认粗细。

默认值：2.0vp

**类型：** Length

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ProgressStyleOptions-scaleWidth?: Length--><!--Device-ProgressStyleOptions-scaleWidth?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeWidth

```TypeScript
strokeWidth?: Length
```

设置进度条宽度（不支持百分比设置）。

默认值：4.0vp

超出取值范围按默认值处理。

**类型：** Length

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ProgressStyleOptions-strokeWidth?: Length--><!--Device-ProgressStyleOptions-strokeWidth?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

