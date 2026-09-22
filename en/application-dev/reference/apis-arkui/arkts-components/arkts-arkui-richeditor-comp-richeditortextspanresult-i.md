# RichEditorTextSpanResult

```TypeScript
declare interface RichEditorTextSpanResult
```

Defines text span information.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offsetInSpan

```TypeScript
offsetInSpan: [number, number]
```

Start and end positions of the valid content in the text span.

**Type:** [number, number]

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## paragraphStyle

```TypeScript
paragraphStyle?: RichEditorParagraphStyle
```

Paragraph style.

If omitted, the system default paragraph style is used.

**Type:** [RichEditorParagraphStyle](arkts-arkui-richeditor-comp-richeditorparagraphstyle-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## previewText

```TypeScript
previewText?: string
```

Content of the preview text.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## spanPosition

```TypeScript
spanPosition: RichEditorSpanPosition
```

Span position.

**Type:** [RichEditorSpanPosition](arkts-arkui-richeditor-comp-richeditorspanposition-i.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## symbolSpanStyle

```TypeScript
symbolSpanStyle?: RichEditorSymbolSpanStyle
```

Style of the **SymbolSpan** component.

**Type:** [RichEditorSymbolSpanStyle](arkts-arkui-richeditor-comp-richeditorsymbolspanstyle-i.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textStyle

```TypeScript
textStyle: RichEditorTextStyleResult
```

Text span style.

**Type:** [RichEditorTextStyleResult](arkts-arkui-richeditor-comp-richeditortextstyleresult-i.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## urlStyle

```TypeScript
urlStyle?: RichEditorUrlStyle
```

URL information.

Default value: undefined.

Pass this parameter when a hyperlink style needs to be set for the text.

**Type:** [RichEditorUrlStyle](arkts-arkui-richeditor-comp-richeditorurlstyle-i.md)

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: string
```

Content of the text span or symbol ID.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## valueResource

```TypeScript
valueResource?: Resource
```

SymbolSpan resource content.

Default value: undefined.

**Type:** [Resource](../arkts-apis/arkts-arkui-resource-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
