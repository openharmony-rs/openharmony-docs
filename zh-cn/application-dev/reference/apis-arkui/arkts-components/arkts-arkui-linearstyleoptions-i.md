# LinearStyleOptions

线性样式选项。 继承自[ScanEffectOptions]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_和[CommonProgressStyleOptions]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_。

**继承/实现关系：** LinearStyleOptions extends [ScanEffectOptions](../arkts-apis/arkts-arkui-component/progress-scaneffectoptions-i.md), [CommonProgressStyleOptions](../arkts-apis/arkts-arkui-component/progress-commonprogressstyleoptions-i.md)

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

<!--Device-unnamed-declare interface LinearStyleOptions extends ScanEffectOptions, CommonProgressStyleOptions--><!--Device-unnamed-declare interface LinearStyleOptions extends ScanEffectOptions, CommonProgressStyleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeRadius

```TypeScript
strokeRadius?: PX | VP | LPX | Resource
```

设置线性进度条的圆角半径。 取值范围[0, strokeWidth / 2]。默认值：strokeWidth / 2。 超出取值范围时按默认值处理。

**类型：** PX \| VP \| LPX \| Resource

**默认值：** strokeWidth / 2

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LinearStyleOptions-strokeRadius?: PX | VP | LPX | Resource--><!--Device-LinearStyleOptions-strokeRadius?: PX | VP | LPX | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeWidth

```TypeScript
strokeWidth?: Length
```

设置进度条宽度。 默认值：4.0vp 取值范围：大于0的数值，不支持百分比设置。 超出取值范围或设置非法值时按默认值处理。

**类型：** Length

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LinearStyleOptions-strokeWidth?: Length--><!--Device-LinearStyleOptions-strokeWidth?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

