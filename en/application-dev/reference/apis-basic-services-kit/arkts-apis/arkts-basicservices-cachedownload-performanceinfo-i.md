# PerformanceInfo

```TypeScript
interface PerformanceInfo
```

Describes the pre-downloaded performance information.

**Since:** 20

<!--Device-cacheDownload-interface PerformanceInfo--><!--Device-cacheDownload-interface PerformanceInfo-End-->

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

<!--Device-PerformanceInfo-readonly connectTime: double--><!--Device-PerformanceInfo-readonly connectTime: double-End-->

**System capability:** SystemCapability.Request.FileTransferAgent

## dnsTime

```TypeScript
readonly dnsTime: number
```

Time taken from DNS startup to resolution completion, in milliseconds.

**Type:** number

**Since:** 20

<!--Device-PerformanceInfo-readonly dnsTime: double--><!--Device-PerformanceInfo-readonly dnsTime: double-End-->

**System capability:** SystemCapability.Request.FileTransferAgent

## firstReceiveTime

```TypeScript
readonly firstReceiveTime: number
```

Time taken from startup to receiving the first byte, in milliseconds.

**Type:** number

**Since:** 20

<!--Device-PerformanceInfo-readonly firstReceiveTime: double--><!--Device-PerformanceInfo-readonly firstReceiveTime: double-End-->

**System capability:** SystemCapability.Request.FileTransferAgent

## firstSendTime

```TypeScript
readonly firstSendTime: number
```

Time taken from startup to sending the first byte, in milliseconds.

**Type:** number

**Since:** 20

<!--Device-PerformanceInfo-readonly firstSendTime: double--><!--Device-PerformanceInfo-readonly firstSendTime: double-End-->

**System capability:** SystemCapability.Request.FileTransferAgent

## redirectTime

```TypeScript
readonly redirectTime: number
```

Time taken from startup to redirection completion, in milliseconds.

**Type:** number

**Since:** 20

<!--Device-PerformanceInfo-readonly redirectTime: double--><!--Device-PerformanceInfo-readonly redirectTime: double-End-->

**System capability:** SystemCapability.Request.FileTransferAgent

## tlsTime

```TypeScript
readonly tlsTime: number
```

Time taken from TLS startup to connection completion, in milliseconds.

**Type:** number

**Since:** 20

<!--Device-PerformanceInfo-readonly tlsTime: double--><!--Device-PerformanceInfo-readonly tlsTime: double-End-->

**System capability:** SystemCapability.Request.FileTransferAgent

## totalTime

```TypeScript
readonly totalTime: number
```

Time taken from startup to request completion, in milliseconds.

**Type:** number

**Since:** 20

<!--Device-PerformanceInfo-readonly totalTime: double--><!--Device-PerformanceInfo-readonly totalTime: double-End-->

**System capability:** SystemCapability.Request.FileTransferAgent
