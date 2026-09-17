# ButtonElement

The &lt;button&gt; component includes capsule, circle, text, arc, and download buttons.

@extends Element @interface ButtonElement

**Inheritance/Implementation:** ButtonElement extends [Element](arkts-arkui-viewmodel-element-i.md)

**Since:** 4

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## setProgress

```TypeScript
setProgress(param: { progress: number }): void
```

Progress bar of the download button. The value ranges from 0 to 100. The progress bar is displayed if the value is greater than 0. If the value is greater than or equal to 100, the progress bar is not displayed. NOTE The text displayed on the progress bar is changed based on the value.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| param | { progress: number } | Yes |  |
