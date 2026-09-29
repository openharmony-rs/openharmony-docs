# OnPasteCallback

```TypeScript
declare type OnPasteCallback = (content: string, event: PasteEvent) => void
```

Paste callback.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-unnamed-declare type OnPasteCallback = (content: string, event: PasteEvent) => void--><!--Device-unnamed-declare type OnPasteCallback = (content: string, event: PasteEvent) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | string | Yes | Pasted text content. |
| event | [PasteEvent](arkts-arkui-richeditor-comp-pasteevent-i.md) | Yes | User-defined paste event. |
