# RingStyleOptions

环形无刻度样式选项。 继承自[ScanEffectOptions](arkts-arkui-scaneffectoptions-i.md#ScanEffectOptions)和[CommonProgressStyleOptions](arkts-arkui-commonprogressstyleoptions-i.md#CommonProgressStyleOptions)。

**继承/实现关系：** RingStyleOptions extends [ScanEffectOptions](arkts-arkui-scaneffectoptions-i.md#ScanEffectOptions), [CommonProgressStyleOptions](arkts-arkui-commonprogressstyleoptions-i.md#CommonProgressStyleOptions)

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

<!--Device-unnamed-declare interface RingStyleOptions--><!--Device-unnamed-declare interface RingStyleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shadow

```TypeScript
shadow?: boolean
```

进度条阴影开关。 true：表示打开进度条阴影；false：表示关闭进度条阴影。 默认值：false

**类型：** boolean

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RingStyleOptions-shadow?: boolean--><!--Device-RingStyleOptions-shadow?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## status

```TypeScript
status?: ProgressStatus
```

设置进度条状态。当设置为ProgressStatus.LOADING时会开启检查更新动效，此时设置进度值不生效。当从ProgressStatus.LOADING设置为ProgressStatus.PROGRESSING时，检查更新 动效会执行到终点再停止。 默认值：ProgressStatus.PROGRESSING

**类型：** [ProgressStatus](arkts-arkui-progressstatus-e.md)

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RingStyleOptions-status?: ProgressStatus--><!--Device-RingStyleOptions-status?: ProgressStatus-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeWidth

```TypeScript
strokeWidth?: Length
```

设置进度条宽度。 默认值：4.0vp 取值范围：大于0的数值，不支持百分比设置。 超出取值范围或设置非法值时按默认值处理。

**类型：** Length

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RingStyleOptions-strokeWidth?: Length--><!--Device-RingStyleOptions-strokeWidth?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

