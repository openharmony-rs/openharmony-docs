# getVss

## Modules to Import

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## getVss

```TypeScript
function getVss(): bigint
```

Obtains the virtual set size used by the application process. This API is implemented by multiplying the value of **size** (number of memory pages) in the **\/proc/{pid}/statm** node by the page size (4 KB per page).

**Since:** 11

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Return value:**

| Type | Description |
| --- | --- |
| bigint | Virtual set size used by the application process, in KB. |

**Examples**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

let vss: bigint = hidebug.getVss();
console.info(`vss = ${vss}`);
```
