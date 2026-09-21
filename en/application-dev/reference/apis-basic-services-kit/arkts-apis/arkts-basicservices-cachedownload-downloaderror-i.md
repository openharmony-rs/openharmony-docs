# DownloadError

```TypeScript
interface DownloadError
```

Describes the error message returned when a pre-download error occurs.

**Since:** 23

**System capability:** SystemCapability.Request.FileTransferAgent

## Modules to Import

```TypeScript
import { cacheDownload } from '@kit.BasicServicesKit';
```

## errorCode

```TypeScript
readonly errorCode: ErrorCode
```

Specific error type returned by the pre-download error callback.

**Type:** [ErrorCode](arkts-basicservices-cachedownload-errorcode-e.md)

**Since:** 23

**System capability:** SystemCapability.Request.FileTransferAgent

## message

```TypeScript
readonly message: string
```

Error message. A [universal error code](../../../reference/errorcode-universal.md) or [HTTP error code](../../../reference/apis-network-kit/errorcode-net-http.md) is returned.

**Type:** string

**Since:** 23

**System capability:** SystemCapability.Request.FileTransferAgent
