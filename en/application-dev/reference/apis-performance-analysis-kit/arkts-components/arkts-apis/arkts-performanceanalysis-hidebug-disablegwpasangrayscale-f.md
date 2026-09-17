# disableGwpAsanGrayscale

## Modules to Import

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## disableGwpAsanGrayscale

```TypeScript
function disableGwpAsanGrayscale(): void
```

Disables GWP-ASan. This API is used to cancel the custom configuration and restore the default parameter [GwpAsanOptions](arkts-performanceanalysis-hidebug-gwpasanoptions-i.md).

> **NOTE:** 
> 
> This API involves cross-process communication and takes a long time. To avoid performance problems, you are
> advised not to call this API in the main thread. You can use [@ohos.taskpool](../../apis-arkts/arkts-apis/arkts-arkts-taskpool.md) or
> [@ohos.worker](../../apis-arkts/arkts-apis/arkts-arkts-worker-n.md) to enable asynchronous threads to avoid application frame freezing.

**Since:** 20

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Examples**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
import { taskpool } from '@kit.ArkTS';

@Concurrent
function disableGwpAsanTask(): void {
  hidebug.disableGwpAsanGrayscale();
}
taskpool.execute(disableGwpAsanTask).then(() => {
  console.info(`Disable GWP-ASan succeeded.`);
})
```
