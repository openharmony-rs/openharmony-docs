# OnBeforeUnloadEvent

```TypeScript
declare interface OnBeforeUnloadEvent
```

Defines the callback triggered when the user is about to leave the current page in refresh or close scenarios. It is suitable for scenarios such as form editing, allowing developers to intercept the leave action and display a confirmation dialog, thereby preventing accidental loss of unsubmitted user data.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## isReload

```TypeScript
isReload?: boolean
```

The isReload parameter is set to true when the page is refreshed; otherwise, it remains false. Defult is false.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

## message

```TypeScript
message: string
```

The message of confirm dialog.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## result

```TypeScript
result: JsResult
```

Handle the user's JavaScript result.

**Type:** [JsResult](arkts-arkweb-web-comp-jsresult-c.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## url

```TypeScript
url: string
```

The url of the page.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core
