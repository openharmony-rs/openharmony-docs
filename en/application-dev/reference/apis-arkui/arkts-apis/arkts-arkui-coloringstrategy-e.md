# ColoringStrategy

Enumerates the coloring strategies.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## INVERT

```TypeScript
INVERT = 'invert'
```

The foreground colors are the inverse of the component background colors. This strategy is only applicable when set within the [foregroundColor](../arkts-components/arkts-arkui-commonmethod-c.md#foregroundcolor) attribute.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## AVERAGE

```TypeScript
AVERAGE = 'average'
```

The shadow colors of the component are the average color obtained from the component background shadow area. This strategy is only applicable when set within the shadow attribute whose input parameter type is ShadowOptions.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## PRIMARY

```TypeScript
PRIMARY = 'primary'
```

The shadow colors of the component are the primary color obtained from the component background shadow area. This strategy is only applicable when set within the shadow attribute whose input parameter type is ShadowOptions.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
