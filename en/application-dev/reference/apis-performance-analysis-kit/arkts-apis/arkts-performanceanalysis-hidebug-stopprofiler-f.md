# stopProfiler

## Modules to Import

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## stopProfiler

```TypeScript
function stopProfiler(): Promise<void>
```

Stop the profiler that has already started.

**Since:** 26.1.0

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-hidebug-function stopProfiler(): Promise<void>--><!--Device-hidebug-function stopProfiler(): Promise<void>-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 11400422 | Failed to stop resource profiling because it is not started. |
| 11400430 | Other profiling errors. |
