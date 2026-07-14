# SheetOptions

继承自[BindOptions](arkts-arkui-bindoptions-i.md)。

半模态页面内容选项。

**继承/实现关系：** SheetOptions extends [BindOptions](arkts-arkui-bindoptions-i.md)

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## edgeLightMode

```TypeScript
edgeLightMode?: EdgeLightMode
```

设置半模态弹窗边缘光效动画模式。

默认值：EdgeLightMode.EDGELIGHT_DISABLED

**系统接口：** 此接口为系统接口。

**类型：** EdgeLightMode

**默认值：** EdgeLightMode.EDGELIGHT_DISABLED

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## enableBlurSnapshot

```TypeScript
enableBlurSnapshot?: boolean
```

指定是否对半模态启用模糊优化。
启用后，将使用模糊快照渲染半模态背景。
该属性在半模态显示后不能动态切换。

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## offset

```TypeScript
offset?: Position
```

设置半模态弹窗偏移量。当半模态为底部弹窗时，支持设置底部间距。不支持设置半模态的[SheetOptions](arkts-arkui-sheetoptions-i.md)中的detents属性。y轴设置为负数的时候不生效。

默认值：x轴为0vp，y轴坐标为0vp。

**系统接口：** 此接口为系统接口。

**类型：** Position

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

