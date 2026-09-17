# getSystemMemInfo

## Modules to Import

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## getSystemMemInfo

```TypeScript
function getSystemMemInfo(): SystemMemInfo
```

Obtains system memory information. This API is implemented by reading data from the **\/proc/meminfo** node.

**Since:** 12

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Return value:**

| Type | Description |
| --- | --- |
| [SystemMemInfo](arkts-performanceanalysis-hidebug-systemmeminfo-i.md) | System memory information. |

**Examples**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

let systemMemInfo: hidebug.SystemMemInfo = hidebug.getSystemMemInfo();

console.info(`totalMem: ${systemMemInfo.totalMem}, freeMem: ${systemMemInfo.freeMem}, ` +
  `availableMem: ${systemMemInfo.availableMem}`);
```
