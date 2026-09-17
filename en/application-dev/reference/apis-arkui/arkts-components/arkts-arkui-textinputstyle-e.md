# TextInputStyle

Text input style.

**Since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Default

```TypeScript
Default
```

Default style. The caret width is fixed at 1.5 vp, and the caret height is subject to the background height and font size of the selected text.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Inline

```TypeScript
Inline
```

Inline style. The background height of the selected text is the same as the height of the text box.

This style is used in scenarios where editing and non-editing states are obvious, for example, renaming in the file list view.

The **showError** attribute is not supported for this style.

In the [inline style](../../../ui/arkts-common-components-text-input.md#inline-style), text cannot be dragged into the text box.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
