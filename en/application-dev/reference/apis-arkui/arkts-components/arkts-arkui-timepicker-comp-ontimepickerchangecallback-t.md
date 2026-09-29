# OnTimePickerChangeCallback

```TypeScript
declare type OnTimePickerChangeCallback = (result: TimePickerResult) => void
```

Triggered when a time is selected.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-unnamed-declare type OnTimePickerChangeCallback = (result: TimePickerResult) => void--><!--Device-unnamed-declare type OnTimePickerChangeCallback = (result: TimePickerResult) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| result | [TimePickerResult](arkts-arkui-timepicker-comp-timepickerresult-i.md) | Yes | Selected time result. The value of hour ranges from 0 to 23, regardless of the display format. |
