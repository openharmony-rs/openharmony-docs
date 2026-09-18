# dumpHeapData

## Modules to Import

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## dumpHeapData

```TypeScript
function dumpHeapData(filename: string): void
```

Dumps the VM heap data and generates the **filename.heapsnapshot** file.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [dumpJsHeapData](arkts-performanceanalysis-hidebug-dumpjsheapdata-f.md)

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filename | string | Yes | User-defined heap file name. The .heapsnapshot file is generated in the **files** directory of the application based on the specified file name. The maximum length of a string is 128. |

**Examples**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

hidebug.dumpHeapData("heap-20220216");
```
