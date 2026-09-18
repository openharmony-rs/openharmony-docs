# SizeResult


> **NOTE:** 
> 
> - The custom layout does not support the LazyForEach syntax.
> - When a custom layout is created in builder mode, only **this.builder()** is allowed in the **build()** method of a custom component, as shown in the recommended usage in the example below.
> - The size parameters of the parent component (custom component), except **aspectRatio**, are at a lower priority than those specified by [onMeasureSize](arkts-arkui-basecustomcomponent-c.md#onmeasuresize).
> - The position parameters of the child component, except **offset**, **position**, and **markAnchor**, are at a lower priority than those specified by [onPlaceChildren](arkts-arkui-basecustomcomponent-c.md#onplacechildren),and do not take effect.
> - When using the custom layout method, you must call **onMeasureSize** and **onPlaceChildren** at the same time for the layout to display properly.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height: number
```

Height obtained from the measurement result. Unit: vp, Value range: (-∞,+∞).

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width: number
```

Width obtained from the measurement result. Unit: vp, Value range: (-∞,+∞).

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
