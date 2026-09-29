# TextChangeOptions

```TypeScript
declare interface TextChangeOptions
```

Text change information, including the selection range before and after the change and the text content before the change.

**Since:** 15

<!--Device-unnamed-declare interface TextChangeOptions--><!--Device-unnamed-declare interface TextChangeOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## oldContent

```TypeScript
oldContent: string
```

Text content before the change.

**Type:** string

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-TextChangeOptions-oldContent: string--><!--Device-TextChangeOptions-oldContent: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## oldPreviewText

```TypeScript
oldPreviewText: PreviewText
```

Preview text before the change.

**Type:** [PreviewText](arkts-arkui-previewtext-i.md)

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-TextChangeOptions-oldPreviewText: PreviewText--><!--Device-TextChangeOptions-oldPreviewText: PreviewText-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## rangeAfter

```TypeScript
rangeAfter: TextRange
```

Selection range after the change.

**Type:** [TextRange](arkts-arkui-textrange-i.md)

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-TextChangeOptions-rangeAfter: TextRange--><!--Device-TextChangeOptions-rangeAfter: TextRange-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## rangeBefore

```TypeScript
rangeBefore: TextRange
```

Selection range before the change.

**Type:** [TextRange](arkts-arkui-textrange-i.md)

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-TextChangeOptions-rangeBefore: TextRange--><!--Device-TextChangeOptions-rangeBefore: TextRange-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
