# LinearStyleOptions

线性样式选项。 继承自[ScanEffectOptions](arkts-na-progress-scaneffectoptions-i.md)和[CommonProgressStyleOptions](arkts-na-progress-commonprogressstyleoptions-i.md)。

**继承/实现关系：** LinearStyleOptions extends [ScanEffectOptions](arkts-na-progress-scaneffectoptions-i.md), [CommonProgressStyleOptions](arkts-na-progress-commonprogressstyleoptions-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface LinearStyleOptions--><!--Device-unnamed-export declare interface LinearStyleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeRadius

```TypeScript
strokeRadius?: PX | VP | LPX | Resource
```

设置线性进度条的圆角半径。 取值范围[0, strokeWidth / 2]。 默认值：strokeWidth / 2。

**类型：** [PX](../../apis-arkui/arkts-apis/arkts-arkui-px-t.md) \| [VP](../../apis-arkui/arkts-apis/arkts-arkui-vp-t.md) \| [LPX](../../apis-arkui/arkts-apis/arkts-arkui-lpx-t.md) \| [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md)

**默认值：** strokeWidth / 2

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LinearStyleOptions-strokeRadius?: PX | VP | LPX | Resource--><!--Device-LinearStyleOptions-strokeRadius?: PX | VP | LPX | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeWidth

```TypeScript
strokeWidth?: Length
```

设置进度条宽度（不支持百分比设置）。 默认值：4vp。

**类型：** [Length](../../apis-arkui/arkts-apis/arkts-arkui-length-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LinearStyleOptions-strokeWidth?: Length--><!--Device-LinearStyleOptions-strokeWidth?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

