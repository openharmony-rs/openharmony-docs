# ChipGroupItemOptions

Defines the specific attributes of individual chips.

> **NOTE:** 
> 
> If **suffixIcon** is specified, **allowClose** has no effect.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { IconOptions, LabelOptions as ChipItemLabelOptions, ChipGroupItemOptions, ChipItemStyle, ChipGroupSpaceOptions, IconItemOptions, IconGroupSuffix, ChipGroup, SuffixImageIconOptions, SymbolItemOptions } from '@kit.ArkUI';
```

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

Accessible description of the chip. You can provide comprehensive text explanations of the chip in **ChipGroup** to help users understand the action they are about to perform and its potential consequences. This is particularly important when such outcomes cannot be directly inferred from the chip's own properties or its accessibility text. If a chip contains both text information and the accessible description, the text is announced first and then the accessible description, when the chip is selected.

The default value is an empty string.

If the value is **undefined**, the default value is used.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

Accessibility level of the chip. It determines whether the chip can be recognized by accessibility services.

The options are as follows:

**"auto"**: It is treated as "yes" by the system.

**"yes"**: The chip can be recognized by accessibility services.

**"no"**: The chip cannot be recognized by accessibility services.

**"no-hide-descendants"**: Neither the chip nor its child components can be recognized by accessibility services.

Default value: **"auto"**

If the value is **undefined**, the default value is used.

**Type:** string

**Default:** "auto"

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## allowClose

```TypeScript
allowClose?: boolean
```

Whether to show the delete icon.

**true** to show, **false** to hide.

Default value: **false**

If the value is **undefined**, the default value is used.

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## closeOptions

```TypeScript
closeOptions?: CloseOptions
```

Accessibility options of the default close icon.

If the value is **undefined**, the default value is used.

**Type:** [CloseOptions](arkts-arkui-arkui-advanced-chip-closeoptions-i.md)

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## label

```TypeScript
label: LabelOptions
```

Text of the chip.

**Type:** [LabelOptions](arkts-arkui-arkui-advanced-chipgroup-labeloptions-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## prefixIcon

```TypeScript
prefixIcon?: IconOptions
```

Prefix image icon of the chip.

Default value: no prefix image icon.

If the value is **undefined**, the default value is used.

**Type:** [IconOptions](arkts-arkui-arkui-advanced-chipgroup-iconoptions-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## prefixSymbol

```TypeScript
prefixSymbol?: ChipSymbolGlyphOptions
```

Prefix symbol glyph icon of the chip.

Default value: no prefix symbol glyph icon.

If the value is **undefined**, the default value is used.

**Type:** [ChipSymbolGlyphOptions](arkts-arkui-arkui-advanced-chip-chipsymbolglyphoptions-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## suffixIcon

```TypeScript
suffixIcon?: IconOptions
```

Suffix image icon of the chip.

Default value: no suffix image icon.

If the value is **undefined**, the default value is used.

Note: This API is supported since API version 12 and deprecated since API version 14. You are advised to use **suffixImageIcon** instead.

**Type:** [IconOptions](arkts-arkui-arkui-advanced-chipgroup-iconoptions-i.md)

**Since:** 12

**Deprecated since:** 14

**Substitutes:** [suffixImageIcon](#suffiximageicon)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## suffixImageIcon

```TypeScript
suffixImageIcon?: SuffixImageIconOptions
```

Suffix image icon of the chip.

Default value: no suffix image icon.

If the value is **undefined**, the default value is used.

**Type:** [SuffixImageIconOptions](arkts-arkui-arkui-advanced-chipgroup-suffiximageiconoptions-i.md)

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## suffixSymbol

```TypeScript
suffixSymbol?: ChipSymbolGlyphOptions
```

Suffix symbol glyph icon of the chip.

Default value: no suffix symbol glyph icon.

If the value is **undefined**, the default value is used.

**Type:** [ChipSymbolGlyphOptions](arkts-arkui-arkui-advanced-chip-chipsymbolglyphoptions-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## suffixSymbolOptions

```TypeScript
suffixSymbolOptions?: ChipSuffixSymbolGlyphOptions
```

Suffix symbol icon of the chip.

Default value: The suffix symbol icon has no function.

If the value is **undefined**, the default value is used.

**Type:** [ChipSuffixSymbolGlyphOptions](arkts-arkui-arkui-advanced-chip-chipsuffixsymbolglyphoptions-i.md)

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
