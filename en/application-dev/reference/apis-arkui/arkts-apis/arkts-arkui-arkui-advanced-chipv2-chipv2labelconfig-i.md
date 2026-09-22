# ChipV2LabelConfig

```TypeScript
export interface ChipV2LabelConfig
```

Defines the text attribute configuration.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ChipV2Size, ChipV2AccessibilitySelectedType, ChipV2ImageIconConfig, ChipV2ImageIcon, ChipV2SuffixImageIconConfig, ChipV2SuffixImageIcon, ChipV2Icon, ChipV2PrefixImageIconConfig, ChipV2PrefixImageIcon, ChipV2AccessibilityConfig, ChipV2Accessibility, ChipV2CloseConfig, ChipV2CloseIcon, ChipV2SymbolIconConfig, ChipV2SymbolIcon, ChipV2PrefixSymbolIconConfig, ChipV2PrefixSymbolIcon, ChipV2SuffixSymbolIconConfig, ChipV2SuffixSymbolIcon, ChipV2LabelMarginConfig, ChipV2LocalizedLabelMarginConfig, ChipV2LabelConfig, ChipV2Label, IChipV2OptionsConfig, ChipV2Options, ChipV2 } from '@kit.ArkUI';
```

## activatedFontColor

```TypeScript
activatedFontColor?: ColorMetrics
```

Font color when **ChipV2** is activated.

Default value: **$r('sys.color.chip_activated_fontcolor')**

When the value is **undefined**, the default value is used.

When the value is invalid, the default value is used.

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor?: ColorMetrics
```

Font color.

Default value: **$r('sys.color.chip_font_color')**

When the value is **undefined**, the default value is used.

When the value is invalid, the default value is used.

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontFamily

```TypeScript
fontFamily?: string
```

Font family.

Default value: **"HarmonyOS Sans"**

When the value is **undefined**, the default value is used.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: LengthMetrics
```

Font size. Percentage values are not supported. When a percentage value is passed, the default value is used.

Default values:

When **size** is **ChipV2Size.SMALL**, the default value is **$r('sys.float.chip_small_font_size')**.

In other cases, the default value is **$r('sys.float.chip_normal_font_size')**

Unit: fp

When the value is **undefined**, the default value is used.

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## labelMargin

```TypeScript
labelMargin?: ChipV2LabelMarginConfig
```

Spacing between the text and the left/right icons.

Default values:

When **size** is **ChipV2Size.SMALL**, the default value is **{ left: 4, right: 4 }**.

When **size** is **ChipV2Size.NORMAL**, the default value is **{ left: 6, right: 6 }**.

When the value is **undefined**, the default value is used.

**Type:** [ChipV2LabelMarginConfig](arkts-arkui-arkui-advanced-chipv2-chipv2labelmarginconfig-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## localizedLabelMargin

```TypeScript
localizedLabelMargin?: ChipV2LocalizedLabelMarginConfig
```

Spacing between the localized text and the left/right icons.

Default values:

When **size** is **ChipV2Size.SMALL**, default value:

`{ start: LengthMetrics.resource($r('sys.float.chip_small_text_margin')), end: LengthMetrics.resource($r('sys.float.chip_small_text_margin')) }`.

When **size** is **ChipV2Size.NORMAL**, default value:

`{ start: LengthMetrics.resource($r('sys.float.chip_normal_text_margin')), end: LengthMetrics.resource($r('sys.float.chip_normal_text_margin')) }`.

When the value is **undefined**, the default value is used.

**Type:** [ChipV2LocalizedLabelMarginConfig](arkts-arkui-arkui-advanced-chipv2-chipv2localizedlabelmarginconfig-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## modifier

```TypeScript
modifier?: TextModifier
```

Text modifier, which is used to set common text attributes. Pass this parameter when you need to dynamically modify text attributes (such as **fontWeight** and **fontStyle**) through the modifier. When no value or **undefined** is passed in, the modifier is not applied and the text uses default attribute settings.

Default value: **undefined**, meaning that the modifier is not applied.

**Type:** [TextModifier](../../apis-default/arkts-apis/arkts-default-arkui-modifier.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text: string
```

Text content.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
