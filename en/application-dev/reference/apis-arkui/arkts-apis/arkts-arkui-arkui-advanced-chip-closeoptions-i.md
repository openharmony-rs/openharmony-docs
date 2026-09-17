# CloseOptions

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

Default close icon size of the chip. Percentage is not supported.

Default value:

When **size** is **ChipSize.SMALL**:**&#36;r('sys.float.chip_small_font_size')**.

Other cases: **&#36;r('sys.float.chip_normal_font_size')**.

If the value is **undefined**, the default value is used.

**Type:** [Dimension](arkts-arkui-dimension-t.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
