# PrefetchOptions

PrefetchOptions is a configuration class in the ArkWeb framework for customizing web page prefetch behavior. It is set through the prefetch-related API of [prefetchPage](arkts-arkweb-webview-webviewcontroller-c.md#prefetchpage), and the customizable settings include whether to ignore Cache-Control: no-store in the response header and the minimum time interval between two prefetches.

**Since:** 21

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## constructor

```TypeScript
constructor()
```

A constructor used to create a **PrefetchOptions** instance.

**Since:** 21

**System capability:** SystemCapability.Web.Webview.Core

## ignoreCacheControlNoStore

```TypeScript
ignoreCacheControlNoStore: boolean
```

Sets whether to ignore Cache-Control: no-store in the response header.

If set to true, the header is ignored; if set to false, it is not ignored.

**Type:** boolean

**Since:** 21

**System capability:** SystemCapability.Web.Webview.Core

## minTimeBetweenPrefetchesMs

```TypeScript
minTimeBetweenPrefetchesMs: number
```

Sets the minimum time interval between two web page prefetches.

During each prefetch, the interval from the last prefetch is calculated. If it is less than the set value, the current prefetch is canceled.

Value range: [0, 500].

If set to a negative number, the default value 0 is used.

Unit: ms

**Type:** number

**Since:** 21

**System capability:** SystemCapability.Web.Webview.Core
