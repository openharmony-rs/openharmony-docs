# OnRefreshAccessedHistoryEvent

```TypeScript
declare interface OnRefreshAccessedHistoryEvent
```

Defines the callback information triggered when navigation is complete, including the URL and refresh status. It is suitable for scenarios where monitoring page navigation history is required, improving navigation behavior tracking accuracy and user experience.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## isMainFrame

```TypeScript
isMainFrame?: boolean
```

Whether the event is triggered by the main frame.

The value **true** indicates that the event is triggered by the main frame, and **false** indicates the opposite.

**Type:** boolean

**Since:** 22

**System capability:** SystemCapability.Web.Webview.Core

## isRefreshed

```TypeScript
isRefreshed: boolean
```

Whether the page is reloaded. The value **true** means that the page is reloaded by invoking the [refresh&lt;sup&gt;9+&lt;/sup&gt;](../arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#refresh) API, and **false** means the opposite.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## url

```TypeScript
url: string
```

URL to be accessed.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core
