# ChipGroupItemOptions

```TypeScript
export interface ChipGroupItemOptions
```

Defines the specific attributes of individual chips.

> **NOTE:** 
> 
> When the **suffixSymbol** parameter is passed in, **allowClose** does not take effect. When the **suffixImageIcon**
> parameter is passed in but **suffixSymbol** is not, **allowClose** does not take effect. When neither
> **suffixSymbol** nor **suffixImageIcon** is passed in, **allowClose** determines whether the close icon is
> displayed. **suffixIcon** is deprecated. Use **suffixImageIcon** instead.
> 
> **suffixSymbol** and **suffixImageIcon** are both suffix icons, and only one of them can be configured for the same
> chip item. If both are configured, only the one with the higher priority takes effect (priority: **suffixSymbol**
> 
> **suffixImageIcon**). **suffixIcon** is deprecated. Use **suffixImageIcon** instead.

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

Accessibility description of the chip in the **ChipGroup**. This description is used to explain the chip in the **ChipGroup** to users in detail. Developers should provide a relatively detailed text description for this attribute of the chip to help users understand the operation to be performed and its possible results, especially when these results cannot be directly learned from the chip's attributes and accessibility text alone. If the chip has both a label text attribute and an accessibility description attribute, when it is selected, the system first announces the chip's label text attribute, and then announces the content of the accessibility description attribute.

Default value: empty string.

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

Accessibility level of the chip in the **ChipGroup**. Controls whether the chip in the **ChipGroup** can be recognized by accessibility services.

The supported values are:

**"auto"**: The chip in the **ChipGroup** is converted to **"yes"** when **action** is set, and to **"no"** otherwise. This applies to most scenarios.

**"yes"**: The chip in the **ChipGroup** can be recognized by accessibility services, which applies to scenarios where accessibility needs to be explicitly enabled.

**"no"**: The chip in the **ChipGroup** cannot be recognized by accessibility services, which applies to purely decorative icon scenarios.

**"no-hide-descendants"**: The chip in the **ChipGroup** and all its child components cannot be recognized by accessibility services, which applies to scenarios where the entire area needs to be hidden.

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

Whether to display the close icon.

The value **false** means the close icon is not displayed, and **true** means the close icon is displayed.

Set this parameter to **true** when users need to be allowed to delete or remove a chip, which applies to scenarios such as edit mode and configurable tag lists.

Default value: **false**

If the value is **undefined**, the default value is used.

**Note:** When a value is passed to **suffixSymbol**, **allowClose** does not take effect. When no value is passed to **suffixSymbol** but a value is passed to **suffixIcon** or **suffixImageIcon**, **allowClose** does not take effect. When no value is passed to **suffixSymbol**, **suffixIcon**, or **suffixImageIcon**, **allowClose** determines whether to display the close icon.

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## closeOptions

```TypeScript
closeOptions?: CloseOptions
```

Accessibility reading and font size properties of the default close icon. Set this parameter when custom accessibility reading content and font size need to be provided for the close icon.

Default value: the default configuration in [CloseOptions](arkts-arkui-arkui-advanced-chip-closeoptions-i.md) is used.

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

Text content and style displayed on the chip.

**Type:** [LabelOptions](arkts-arkui-arkui-advanced-chipgroup-labeloptions-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## prefixIcon

```TypeScript
prefixIcon?: IconOptions
```

Prefix image icon property. Set this parameter when an icon needs to be displayed before the chip to enhance visual recognition or provide a functional hint.

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

Prefix SymbolGlyph icon property. Set this parameter when a SymbolGlyph icon needs to be displayed before the chip to enhance visual recognition or provide a functional hint.

Default value: no prefix SymbolGlyph icon.

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

Suffix image icon property. Set this parameter when an image icon needs to be displayed after the chip to provide an additional action or status hint.

Default value: no suffix image icon displayed.

If the value is **undefined**, the default value is used.

**Note:** When a value is passed to **suffixIcon**, **allowClose** does not take effect.

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

Suffix image icon property. Set this parameter when an icon needs to be displayed after the chip to provide an additional action or status hint.

**Note:** When a value is passed to **suffixImageIcon**, **allowClose** does not take effect. When both **suffixSymbol** and **suffixImageIcon** are configured, only **suffixSymbol** takes effect and **suffixImageIcon** does not.

Default value: no suffix image icon displayed.

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

Suffix SymbolGlyph icon property. Set this parameter when a SymbolGlyph icon needs to be displayed after the chip to provide an additional action or status hint.

**Note:** When a value is passed to **suffixSymbol**, **allowClose** does not take effect. **suffixSymbol** and **suffixImageIcon** are mutually exclusive. Only one of them can be configured for the same chip. If both are configured, only the one with the higher priority takes effect (priority: **suffixSymbol**
> **suffixImageIcon**).

Default value: no suffix SymbolGlyph icon displayed.

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

Suffix symbol icon property, which configures the interaction function and accessibility attributes of the suffix symbol icon. Set this parameter when a click event or accessibility support needs to be added to the suffix symbol icon.

Default value: the default value of [ChipSuffixSymbolGlyphOptions](arkts-arkui-arkui-advanced-chip-chipsuffixsymbolglyphoptions-i.md) is used.

If the value is **undefined**, the default value is used.

**Type:** [ChipSuffixSymbolGlyphOptions](arkts-arkui-arkui-advanced-chip-chipsuffixsymbolglyphoptions-i.md)

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
