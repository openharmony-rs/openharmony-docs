# startProfiler

## Modules to Import

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## startProfiler

```TypeScript
function startProfiler(type: ProfilerResourceType, callback: ProfilerCallback, config?: ProfilerConfig): Promise<void>
```

Start the profiler to capture data. After starting, when the duration reaches the specified or default maximum value, or the size of the result file exceeds the limit, the system automatically stops capturing data and notifies the application through the callback function.

**Since:** 26.1.0

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-hidebug-function startProfiler(type: ProfilerResourceType, callback: ProfilerCallback, config?: ProfilerConfig): Promise<void>--><!--Device-hidebug-function startProfiler(type: ProfilerResourceType, callback: ProfilerCallback, config?: ProfilerConfig): Promise<void>-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [ProfilerResourceType](arkts-performanceanalysis-hidebug-profilerresourcetype-e.md) | Yes | Target profiler resource type. |
| callback | [ProfilerCallback](arkts-performanceanalysis-hidebug-profilercallback-t.md) | Yes | Callback function. |
| config | [ProfilerConfig](arkts-performanceanalysis-hidebug-profilerconfig-i.md) | No | Profiler configuration. <br>Default value: Use the default values for all configuration parameters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 11400416 | Invalid resource type. |
| 11400411 | Invalid maximum duration. |
| 11400412 | Invalid filter size. |
| 11400413 | Invalid stack depth. |
| 11400431 | Invalid nesting depth. |
| 11400432 | Invalid async-stack depth. |
| 11400414 | Invalid statistics interval. |
| 11400415 | Invalid sample interval bytes. |
| 11400421 | Resource profiler already started. |
| 11400423 | The number of resource profiling processes exceeds. |
| 11400424 | Resource profiling conflicts with CLI tools or system profiling tasks. |
| 11400426 | The daily quota for resource collection has been exhausted. |
| 11400427 | The system CPU is overloaded. |
| 11400428 | The available memory space is insufficient. |
| 11400429 | The available storage space is insufficient. |
| 11400430 | Other profiling errors. |
