# OnCounterV2HoverCallback

```TypeScript
export type OnCounterV2HoverCallback = (isHover: boolean) => void
```

Defines the mouse hover callback type for the **CounterV2** component.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isHover | boolean | Yes | Whether the mouse is hovering over the component. The value is **true** when the mouse enters and **false** when it leaves. |
