# ChipV2SuffixSymbolIcon

```TypeScript
export declare class ChipV2SuffixSymbolIcon extends ChipV2SymbolIcon
```

Defines the suffix symbol icon class.

This API inherits from [ChipV2SymbolIcon](arkts-arkui-arkui-advanced-chipv2-chipv2symbolicon-c.md).

**Inheritance/Implementation:** ChipV2SuffixSymbolIcon extends [ChipV2SymbolIcon](arkts-arkui-arkui-advanced-chipv2-chipv2symbolicon-c.md)

**Since:** 26.0.0

**Decorator:** @ObservedV2

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ChipV2Size, ChipV2AccessibilitySelectedType, ChipV2ImageIconConfig, ChipV2ImageIcon, ChipV2SuffixImageIconConfig, ChipV2SuffixImageIcon, ChipV2Icon, ChipV2PrefixImageIconConfig, ChipV2PrefixImageIcon, ChipV2AccessibilityConfig, ChipV2Accessibility, ChipV2CloseConfig, ChipV2CloseIcon, ChipV2SymbolIconConfig, ChipV2SymbolIcon, ChipV2PrefixSymbolIconConfig, ChipV2PrefixSymbolIcon, ChipV2SuffixSymbolIconConfig, ChipV2SuffixSymbolIcon, ChipV2LabelMarginConfig, ChipV2LocalizedLabelMarginConfig, ChipV2LabelConfig, ChipV2Label, IChipV2OptionsConfig, ChipV2Options, ChipV2 } from '@kit.ArkUI';
```

## action

```TypeScript
public action?: VoidCallback
```

Callback for the suffix icon tap event, which is triggered when the suffix icon is tapped.

Default value: no suffix icon event is set.

When the value is **undefined**, the default value is used.

**Decorator:** @Trace

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(config: ChipV2SuffixSymbolIconConfig)
```

A constructor used to create a **ChipV2SuffixSymbolIcon** object.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [ChipV2SuffixSymbolIconConfig](arkts-arkui-arkui-advanced-chipv2-chipv2suffixsymboliconconfig-i.md) | Yes | Attribute configuration of the suffix symbol icon, which is used to set the display attributes and accessibility features of the suffix symbol icon. This parameter inherits from **ChipV2SymbolIconConfig** and includes configuration options such as **normal**, **activated**, **normalAccessibility**, **activatedAccessibility**, and **action**. |

## activatedAccessibility

```TypeScript
public activatedAccessibility?: ChipV2Accessibility
```

Accessibility attribute in the active state.

Default value: **undefined**, meaning no content is read aloud.

**Decorator:** @Trace

**Type:** [ChipV2Accessibility](arkts-arkui-arkui-advanced-chipv2-chipv2accessibility-c.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## normalAccessibility

```TypeScript
public normalAccessibility?: ChipV2Accessibility
```

Accessibility attribute in the inactive state.

Default value: **undefined**, meaning no content is read aloud.

**Decorator:** @Trace

**Type:** [ChipV2Accessibility](arkts-arkui-arkui-advanced-chipv2-chipv2accessibility-c.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
