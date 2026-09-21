# WebKeyboardCallbackInfo

```TypeScript
declare interface WebKeyboardCallbackInfo
```

Input parameters of the callback used to intercept the soft keyboard started from editable elements on a web page, including [WebKeyboardController](arkts-arkweb-web-comp.md#web) and the attributes of the editable element. It is suitable for scenarios where custom keyboard interaction is required, improving input experience customization and flexibility.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## attributes

```TypeScript
attributes: Record<string, string>
```

Attribute of the web page element that triggers the display of the soft keyboard.

**Type:** Record&lt;string, string&gt;

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## controller

```TypeScript
controller: WebKeyboardController
```

Controller used to control the input, deletion, and closure of the custom keyboard.

**Type:** [WebKeyboardController](arkts-arkweb-web-comp-webkeyboardcontroller-c.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core
