# startProfiling

## Modules to Import

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## startProfiling

```TypeScript
function startProfiling(filename: string): void
```

Starts the VM profiling method. **startProfiling(filename: string)** and **stopProfiling()** are called in pairs. **startProfiling(filename: string)** always occurs before **stopProfiling()**. You are advised not to call either of these methods repeatedly. Otherwise, an exception may occur.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [startJsCpuProfiling](arkts-performanceanalysis-hidebug-startjscpuprofiling-f.md)

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filename | string | Yes | Custom file name of the sampling data. The .json file is generated in the **files** directory of the application based on the specified file name. The maximum length of a string is 128. |

**Examples**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

hidebug.startProfiling("cpuprofiler-20220216");
// code block
// ...
// code block
hidebug.stopProfiling();
```
