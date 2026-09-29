# OnDateCounterV2ChangeCallback

```TypeScript
export type OnDateCounterV2ChangeCallback = (date: CounterV2DateData) => void
```

Defines the callback for date changes of the inline date **CounterV2**.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-unnamed-export type OnDateCounterV2ChangeCallback = (date: CounterV2DateData) => void--><!--Device-unnamed-export type OnDateCounterV2ChangeCallback = (date: CounterV2DateData) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| date | [CounterV2DateData](arkts-arkui-arkui-advanced-counterv2-counterv2datedata-c.md) | Yes | Current date value. |
