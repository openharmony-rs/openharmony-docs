# LabelOptions

Defines text configuration options.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { Chip, ChipOptions, ChipSize, IconCommonOptions, LabelMarginOptions, LabelOptions, PrefixIconOptions, SuffixIconOptions, ChipSymbolGlyphOptions, AccessibilitySelectedType, AccessibilityOptions, CloseOptions, ChipSuffixSymbolGlyphOptions } from '@kit.ArkUI';
```

## activatedFontColor

```TypeScript
activatedFontColor?: ResourceColor
```

Font color when the chip is activated.

Default value: **&#36;r('sys.color.ohos_id_color_text_primary_contrary')**

If the value is **undefined**, the default value is used.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor?: ResourceColor
```

Font color.

Default value: **&#36;r('sys.color.ohos_id_color_text_primary')**

If the value is **undefined**, the default value is used.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontFamily

```TypeScript
fontFamily?: string
```

Font family.

Default value: **"HarmonyOS Sans"**

If the value is **undefined**, the default value is used.

**Type:** string

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: Dimension
```

Font size. This parameter cannot be set in percentage.

Default value: **&#36;r('sys.float.ohos_id_text_size_button2')**

If the value is **undefined**, the default value is used.

**Type:** [Dimension](arkts-arkui-dimension-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## labelMargin

```TypeScript
labelMargin?: LabelMarginOptions
```

Spacing between the text and the left and right icons.

Default value:

When **size** is **ChipSize.SMALL**: **{ left: 4, right: 4 }**.

When **size** is **ChipSize.NORMAL**: **{ left: 6, right: 6 }**.

Unit: vp.

If the value is **undefined**, the default value is used.

**Type:** [LabelMarginOptions](arkts-arkui-arkui-advanced-chip-labelmarginoptions-i.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## localizedLabelMargin

```TypeScript
localizedLabelMargin?: LocalizedLabelMarginOptions
```

Spacing between the localized text and the left and right icons.

Default value:

When **size** is set to **ChipSize.SMALL**, the default value is as follows:

`{ start: LengthMetrics.resource(&#36;r('sys.float.chip_small_text_margin')), end: LengthMetrics.resource(&#36;r('sys.float.chip_small_text_margin')) }`

When **size** is set to **ChipSize.NORMAL**, the default value is as follows:

`{ start: LengthMetrics.resource(&#36;r('sys.float.chip_normal_text_margin')), end: LengthMetrics.resource(&#36;r('sys.float.chip_normal_text_margin')) }`

If the value is **undefined**, the default value is used.

**Type:** [LocalizedLabelMarginOptions](arkts-arkui-arkui-advanced-chip-localizedlabelmarginoptions-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text: string
```

Text content.

**Type:** string

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
