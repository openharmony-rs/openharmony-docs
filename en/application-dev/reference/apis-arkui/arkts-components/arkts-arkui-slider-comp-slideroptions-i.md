# SliderOptions

```TypeScript
declare interface SliderOptions
```

Provides information about the slider.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: Axis
```

Whether the slider moves horizontally or vertically.

Default value: **Axis.Horizontal**

**Type:** [Axis](../arkts-apis/arkts-arkui-axis-e.md)

**Default:** 
- API version 11+: Axis.Horizontal

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## max

```TypeScript
max?: number
```

Maximum value.

Default value: **100**

**NOTE:** 

If the value of **min** is greater than or equal to the value of **max**, the **min** value defaults to **0**, and the **max** value defaults to **100**.

If the value is not within the [min, max] range, the value of **min** or **max** is used, whichever is closer.

**Type:** number

**Default:** 
- API version 11+: 100

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## min

```TypeScript
min?: number
```

Minimum value.

Default value: **0**

**Type:** number

**Default:** 
- API version 11+: 0

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## reverse

```TypeScript
reverse?: boolean
```

Whether the slider values are reversed.

**true**: A horizontal slider slides from right to left, and a vertical slider slides from bottom to top. **false**: A horizontal slider slides from left to right, and a vertical slider slides from top to bottom.

Default value: **false**

**Type:** boolean

**Default:** 
- API version 11+: false

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## step

```TypeScript
step?: number
```

Step of the slider.

Default value: **1**

Value range: [0.01, max - min]

**NOTE:** 

If this parameter is set to a value less than 0 or greater than the value of **max**, the default value is used.

**Type:** number

**Default:** 
- API version 11+: 1 - Value range: [0.01, max - min]

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: SliderStyle
```

Style of the slider thumb and track.

Default value: **SliderStyle.OutSet**

**Type:** [SliderStyle](arkts-arkui-slider-comp-sliderstyle-e.md)

**Default:** 
- API version 11+: SliderStyle.OutSet

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value?: number
```

Current progress.

Default value: same as the value of **min**.

Since API version 10, this property supports two-way binding through [$$](../../../ui/state-management/arkts-two-way-sync.md).

This property supports two-way binding through [!!](../../../ui/state-management/arkts-new-binding.md#two-way-binding-between-built-in-component-parameters).

Value range: [min, max]

Values less than the value of **min** are adjusted to the value of **min**, and values greater than the value of **max** are capped at the value of **max**.

The $$ operator enables two-way synchronization between the TS variable and the **Slider** component's **value**. For details, see [Example 7: Setting Two-Way Binding for the Slider](../../../reference/apis-arkui/arkui-ts/ts-basic-components-slider.md#example-7-setting-two-way-binding-for-the-slider).

**Type:** number

**Default:** 
- API version 11+: same as the value of min

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
