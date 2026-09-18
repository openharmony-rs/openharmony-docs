# CacheMode

Enumerates the cache modes.

**Since:** 8

**System capability:** SystemCapability.Web.Webview.Core

## Default

```TypeScript
Default = 0
```

The cache that has not expired is preferentially used to load resources. If the cache is invalid or no cache is available, resources are obtained from the Internet.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## None

```TypeScript
None = 1
```

Preferentially loads resources from the cache (including expired ones), and fetches them from the network when no cache is available.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## Online

```TypeScript
Online = 2
```

The cache is not used to load the resources. All resources are forcibly obtained from the Internet.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## Only

```TypeScript
Only = 3
```

The local cache alone is used to load the resources.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core
