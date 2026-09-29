# OnAlertEvent

```TypeScript
declare interface OnAlertEvent
```

Defines the callback used when a web page triggers **alert()**.

**Since:** 12

<!--Device-unnamed-declare interface OnAlertEvent--><!--Device-unnamed-declare interface OnAlertEvent-End-->

**System capability:** SystemCapability.Web.Webview.Core

## message

```TypeScript
message: string
```

Information displayed in the dialog box.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-OnAlertEvent-message: string--><!--Device-OnAlertEvent-message: string-End-->

**System capability:** SystemCapability.Web.Webview.Core

## result

```TypeScript
result: JsResult
```

User operation result that is notified to the **Web** component.

**Type:** [JsResult](arkts-arkweb-web-comp-jsresult-c.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-OnAlertEvent-result: JsResult--><!--Device-OnAlertEvent-result: JsResult-End-->

**System capability:** SystemCapability.Web.Webview.Core

## url

```TypeScript
url: string
```

URL of the web page where the dialog box is displayed.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-OnAlertEvent-url: string--><!--Device-OnAlertEvent-url: string-End-->

**System capability:** SystemCapability.Web.Webview.Core
