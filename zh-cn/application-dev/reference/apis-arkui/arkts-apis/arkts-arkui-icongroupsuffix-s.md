# IconGroupSuffix

> **说明：**
>
> 传参SymbolGlyphModifier时，不支持使用symbolEffect修改动效类型和[effectStrategy](SymbolGlyphAttribute#effectStrategy)设置动效。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## iconBackgroundSystemMaterial

```TypeScript
iconBackgroundSystemMaterial?: uiMaterial.Material
```

设置组件系统材质样式。不同材质具有不同的效果，能够影响组件的[backgroundColor](../arkts-components/arkts-arkui-commonmethod-c.md#backgroundcolor-1)、
[border](../arkts-components/arkts-arkui-commonmethod-c.md#border-1)、[shadow](../arkts-components/arkts-arkui-commonmethod-c.md#shadow-1)等视觉属性。

默认值：undefined

值为undefined时，不应用材质样式。

**类型：** uiMaterial.Material

**起始版本：** 26.0.0

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## items

```TypeScript
items: Array<IconItemOptions | SymbolGlyphModifier | SymbolItemOptions>
```

尾部区域显示的自定义项数组，支持IconItemOptions（Image图标）、SymbolGlyphModifier（Symbol图标）或SymbolItemOptions（Symbol图标配置）类型。

**类型：** Array<IconItemOptions | SymbolGlyphModifier | SymbolItemOptions>

**起始版本：** 12

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

