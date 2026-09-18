# RssInfo

Describes the physical memory information about an application process.

**Since:** 24

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## Modules to Import

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## rss

```TypeScript
rss: bigint
```

Resident set size (RSS), in KB. It includes anonymous pages, file mapping pages, and shared memory pages. The calculation formula is **\/proc/{pid}/status: VmRss**.

**Type:** bigint

**Since:** 24

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## swapRss

```TypeScript
swapRss: bigint
```

Total size of anonymous private pages swapped out to the swap partition, in KB. The calculation formula is **\/proc/{pid}/status: VmSwap**.

**Type:** bigint

**Since:** 24

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug
