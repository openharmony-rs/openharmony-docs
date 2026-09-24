# RichEditorSelection

```TypeScript
declare interface RichEditorSelection
```

Defines information about the selected content.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selection

```TypeScript
selection: [number, number]
```

Range of the selection.

**Type:** [number, number]

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## spans

```TypeScript
spans: Array<RichEditorTextSpanResult | RichEditorImageSpanResult>
```

Span information.

**Type:** Array&lt;[RichEditorTextSpanResult](arkts-arkui-richeditor-comp-richeditortextspanresult-i.md) &#124; [RichEditorImageSpanResult](arkts-arkui-richeditor-comp-richeditorimagespanresult-i.md)&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
