# ChipV2CloseConfig

```TypeScript
export interface ChipV2CloseConfig extends ChipV2AccessibilityConfig
```

Defines the functional attribute configuration for the close icon of the **ChipV2** component, including accessibility attribute.

This API inherits from [ChipV2AccessibilityConfig](arkts-arkui-arkui-advanced-chipv2-chipv2accessibilityconfig-i.md).

**Inheritance/Implementation:** ChipV2CloseConfig extends [ChipV2AccessibilityConfig](arkts-arkui-arkui-advanced-chipv2-chipv2accessibilityconfig-i.md)

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ChipV2Size, ChipV2AccessibilitySelectedType, ChipV2ImageIconConfig, ChipV2ImageIcon, ChipV2SuffixImageIconConfig, ChipV2SuffixImageIcon, ChipV2Icon, ChipV2PrefixImageIconConfig, ChipV2PrefixImageIcon, ChipV2AccessibilityConfig, ChipV2Accessibility, ChipV2CloseConfig, ChipV2CloseIcon, ChipV2SymbolIconConfig, ChipV2SymbolIcon, ChipV2PrefixSymbolIconConfig, ChipV2PrefixSymbolIcon, ChipV2SuffixSymbolIconConfig, ChipV2SuffixSymbolIcon, ChipV2LabelMarginConfig, ChipV2LocalizedLabelMarginConfig, ChipV2LabelConfig, ChipV2Label, IChipV2OptionsConfig, ChipV2Options, ChipV2 } from '@kit.ArkUI';
```

## fontSize

```TypeScript
fontSize?: LengthMetrics
```

Size of the default close icon of the **ChipV2** component. Percentage values are not supported. If a percentage value is passed, the default value is used.

Default values:

When **size** is **ChipV2Size.SMALL**, the default value is `$r('sys.float.chip_small_font_size')`.

When **size** is not **ChipV2Size.SMALL**, the default value is `$r('sys.float.chip_normal_font_size')`.

Unit: fp

If the value is **undefined**, the default value is used.

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
