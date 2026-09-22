# ChipV2

```TypeScript
export declare struct ChipV2
```

The **ChipV2** component is a chip component that delivers rich styles and interaction capabilities. It provides features such as prefix icons, suffix icons, active states, and close buttons, supports the symbol and image icon types, and offers comprehensive accessibility capabilities. This component is suitable for scenarios such as search history, email recipient lists, tag selection, filters, and contact display.

This component is implemented based on [state management V2](../../../ui/state-management/arkts-state-management-overview.md#state-management-v2). Compared with [state management V1](../../../ui/state-management/arkts-state-management-overview.md#state-management-v1), state management V2 delivers enhanced capabilities for deep observation and management of data objects, and is no longer limited to the component level. With state management V2, you can control component data and state more flexibly, achieving more efficient UI refresh.

> **NOTE:** 
> 
> The APIs of this module can only be used in the stage model.

**Since:** 26.0.0

**Decorator:** @ComponentV2

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ChipV2Size, ChipV2AccessibilitySelectedType, ChipV2ImageIconConfig, ChipV2ImageIcon, ChipV2SuffixImageIconConfig, ChipV2SuffixImageIcon, ChipV2Icon, ChipV2PrefixImageIconConfig, ChipV2PrefixImageIcon, ChipV2AccessibilityConfig, ChipV2Accessibility, ChipV2CloseConfig, ChipV2CloseIcon, ChipV2SymbolIconConfig, ChipV2SymbolIcon, ChipV2PrefixSymbolIconConfig, ChipV2PrefixSymbolIcon, ChipV2SuffixSymbolIconConfig, ChipV2SuffixSymbolIcon, ChipV2LabelMarginConfig, ChipV2LocalizedLabelMarginConfig, ChipV2LabelConfig, ChipV2Label, IChipV2OptionsConfig, ChipV2Options, ChipV2 } from '@kit.ArkUI';
```

## build

```TypeScript
build(): void
```

Constructs the UI structure of the advanced **ChipV2** component.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## chipV2Options

```TypeScript
readonly chipV2Options: ChipV2Options
```

Parameters of the **ChipV2** component, which are used to customize the appearance and behavior of the **ChipV2** component, including configuration options such as **label**, **prefixIcon**, **suffixIcon**, **allowClose**, **activated**, **backgroundColor**, and **size**.

**Type:** [ChipV2Options](arkts-arkui-arkui-advanced-chipv2-chipv2options-c.md)

**Since:** 26.0.0

**Decorator:** @Require

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
