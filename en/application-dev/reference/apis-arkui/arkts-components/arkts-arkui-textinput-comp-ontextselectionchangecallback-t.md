# OnTextSelectionChangeCallback

```TypeScript
declare type OnTextSelectionChangeCallback = (selectionStart: number, selectionEnd: number) => void
```

Callback for text selection changes or cursor position changes.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-unnamed-declare type OnTextSelectionChangeCallback = (selectionStart: number, selectionEnd: number) => void--><!--Device-unnamed-declare type OnTextSelectionChangeCallback = (selectionStart: number, selectionEnd: number) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| selectionStart | number | Yes | Start position of the selected text. The start position of the text is 0. |
| selectionEnd | number | Yes | End position of the selected text. |
