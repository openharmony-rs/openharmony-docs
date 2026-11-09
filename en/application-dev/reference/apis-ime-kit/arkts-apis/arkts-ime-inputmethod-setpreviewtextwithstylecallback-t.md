# SetPreviewTextWithStyleCallback

```TypeScript
export type SetPreviewTextWithStyleCallback = (text: string, range: Range, style: PreviewTextStyle) => void
```

Callback triggered when the input method framework needs to display the text preview with style.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-inputMethod-export type SetPreviewTextWithStyleCallback = (text: string, range: Range, style: PreviewTextStyle) => void--><!--Device-inputMethod-export type SetPreviewTextWithStyleCallback = (text: string, range: Range, style: PreviewTextStyle) => void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Preview text content. |
| range | [Range](arkts-ime-inputmethod-range-i.md) | Yes | Selected range of the text. |
| style | [PreviewTextStyle](arkts-ime-inputmethod-previewtextstyle-i.md) | Yes | Style of the preview text. |
