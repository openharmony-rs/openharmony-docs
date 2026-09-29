# TimePickerResult

```TypeScript
declare interface TimePickerResult
```

Returns the selected time result, where hour ranges from 0 to 23, regardless of the display format.

**Since:** 8

<!--Device-unnamed-declare interface TimePickerResult--><!--Device-unnamed-declare interface TimePickerResult-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## hour

```TypeScript
hour: number
```

Hour of the selected time.

Value range: [0-23], independent of the display format.

**Type:** number

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TimePickerResult-hour: number--><!--Device-TimePickerResult-hour: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## minute

```TypeScript
minute: number
```

Minute of the selected time.

Value range: [0-59]

**Type:** number

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TimePickerResult-minute: number--><!--Device-TimePickerResult-minute: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## second

```TypeScript
second: number
```

Second of the selected time.

Value range: [0-59]

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TimePickerResult-second: number--><!--Device-TimePickerResult-second: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
