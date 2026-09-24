# Chip

## Modules to Import

```TypeScript
import { Chip, ChipOptions, ChipSize, IconCommonOptions, LabelMarginOptions, LabelOptions, PrefixIconOptions, SuffixIconOptions, ChipSymbolGlyphOptions, AccessibilitySelectedType, AccessibilityOptions, CloseOptions, ChipSuffixSymbolGlyphOptions } from '@kit.ArkUI';
```

## Chip

```TypeScript
export declare function Chip(options: ChipOptions): void
```

Creates a **Chip** component.

**Since:** 11

**Decorator:** @Builder

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ChipOptions](arkts-arkui-arkui-advanced-chip-chipoptions-i.md) | Yes | Parameters of the **Chip** component, including size, enabled state, activated state, prefix/suffix icons, text content, background color, rounded corners, accessibility attributes, etc., used to customize the style and behavior of the **Chip** component. |
