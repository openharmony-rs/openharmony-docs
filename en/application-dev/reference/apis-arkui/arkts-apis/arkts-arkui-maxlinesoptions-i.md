# MaxLinesOptions

Configures the display effect of the **TextArea** component when the text exceeds the maximum number of lines.

**Since:** 20

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## overflowMode

```TypeScript
overflowMode?: MaxLinesMode
```

**overflowMode** can be used to set the non-inline mode for the TextArea component. When the text exceeds the set value of **maxLines** (maximum number of lines), a scroll effect is enabled. This requires configuration of textOverflow, and **MaxLinesMode** takes effect only when **textOverflow** is set to **None** or **Clip**. The default value of **MaxLinesMode** is **Clip**, indicating that text is truncated when it exceeds the value of **maxLines**.

**Type:** [MaxLinesMode](arkts-arkui-maxlinesmode-e.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
