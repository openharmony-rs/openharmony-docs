# BorderOptions

```TypeScript
declare interface BorderOptions
```

Defines border information.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: EdgeColors | ResourceColor | LocalizedEdgeColors
```

Border color.

**Type:** EdgeColors &#124; [ResourceColor](arkts-arkui-resourcecolor-t.md) &#124; [LocalizedEdgeColors](arkts-arkui-localizededgecolors-i.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## dashGap

```TypeScript
dashGap?: EdgeWidths | LengthMetrics | LocalizedEdgeWidths
```

Sets the gap between dashed line segments. This takes effect only when the border style is dashed.

Percentage values are not supported.

**Widget capability**: This API cannot be used in ArkTS widgets.

**Type:** EdgeWidths &#124; [LengthMetrics](arkts-arkui-lengthmetrics-t.md) &#124; [LocalizedEdgeWidths](arkts-arkui-localizededgewidths-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## dashWidth

```TypeScript
dashWidth?: EdgeWidths | LengthMetrics | LocalizedEdgeWidths
```

Sets the length of dashed line segments. This takes effect only when the border style is dashed.

Percentage values are not supported.

**Widget capability**: This API cannot be used in ArkTS widgets.

**Type:** EdgeWidths &#124; [LengthMetrics](arkts-arkui-lengthmetrics-t.md) &#124; [LocalizedEdgeWidths](arkts-arkui-localizededgewidths-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## radius

```TypeScript
radius?: BorderRadiuses | Length | LocalizedBorderRadiuses
```

Border corner radius.

**Type:** [BorderRadiuses](arkts-arkui-borderradiuses-t.md) &#124; [Length](arkts-arkui-length-t.md) &#124; [LocalizedBorderRadiuses](arkts-arkui-localizedborderradiuses-i.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: EdgeStyles | BorderStyle
```

Border style.

**Type:** EdgeStyles &#124; [BorderStyle](arkts-arkui-borderstyle-e.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: EdgeWidths | Length | LocalizedEdgeWidths
```

Border width.

**Type:** EdgeWidths &#124; [Length](arkts-arkui-length-t.md) &#124; [LocalizedEdgeWidths](arkts-arkui-localizededgewidths-i.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
