# ScaleRingStyleOptions

环形有刻度样式选项。 继承自[CommonProgressStyleOptions](arkts-na-progress-commonprogressstyleoptions-i.md#CommonProgressStyleOptions)。

**继承/实现关系：** ScaleRingStyleOptions extends [CommonProgressStyleOptions](arkts-na-progress-commonprogressstyleoptions-i.md#CommonProgressStyleOptions)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface ScaleRingStyleOptions--><!--Device-unnamed-export declare interface ScaleRingStyleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scaleCount

```TypeScript
scaleCount?: int
```

设置环形进度条总刻度数。 取值范围：[2, min(width, height)/scaleWidth/2/π]。默认值：120。 &lt;br&gt;超出取值范围时，样式显示为环形无刻度进度条。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScaleRingStyleOptions-scaleCount?: int--><!--Device-ScaleRingStyleOptions-scaleCount?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scaleWidth

```TypeScript
scaleWidth?: Length
```

设置环形进度条刻度粗细（不支持百分比设置）。刻度粗细大于进度条宽度时，为系统默认粗细。 默认值：2vp。

**类型：** [Length](../../apis-arkui/arkts-apis/arkts-arkui-length-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScaleRingStyleOptions-scaleWidth?: Length--><!--Device-ScaleRingStyleOptions-scaleWidth?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeWidth

```TypeScript
strokeWidth?: Length
```

设置进度条宽度（不支持百分比设置）。 默认值：4vp。

**类型：** [Length](../../apis-arkui/arkts-apis/arkts-arkui-length-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScaleRingStyleOptions-strokeWidth?: Length--><!--Device-ScaleRingStyleOptions-strokeWidth?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

