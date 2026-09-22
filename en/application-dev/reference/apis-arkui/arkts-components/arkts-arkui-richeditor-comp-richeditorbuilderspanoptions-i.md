# RichEditorBuilderSpanOptions

```TypeScript
declare interface RichEditorBuilderSpanOptions
```

Sets the offset position and style of the inserted builder.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilitySpanOptions

```TypeScript
accessibilitySpanOptions?: AccessibilitySpanOptions
```

Accessibility settings. By default, the default value of [AccessibilitySpanOptions](../arkts-apis/arkts-arkui-accessibilityspanoptions-i.md) is used.

**Type:** [AccessibilitySpanOptions](../arkts-apis/arkts-arkui-accessibilityspanoptions-i.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: number
```

Position to add the builder. Value range: [0, total content length]. If omitted or if the value is less than 0 or greater than the total content length, it is added to the end of all content.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
