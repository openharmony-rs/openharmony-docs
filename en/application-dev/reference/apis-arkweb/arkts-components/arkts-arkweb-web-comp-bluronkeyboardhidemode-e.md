# BlurOnKeyboardHideMode

```TypeScript
declare enum BlurOnKeyboardHideMode
```

Enumerates whether the **Web** component loses focus when the soft keyboard is hidden.

**Since:** 14

<!--Device-unnamed-declare enum BlurOnKeyboardHideMode--><!--Device-unnamed-declare enum BlurOnKeyboardHideMode-End-->

**System capability:** SystemCapability.Web.Webview.Core

## BLUR

```TypeScript
BLUR = 1
```

The blur function of the Web component is enabled when the soft keyboard is hidden. When the user manually hides the soft keyboard, the focus moves from the text box to the body of the Web component, and the text box loses focus. This is applicable to scenarios where standard input box behavior is required.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-BlurOnKeyboardHideMode-BLUR = 1--><!--Device-BlurOnKeyboardHideMode-BLUR = 1-End-->

**System capability:** SystemCapability.Web.Webview.Core

## SILENT

```TypeScript
SILENT = 0
```

The blur function of the Web component is disabled when the soft keyboard is hidden. When the user manually hides the soft keyboard, the focus remains on the text box. This is applicable to scenarios where the input focus needs to be retained.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-BlurOnKeyboardHideMode-SILENT = 0--><!--Device-BlurOnKeyboardHideMode-SILENT = 0-End-->

**System capability:** SystemCapability.Web.Webview.Core
