# @ohos.arkui.advanced.Chip

## Modules to Import

```TypeScript
import { Chip, ChipOptions, ChipSize, IconCommonOptions, LabelMarginOptions, LabelOptions, PrefixIconOptions, SuffixIconOptions, ChipSymbolGlyphOptions, AccessibilitySelectedType, AccessibilityOptions, CloseOptions, ChipSuffixSymbolGlyphOptions } from '@kit.ArkUI';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [Chip](arkts-arkui-arkui-advanced-chip-chip-f.md) | Build function of Chip. |

### Interfaces

| Name | Description |
| --- | --- |
| [AccessibilityOptions](arkts-arkui-arkui-advanced-chip-accessibilityoptions-i.md) | Defines the accessibility options of the suffix icon. |
| [ChipOptions](arkts-arkui-arkui-advanced-chip-chipoptions-i.md) | Defines the type and style parameters of the chip. |
| [ChipSuffixSymbolGlyphOptions](arkts-arkui-arkui-advanced-chip-chipsuffixsymbolglyphoptions-i.md) | Defines the accessibility options of the symbol-type suffix icon. |
| [ChipSymbolGlyphOptions](arkts-arkui-arkui-advanced-chip-chipsymbolglyphoptions-i.md) | Defines the prefix and suffix icon options. |
| [CloseOptions](arkts-arkui-arkui-advanced-chip-closeoptions-i.md) | Defines the default close icon behavior attributes for the chip, including accessibility attributes. The default value of **accessibilityText** is **"Delete"**. |
| [IconCommonOptions](arkts-arkui-arkui-advanced-chip-iconcommonoptions-i.md) | Defines the common icon options of the chip. |
| [LabelMarginOptions](arkts-arkui-arkui-advanced-chip-labelmarginoptions-i.md) | Defines the spacing between the text and the left and right icons. |
| [LabelOptions](arkts-arkui-arkui-advanced-chip-labeloptions-i.md) | Defines text configuration options. |
| [LocalizedLabelMarginOptions](arkts-arkui-arkui-advanced-chip-localizedlabelmarginoptions-i.md) | Defines the spacing between the localized text and the left and right icons. |
| [PrefixIconOptions](arkts-arkui-arkui-advanced-chip-prefixiconoptions-i.md) | Defines the prefix icon options. |
| [SuffixIconOptions](arkts-arkui-arkui-advanced-chip-suffixiconoptions-i.md) | Defines the suffix icon options. |

### Enums

| Name | Description |
| --- | --- |
| [AccessibilitySelectedType](arkts-arkui-arkui-advanced-chip-accessibilityselectedtype-e.md) | Enumerates the selected state types of the chip. It allows you to specify how accessibility services convey the component's selected state to users. Different selected state types provide distinct semantics and user experiences. |
| [ChipSize](arkts-arkui-arkui-advanced-chip-chipsize-e.md) | Enumerates the chip size types. |

## Examples

```TypeScript
### Example 1: Setting a Custom Suffix Icon

This example sets a custom suffix icon by configuring suffixIcon.


```

```TypeScript
### Example 2: Using the Default Suffix Icon

Set allowClose to true to display the close icon.


```

```TypeScript
### Example 3: Displaying No Suffix Icon

Set allowClose to false to hide the close icon.


```

```TypeScript
### Example 4: Implementing the Activated State

This example shows how to implement the activated state for a chip by configuring activated.


```

```TypeScript
### Example 5: Setting the Symbol Icon

This example demonstrates how to set the symbol-type prefix icon of the chip.


```

```TypeScript
### Example 6: Implementing a Mirrored Layout

This example shows how to implement a chip mirrored layout by configuring direction.


```

```TypeScript
### Example 7: Implementing Accessibility for an Image-Type Suffix Icon

This example demonstrates how to implement the accessibility feature for a chip with an image-type suffix icon. Clicking the suffix icon triggers the announcement of "icon, button, usage hints."
```

```TypeScript
### Example 8: Implementing Accessibility for a Symbol-Type Suffix Icon

This example demonstrates how to implement the accessibility feature for a chip with a symbol-type suffix icon. Clicking the suffix icon triggers the announcement of "music, button, usage hints."
```

```TypeScript
### Example 9: Implementing Chip Accessibility

This example shows the accessibility property settings of the Chip component, including different accessibilitySelectedType types and various accessibility properties.
```

```TypeScript
### Example 10: Setting the System Material Style

This example implements the system material style by configuring backgroundSystemMaterial and activatedBackgroundSystemMaterial, and enables the auto-invert feature to adapt the label text color.

Starting from API version 26.0.0, the backgroundSystemMaterial and activatedBackgroundSystemMaterial attributes are added to [ChipOptions](arkts-arkui-arkui-advanced-chip-chipoptions-i.md).
```
