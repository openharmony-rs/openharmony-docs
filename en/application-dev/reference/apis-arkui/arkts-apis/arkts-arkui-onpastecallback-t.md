# OnPasteCallback

```TypeScript
declare type OnPasteCallback = (pasteValue: string, event: PasteEvent) => void
```

Called when a paste operation is performed.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pasteValue | string | Yes | Text to be pasted. |
| event | [PasteEvent](../arkts-components/arkts-arkui-pasteevent-i.md) | Yes | Custom paste event. |
