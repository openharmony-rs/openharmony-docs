# startProfiler

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## startProfiler

```TypeScript
function startProfiler(type: ProfilerResourceType, callback: ProfilerCallback, config?: ProfilerConfig): Promise<void>
```

启动Profiler采集数据。启动后，当持续时间达到指定或默认的最大值，或结果文件超过限制时，系统会自动停止采集数据，并通过回调函数通知应用程序。

**起始版本：** 26.1.0

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-hidebug-function startProfiler(type: ProfilerResourceType, callback: ProfilerCallback, config?: ProfilerConfig): Promise<void>--><!--Device-hidebug-function startProfiler(type: ProfilerResourceType, callback: ProfilerCallback, config?: ProfilerConfig): Promise<void>-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [ProfilerResourceType](arkts-performanceanalysis-hidebug-profilerresourcetype-e.md) | 是 | 目标资源类型。 |
| callback | [ProfilerCallback](arkts-performanceanalysis-hidebug-profilercallback-t.md) | 是 | 回调函数。 |
| config | [ProfilerConfig](arkts-performanceanalysis-hidebug-profilerconfig-i.md) | 否 | 资源采集的配置。<br>默认值：所有配置参数使用默认值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
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
