# TextContentStyle

The polymorphic style of the text box.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT
```

Default style. The caret width is fixed at 1.5 vp, and the caret height is subject to the background height and font size of the selected text.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## INLINE

```TypeScript
INLINE
```

Inline input style. The background height of the selected text is the same as the height of the text box.

This style is used in scenarios where editing and non-editing states are obvious, for example, renaming in the file list view.

The **showError** attribute is not supported for this style.

This style does not allow for text dragging and dropping.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
