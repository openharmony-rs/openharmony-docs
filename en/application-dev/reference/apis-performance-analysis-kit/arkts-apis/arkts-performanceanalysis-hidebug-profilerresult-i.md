# ProfilerResult

```TypeScript
interface ProfilerResult
```

Profiler result.

**Since:** 26.1.0

<!--Device-hidebug-interface ProfilerResult--><!--Device-hidebug-interface ProfilerResult-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## Modules to Import

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## filePath

```TypeScript
filePath: string
```

Profiler result file path. If no file is collected, a string of 0 characters is returned.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-ProfilerResult-filePath: string--><!--Device-ProfilerResult-filePath: string-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## type

```TypeScript
type: ProfilerResourceType
```

Profiler resource type.

**Type:** [ProfilerResourceType](arkts-performanceanalysis-hidebug-profilerresourcetype-e.md)

**Since:** 26.1.0

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-ProfilerResult-type: ProfilerResourceType--><!--Device-ProfilerResult-type: ProfilerResourceType-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug
