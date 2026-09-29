# OutlineOptions

```TypeScript
declare interface OutlineOptions
```

Defines the outline options.

**Since:** 11

<!--Device-unnamed-declare interface OutlineOptions--><!--Device-unnamed-declare interface OutlineOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: EdgeColors | ResourceColor | LocalizedEdgeColors
```

Sets the outer outline color.

Default value: **Color.Black**

**Type:** EdgeColors &#124; [ResourceColor](arkts-arkui-resourcecolor-t.md) &#124; [LocalizedEdgeColors](arkts-arkui-localizededgecolors-i.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

<!--Device-OutlineOptions-color?: EdgeColors | ResourceColor | LocalizedEdgeColors--><!--Device-OutlineOptions-color?: EdgeColors | ResourceColor | LocalizedEdgeColors-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## radius

```TypeScript
radius?: OutlineRadiuses | Dimension
```

Sets the corner radius of the outer outline. Percentages are not supported.

Default value: **0**

Maximum effective value: Component width/2 + outlineWidth or component height/2 + outlineWidth

**Type:** OutlineRadiuses &#124; [Dimension](arkts-arkui-dimension-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

<!--Device-OutlineOptions-radius?: OutlineRadiuses | Dimension--><!--Device-OutlineOptions-radius?: OutlineRadiuses | Dimension-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: EdgeOutlineStyles | OutlineStyle
```

Sets the outer outline style.

Default value: **OutlineStyle.SOLID**

**Type:** EdgeOutlineStyles &#124; [OutlineStyle](../arkts-components/arkts-arkui-common-comp-outlinestyle-e.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

<!--Device-OutlineOptions-style?: EdgeOutlineStyles | OutlineStyle--><!--Device-OutlineOptions-style?: EdgeOutlineStyles | OutlineStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: EdgeOutlineWidths | Dimension
```

Sets the outer outline width. Percentages are not supported.

Default value: **0**

**width** must be set to display the outline effect.

**Type:** EdgeOutlineWidths &#124; [Dimension](arkts-arkui-dimension-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

<!--Device-OutlineOptions-width?: EdgeOutlineWidths | Dimension--><!--Device-OutlineOptions-width?: EdgeOutlineWidths | Dimension-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
