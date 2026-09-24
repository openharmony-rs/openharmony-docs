# DecorationStyleInterface

```TypeScript
declare interface DecorationStyleInterface
```

Describes the API object for text decoration line styles.

> **NOTE:** 
> 
> When the bottom contour of a character intersects with the decoration, underline avoidance is triggered, commonly
> affecting characters like "g", "j", "y", "q", and "p."
> 
> If the decoration color is set to **Color.Transparent**, it inherits the text color of the first character in each
> line. If the decoration color is set to **"#00FFFFFF"**, the line becomes fully transparent.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ResourceColor
```

Color of the text decorative line.

Default value: **Color.Black**.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: TextDecorationStyle
```

Style of the text decorative line.

Default value: **TextDecorationStyle.SOLID**.

**Type:** [TextDecorationStyle](arkts-arkui-textdecorationstyle-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## thicknessScale

```TypeScript
thicknessScale?: number
```

Scale factor for the decoration line thickness.

Default value: **1.0**.

Value range: [0, +∞).

Note: Negative values are treated as the default value.

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: TextDecorationType
```

Type of the text decorative line.

Default value: **TextDecorationType.None**.

**Type:** [TextDecorationType](arkts-arkui-textdecorationtype-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
