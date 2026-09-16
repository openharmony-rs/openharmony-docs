# SheetOptions

继承自[BindOptions](arkts-arkui-bindoptions-i.md)。

半模态页面内容选项。

**继承/实现关系：** SheetOptions extends [BindOptions](arkts-arkui-bindoptions-i.md)

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## blurSnapshot

```TypeScript
blurSnapshot?: BlurSnapshotOptions
```

半模态模糊快照优化选项，用于降低模糊渲染的计算开销。当使用blurStyle或systemMaterial设置模糊或材质效果时发现功耗明显增加时，可开启模糊优化。开启后，若半模态配置了blurStyle或systemMaterial，其模糊效果将使用快照渲染以降低计算开销；若未设置blurStyle或systemMaterial，则开启enableBlurSnapshot不产生模糊优化效果。该属性在半模态展示后不支持和undefined之间的动态切换，若在展示后尝试切换则设置不生效。半模态的POPUP类型不支持模糊优化，若在POPUP类型上设置enableBlurSnapshot=true则该设置不生效。

默认值：undefined，关闭模糊优化

**系统接口：** 此接口为系统接口。

**类型：** [BlurSnapshotOptions](arkts-arkui-blursnapshotoptions-i-sys.md)

**默认值：** undefined

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## edgeLightMode

```TypeScript
edgeLightMode?: EdgeLightMode
```

设置半模态弹窗边缘光效动画模式。未设置该属性时，边缘光效动画默认关闭。对于半模态弹窗的边缘光效动画，EDGELIGHT_AUTO：在所有算力设备都关闭；EDGELIGHT_ENABLED：开启边缘光效动画；EDGELIGHT_DISABLED：关闭边缘光效动画。

默认值：EdgeLightMode.EDGELIGHT_DISABLED

**系统接口：** 此接口为系统接口。

**类型：** [EdgeLightMode](arkts-arkui-edgelightmode-e-sys.md)

**默认值：** EdgeLightMode.EDGELIGHT_DISABLED

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## offset

```TypeScript
offset?: Position
```

设置半模态弹窗偏移量。仅当半模态为底部弹窗时，支持设置底部间距。不支持设置半模态的[SheetOptions](arkts-arkui-sheetoptions-i.md)中的detents属性。y轴设置为正数时不生效，将回退至默认值0vp。

默认值：x轴坐标为0vp，y轴坐标为0vp。

**系统接口：** 此接口为系统接口。

**类型：** Position

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
