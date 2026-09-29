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

<!--Device-unnamed-declare interface DecorationStyleInterface--><!--Device-unnamed-declare interface DecorationStyleInterface-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ResourceColor
```

Color of the decoration line.

Default value: **Color.Black**

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DecorationStyleInterface-color?: ResourceColor--><!--Device-DecorationStyleInterface-color?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: TextDecorationStyle
```

Style of the decoration line. For details about the enums and their descriptions, see **TextDecorationStyle**.

Default value: **TextDecorationStyle.SOLID**

**Type:** [TextDecorationStyle](arkts-arkui-textdecorationstyle-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DecorationStyleInterface-style?: TextDecorationStyle--><!--Device-DecorationStyleInterface-style?: TextDecorationStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## thicknessScale

```TypeScript
thicknessScale?: number
```

Scale ratio of the decoration line thickness.

Default value: 1.0

Value range: [0, +∞)

**Note:** A negative value is processed as the default value.

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-DecorationStyleInterface-thicknessScale?: number--><!--Device-DecorationStyleInterface-thicknessScale?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: TextDecorationType
```

Type of the decoration line. For details about the enums and their descriptions, see **TextDecorationType**.

Default value: **TextDecorationType.None**

**Type:** [TextDecorationType](arkts-arkui-textdecorationtype-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DecorationStyleInterface-type: TextDecorationType--><!--Device-DecorationStyleInterface-type: TextDecorationType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
