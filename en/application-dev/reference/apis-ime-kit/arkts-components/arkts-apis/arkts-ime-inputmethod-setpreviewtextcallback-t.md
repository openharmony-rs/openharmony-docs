# SetPreviewTextCallback

```TypeScript
export type SetPreviewTextCallback = (text: string, range: Range) => void
```

Callback triggered when the input method framework needs to display the text preview.

**Since:** 17

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Text preview. |
| range | [Range](arkts-ime-inputmethod-range-i.md) | Yes | Describes the range of the selected text. |
