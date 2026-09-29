# RetryOptions

```TypeScript
interface RetryOptions
```

Task retry configuration.

**Since:** 26.0.0

<!--Device-cacheDownload-interface RetryOptions--><!--Device-cacheDownload-interface RetryOptions-End-->

**System capability:** SystemCapability.Request.FileTransferAgent

## Modules to Import

```TypeScript
import { cacheDownload } from '@kit.BasicServicesKit';
```

## maxRetryCount

```TypeScript
maxRetryCount?: number
```

Maximum number of retry attempts. The default value is 1. The minimum value is 0. The maximum value is 10. When set to 0, no retries will be performed.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-RetryOptions-maxRetryCount?: int--><!--Device-RetryOptions-maxRetryCount?: int-End-->

**System capability:** SystemCapability.Request.FileTransferAgent
