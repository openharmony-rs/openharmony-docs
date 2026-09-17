# ResourceInfo

Describes the pre-downloaded resource information.

**Since:** 20

**System capability:** SystemCapability.Request.FileTransferAgent

## Modules to Import

```TypeScript
import { cacheDownload } from '@kit.BasicServicesKit';
```

## size

```TypeScript
readonly size: number
```

Size of a pre-downloaded resource after decompression, in bytes. If the value is a positive integer, the resource is successfully downloaded; if the value is **-1**, the resource fails to be downloaded.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.Request.FileTransferAgent
