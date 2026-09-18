# getGwpAsanGrayscaleState

## Modules to Import

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## getGwpAsanGrayscaleState

```TypeScript
function getGwpAsanGrayscaleState(): number
```

Obtains the number of remaining days for enabling GWP-ASan.

> **NOTE:** 
> 
> This API involves cross-process communication and takes a long time. To avoid performance problems, you are
> advised not to call this API in the main thread. You can use [@ohos.taskpool](../../apis-arkts/arkts-apis/arkts-arkts-taskpool.md) or
> [@ohos.worker](../../apis-arkts/arkts-apis/arkts-arkts-worker-n.md) to enable asynchronous threads to avoid application frame freezing.

**Since:** 20

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of remaining days for enabling GWP-ASan. If GWP-Asan is disabled, **0** is returned. |

**Examples**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
import { taskpool } from '@kit.ArkTS';

@Concurrent
function getGwpAsanStateTask(): number {
  return hidebug.getGwpAsanGrayscaleState();
}
taskpool.execute(getGwpAsanStateTask).then((remainDays: Object) => {
  console.info(`GWP-ASan remain days: ${remainDays as number}.`);
})
```
