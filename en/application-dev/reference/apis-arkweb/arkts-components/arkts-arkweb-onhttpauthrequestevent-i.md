# OnHttpAuthRequestEvent

Defines the callback information triggered when an HTTP authentication request is received, including the host and realm information. It is suitable for scenarios where handling HTTP authentication is required, improving authentication process flexibility and security.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## handler

```TypeScript
handler: HttpAuthHandler
```

User operation.

**Type:** [HttpAuthHandler](arkts-arkweb-httpauthhandler-c.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## host

```TypeScript
host: string
```

Host to which the HTTP authentication credential is applied.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## realm

```TypeScript
realm: string
```

Realm to which the HTTP authentication credential is applied.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core
