# MemoryLimit

Defines the memory limit of the application process.

**Since:** 12

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

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## vmHeapLimit

```TypeScript
vmHeapLimit: bigint
```

The limit of the js vm heap size of current virtual machine, in kilobyte

**Type:** bigint

**Since:** 12

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## vmTotalHeapSize

```TypeScript
vmTotalHeapSize: bigint
```

The limit of the total js vm heap size of process, in kilobyte

**Type:** bigint

**Since:** 12

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## vssLimit

```TypeScript
vssLimit: bigint
```

The limit of the application process's virtual memory, in kilobyte

**Type:** bigint

**Since:** 12

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug
