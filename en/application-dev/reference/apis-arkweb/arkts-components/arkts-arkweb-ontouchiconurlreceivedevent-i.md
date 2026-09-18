# OnTouchIconUrlReceivedEvent

Defines the callback information triggered when an apple-touch-icon URL is received, including the URL and precomposed status. It is suitable for scenarios where obtaining web page icons is required, improving icon management flexibility and user experience.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## precomposed

```TypeScript
precomposed: boolean
```

Whether the apple-touch-icon is precomposed.

**true** indicates that the apple-touch-icon is precomposed, and **false** indicates the opposite.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## url

```TypeScript
url: string
```

Received apple-touch-icon URL.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core
