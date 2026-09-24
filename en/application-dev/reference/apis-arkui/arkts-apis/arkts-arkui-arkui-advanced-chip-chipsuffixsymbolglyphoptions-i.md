# ChipSuffixSymbolGlyphOptions

```TypeScript
export interface ChipSuffixSymbolGlyphOptions
```

Defines the accessibility reading functional attributes and tap event callback of the symbol-type suffix icon.

**Since:** 14

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { Chip, ChipOptions, ChipSize, IconCommonOptions, LabelMarginOptions, LabelOptions, PrefixIconOptions, SuffixIconOptions, ChipSymbolGlyphOptions, AccessibilitySelectedType, AccessibilityOptions, CloseOptions, ChipSuffixSymbolGlyphOptions } from '@kit.ArkUI';
```

## action

```TypeScript
action?: VoidCallback
```

Callback for the suffix icon tap event, with no parameters and no return value. This callback is triggered when the user taps the suffix icon.

When the value is **undefined**, no suffix icon event is set.

Default value: **undefined**

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## activatedAccessibility

```TypeScript
activatedAccessibility?: AccessibilityOptions
```

Accessibility settings for the activated state.

Default value: **undefined**

**Type:** [AccessibilityOptions](arkts-arkui-arkui-advanced-chip-accessibilityoptions-i.md)

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## normalAccessibility

```TypeScript
normalAccessibility?: AccessibilityOptions
```

Accessibility settings for the normal state.

Default value: **undefined**

**Type:** [AccessibilityOptions](arkts-arkui-arkui-advanced-chip-accessibilityoptions-i.md)

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
