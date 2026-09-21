# GaugeIndicatorOptions

```TypeScript
declare interface GaugeIndicatorOptions
```

Provides gauge indicator options.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: ResourceStr
```

Image path of the icon.

**NOTE:** 

If this parameter is not set, the default style is used, which is a triangle pointer.

Only icons in SVG format are supported. If icons in other formats are used, the default triangle style indicator is used.

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Default:** system style.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## space

```TypeScript
space?: Dimension
```

Distance between the indicator and the outer edge of the ring. The value cannot be in percentage.

Default value: **8**

Unit: vp

**NOTE:** 

For the default triangle style indicator, the distance is the amount of space between the triangle and the outer edge of the ring.

If this parameter is set to a value less than 0, the default value will be used.

If this parameter is set to a value greater than the ring radius, the default value will be used.

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**Default:** 8vp

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
