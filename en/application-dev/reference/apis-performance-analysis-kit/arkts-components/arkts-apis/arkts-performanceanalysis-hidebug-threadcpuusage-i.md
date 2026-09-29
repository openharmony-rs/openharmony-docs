# ThreadCpuUsage

```TypeScript
interface ThreadCpuUsage
```

Describes the CPU usage of a thread.

**Since:** 12

<!--Device-hidebug-interface ThreadCpuUsage--><!--Device-hidebug-interface ThreadCpuUsage-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## Modules to Import

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## cpuUsage

```TypeScript
cpuUsage: number
```

CPU usage of the thread.

**Type:** number

**Since:** 12

<!--Device-ThreadCpuUsage-cpuUsage: double--><!--Device-ThreadCpuUsage-cpuUsage: double-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## threadId

```TypeScript
threadId: number
```

Thread ID.

**Type:** number

**Since:** 12

<!--Device-ThreadCpuUsage-threadId: long--><!--Device-ThreadCpuUsage-threadId: long-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## threadName

```TypeScript
threadName?: string
```

Thread name.

**Type:** string

**Since:** 26.0.1

<!--Device-ThreadCpuUsage-threadName?: string--><!--Device-ThreadCpuUsage-threadName?: string-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug
