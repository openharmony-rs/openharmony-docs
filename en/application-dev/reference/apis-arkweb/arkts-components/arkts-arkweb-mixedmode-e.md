# MixedMode

Enumerates the mixed content modes.

**Since:** 8

**System capability:** SystemCapability.Web.Webview.Core

## All

```TypeScript
All = 0
```

Loose mode: HTTP and HTTPS hybrid content can be loaded. This means that all insecure content can be loaded.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## Compatible

```TypeScript
Compatible = 1
```

Compatible mode. Allows some HTTP content to be loaded on an HTTPS page.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## None

```TypeScript
None = 2
```

Strict mode: HTTP and HTTPS hybrid content cannot be loaded.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core
