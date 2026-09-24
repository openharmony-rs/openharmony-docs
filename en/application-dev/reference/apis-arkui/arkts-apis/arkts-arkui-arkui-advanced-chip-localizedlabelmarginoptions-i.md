# LocalizedLabelMarginOptions

```TypeScript
export interface LocalizedLabelMarginOptions
```

Defines the spacing between the localized text and the left and right icons.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { Chip, ChipOptions, ChipSize, IconCommonOptions, LabelMarginOptions, LabelOptions, PrefixIconOptions, SuffixIconOptions, ChipSymbolGlyphOptions, AccessibilitySelectedType, AccessibilityOptions, CloseOptions, ChipSuffixSymbolGlyphOptions } from '@kit.ArkUI';
```

## end

```TypeScript
end?: LengthMetrics
```

Margin between the text and the end-side icon. Percentage values are not supported.

Default values:

When **size** is **ChipSize.SMALL**, the default value of **end** is:

`LengthMetrics.resource($r('sys.float.chip_small_text_margin'))`

When **size** is **ChipSize.NORMAL**, the default value of **end** is:

`LengthMetrics.resource($r('sys.float.chip_normal_text_margin'))`

If the value is **undefined**, the default value is used.

**Type:** LengthMetrics

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start?: LengthMetrics
```

Margin between the text and the start-side icon. Percentage values are not supported.

Default values:

When **size** is **ChipSize.SMALL**, the default value of **start** is:

`LengthMetrics.resource($r('sys.float.chip_small_text_margin'))`

When **size** is **ChipSize.NORMAL**, the default value of **start** is:

`LengthMetrics.resource($r('sys.float.chip_normal_text_margin'))`

If the value is **undefined**, the default value is used.

**Type:** LengthMetrics

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
