# ProfilerResult

```TypeScript
interface ProfilerResult
```

Profiler结果。

**起始版本：** 26.1.0

<!--Device-hidebug-interface ProfilerResult--><!--Device-hidebug-interface ProfilerResult-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## filePath

```TypeScript
filePath: string
```

Profiler结果文件路径。如果没有采集到文件，则长度为0的字符串。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-ProfilerResult-filePath: string--><!--Device-ProfilerResult-filePath: string-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## type

```TypeScript
type: ProfilerResourceType
```

profiler资源类型。

**类型：** [ProfilerResourceType](arkts-performanceanalysis-hidebug-profilerresourcetype-e.md)

**起始版本：** 26.1.0

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-ProfilerResult-type: ProfilerResourceType--><!--Device-ProfilerResult-type: ProfilerResourceType-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug
