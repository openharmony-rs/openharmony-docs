# RadioOptions

```TypeScript
declare interface RadioOptions
```

Radio button information.

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## group

```TypeScript
group: string
```

Name of the group to which the radio button belongs. Only one radio button in a given group can be selected at a time.

**Type:** string

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## indicatorBuilder

```TypeScript
indicatorBuilder?: CustomBuilder
```

Custom component to indicate that the radio button is selected. This custom component is center aligned with the radio button. If this parameter is set to **undefined**, the value of **RadioIndicatorType.TICK** is used as the indicator type.

**Type:** [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## indicatorType

```TypeScript
indicatorType?: RadioIndicatorType
```

Indicator type of the radio button. If no value is specified, the value of **RadioIndicatorType.TICK** is used.

**Type:** [RadioIndicatorType](arkts-arkui-radio-comp-radioindicatortype-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: string
```

Current value of the radio button.

**Type:** string

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
