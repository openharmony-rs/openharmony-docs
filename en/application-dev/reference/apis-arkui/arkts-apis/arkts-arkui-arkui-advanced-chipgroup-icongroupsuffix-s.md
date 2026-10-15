# IconGroupSuffix

```TypeScript
export declare struct IconGroupSuffix
```

Defines the suffix area icon of a ChipGroup. It is used in the configurable suffix property, which displays custom content at the far right of the ChipGroup component.

**Since:** 12

**Decorator:** @Component

<!--Device-unnamed-export declare struct IconGroupSuffix--><!--Device-unnamed-export declare struct IconGroupSuffix-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { IconOptions, LabelOptions as ChipItemLabelOptions, ChipGroupItemOptions, ChipItemStyle, ChipGroupSpaceOptions, IconItemOptions, IconGroupSuffix, ChipGroup, SuffixImageIconOptions, SymbolItemOptions } from '@kit.ArkUI';
```

## iconBackgroundSystemMaterial

```TypeScript
iconBackgroundSystemMaterial?: uiMaterial.Material
```

System material style of the component. Different materials have different effects and can affect the [backgroundColor](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor1), [border](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#border), and [shadow](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#shadow1) visual properties of the component. When a system material with auto-invert is set, if **fontColor** uses a system-predefined invertible color resource (such as `$r('sys.color.font_primary')`), the color automatically adapts to the inverted color of the material background color.

Default value: **undefined**

When the **value** is **undefined**, no material style is applied.

**Type:** [uiMaterial.Material](arkts-arkui-uimaterial-material-c.md)

**Since:** 26.0.0

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-IconGroupSuffix-iconBackgroundSystemMaterial?: uiMaterial.Material--><!--Device-IconGroupSuffix-iconBackgroundSystemMaterial?: uiMaterial.Material-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## items

```TypeScript
items: Array<IconItemOptions | SymbolGlyphModifier | SymbolItemOptions>
```

Array of custom items displayed in the trailing area. The array supports **IconItemOptions** (image icon), **SymbolGlyphModifier** (symbol icon), or **SymbolItemOptions** (symbol icon configuration) types.

**Type:** Array&lt;[IconItemOptions](arkts-arkui-arkui-advanced-chipgroup-iconitemoptions-i.md) &#124; [SymbolGlyphModifier](../../apis-default/arkts-apis/arkts-default-arkui-modifier.md) &#124; [SymbolItemOptions](arkts-arkui-arkui-advanced-chipgroup-symbolitemoptions-i.md)&gt;

**Since:** 12

**Decorator:** @Require, @Prop

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-IconGroupSuffix-items: Array<IconItemOptions | SymbolGlyphModifier | SymbolItemOptions>--><!--Device-IconGroupSuffix-items: Array<IconItemOptions | SymbolGlyphModifier | SymbolItemOptions>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
