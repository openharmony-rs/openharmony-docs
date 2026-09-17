# PerformanceInfo

Describes the pre-downloaded performance information.

**Since:** 20

**System capability:** SystemCapability.Request.FileTransferAgent

## Modules to Import

```TypeScript
import { cacheDownload } from '@kit.BasicServicesKit';
```

## connectTime

```TypeScript
readonly connectTime: number
```

Time taken from TCP startup to connection completion, in milliseconds.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.Request.FileTransferAgent

## dnsTime

```TypeScript
readonly dnsTime: number
```

Time taken from DNS startup to resolution completion, in milliseconds.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.Request.FileTransferAgent

## firstReceiveTime

```TypeScript
readonly firstReceiveTime: number
```

Time taken from startup to receiving the first byte, in milliseconds.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.Request.FileTransferAgent

## firstSendTime

```TypeScript
readonly firstSendTime: number
```

Time taken from startup to sending the first byte, in milliseconds.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.Request.FileTransferAgent

## redirectTime

```TypeScript
readonly redirectTime: number
```

Time taken from startup to redirection completion, in milliseconds.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.Request.FileTransferAgent

## tlsTime

```TypeScript
readonly tlsTime: number
```

Time taken from TLS startup to connection completion, in milliseconds.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.Request.FileTransferAgent

## totalTime

```TypeScript
readonly totalTime: number
```

Time taken from startup to request completion, in milliseconds.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.Request.FileTransferAgent
