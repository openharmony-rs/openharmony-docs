# BackForwardCacheOptions

Implements a **BackForwardCacheOptions** object to set back-forward cache options of the **Web** component.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## constructor

```TypeScript
constructor()
```

Constructs a **BackForwardCacheOptions** object.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## size

```TypeScript
size: number
```

The maximum number of pages that can be cached in a Web component.

The default value is 1, and the maximum value is 50.

If this parameter is set to 0 or a negative value, the back-forward cache is disabled.

The Web component reclaims the cache for memory pressure.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## timeToLive

```TypeScript
timeToLive: number
```

The time that a Web component allows a page to stay in the back-forward cache.

If this parameter is set to 0 or a negative value, the back-forward cache is disabled.

Default value: 600

Unit: second

**Type:** number

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core
