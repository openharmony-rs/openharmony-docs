# BlurOnKeyboardHideMode

Enumerates whether the **Web** component loses focus when the soft keyboard is hidden.

**Since:** 14

**System capability:** SystemCapability.Web.Webview.Core

## SILENT

```TypeScript
SILENT = 0
```

The blur function of the Web component is disabled when the soft keyboard is hidden. When the user manually hides the soft keyboard, the focus remains on the text box. This is applicable to scenarios where the input focus needs to be retained.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Web.Webview.Core

## BLUR

```TypeScript
BLUR = 1
```

The blur function of the Web component is enabled when the soft keyboard is hidden. When the user manually hides the soft keyboard, the focus moves from the text box to the body of the Web component, and the text box loses focus. This is applicable to scenarios where standard input box behavior is required.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Web.Webview.Core
