# ChipV2SuffixImageIconConfig

```TypeScript
export interface ChipV2SuffixImageIconConfig extends ChipV2ImageIconConfig, ChipV2AccessibilityConfig
```

Defines the attribute configuration of the suffix icon.

This API inherits from [ChipV2ImageIconConfig](arkts-arkui-arkui-advanced-chipv2-chipv2imageiconconfig-i.md) and [ChipV2AccessibilityConfig](arkts-arkui-arkui-advanced-chipv2-chipv2accessibilityconfig-i.md).

**Inheritance/Implementation:** ChipV2SuffixImageIconConfig extends [ChipV2ImageIconConfig](arkts-arkui-arkui-advanced-chipv2-chipv2imageiconconfig-i.md), [ChipV2AccessibilityConfig](arkts-arkui-arkui-advanced-chipv2-chipv2accessibilityconfig-i.md)

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ChipV2Size, ChipV2AccessibilitySelectedType, ChipV2ImageIconConfig, ChipV2ImageIcon, ChipV2SuffixImageIconConfig, ChipV2SuffixImageIcon, ChipV2Icon, ChipV2PrefixImageIconConfig, ChipV2PrefixImageIcon, ChipV2AccessibilityConfig, ChipV2Accessibility, ChipV2CloseConfig, ChipV2CloseIcon, ChipV2SymbolIconConfig, ChipV2SymbolIcon, ChipV2PrefixSymbolIconConfig, ChipV2PrefixSymbolIcon, ChipV2SuffixSymbolIconConfig, ChipV2SuffixSymbolIcon, ChipV2LabelMarginConfig, ChipV2LocalizedLabelMarginConfig, ChipV2LabelConfig, ChipV2Label, IChipV2OptionsConfig, ChipV2Options, ChipV2 } from '@kit.ArkUI';
```

## action

```TypeScript
action?: VoidCallback
```

Callback for the suffix icon tap event. Pass in this callback when you need to bind a tap event to the suffix icon and perform a custom operation (such as triggering a specific function or opening a dialog box). This callback is invoked when the suffix icon is tapped.

Default value: **undefined**, meaning no suffix icon event is set. When **undefined** or no value is passed, tapping the suffix icon triggers no custom response.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
