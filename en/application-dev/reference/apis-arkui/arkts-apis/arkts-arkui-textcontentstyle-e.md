# TextContentStyle

```TypeScript
declare enum TextContentStyle
```

Sets the polymorphic style of the text box.

**Since:** 10

<!--Device-unnamed-declare enum TextContentStyle--><!--Device-unnamed-declare enum TextContentStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT
```

Default style. The caret width is 1.5 vp, and the caret height is subject to the background height and font size of the selected text.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextContentStyle-DEFAULT--><!--Device-TextContentStyle-DEFAULT-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## INLINE

```TypeScript
INLINE
```

Inline input style, also known as inline mode. The text selection background height is the same as the input box height.

Inline input is used in scenarios where there is a clear distinction between editing and non-editing states, for example, renaming in a file list view.

The **showError** attribute is not supported.

In inline mode, dragging text is not supported.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextContentStyle-INLINE--><!--Device-TextContentStyle-INLINE-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
