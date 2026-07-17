# ChipGroupV2IconGroupSuffix

定义后缀图标群

**起始版本：** 26.0.0

<!--Device-unnamed-export declare struct ChipGroupV2IconGroupSuffix--><!--Device-unnamed-export declare struct ChipGroupV2IconGroupSuffix-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ChipGroupV2ItemConfig, ChipGroupV2ItemStyleConfig, ChipGroupV2SpaceConfig, ChipGroupV2IconGroupSuffix, ChipGroupV2Items, ChipGroupV2Padding, ChipGroupV2Item, ChipGroupV2ItemStyle, ChipGroupV2, ChipGroupV2PaddingConfig, ChipGroupV2IconItemConfig, ChipGroupV2SymbolItemConfig, ChipGroupV2Space } from '@kit.ArkUI';
```

## build

```TypeScript
build(): void
```

build函数用于构造ChipGroupV2IconGroupSuffix组件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2IconGroupSuffix-build(): void--><!--Device-ChipGroupV2IconGroupSuffix-build(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## iconBackgroundSystemMaterial

```TypeScript
iconBackgroundSystemMaterial?: uiMaterial.Material
```

设置组件系统材质样式。不同材质具有不同的效果，能够影响组件的背景色[backgroundColor](../arkts-components/arkts-arkui-common-commonmethod-c.md#backgroundcolor-1)、边框颜色[borderColor](../arkts-components/arkts-arkui-common-commonmethod-c.md#bordercolor-1)、边框宽度[borderWidth](../arkts-components/arkts-arkui-common-commonmethod-c.md#borderwidth-1)、阴影[shadow](../arkts-components/arkts-arkui-common-commonmethod-c.md#shadow-1)效果、材质层滤镜效果[materialFilter](../arkts-components/arkts-arkui-common-commonmethod-c.md#materialfilter-1)。

默认值：undefined，不应用材质样式。

**类型：** uiMaterial.Material

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2IconGroupSuffix-iconBackgroundSystemMaterial?: uiMaterial.Material--><!--Device-ChipGroupV2IconGroupSuffix-iconBackgroundSystemMaterial?: uiMaterial.Material-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## items

```TypeScript
items: Array<ChipGroupV2IconItemConfig | SymbolGlyphModifier | ChipGroupV2SymbolItemConfig>
```

尾部区域显示的自定义项数组，支持ChipGroupV2IconItemConfig（Image图标）、SymbolGlyphModifier（Symbol图标）或ChipGroupV2SymbolItemConfig（Symbol图标配置）类型。

传参SymbolGlyphModifier时，不支持使用symbolEffect修改动效类型和[effectStrategy](SymbolGlyphAttribute#effectStrategy)设置动效。

**类型：** Array<ChipGroupV2IconItemConfig | SymbolGlyphModifier | ChipGroupV2SymbolItemConfig>

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2IconGroupSuffix-items: Array<ChipGroupV2IconItemConfig | SymbolGlyphModifier | ChipGroupV2SymbolItemConfig>--><!--Device-ChipGroupV2IconGroupSuffix-items: Array<ChipGroupV2IconItemConfig | SymbolGlyphModifier | ChipGroupV2SymbolItemConfig>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

