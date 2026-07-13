# ChipGroupV2IconGroupSuffix

定义后缀图标群

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## build

```TypeScript
build(): void
```

build函数用于构造ChipGroupV2IconGroupSuffix组件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## iconBackgroundSystemMaterial

```TypeScript
iconBackgroundSystemMaterial?: uiMaterial.Material
```

设置组件系统材质样式。不同材质具有不同的效果，能够影响组件的背景色[backgroundColor](../arkts-components/arkts-arkui-commonmethod-c.md#backgroundcolor-1)、边框颜色
[borderColor](../arkts-components/arkts-arkui-commonmethod-c.md#bordercolor-1)、边框宽度[borderWidth](../arkts-components/arkts-arkui-commonmethod-c.md#borderwidth-1)、阴影
[shadow](../arkts-components/arkts-arkui-commonmethod-c.md#shadow-1)效果、材质层滤镜效果
[materialFilter](../arkts-components/arkts-arkui-commonmethod-c.md#materialfilter-1)。

默认值：undefined，不应用材质样式。

**类型：** uiMaterial.Material

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## items

```TypeScript
items: Array<ChipGroupV2IconItemConfig | SymbolGlyphModifier | ChipGroupV2SymbolItemConfig>
```

尾部区域显示的自定义项数组，支持ChipGroupV2IconItemConfig（Image图标）、SymbolGlyphModifier（Symbol图标）或ChipGroupV2SymbolItemConfig（Symbol
图标配置）类型。

传参SymbolGlyphModifier时，不支持使用symbolEffect修改动效类型和[effectStrategy](SymbolGlyphAttribute#effectStrategy)设置动效。

**类型：** Array<ChipGroupV2IconItemConfig | SymbolGlyphModifier | ChipGroupV2SymbolItemConfig>

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

