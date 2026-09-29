# GaugeIndicatorOptions

```TypeScript
declare interface GaugeIndicatorOptions
```

Provides gauge indicator options.

**Since:** 11

<!--Device-unnamed-declare interface GaugeIndicatorOptions--><!--Device-unnamed-declare interface GaugeIndicatorOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: ResourceStr
```

Icon resource path.

**Note:** 

If this parameter is not set, the system default style is used, which is a triangle pointer.

Only icons in SVG format are supported. If an icon in another format is used, the default triangle pointer is used.

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Default:** system style.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

<!--Device-GaugeIndicatorOptions-icon?: ResourceStr--><!--Device-GaugeIndicatorOptions-icon?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## space

```TypeScript
space?: Dimension
```

Spacing between the pointer and the outer edge of the ring.

Default value: **8**

Unit: vp

**Note:** 

Percentage is not supported.

For the default triangle pointer, this is the spacing between the black triangle and the outer edge of the ring.

If the value is less than 0, the default value is used.

If the value is greater than the ring radius, the default value is used.

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**Default:** 8vp

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

<!--Device-GaugeIndicatorOptions-space?: Dimension--><!--Device-GaugeIndicatorOptions-space?: Dimension-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
