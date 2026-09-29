# WebStorageOrigin

```TypeScript
interface WebStorageOrigin
```

Provides usage information of the Web SQL Database.

@interface WebStorageOrigin [since 9 - 11]

**Since:** 9

<!--Device-webview-interface WebStorageOrigin--><!--Device-webview-interface WebStorageOrigin-End-->

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## origin

```TypeScript
origin: string
```

Index of the origin.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WebStorageOrigin-origin: string--><!--Device-WebStorageOrigin-origin: string-End-->

**System capability:** SystemCapability.Web.Webview.Core

## quota

```TypeScript
quota: number
```

Storage quota of the specified source.

Unit: byte.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WebStorageOrigin-quota: number--><!--Device-WebStorageOrigin-quota: number-End-->

**System capability:** SystemCapability.Web.Webview.Core

## usage

```TypeScript
usage: number
```

Storage usage of the specified source.

Unit: byte.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WebStorageOrigin-usage: number--><!--Device-WebStorageOrigin-usage: number-End-->

**System capability:** SystemCapability.Web.Webview.Core
