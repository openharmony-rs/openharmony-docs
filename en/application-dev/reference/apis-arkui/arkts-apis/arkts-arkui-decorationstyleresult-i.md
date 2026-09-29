# DecorationStyleResult

```TypeScript
interface DecorationStyleResult
```

Provides the text decoration information returned by the backend.

**Since:** 12

<!--Device-unnamed-interface DecorationStyleResult--><!--Device-unnamed-interface DecorationStyleResult-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color: ResourceColor
```

Color of the decoration line.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DecorationStyleResult-color: ResourceColor--><!--Device-DecorationStyleResult-color: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: TextDecorationStyle
```

Style of the decoration line.

Default value: TextDecorationStyle.SOLID

**Type:** [TextDecorationStyle](arkts-arkui-textdecorationstyle-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DecorationStyleResult-style?: TextDecorationStyle--><!--Device-DecorationStyleResult-style?: TextDecorationStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## thicknessScale

```TypeScript
thicknessScale?: number
```

Scale ratio of the decoration line thickness.

Default value: 1.0

Value range: [0, +∞)

**Note:** Negative values are processed as the default value.

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-DecorationStyleResult-thicknessScale?: number--><!--Device-DecorationStyleResult-thicknessScale?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: TextDecorationType
```

Type of the decoration line.

**Type:** [TextDecorationType](arkts-arkui-textdecorationtype-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DecorationStyleResult-type: TextDecorationType--><!--Device-DecorationStyleResult-type: TextDecorationType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
