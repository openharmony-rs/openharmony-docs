# SweepGradientOptions

Defines the sweep gradient parameters.

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

Center of the sweep gradient, that is, the coordinates relative to the upper left corner of the current component.

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

## end

```TypeScript
end?: number | string
```

End point of the sweep gradient.

Default value: **0**.

When specified as a string, valid values are pure numbers or numbers followed by units: "deg" (degrees), "rad" (radians), "grad" (gradians), or "turn" (turns). Examples: "90", "90deg", "1.57rad". The value is limited to 0 to 36 0 degrees after unit conversion. Values less than 0 degrees are treated as 0 degrees; values greater than 360 degrees are treated as 360 degrees.

**Type:** number &#124; string

**Default:** 
- API version 18+: 0

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## metricsColors

```TypeScript
metricsColors?: Array<[ColorMetrics, number]>
```

Array of color stops, each of which consists of a color and its stop position. Invalid colors are automatically skipped. When specified, **metricsColors** overrides **colors**. The color gamut attributes must be consistent across color stops. The value is considered invalid if mixed color gamut attributes are detected. The default value is transparent.

**Type:** Array&lt;[ColorMetrics, number]&gt;

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

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

## rotation

```TypeScript
rotation?: number | string
```

Rotation angle of the sweep gradient. Default value: **0**.

When specified as a string, valid values are pure numbers or numbers followed by units: "deg" (degrees), "rad" (radians), "grad" (gradians), or "turn" (turns). Examples: "90", "90deg", "1.57rad". The value is limited to 0 to 36 0 degrees after unit conversion. Values less than 0 degrees are treated as 0 degrees; values greater than 360 degrees are treated as 360 degrees.

**Type:** number &#124; string

**Default:** 
- API version 18+: 0

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start?: number | string
```

Start point of the sweep gradient.

Default value: **0**.

When specified as a string, valid values are pure numbers or numbers followed by units: "deg" (degrees), "rad" (radians), "grad" (gradians), or "turn" (turns). Examples: "90", "90deg", "1.57rad". The value is limited to 0 to 36 0 degrees after unit conversion. Values less than 0 degrees are treated as 0 degrees; values greater than 360 degrees are treated as 360 degrees.

**Type:** number &#124; string

**Default:** 
- API version 18+: 0

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
