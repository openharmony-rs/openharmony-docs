# MemoryLimit

```TypeScript
interface MemoryLimit
```

Defines the memory limit of the application process.

**Since:** 12

<!--Device-hidebug-interface MemoryLimit--><!--Device-hidebug-interface MemoryLimit-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## Modules to Import

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## rssLimit

```TypeScript
rssLimit: bigint
```

The limit of the application process's resident set, in kilobyte

**Type:** bigint

**Since:** 12

<!--Device-MemoryLimit-rssLimit: bigint--><!--Device-MemoryLimit-rssLimit: bigint-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## vmHeapLimit

```TypeScript
vmHeapLimit: bigint
```

The limit of the js vm heap size of current virtual machine, in kilobyte

**Type:** bigint

**Since:** 12

<!--Device-MemoryLimit-vmHeapLimit: bigint--><!--Device-MemoryLimit-vmHeapLimit: bigint-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## vmTotalHeapSize

```TypeScript
vmTotalHeapSize: bigint
```

The limit of the total js vm heap size of process, in kilobyte

**Type:** bigint

**Since:** 12

<!--Device-MemoryLimit-vmTotalHeapSize: bigint--><!--Device-MemoryLimit-vmTotalHeapSize: bigint-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## vssLimit

```TypeScript
vssLimit: bigint
```

The limit of the application process's virtual memory, in kilobyte

**Type:** bigint

**Since:** 12

<!--Device-MemoryLimit-vssLimit: bigint--><!--Device-MemoryLimit-vssLimit: bigint-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug
