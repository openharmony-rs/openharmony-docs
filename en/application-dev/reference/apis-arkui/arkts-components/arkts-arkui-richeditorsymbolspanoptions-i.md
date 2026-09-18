# RichEditorSymbolSpanOptions

Sets the offset and style of the **SymbolSpan** component.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: number
```

Position at which the SymbolSpan is added. If omitted, it is added to the end of all content.

If the value is less than 0, it is added to the beginning of all content; if the value is greater than the length of all content, it is added to the end of all content.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: RichEditorSymbolSpanStyle
```

Style information of the SymbolSpan. Pass this parameter when you need to customize the color, size, weight, rendering policy, and other styles of the SymbolSpan; if omitted, the system default style information is used.

**Type:** [RichEditorSymbolSpanStyle](arkts-arkui-richeditorsymbolspanstyle-i.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
