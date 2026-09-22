# CloseOptions

```TypeScript
export interface CloseOptions extends AccessibilityOptions
```

Defines the default close icon behavior attributes for the chip, including accessibility attributes. The default value of **accessibilityText** is **"Delete"**.

Inherits from [AccessibilityOptions](arkts-arkui-arkui-advanced-chip-accessibilityoptions-i.md).

**Inheritance/Implementation:** CloseOptions extends [AccessibilityOptions](arkts-arkui-arkui-advanced-chip-accessibilityoptions-i.md)

**Since:** 14

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { Chip, ChipOptions, ChipSize, IconCommonOptions, LabelMarginOptions, LabelOptions, PrefixIconOptions, SuffixIconOptions, ChipSymbolGlyphOptions, AccessibilitySelectedType, AccessibilityOptions, CloseOptions, ChipSuffixSymbolGlyphOptions } from '@kit.ArkUI';
```

## fontSize

```TypeScript
fontSize?: Dimension
```

Size of the default close icon of the **Chip** component. Percentage is not supported. If a percentage is passed, the default value is used.

Default value:

When **size** is **ChipSize.SMALL**, `$r('sys.float.chip_small_font_size')`

Other cases: `$r('sys.float.chip_normal_font_size')`

Unit: fp

If a negative number is passed, the default value is used. If the value is **undefined**, the default value is used.

**Type:** [Dimension](arkts-arkui-dimension-t.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
