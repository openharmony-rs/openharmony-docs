# SliderTriggerChangeCallback

```TypeScript
declare type SliderTriggerChangeCallback = (value: number, mode: SliderChangeMode) => void
```

Defines the callback type used in **SliderConfiguration**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Current progress.<br>Value range: [[min](arkts-arkui-slideroptions-i.md), [max](arkts-arkui-slideroptions-i.md)] |
| mode | [SliderChangeMode](arkts-arkui-sliderchangemode-e.md) | Yes | State triggered by the event. |
