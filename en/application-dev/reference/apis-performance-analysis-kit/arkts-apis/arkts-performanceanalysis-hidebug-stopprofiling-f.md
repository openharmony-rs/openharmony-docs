# stopProfiling

## Modules to Import

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## stopProfiling

```TypeScript
function stopProfiling(): void
```

Stops the VM profiling method. **stopProfiling()** and **startProfiling(filename: string)** are called in pairs. **startProfiling(filename: string)** always occurs before **stopProfiling()**. You are advised not to call either of these methods repeatedly. Otherwise, an exception may occur.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [stopJsCpuProfiling](arkts-performanceanalysis-hidebug-stopjscpuprofiling-f.md)

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Examples**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

hidebug.startProfiling("cpuprofiler-20220216");
// code block
// ...
// code block
hidebug.stopProfiling();
```
