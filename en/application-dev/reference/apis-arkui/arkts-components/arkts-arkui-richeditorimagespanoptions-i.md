# RichEditorImageSpanOptions

Sets the offset and style of an image span.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onHover

```TypeScript
onHover?: OnHoverCallback
```

Callback triggered when the mouse hovers over the component. If this parameter is omitted, the mouse hover callback behavior is not executed.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## gesture

```TypeScript
gesture?: RichEditorGesture
```

Gesture event that triggers a callback. If this parameter is omitted, only the default system behavior is supported.

**Type:** [RichEditorGesture](arkts-arkui-richeditorgesture-i.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## imageStyle

```TypeScript
imageStyle?: RichEditorImageSpanStyle
```

Image style information. Pass this parameter when you need to customize the image size, vertical alignment mode, scaling type, and other styles. If this parameter is omitted, the default image style of the system is used.

**Type:** [RichEditorImageSpanStyle](arkts-arkui-richeditorimagespanstyle-i.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: number
```

Position of the image span to be added. If this parameter is omitted, the span is added to the end of all content.

If the value specified is less than 0, the span is placed at the beginning of all content. If the value is greater than the length of all content, the span is placed at the end of all content.

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
