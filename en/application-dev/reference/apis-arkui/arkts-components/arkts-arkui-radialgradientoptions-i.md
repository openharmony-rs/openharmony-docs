# RadialGradientOptions

Defines the radial gradient parameters.

> **NOTE:** 
> 
> To standardize anonymous object definitions, the element definitions here have been revised in API version 18.
> While historical version information is preserved for anonymous objects, there may be cases where the outer element
> 's

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## center

```TypeScript
center: [Length, Length]
```

Center of the radial gradient, that is, the coordinates relative to the upper left corner of the current component.

**Type:** [Length, Length]

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## colors

```TypeScript
colors: Array<[ResourceColor, number]>
```

Array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped. **ResourceColor** represents the color. **number** represents the stop position of the color, with a range of [0, 1.0]. Values less than 0 are treated as **0**, and values greater than 1.0 are treated as **1.0**. **0** indicates the start of the gradient; **1.0** indicates the end. To achieve multi-color gradients, the **number** parameters in the array should be set in ascending order. If a later number is less than a previous one, it is treated as equal to the previous value.

Default value: **[]**, meaning no gradient effect.

**Type:** Array&lt;[ResourceColor, number]&gt;

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## radius

```TypeScript
radius: Length
```

Radius of the radial gradient.

Value range: [0, +∞). A value less than 0 is treated as **0**. If the value is **undefined**, the system adaptively determines the gradient radius.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

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
