# ProgressStyleOptions

进度条样式选项。 继承自[CommonProgressStyleOptions]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。

**继承/实现关系：** ProgressStyleOptions extends [CommonProgressStyleOptions](progress-commonprogressstyleoptions-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface ProgressStyleOptions extends CommonProgressStyleOptions--><!--Device-unnamed-export declare interface ProgressStyleOptions extends CommonProgressStyleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scaleCount

```TypeScript
scaleCount?: int
```

设置环形进度条总刻度数。 取值范围：[2, min(width, height)/scaleWidth/2/π]。默认值：120。 \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_超出取值范围时，样式显示为环形无刻度进度条。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ProgressStyleOptions-scaleCount?: int--><!--Device-ProgressStyleOptions-scaleCount?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scaleWidth

```TypeScript
scaleWidth?: Length
```

设置环形进度条刻度粗细（不支持百分比设置）。刻度粗细大于进度条宽度时，为系统默认粗细。 默认值：2vp。

**类型：** Length

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ProgressStyleOptions-scaleWidth?: Length--><!--Device-ProgressStyleOptions-scaleWidth?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeWidth

```TypeScript
strokeWidth?: Length
```

设置进度条宽度（不支持百分比设置）。 默认值：4vp。

**类型：** Length

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ProgressStyleOptions-strokeWidth?: Length--><!--Device-ProgressStyleOptions-strokeWidth?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

