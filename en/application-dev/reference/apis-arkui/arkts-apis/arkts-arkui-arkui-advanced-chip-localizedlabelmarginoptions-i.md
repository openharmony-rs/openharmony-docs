# LocalizedLabelMarginOptions

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

Spacing between the text and the right icon. This parameter cannot be set in percentage.

Default value:

When **size** is set to **ChipSize.SMALL**, the default value of **end** is as follows:

`LengthMetrics.resource(&#36;r('sys.float.chip_small_text_margin'))`

When **size** is set to **ChipSize.NORMAL**, the default value of **end** is as follows:

`LengthMetrics.resource(&#36;r('sys.float.chip_normal_text_margin'))`

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

Spacing between the text and the left icon. This parameter cannot be set in percentage.

Default value:

When **size** is set to **ChipSize.SMALL**, the default value of **start** is as follows:

`LengthMetrics.resource(&#36;r('sys.float.chip_small_text_margin'))`

When **size** is set to **ChipSize.NORMAL**, the default value of **start** is as follows:

`LengthMetrics.resource(&#36;r('sys.float.chip_normal_text_margin'))`

If the value is **undefined**, the default value is used.

**Type:** LengthMetrics

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
