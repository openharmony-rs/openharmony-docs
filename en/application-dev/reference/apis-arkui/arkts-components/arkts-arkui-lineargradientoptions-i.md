# LinearGradientOptions

Defines the linear gradient parameters.

> **NOTE:** 
> 
> To standardize anonymous object definitions, the element definitions here have been revised in API version 18.
> While historical version information is preserved for anonymous objects, there may be cases where the outer element
> 's

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## angle

```TypeScript
angle?: number | string
```

Start angle of the linear gradient. When the angle is 0 degrees, the gradient direction is from bottom to top (that is, 0 o'clock direction). A positive value indicates a clockwise rotation from the origin, (0, 0).

Value range: (-∞, +∞). Positive values indicate clockwise rotation, and negative values indicate counterclockwise rotation.

Default value: **180**

When specified as a string, valid values are pure numbers or numbers followed by units: "deg" (degrees), "rad" (radians), "grad" (gradians), or "turn" (turns). Examples: "90", "90deg", "1.57rad".

**Type:** number &#124; string

**Default:** 
- API version 18+: 180

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## colors

```TypeScript
colors: Array<[ResourceColor, number]>
```

Array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped. **ResourceColor** indicates the color. **number** represents the stop position of the color, with a range of [0, 1.0]. Values less than 0 are treated as **0**, and values greater than 1.0 are treated as **1.0**. **0** indicates the start of the gradient; **1.0** indicates the end. To achieve multi-color gradients, the **number** parameters in the array should be set in ascending order. If a later number is less than a previous one, it is treated as equal to the previous value.

Default value: **[]**, meaning no gradient effect.

**Type:** Array&lt;[ResourceColor, number]&gt;

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: GradientDirection
```

Direction of the linear gradient. It does not take effect when **angle** is set to a non-undefined value. **GradientDirection.None** uses the default direction.

Default value: **GradientDirection.Bottom**.

**Type:** [GradientDirection](../arkts-apis/arkts-arkui-gradientdirection-e.md)

**Default:** 
- API version 18+: GradientDirection.Bottom

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## repeating

```TypeScript
repeating?: boolean
```

Whether the colors are repeated.

Default value: **false**.

**true**: The colors are repeated.

**false**: The colors are not repeated.

**Type:** boolean

**Default:** 
- API version 18+: false

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
