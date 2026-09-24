# ChipV2ImageIcon

```TypeScript
export abstract class ChipV2ImageIcon extends ChipV2Icon
```

Defines the base class of icon images.

This API inherits from [ChipV2Icon](arkts-arkui-arkui-advanced-chipv2-chipv2icon-c.md).

**Inheritance/Implementation:** ChipV2ImageIcon extends [ChipV2Icon](arkts-arkui-arkui-advanced-chipv2-chipv2icon-c.md)

**Since:** 26.0.0

**Decorator:** @ObservedV2

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ChipV2Size, ChipV2AccessibilitySelectedType, ChipV2ImageIconConfig, ChipV2ImageIcon, ChipV2SuffixImageIconConfig, ChipV2SuffixImageIcon, ChipV2Icon, ChipV2PrefixImageIconConfig, ChipV2PrefixImageIcon, ChipV2AccessibilityConfig, ChipV2Accessibility, ChipV2CloseConfig, ChipV2CloseIcon, ChipV2SymbolIconConfig, ChipV2SymbolIcon, ChipV2PrefixSymbolIconConfig, ChipV2PrefixSymbolIcon, ChipV2SuffixSymbolIconConfig, ChipV2SuffixSymbolIcon, ChipV2LabelMarginConfig, ChipV2LocalizedLabelMarginConfig, ChipV2LabelConfig, ChipV2Label, IChipV2OptionsConfig, ChipV2Options, ChipV2 } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(config: ChipV2ImageIconConfig)
```

A constructor used to create a **ChipV2ImageIcon** object.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [ChipV2ImageIconConfig](arkts-arkui-arkui-advanced-chipv2-chipv2imageiconconfig-i.md) | Yes | Common icon attribute configuration, which is used to set the basic display attributes of the image icon, including configuration options such as **src**, **size**, **fillColor**, **activatedFillColor**. |

## activatedFillColor

```TypeScript
public activatedFillColor?: ColorMetrics
```

Icon fill color when **ChipV2** is activated.

Default value: **$r('sys.color.chip_active_icon_color')**. The default value is not applied to non-SVG images.

If the value is **undefined**, the default value is used.

This attribute takes effect only when the image format is SVG.

**Decorator:** @Trace

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fillColor

```TypeScript
public fillColor?: ColorMetrics
```

Icon fill color.

Default value: **$r('sys.color.chip_usually_icon_color')**. The default value is not applied to non-SVG images.

If the value is **undefined**, the default value is used.

This attribute takes effect only when the image format is SVG.

**Decorator:** @Trace

**Type:** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## modifier

```TypeScript
public modifier?: ImageModifier
```

Icon modifier, which is used to set common attributes of the icon. Pass this parameter when you need to dynamically modify icon attributes (such as **opacity** and **objectFit**) through the modifier. If this parameter is not passed or is **undefined**, the modifier is not applied, and the icon uses the default attribute settings.

Default value: **undefined**, meaning the modifier is not applied.

**Decorator:** @Trace

**Type:** [ImageModifier](../../apis-default/arkts-apis/arkts-default-arkui-modifier.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
public size?: SizeT<LengthMetrics>
```

Icon size. Percentage values are not supported. If an invalid value is passed, the default value will be used.

Default value:

- When **ChipV2Options.size** is **ChipV2Size.SMALL**, the default value is  
**{width: $r('sys.float.chip_small_icon_size'), height: $r('sys.float.chip_small_icon_size')}**.  
- When **ChipV2Options.size** is **ChipV2Size.NORMAL**, the default value is  
**{width: $r('sys.float.chip_normal_icon_size'), height: $r('sys.float.chip_normal_icon_size')}**.

Unit: vp

If the value is **undefined**, the default value is used.

**Decorator:** @Trace

**Type:** [SizeT](arkts-arkui-graphics-sizet-i.md)&lt;[LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)&gt;

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## src

```TypeScript
public src: ResourceStr
```

Icon image or image address reference.

**Decorator:** @Trace

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
