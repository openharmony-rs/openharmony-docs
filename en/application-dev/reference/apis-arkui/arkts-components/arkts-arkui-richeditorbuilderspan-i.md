# RichEditorBuilderSpan

Defines the BuilderSpan object of **RichEditor**, providing identity recognition and lifecycle awareness capabilities.

> **NOTE:** 
> 
> This interface is not supported when the **RichEditor** component is constructed with
> [RichEditorStyledStringOptions](arkts-arkui-richeditorstyledstringoptions-i.md).

**Since:** 26.2.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilitySpanOptions

```TypeScript
accessibilitySpanOptions?: AccessibilitySpanOptions
```

Accessibility reading feature. When omitted, the default value of [AccessibilitySpanOptions](../arkts-apis/arkts-arkui-accessibilityspanoptions-i.md) is used.

**Type:** [AccessibilitySpanOptions](../arkts-apis/arkts-arkui-accessibilityspanoptions-i.md)

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## builder

```TypeScript
builder: CustomBuilder
```

Custom component builder.

**Type:** [CustomBuilder](arkts-arkui-custombuilder-t.md)

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onAttach

```TypeScript
onAttach?: Callback<BuilderSpanInfo>
```

Callback triggered when the BuilderSpan is attached to **RichEditor**. The callback receives a [BuilderSpanInfo](arkts-arkui-builderspaninfo-i.md) object containing the id and offset.

**Type:** [Callback](arkts-arkui-callback-i.md)&lt;[BuilderSpanInfo](arkts-arkui-builderspaninfo-i.md)&gt;

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDetach

```TypeScript
onDetach?: Callback<BuilderSpanInfo>
```

Callback triggered when the BuilderSpan is removed from **RichEditor**. This includes deletion scenarios such as deletion via deleteSpans API, IME keyboard deletion, cut operations, and normal Undo degradation. The callback receives a [BuilderSpanInfo](arkts-arkui-builderspaninfo-i.md) object containing the id and offset.

> **NOTE:** 
> 
> In drag undo (undoStyle=KEEP_STYLE) scenarios, the onDetach callback is not triggered
> because the BuilderSpan is being restored rather than deleted.

**Type:** [Callback](arkts-arkui-callback-i.md)&lt;[BuilderSpanInfo](arkts-arkui-builderspaninfo-i.md)&gt;

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
