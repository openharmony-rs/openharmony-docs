# ChipSymbolGlyphOptions

```TypeScript
export interface ChipSymbolGlyphOptions
```

Defines the prefix and suffix icon options.

> **NOTE:** 
> 
> The animation type cannot be modified via
> [SymbolEffect](../arkts-components/arkts-arkui-symbolglyph-comp-attribute.md#symboleffect) and
> animations cannot be set via **effectStrategy**.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { Chip, ChipOptions, ChipSize, IconCommonOptions, LabelMarginOptions, LabelOptions, PrefixIconOptions, SuffixIconOptions, ChipSymbolGlyphOptions, AccessibilitySelectedType, AccessibilityOptions, CloseOptions, ChipSuffixSymbolGlyphOptions } from '@kit.ArkUI';
```

## activated

```TypeScript
activated?: SymbolGlyphModifier
```

Symbol type icon displayed for the **Chip** in the activated state.

Default value: no prefix icon or suffix icon displayed

When the value is **undefined**, the default value is used.

**Type:** [SymbolGlyphModifier](../../apis-default/arkts-apis/arkts-default-arkui-modifier.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## normal

```TypeScript
normal?: SymbolGlyphModifier
```

Symbol type icon displayed for the **Chip** in the inactive state.

Default value: no prefix icon or suffix icon displayed

When the value is **undefined**, the default value is used.

**Type:** [SymbolGlyphModifier](../../apis-default/arkts-apis/arkts-default-arkui-modifier.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
