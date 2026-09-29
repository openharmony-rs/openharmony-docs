# RatingConfiguration

```TypeScript
declare interface RatingConfiguration extends CommonConfiguration<RatingConfiguration>
```

You need a custom class to implement the **ContentModifier** API. Inherits from [CommonConfiguration](arkts-arkui-common-comp-commonconfiguration-i.md).

**Inheritance/Implementation:** RatingConfiguration extends CommonConfiguration<RatingConfiguration>

**Since:** 12

<!--Device-unnamed-declare interface RatingConfiguration extends CommonConfiguration<RatingConfiguration>--><!--Device-unnamed-declare interface RatingConfiguration extends CommonConfiguration<RatingConfiguration>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## indicator

```TypeScript
indicator: boolean
```

Whether the rating bar is used as an indicator. **true**: used as an indicator. **false**: not used as an indicator.

Default value: **false**

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RatingConfiguration-indicator: boolean--><!--Device-RatingConfiguration-indicator: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## rating

```TypeScript
rating: number
```

Value to rate.

Default value: **0**

Value range: [0, stars]

If the value is less than 0, 0 is used. If the value is greater than the value of [stars](arkts-arkui-rating-comp-attribute.md#stars), the value of [stars](arkts-arkui-rating-comp-attribute.md#stars) is used.

This parameter supports two-way binding through [$$](../../../ui/state-management/arkts-two-way-sync.md).

This parameter supports two-way binding through [!!](../../../ui/state-management/arkts-new-binding.md#two-way-binding-between-built-in-component-parameters).

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RatingConfiguration-rating: number--><!--Device-RatingConfiguration-rating: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## stars

```TypeScript
stars: number
```

Total number of stars.

Default value: **5**

Value range: greater than 0. Values less than or equal to 0 are treated as the default value.

This parameter also defines the maximum values of both **rating** and **stepSize**.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RatingConfiguration-stars: number--><!--Device-RatingConfiguration-stars: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## stepSize

```TypeScript
stepSize: number
```

Step of an operation.

Default value: **0.5**

Value range: [0.1, stars]

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RatingConfiguration-stepSize: number--><!--Device-RatingConfiguration-stepSize: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## triggerChange

```TypeScript
triggerChange: Callback<number>
```

Called when the rating value changes. The parameter is the new rating value.

**Type:** Callback&lt;number&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RatingConfiguration-triggerChange: Callback<number>--><!--Device-RatingConfiguration-triggerChange: Callback<number>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
