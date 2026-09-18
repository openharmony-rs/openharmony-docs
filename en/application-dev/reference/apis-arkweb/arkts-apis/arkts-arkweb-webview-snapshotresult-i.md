# SnapshotResult

Represents a full drawing result.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## id

```TypeScript
id?: string
```

Snapshot ID.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## imagePixelMap

```TypeScript
imagePixelMap?: image.PixelMap
```

The **image.PixelMap** format.

**Type:** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## size

```TypeScript
size?: SizeOptions
```

Actual size rendered by Web. The SizeOptions object contains the width and height attributes, both of which are of the number type, in vp.

**Type:** [SizeOptions](../../apis-arkui/arkts-apis/arkts-arkui-sizeoptions-i.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## status

```TypeScript
status?: boolean
```

Status of the snapshot. The value **true** indicates normal, and **false** indicates failure. If obtaining the full rendering result fails, the width and height of the returned size are both 0, and imagePixelMap is empty.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core
