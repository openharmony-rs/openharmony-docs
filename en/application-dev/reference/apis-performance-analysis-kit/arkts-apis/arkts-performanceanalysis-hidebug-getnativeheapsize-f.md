# getNativeHeapSize

## Modules to Import

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## getNativeHeapSize

```TypeScript
function getNativeHeapSize() : bigint
```

Obtains the total number of bytes occupied by the total space (**uordblks** + **fordblks**, which are obtained from **mallinfo**) held by a process, which is measured by the memory allocator.

**Since:** 8

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Return value:**

| Type | Description |
| --- | --- |
| bigint | Size of the memory occupied by the total space held by the process, in bytes. |

**Examples**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

let nativeHeapSize: bigint = hidebug.getNativeHeapSize();
console.info(`nativeHeapSize = ${nativeHeapSize}`);
```
