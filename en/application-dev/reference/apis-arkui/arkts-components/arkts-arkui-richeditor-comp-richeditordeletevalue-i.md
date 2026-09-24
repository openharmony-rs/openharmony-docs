# RichEditorDeleteValue

```TypeScript
declare interface RichEditorDeleteValue
```

Defines information about the deletion operation and the content to be deleted.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction: RichEditorDeleteDirection
```

Direction of the delete operation.

**Type:** [RichEditorDeleteDirection](arkts-arkui-richeditor-comp-richeditordeletedirection-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## length

```TypeScript
length: number
```

Length of the content to be deleted.

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset: number
```

Offset of the content to be deleted.

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## richEditorDeleteSpans

```TypeScript
richEditorDeleteSpans: Array<RichEditorTextSpanResult | RichEditorImageSpanResult>
```

Information about the text or image spans to be deleted.

**Type:** Array&lt;[RichEditorTextSpanResult](arkts-arkui-richeditor-comp-richeditortextspanresult-i.md) &#124; [RichEditorImageSpanResult](arkts-arkui-richeditor-comp-richeditorimagespanresult-i.md)&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
