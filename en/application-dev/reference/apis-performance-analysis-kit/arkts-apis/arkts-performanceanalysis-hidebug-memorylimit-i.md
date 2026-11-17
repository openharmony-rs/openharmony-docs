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

Limit on the physical memory size of the application process, in KB. Currently, the system does not limit the physical memory size of the process. However, the available physical memory of the process cannot exceed the maximum physical memory of the device. You can call [hidebug.getSystemMemInfo](arkts-performanceanalysis-hidebug-getsystemmeminfo-f.md) to obtain the physical memory usage of the device.

**Type:** bigint

**Since:** 12

<!--Device-MemoryLimit-rssLimit: bigint--><!--Device-MemoryLimit-rssLimit: bigint-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## vmHeapLimit

```TypeScript
vmHeapLimit: bigint
```

Limit on the JS VM heap size of the calling thread, in KB.

**Type:** bigint

**Since:** 12

<!--Device-MemoryLimit-vmHeapLimit: bigint--><!--Device-MemoryLimit-vmHeapLimit: bigint-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## vmTotalHeapSize

```TypeScript
vmTotalHeapSize: bigint
```

Limit on the JS heap memory size of the process, in KB.

**Type:** bigint

**Since:** 12

<!--Device-MemoryLimit-vmTotalHeapSize: bigint--><!--Device-MemoryLimit-vmTotalHeapSize: bigint-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## vssLimit

```TypeScript
vssLimit: bigint
```

Limit on the virtual memory size, in KB.

**Type:** bigint

**Since:** 12

<!--Device-MemoryLimit-vssLimit: bigint--><!--Device-MemoryLimit-vssLimit: bigint-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug
