# TextInputStyle

```TypeScript
declare enum TextInputStyle
```

Text input style.

**Since:** 9

<!--Device-unnamed-declare enum TextInputStyle--><!--Device-unnamed-declare enum TextInputStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Default

```TypeScript
Default
```

Default style. The cursor is 1.5 vp wide, and the cursor height is related to the text selection highlight height and font size.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputStyle-Default--><!--Device-TextInputStyle-Default-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Inline

```TypeScript
Inline
```

Inline input style, also called inline mode. The text selection highlight height is the same as the input box height.

Inline input is used in scenarios where there is a clear distinction between the editing state and the non-editing state, for example, renaming in a file list view.

The showError attribute is not supported.

The showCounter attribute is not supported, and the character counter is not displayed in inline mode.

In inline mode, dragging text into the input box is not supported.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputStyle-Inline--><!--Device-TextInputStyle-Inline-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
