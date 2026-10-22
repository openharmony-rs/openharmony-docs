# IconGroupSuffix

```TypeScript
export declare struct IconGroupSuffix
```

用于定义ChipGroup的后缀区域图标属性，在ChipGroup组件最右侧显示自定义内容的可配置suffix属性中使用。

**起始版本：** 12

**装饰器类型：** @Component

<!--Device-unnamed-export declare struct IconGroupSuffix--><!--Device-unnamed-export declare struct IconGroupSuffix-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { IconOptions, LabelOptions as ChipItemLabelOptions, ChipGroupItemOptions, ChipItemStyle, ChipGroupSpaceOptions, IconItemOptions, IconGroupSuffix, ChipGroup, SuffixImageIconOptions, SymbolItemOptions } from '@kit.ArkUI';
```

## iconBackgroundSystemMaterial

```TypeScript
iconBackgroundSystemMaterial?: uiMaterial.Material
```

设置组件系统材质样式。不同材质具有不同的效果，能够影响组件的[backgroundColor](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor-1)、[border](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#border)、[shadow](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#shadow-1)视觉属性。设置自动反色的系统材质时，fontColor如果使用系统预定义的可反色颜色资源（如`$r('sys.color.font_primary')`），颜色自动适配到材质背景色的反色。

默认值：undefined

值为undefined时，不应用材质样式。

**类型：** [uiMaterial.Material](arkts-arkui-uimaterial-material-c.md)

**起始版本：** 26.0.0

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-IconGroupSuffix-iconBackgroundSystemMaterial?: uiMaterial.Material--><!--Device-IconGroupSuffix-iconBackgroundSystemMaterial?: uiMaterial.Material-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## items

```TypeScript
items: Array<IconItemOptions | SymbolGlyphModifier | SymbolItemOptions>
```

尾部区域显示的自定义项数组，支持IconItemOptions（Image图标）、SymbolGlyphModifier（Symbol图标）或SymbolItemOptions（Symbol图标配置）类型。

**类型：** Array&lt;[IconItemOptions](arkts-arkui-arkui-advanced-chipgroup-iconitemoptions-i.md) &#124; [SymbolGlyphModifier](../../apis-default/arkts-apis/arkts-default-arkui-modifier.md) &#124; [SymbolItemOptions](arkts-arkui-arkui-advanced-chipgroup-symbolitemoptions-i.md)&gt;

**起始版本：** 12

**装饰器类型：** @Require、@Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-IconGroupSuffix-items: Array<IconItemOptions | SymbolGlyphModifier | SymbolItemOptions>--><!--Device-IconGroupSuffix-items: Array<IconItemOptions | SymbolGlyphModifier | SymbolItemOptions>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
