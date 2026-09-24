# IconCommonOptions

```TypeScript
export interface IconCommonOptions
```

Defines the common icon options of the chip.

> **NOTE:** 
> 
> **fillColor** and **activatedFillColor** take effect only when the icon format is SVG.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { Chip, ChipOptions, ChipSize, IconCommonOptions, LabelMarginOptions, LabelOptions, PrefixIconOptions, SuffixIconOptions, ChipSymbolGlyphOptions, AccessibilitySelectedType, AccessibilityOptions, CloseOptions, ChipSuffixSymbolGlyphOptions } from '@kit.ArkUI';
```

## activatedFillColor

```TypeScript
activatedFillColor?: ResourceColor
```

Icon fill color when the **Chip** is activated. This attribute takes effect only when the image format is SVG.

Default value: **$r('sys.color.chip_active_icon_color')**

If the value is **undefined**, the default value is used.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fillColor

```TypeScript
fillColor?: ResourceColor
```

Icon fill color. This attribute takes effect only when the image format is SVG.

Default value: **$r('sys.color.chip_usually_icon_color')**

If the value is **undefined**, the default value is used.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: SizeOptions
```

Icon size. Percentage is not supported. Abnormal values are handled as the default value.

Default value:

- When **ChipOptions.size** is **ChipSize.SMALL**, the default value is  
**{width: $r('sys.float.chip_small_icon_size'), height: $r('sys.float.chip_small_icon_size')}**  
- When **ChipOptions.size** is **ChipSize.NORMAL**, the default value is  
**{width: $r('sys.float.chip_normal_icon_size'), height: $r('sys.float.chip_normal_icon_size')}**

Unit: vp

If the value is **undefined**, the default value is used.

**Type:** [SizeOptions](arkts-arkui-sizeoptions-i.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## src

```TypeScript
src: ResourceStr
```

Icon source, which can be a specific image path or an image reference.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
