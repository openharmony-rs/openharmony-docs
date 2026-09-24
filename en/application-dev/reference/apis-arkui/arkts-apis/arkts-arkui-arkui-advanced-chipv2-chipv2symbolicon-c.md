# ChipV2SymbolIcon

```TypeScript
export abstract class ChipV2SymbolIcon extends ChipV2Icon
```

Defines the symbol icon class.

This API inherits from [ChipV2Icon](arkts-arkui-arkui-advanced-chipv2-chipv2icon-c.md).

**Inheritance/Implementation:** ChipV2SymbolIcon extends [ChipV2Icon](arkts-arkui-arkui-advanced-chipv2-chipv2icon-c.md)

**Since:** 26.0.0

**Decorator:** @ObservedV2

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ChipV2Size, ChipV2AccessibilitySelectedType, ChipV2ImageIconConfig, ChipV2ImageIcon, ChipV2SuffixImageIconConfig, ChipV2SuffixImageIcon, ChipV2Icon, ChipV2PrefixImageIconConfig, ChipV2PrefixImageIcon, ChipV2AccessibilityConfig, ChipV2Accessibility, ChipV2CloseConfig, ChipV2CloseIcon, ChipV2SymbolIconConfig, ChipV2SymbolIcon, ChipV2PrefixSymbolIconConfig, ChipV2PrefixSymbolIcon, ChipV2SuffixSymbolIconConfig, ChipV2SuffixSymbolIcon, ChipV2LabelMarginConfig, ChipV2LocalizedLabelMarginConfig, ChipV2LabelConfig, ChipV2Label, IChipV2OptionsConfig, ChipV2Options, ChipV2 } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(config: ChipV2SymbolIconConfig)
```

A constructor used to create a **ChipV2SymbolIcon** object.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [ChipV2SymbolIconConfig](arkts-arkui-arkui-advanced-chipv2-chipv2symboliconconfig-i.md) | Yes | Attribute configuration of the symbol icon, which is used to set the display attributes of the symbol icon in different states, including configuration options such as **normal** and **activated**. |

## activated

```TypeScript
public activated?: SymbolGlyphModifier
```

Icon settings in the active state.

Default value: **undefined**, which means no prefix icon or suffix icon is displayed. When the value is **undefined**, the default value is used.

Modifying the animation type using [SymbolEffect](../arkts-components/arkts-arkui-symbolglyph-comp-attribute.md#symboleffect) and setting the animation effect using [effectStrategy](../arkts-components/arkts-arkui-symbolglyph-comp-attribute.md#effectstrategy) are not supported.

**Decorator:** @Trace

**Type:** [SymbolGlyphModifier](../../apis-default/arkts-apis/arkts-default-arkui-modifier.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## normal

```TypeScript
public normal?: SymbolGlyphModifier
```

Icon settings in the inactive state.

Default value: **undefined**, which means no prefix icon or suffix icon is displayed. When the value is **undefined**, the default value is used.

Modifying the animation type using [SymbolEffect](../arkts-components/arkts-arkui-symbolglyph-comp-attribute.md#symboleffect) and setting the animation effect using [effectStrategy](../arkts-components/arkts-arkui-symbolglyph-comp-attribute.md#effectstrategy) are not supported.

**Decorator:** @Trace

**Type:** [SymbolGlyphModifier](../../apis-default/arkts-apis/arkts-default-arkui-modifier.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
