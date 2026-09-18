# PasteEventCallback

```TypeScript
declare type PasteEventCallback = (event?: PasteEvent) => void
```

Represents the callback invoked when a paste operation is about to complete.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [PasteEvent](arkts-arkui-pasteevent-i.md) | No | Defines the user paste event. When omitted, paste event information is not received. |
