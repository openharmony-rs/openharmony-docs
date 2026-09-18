# RatingConfiguration

You need a custom class to implement the **ContentModifier** API. Inherits from [CommonConfiguration](arkts-arkui-commonconfiguration-i.md).

**Inheritance/Implementation:** RatingConfiguration extends CommonConfiguration<RatingConfiguration>

**Since:** 12

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## rating

```TypeScript
rating: number
```

Value to rate.

Default value: **0**

Value range: [0, stars]

Values less than 0 are treated as **0**, and values greater than the value of [stars](arkts-arkui-rating-comp-attribute.md#stars) are treated as the value of **stars**.

This parameter supports two-way binding through [&#36;&#36;](../../../ui/state-management/arkts-two-way-sync.md).

This parameter supports two-way binding through [!!](../../../ui/state-management/arkts-new-binding.md#two-way-binding-between-built-in-component-parameters).

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## stars

```TypeScript
stars: number
```

Total number of ratings.

Default value: **5**

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## stepSize

```TypeScript
stepSize: number
```

Step of an operation.

Default value: **0.5**

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## triggerChange

```TypeScript
triggerChange: Callback<number>
```

Callback triggered when the rating value changes.

**Type:** [Callback](arkts-arkui-callback-i.md)&lt;number&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
