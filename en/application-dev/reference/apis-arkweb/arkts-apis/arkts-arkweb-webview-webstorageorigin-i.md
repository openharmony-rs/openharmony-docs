# WebStorageOrigin

Provides usage information of the Web SQL Database.

@interface WebStorageOrigin [since 9 - 11]

**Since:** 9

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

**System capability:** SystemCapability.Web.Webview.Core
