# RichEditorChangeValue

```TypeScript
declare interface RichEditorChangeValue
```

Defines image and text change information.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## rangeBefore

```TypeScript
rangeBefore: TextRange
```

Start and end indexes of the content to be replaced.

**Type:** [TextRange](../arkts-apis/arkts-arkui-textrange-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## replacedImageSpans

```TypeScript
replacedImageSpans: Array<RichEditorImageSpanResult>
```

Information about the image span after the change.

**Type:** Array&lt;[RichEditorImageSpanResult](arkts-arkui-richeditor-comp-richeditorimagespanresult-i.md)&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## replacedSpans

```TypeScript
replacedSpans: Array<RichEditorTextSpanResult>
```

Information about the text span after the change.

**Type:** Array&lt;[RichEditorTextSpanResult](arkts-arkui-richeditor-comp-richeditortextspanresult-i.md)&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## replacedSymbolSpans

```TypeScript
replacedSymbolSpans: Array<RichEditorTextSpanResult>
```

Information about the symbol span after the change.

**Type:** Array&lt;[RichEditorTextSpanResult](arkts-arkui-richeditor-comp-richeditortextspanresult-i.md)&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
