# ChipGroupV2IconGroupSuffix

```TypeScript
export declare struct ChipGroupV2IconGroupSuffix
```

Display custom content on the far right of the **ChipGroupV2** component. It supports configuring image icons, symbol icons, symbol icon configuration items, and icon background material styles. It is suitable for scenarios where an additional operation entry needs to be added at the end of a chip group.

**Since:** 26.0.0

**Decorator:** @ComponentV2

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ChipGroupV2ItemConfig, ChipGroupV2Item, ChipGroupV2Items, ChipGroupV2ItemStyleConfig, ChipGroupV2ItemStyle, ChipGroupV2SpaceConfig, ChipGroupV2Space, ChipGroupV2IconItemConfig, ChipGroupV2SymbolItemConfig, ChipGroupV2PaddingConfig, ChipGroupV2Padding, ChipGroupV2IconGroupSuffix, ChipGroupV2 } from '@kit.ArkUI';
```

## build

```TypeScript
build(): void
```

Constructs a **ChipGroupV2IconGroupSuffix** component.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## iconBackgroundSystemMaterial

```TypeScript
iconBackgroundSystemMaterial?: uiMaterial.Material
```

System material style of the component. Different materials have different effects, which can affect the component's [backgroundColor](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor), [borderColor](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#bordercolor), [borderWidth](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#borderwidth), [shadow](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#shadow) effect, and [materialFilter](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#materialfilter) effect.

Default value: **undefined**, meaning no material style is applied.

**Type:** [uiMaterial.Material](arkts-arkui-uimaterial-material-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## items

```TypeScript
items: Array<ChipGroupV2IconItemConfig | SymbolGlyphModifier | ChipGroupV2SymbolItemConfig>
```

Array of custom items displayed in the suffix area, supporting **ChipGroupV2IconItemConfig** (image icon), **SymbolGlyphModifier** (symbol icon), or **ChipGroupV2SymbolItemConfig** (symbol icon configuration) types.

When **SymbolGlyphModifier** is passed, using **symbolEffect** to modify the animation type and [effectStrategy](../arkts-components/arkts-arkui-symbolglyph-comp-attribute.md#effectstrategy) to set the animation is not supported.

**Type:** Array&lt;[ChipGroupV2IconItemConfig](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2iconitemconfig-i.md) &#124; [SymbolGlyphModifier](../../apis-default/arkts-apis/arkts-default-arkui-modifier.md) &#124; [ChipGroupV2SymbolItemConfig](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2symbolitemconfig-i.md)&gt;

**Since:** 26.0.0

**Decorator:** @Require

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
