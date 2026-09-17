# EditableTextOnChangeCallback

```TypeScript
declare type EditableTextOnChangeCallback = (value: string, previewText?: PreviewText, options?: TextChangeOptions) => void
```

Represents the callback triggered when the content in the text box changes.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | Yes | Text displayed in the text box. |
| previewText | [PreviewText](arkts-arkui-previewtext-i.md) | No | Information about the preview text, including its start position and text content. |
| options | [TextChangeOptions](arkts-arkui-textchangeoptions-i.md) | No | Information about the text change, including the selection range, text displayed in the text box, and preview text. |
