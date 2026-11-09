# MemoryLimit

```TypeScript
interface MemoryLimit
```

应用进程内存限制。

**起始版本：** 12

<!--Device-hidebug-interface MemoryLimit--><!--Device-hidebug-interface MemoryLimit-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## rssLimit

```TypeScript
rssLimit: bigint
```

应用程序进程可用的物理内存限制，以KB为单位，实际当前系统未对进程可用物理内存做限制，但是进程的可用物理内存仍然不会超过设备的实际最大可用物理内存，当前设备的物理内存使用情况可通过[hidebug.getSystemMemInfo](arkts-performanceanalysis-hidebug-getsystemmeminfo-f.md)获取。

**类型：** bigint

**起始版本：** 12

<!--Device-MemoryLimit-rssLimit: bigint--><!--Device-MemoryLimit-rssLimit: bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## vmHeapLimit

```TypeScript
vmHeapLimit: bigint
```

当前线程的 JS VM 堆大小限制，以KB为单位。

**类型：** bigint

**起始版本：** 12

<!--Device-MemoryLimit-vmHeapLimit: bigint--><!--Device-MemoryLimit-vmHeapLimit: bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## vmTotalHeapSize

```TypeScript
vmTotalHeapSize: bigint
```

当前进程的 JS 堆内存大小限制，以KB为单位。

**类型：** bigint

**起始版本：** 12

<!--Device-MemoryLimit-vmTotalHeapSize: bigint--><!--Device-MemoryLimit-vmTotalHeapSize: bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## vssLimit

```TypeScript
vssLimit: bigint
```

进程的虚拟内存限制，以KB为单位。

**类型：** bigint

**起始版本：** 12

<!--Device-MemoryLimit-vssLimit: bigint--><!--Device-MemoryLimit-vssLimit: bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug
