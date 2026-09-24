# ButtonTriggerClickCallback

```TypeScript
declare type ButtonTriggerClickCallback = (xPos: number, yPos: number) => void
```

Defines the callback type used in **ButtonConfiguration**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| xPos | number | Yes | X-coordinate of the click point.<br>Unit: vp |
| yPos | number | Yes | Y-coordinate of the click point.<br>Unit: vp |
