# OnInlineCounterV2Change

```TypeScript
export type OnInlineCounterV2Change = (value: number) => void
```

Defines the callback for the value change of the inline number **CounterV2**.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-unnamed-export type OnInlineCounterV2Change = (value: int) => void--><!--Device-unnamed-export type OnInlineCounterV2Change = (value: int) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Current value.<br>Value range: [min, max], where **min** and **max** correspond to the minimum and maximum values of **CounterV2**, respectively. |
