# SheetOptions

继承自[BindOptions](arkts-arkui-bindoptions-i.md#BindOptions)。 半模态页面内容选项。

**继承/实现关系：** SheetOptions extends [BindOptions](arkts-arkui-bindoptions-i.md#BindOptions)

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

<!--Device-unnamed-declare interface SheetOptions--><!--Device-unnamed-declare interface SheetOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## edgeLightMode

```TypeScript
edgeLightMode?: EdgeLightMode
```

设置半模态弹窗边缘光效动画模式。 默认值：EdgeLightMode.EDGELIGHT_DISABLED **系统接口：** 此接口为系统接口。

**类型：** [EdgeLightMode](arkts-arkui-edgelightmode-e-sys.md)

**默认值：** EdgeLightMode.EDGELIGHT_DISABLED

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SheetOptions-edgeLightMode?: EdgeLightMode--><!--Device-SheetOptions-edgeLightMode?: EdgeLightMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## offset

```TypeScript
offset?: Position
```

设置半模态弹窗偏移量。当半模态为底部弹窗时，支持设置底部间距。不支持设置半模态的[SheetOptions](arkts-arkui-sheetoptions-i.md#SheetOptions)中的detents属性。y轴设置为负数的时候不生效。 默认值：x轴为0vp，y轴坐标为0vp。 **系统接口：** 此接口为系统接口。

**类型：** Position

**起始版本：** 14

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为14。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SheetOptions-offset?: Position--><!--Device-SheetOptions-offset?: Position-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

