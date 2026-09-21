# RatingOptions

```TypeScript
declare interface RatingOptions
```

Provides configuration options for the **Rating** component.

> **NOTE:** 
> 
> To standardize anonymous object definitions, the element definitions here have been revised in API version 18.
> While historical version information is preserved for anonymous objects, there may be cases where the outer element
> 's

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## indicator

```TypeScript
indicator?: boolean
```

Whether the component is used as an indicator. If this parameter is set to **true**, the rating value cannot be changed.

Default value: **false**

**NOTE:** 

When **indicator** is set to **true**, the default component height is 12.0 vp, and the component width is calculated as follows: Height x Value of **stars**.

When **indicator** is set to **false**, the default component height is 28.0 vp, and the component width is calculated as follows: Height x Value of **stars**.

**Type:** boolean

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## rating

```TypeScript
rating: number
```

Value to rate.

Default value: **0**

Value range: [0, stars]

Values less than 0 are treated as **0**, and values greater than the value of [stars](arkts-arkui-rating-comp-attribute.md#stars) are treated as the value of **stars**.

This parameter supports two-way binding through [$$](../../../ui/state-management/arkts-two-way-sync.md).

**Type:** number

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
