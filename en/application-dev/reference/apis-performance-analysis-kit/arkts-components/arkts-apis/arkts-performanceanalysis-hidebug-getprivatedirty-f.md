# getPrivateDirty

## Modules to Import

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## getPrivateDirty

```TypeScript
function getPrivateDirty() : bigint
```

Obtains the size of the private dirty memory of a process. This API is implemented by reading the value of **Private_Dirty** in the **\/proc/{pid}/smaps_rollup** node.

> **NOTE:** 
> 
> Reading the **\/proc/{pid}/smaps_rollup** node is time-consuming. Therefore, you are advised not to use this API
> in the main thread. You can use this API in the asynchronous thread started by calling
> [@ohos.taskpool](../../apis-arkts/arkts-apis/arkts-arkts-taskpool.md) or [@ohos.worker](../../apis-arkts/arkts-apis/arkts-arkts-worker-n.md) to avoid frame freezing.

**Since:** 9

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Return value:**

| Type | Description |
| --- | --- |
| bigint | Size of the private dirty memory of the process, in KB. |

**Examples**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

let privateDirty: bigint = hidebug.getPrivateDirty();
console.info(`privateDirty = ${privateDirty}`);
```
