# ButtonTriggerClickCallback

```TypeScript
declare type ButtonTriggerClickCallback = (xPos: number, yPos: number) => void
```

Defines the callback type used in ButtonConfiguration.

@typedef {function} ButtonTriggerClickCallback

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-unnamed-declare type ButtonTriggerClickCallback = (xPos: number, yPos: number) => void--><!--Device-unnamed-declare type ButtonTriggerClickCallback = (xPos: number, yPos: number) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| xPos | number | Yes | The value of xPos is x coordinate. |
| yPos | number | Yes | The value of yPos is y coordinate. |
