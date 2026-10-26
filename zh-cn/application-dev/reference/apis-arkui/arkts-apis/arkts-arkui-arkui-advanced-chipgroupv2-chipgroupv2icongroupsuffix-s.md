# ChipGroupV2IconGroupSuffix

```TypeScript
export declare struct ChipGroupV2IconGroupSuffix
```

ChipGroupV2IconGroupSuffix用于在ChipGroupV2组件最右侧显示自定义内容，支持配置Image图标、Symbol图标或Symbol图标配置项，以及图标背景材质样式，适用于需要在标签组尾部添加额外操作入口的场景。

**起始版本：** 26.0.0

**装饰器类型：** @ComponentV2

<!--Device-unnamed-export declare struct ChipGroupV2IconGroupSuffix--><!--Device-unnamed-export declare struct ChipGroupV2IconGroupSuffix-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ChipGroupV2ItemConfig, ChipGroupV2Item, ChipGroupV2Items, ChipGroupV2ItemStyleConfig, ChipGroupV2ItemStyle, ChipGroupV2SpaceConfig, ChipGroupV2Space, ChipGroupV2IconItemConfig, ChipGroupV2SymbolItemConfig, ChipGroupV2PaddingConfig, ChipGroupV2Padding, ChipGroupV2IconGroupSuffix, ChipGroupV2 } from '@kit.ArkUI';
```

## build

```TypeScript
build(): void
```

build函数用于构造ChipGroupV2IconGroupSuffix组件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-ChipGroupV2IconGroupSuffix-build(): void--><!--Device-ChipGroupV2IconGroupSuffix-build(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## iconBackgroundSystemMaterial

```TypeScript
iconBackgroundSystemMaterial?: uiMaterial.Material
```

设置组件系统材质样式。不同材质具有不同的效果，能够影响组件的背景色[backgroundColor](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor-1)、边框颜色[borderColor](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#bordercolor)、边框宽度[borderWidth](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#borderwidth)、阴影[shadow](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#shadow-1)效果、材质层滤镜效果[materialFilter](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#materialfilter)。

默认值：undefined，不应用材质样式。

**类型：** [uiMaterial.Material](arkts-arkui-uimaterial-material-c.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-ChipGroupV2IconGroupSuffix-iconBackgroundSystemMaterial?: uiMaterial.Material--><!--Device-ChipGroupV2IconGroupSuffix-iconBackgroundSystemMaterial?: uiMaterial.Material-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## items

```TypeScript
items: Array<ChipGroupV2IconItemConfig | SymbolGlyphModifier | ChipGroupV2SymbolItemConfig>
```

尾部区域显示的自定义项数组，支持ChipGroupV2IconItemConfig（Image图标）、SymbolGlyphModifier（Symbol图标）或ChipGroupV2SymbolItemConfig（Symbol图标配置）类型。

传参SymbolGlyphModifier时，不支持使用symbolEffect修改动效类型和[effectStrategy](../arkts-components/arkts-arkui-symbolglyph-comp-attribute.md#effectstrategy)设置动效。

**类型：** Array&lt;[ChipGroupV2IconItemConfig](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2iconitemconfig-i.md) &#124; [SymbolGlyphModifier](../../apis-default/arkts-apis/arkts-default-arkui-modifier.md) &#124; [ChipGroupV2SymbolItemConfig](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2symbolitemconfig-i.md)&gt;

**起始版本：** 26.0.0

**装饰器类型：** @Require

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-ChipGroupV2IconGroupSuffix-items: Array<ChipGroupV2IconItemConfig | SymbolGlyphModifier | ChipGroupV2SymbolItemConfig>--><!--Device-ChipGroupV2IconGroupSuffix-items: Array<ChipGroupV2IconItemConfig | SymbolGlyphModifier | ChipGroupV2SymbolItemConfig>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
