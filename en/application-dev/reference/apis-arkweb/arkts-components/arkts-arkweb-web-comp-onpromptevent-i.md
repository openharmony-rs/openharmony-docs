# OnPromptEvent

```TypeScript
declare interface OnPromptEvent
```

Defines the callback used when a web page triggers **prompt()**.

**Since:** 12

<!--Device-unnamed-declare interface OnPromptEvent--><!--Device-unnamed-declare interface OnPromptEvent-End-->

**System capability:** SystemCapability.Web.Webview.Core

## message

```TypeScript
message: string
```

Information displayed in the dialog box.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-OnPromptEvent-message: string--><!--Device-OnPromptEvent-message: string-End-->

**System capability:** SystemCapability.Web.Webview.Core

## result

```TypeScript
result: JsResult
```

User operation result that is notified to the **Web** component.

**Type:** [JsResult](arkts-arkweb-web-comp-jsresult-c.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-OnPromptEvent-result: JsResult--><!--Device-OnPromptEvent-result: JsResult-End-->

**System capability:** SystemCapability.Web.Webview.Core

## url

```TypeScript
url: string
```

URL of the web page where the dialog box is displayed.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-OnPromptEvent-url: string--><!--Device-OnPromptEvent-url: string-End-->

**System capability:** SystemCapability.Web.Webview.Core

## value

```TypeScript
value: string
```

Default information returned by the dialog box.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-OnPromptEvent-value: string--><!--Device-OnPromptEvent-value: string-End-->

**System capability:** SystemCapability.Web.Webview.Core
