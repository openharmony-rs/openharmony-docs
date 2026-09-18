# isDebugState

## Modules to Import

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## isDebugState

```TypeScript
function isDebugState(): boolean
```

Obtains the debugging state of an application process.

**Since:** 12

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the Ark or native layer of the application process is in the debugging state. The value **true** indicates that the layer is in the debugging state, and **false** indicates the opposite. |

**Examples**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

console.info(`isDebugState = ${hidebug.isDebugState()}`)
```
