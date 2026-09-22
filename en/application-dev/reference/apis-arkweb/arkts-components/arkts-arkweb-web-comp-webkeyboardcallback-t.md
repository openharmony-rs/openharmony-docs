# WebKeyboardCallback

```TypeScript
type WebKeyboardCallback = (keyboardCallbackInfo: WebKeyboardCallbackInfo) => WebKeyboardOptions
```

Defines a callback to intercept the soft keyboard initiated from editable elements on a web page. This event is typically called when the **\&lt;input&gt;** tag on the web page is clicked.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyboardCallbackInfo | [WebKeyboardCallbackInfo](arkts-arkweb-web-comp-webkeyboardcallbackinfo-i.md) | Yes | Input parameter of the callback used to intercept the soft keyboard initiated from editable elements on a web page, including [WebKeyboardController](arkts-arkweb-web-comp.md#web) and editable element attributes. |

**Return value:**

| Type | Description |
| --- | --- |
| [WebKeyboardOptions](arkts-arkweb-web-comp-webkeyboardoptions-i.md) | [WebKeyboardOptions](arkts-arkweb-web-comp-webkeyboardoptions-i.md) instance, which is used to determine which type of soft keyboard to start by the ArkWeb kernel. |
