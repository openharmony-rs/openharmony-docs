# LinearStyleOptions

```TypeScript
declare interface LinearStyleOptions extends ScanEffectOptions, CommonProgressStyleOptions
```

线性样式选项。

继承自[ScanEffectOptions](arkts-arkui-progress-comp-scaneffectoptions-i.md)和[CommonProgressStyleOptions](arkts-arkui-progress-comp-commonprogressstyleoptions-i.md)。

**继承/实现关系：** LinearStyleOptions extends [ScanEffectOptions](arkts-arkui-progress-comp-scaneffectoptions-i.md), [CommonProgressStyleOptions](arkts-arkui-progress-comp-commonprogressstyleoptions-i.md)

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeRadius

```TypeScript
strokeRadius?: PX | VP | LPX | Resource
```

设置线性进度条的圆角半径。

取值范围[0, strokeWidth / 2]。默认值：strokeWidth / 2。

超出取值范围时按默认值处理。

**类型：** PX &#124; VP &#124; LPX &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md)

**默认值：** strokeWidth / 2

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeWidth

```TypeScript
strokeWidth?: Length
```

设置进度条宽度。

默认值：4.0vp

取值范围：大于0的数值，不支持百分比设置。

超出取值范围或设置非法值时按默认值处理。

**类型：** [Length](../arkts-apis/arkts-arkui-length-t.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
