# DatePickerResult

```TypeScript
declare interface DatePickerResult
```

Defines the time format returned by the date picker.

**Since:** 8

<!--Device-unnamed-declare interface DatePickerResult--><!--Device-unnamed-declare interface DatePickerResult-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## day

```TypeScript
day?: number
```

Day of the selected date.

Value range: related to the set **start** and **end** parameters. If **start** and **end** are not set, the value range is [1, 31].

**Type:** number

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DatePickerResult-day?: number--><!--Device-DatePickerResult-day?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## month

```TypeScript
month?: number
```

Index of the month of the selected date. The index starts from 0, where **0** indicates January and **11** indicates December.

Value range: related to the set **start** and **end** parameters. If **start** and **end** are not set, the value range is [0, 11].

**Type:** number

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DatePickerResult-month?: number--><!--Device-DatePickerResult-month?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## year

```TypeScript
year?: number
```

Year of the selected date.

Value range: related to the set **start** and **end** parameters. If **start** and **end** are not set, the value range is [1970, 2100].

**Type:** number

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-DatePickerResult-year?: number--><!--Device-DatePickerResult-year?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
