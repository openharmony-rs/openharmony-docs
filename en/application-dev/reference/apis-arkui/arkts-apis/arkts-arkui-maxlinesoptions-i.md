# MaxLinesOptions

```TypeScript
declare interface MaxLinesOptions
```

Configures the display effect of the **TextArea** component when the text exceeds the maximum number of lines.

**Since:** 20

<!--Device-unnamed-declare interface MaxLinesOptions--><!--Device-unnamed-declare interface MaxLinesOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## overflowMode

```TypeScript
overflowMode?: MaxLinesMode
```

`overflowMode` configures the non-inline mode of the [TextArea](../arkts-components/arkts-arkui-textarea-comp.md) component. When the number of lines exceeds the configured `maxLines`, scrolling is enabled. It must be used together with [textOverflow](../arkts-components/arkts-arkui-textarea-comp-attribute.md#textoverflow), and `MaxLinesMode` takes effect only when `textOverflow` is set to None or Clip. By default, the value of `MaxLinesMode` is Clip, and text is truncated when the number of lines exceeds `maxLines`.

**Type:** [MaxLinesMode](arkts-arkui-maxlinesmode-e.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-MaxLinesOptions-overflowMode?: MaxLinesMode--><!--Device-MaxLinesOptions-overflowMode?: MaxLinesMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
