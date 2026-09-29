# ColoringStrategy

```TypeScript
declare enum ColoringStrategy
```

Enumerates the coloring strategies.

**Since:** 10

<!--Device-unnamed-declare enum ColoringStrategy--><!--Device-unnamed-declare enum ColoringStrategy-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## INVERT

```TypeScript
INVERT = 'invert'
```

The foreground colors are the inverse of the component background colors. This strategy is only applicable when set within the [foregroundColor](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#foregroundcolor) attribute.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ColoringStrategy-INVERT = 'invert'--><!--Device-ColoringStrategy-INVERT = 'invert'-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## AVERAGE

```TypeScript
AVERAGE = 'average'
```

The shadow colors of the component are the average color obtained from the component background shadow area. This strategy is only applicable when set within the [shadow](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#shadow) attribute whose input parameter type is ShadowOptions.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ColoringStrategy-AVERAGE = 'average'--><!--Device-ColoringStrategy-AVERAGE = 'average'-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## PRIMARY

```TypeScript
PRIMARY = 'primary'
```

The shadow colors of the component are the primary color obtained from the component background shadow area. This strategy is only applicable when set within the [shadow](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#shadow) attribute whose input parameter type is ShadowOptions.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ColoringStrategy-PRIMARY = 'primary'--><!--Device-ColoringStrategy-PRIMARY = 'primary'-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
