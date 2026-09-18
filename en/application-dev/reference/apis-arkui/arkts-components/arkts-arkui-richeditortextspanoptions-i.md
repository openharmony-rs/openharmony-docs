# RichEditorTextSpanOptions

Defines the options for adding a text span.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## gesture

```TypeScript
gesture?: RichEditorGesture
```

Behavior trigger callback. Pass this parameter when the tap or long-press interaction behavior of a text span needs to be customized. If omitted, only the system default behavior is used.

**Type:** [RichEditorGesture](arkts-arkui-richeditorgesture-i.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: number
```

Position of the text span to be added. If this parameter is omitted, the span is added to the end of all content.

If the value specified is less than 0, the span is placed at the beginning of all content. If the value is greater than the length of all content, the span is placed at the end of all content.

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## paragraphStyle

```TypeScript
paragraphStyle?: RichEditorParagraphStyle
```

Paragraph style. Pass this parameter when paragraph-level layout properties such as text alignment, indentation, and line breaking rules need to be set. If not passed, the system default paragraph style (left-aligned, no indentation, word-based line breaking) is used.

**Type:** [RichEditorParagraphStyle](arkts-arkui-richeditorparagraphstyle-i.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: RichEditorTextStyle
```

Text style information. Pass this parameter when custom styles such as text color, font size, and font weight need to be set. If omitted, the system default text information is used.

**Type:** [RichEditorTextStyle](arkts-arkui-richeditortextstyle-i.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## urlStyle

```TypeScript
urlStyle?: RichEditorUrlStyle
```

URL information.

Default value: **undefined**

**Type:** [RichEditorUrlStyle](arkts-arkui-richeditorurlstyle-i.md)

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
