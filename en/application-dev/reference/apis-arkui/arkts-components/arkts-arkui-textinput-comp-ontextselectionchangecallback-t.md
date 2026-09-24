# OnTextSelectionChangeCallback

```TypeScript
declare type OnTextSelectionChangeCallback = (selectionStart: number, selectionEnd: number) => void
```

Defines the callback for text selection changes or caret position changes.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| selectionStart | number | Yes | Start position of the selected text. The start position of text is 0. |
| selectionEnd | number | Yes | End position of the selected text. |
