# LabelOptions

```TypeScript
export interface LabelOptions
```

Defines text configuration options.

> **NOTE:** 
> 
> Starting from API version 26.0.0, when **backgroundSystemMaterial** is set to an auto-invert system material,
> **fontColor** uses a special system resource that supports color inversion, and the text color automatically adapts
> to the inverted color of the material background. When **activatedBackgroundSystemMaterial** is set to an auto-
> invert system material, **activatedFontColor** uses a special system resource that supports color inversion, and
> the text color of the chip in the activated state automatically adapts to the inverted color of the material
> background.

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

Text color when the **Chip** is activated.

Default value: $r('sys.color.ohos_id_color_text_primary_contrary')

When the value is **undefined**, the default value is used.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor?: ResourceColor
```

Text color.

Default value: **$r('sys.color.ohos_id_color_text_primary')**

When the value is **undefined**, the default value is used.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontFamily

```TypeScript
fontFamily?: string
```

Font style of the **Chip** component text.

Default value: **"HarmonyOS Sans"**

When the value is **undefined**, the default value is used.

**Type:** string

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: Dimension
```

Font size. Percentage is not supported. If a percentage is passed, the default value is used.

If a negative value is passed, the default value is used.

Default value: **$r('sys.float.ohos_id_text_size_button2')**

Unit: fp

When the value is **undefined**, the default value is used.

**Type:** [Dimension](arkts-arkui-dimension-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## labelMargin

```TypeScript
labelMargin?: LabelMarginOptions
```

Spacing between the text and the left/right icons.

Default values:

When **size** is **ChipSize.SMALL**, the default value is **{ left: 4, right: 4 }**.

When **size** is **ChipSize.NORMAL**, the default value is **{ left: 6, right: 6 }**

Unit: vp

When the value is **undefined**, the default value is used.

**Type:** [LabelMarginOptions](arkts-arkui-arkui-advanced-chip-labelmarginoptions-i.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## localizedLabelMargin

```TypeScript
localizedLabelMargin?: LocalizedLabelMarginOptions
```

Spacing between the localized text and the left/right icons.

Default values:

When **size** is **ChipSize.SMALL**:

`{ start: LengthMetrics.resource($r('sys.float.chip_small_text_margin')), end: LengthMetrics.resource($r('sys.float.chip_small_text_margin')) }`

When **size** is **ChipSize.NORMAL**:

`{ start: LengthMetrics.resource($r('sys.float.chip_normal_text_margin')), end: LengthMetrics.resource($r('sys.float.chip_normal_text_margin')) }`

When the value is **undefined**, the default value is used.

**Type:** [LocalizedLabelMarginOptions](arkts-arkui-arkui-advanced-chip-localizedlabelmarginoptions-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text: string
```

Text content displayed by the **Chip** component.

**Type:** string

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
