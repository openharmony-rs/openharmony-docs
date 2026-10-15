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

<!--Device-unnamed-declare interface RatingOptions--><!--Device-unnamed-declare interface RatingOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## indicator

```TypeScript
indicator?: boolean
```

Whether the **Rating** component is used as an indicator. The value **true** indicates the component is used as an indicator without changing the rating. The value **false** indicates the component is not used as an indicator and the rating can be changed.

Default value: **false**

**NOTE:** 

When **indicator** is set to **true**, the default component height is 12.0 vp, and the component width is calculated as follows: Height x Value of **stars**.

When **indicator** is set to **false**, the default component height is 28.0 vp, and the component width is calculated as follows: Height x Value of **stars**.

**Type:** boolean

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-RatingOptions-indicator?: boolean--><!--Device-RatingOptions-indicator?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## rating

```TypeScript
rating: number
```

Value to rate.

Default value: **0**

Value range: [0, stars]

Values less than 0 are treated as **0**, and values greater than the value of [stars](arkts-arkui-rating-comp-attribute.md#stars1) are treated as the value of **stars**.

This parameter supports two-way binding through [$$](../../../ui/state-management/arkts-two-way-sync.md).

**Type:** number

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-RatingOptions-rating: number--><!--Device-RatingOptions-rating: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
