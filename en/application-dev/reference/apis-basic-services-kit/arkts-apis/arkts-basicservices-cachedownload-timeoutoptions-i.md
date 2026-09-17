# TimeoutOptions

Task timeout configuration.

**Since:** 26.0.0

**System capability:** SystemCapability.Request.FileTransferAgent

## Modules to Import

```TypeScript
import { cacheDownload } from '@kit.BasicServicesKit';
```

## httpTotalTimeout

```TypeScript
httpTotalTimeout?: number
```

Complete HTTP request-response cycle timeout, in seconds. The default value is 60. The minimum value is 1. The value should be an integer.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Request.FileTransferAgent

## networkCheckTimeout

```TypeScript
networkCheckTimeout?: number
```

Network availability check timeout, in seconds. The default value is 20. The minimum value is 0. The maximum value is 20. When set to 0, no check will be performed. The value should be an integer.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Request.FileTransferAgent
