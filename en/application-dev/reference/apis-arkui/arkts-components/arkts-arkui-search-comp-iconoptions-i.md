# IconOptions

```TypeScript
interface IconOptions
```

Defines the icon options.

**Since:** 10

<!--Device-unnamed-interface IconOptions--><!--Device-unnamed-interface IconOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ResourceColor
```

Icon color. If not set, the default color is used (in light mode, '#99182431', which is dark gray with 60% opacity; in dark mode, '#99ffffff', which is white with 60% opacity).

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-IconOptions-color?: ResourceColor--><!--Device-IconOptions-color?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: Length
```

Icon size. The default unit is vp when no unit is specified. Percentage is not supported; if a percentage is passed, it does not take effect.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-IconOptions-size?: Length--><!--Device-IconOptions-size?: Length-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## src

```TypeScript
src?: ResourceStr
```

Icon/image source. If not set, the system default icon is used.

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-IconOptions-src?: ResourceStr--><!--Device-IconOptions-src?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
