# LinearStyleOptions

线性样式选项。

继承自[ScanEffectOptions](arkts-arkui-scaneffectoptions-i.md)和[CommonProgressStyleOptions](arkts-arkui-commonprogressstyleoptions-i.md)。

**继承/实现关系：** LinearStyleOptions extends [ScanEffectOptions](arkts-arkui-scaneffectoptions-i.md), [CommonProgressStyleOptions](arkts-arkui-commonprogressstyleoptions-i.md)

**起始版本：** 10

<!--Device-unnamed-declare interface LinearStyleOptions extends ScanEffectOptions, CommonProgressStyleOptions--><!--Device-unnamed-declare interface LinearStyleOptions extends ScanEffectOptions, CommonProgressStyleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeRadius

```TypeScript
strokeRadius?: PX | VP | LPX | Resource
```

设置线性进度条的圆角半径。

取值范围[0, strokeWidth / 2]。默认值：strokeWidth / 2。

**类型：** PX \| VP \| LPX \| Resource

**默认值：** strokeWidth / 2

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LinearStyleOptions-strokeRadius?: PX | VP | LPX | Resource--><!--Device-LinearStyleOptions-strokeRadius?: PX | VP | LPX | Resource-End-->

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

<!--Device-LinearStyleOptions-strokeWidth?: Length--><!--Device-LinearStyleOptions-strokeWidth?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

