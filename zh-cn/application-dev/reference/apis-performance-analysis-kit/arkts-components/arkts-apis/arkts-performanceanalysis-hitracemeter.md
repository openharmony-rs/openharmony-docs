# @ohos.hiTraceMeter(性能打点)

本模块提供了跟踪进程轨迹，度量程序执行性能的打点能力，支持异步耗时任务跟踪、同步耗时任务跟踪、整数变量跟踪等多种性能分析场景。本模块打点的数据供HiTraceMeter工具分析使用，能够帮助开发者快速定位性能瓶颈，优化应用性能。

详细开发流程请参考：[使用HiTraceMeter跟踪性能（ArkTS）](../../../dfx/hitracemeter-guidelines-arkts.md)。

建议使用API version 19的性能打点接口，后续性能打点接口[startTrace()](arkts-performanceanalysis-hitracemeter-starttrace-f.md)、[finishTrace()](arkts-performanceanalysis-hitracemeter-finishtrace-f.md)、[traceByValue()](arkts-performanceanalysis-hitracemeter-tracebyvalue-f.md)将逐步废弃。

性能打点接口[startTrace()](arkts-performanceanalysis-hitracemeter-starttrace-f.md)、[finishTrace()](arkts-performanceanalysis-hitracemeter-finishtrace-f.md)、[traceByValue()](arkts-performanceanalysis-hitracemeter-tracebyvalue-f.md)固定使用COMMERCIAL级别。

[用户态trace格式](../../../dfx/hitracemeter-view.md#用户态trace格式说明)使用竖线 `|` 作为分隔符，所以通过性能打点接口传递的字符串类型参数应避免包含该字符，防止trace解析异常。

[用户态trace](../../../dfx/hitracemeter-view.md#用户态trace格式说明)总长度限制512字符，超过的部分将会被截断。

**起始版本：** 8

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## 导入模块

```TypeScript
import { hiTraceMeter } from '@kit.PerformanceAnalysisKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [finishAsyncTrace](arkts-performanceanalysis-hitracemeter-finishasynctrace-f.md) | 标记一个异步跟踪耗时任务的结束，分级控制跟踪输出。 |
| [finishSyncTrace](arkts-performanceanalysis-hitracemeter-finishsynctrace-f.md) | 标记一个同步跟踪耗时任务的结束，分级控制跟踪输出。 |
| [finishTrace](arkts-performanceanalysis-hitracemeter-finishtrace-f.md) | 标记一个异步跟踪耗时任务的结束。调用成功后，完成该任务的跟踪。 |
| [isTraceEnabled](arkts-performanceanalysis-hitracemeter-istraceenabled-f.md) | 判断当前是否开启应用trace捕获。 |
| [registerTraceListener](arkts-performanceanalysis-hitracemeter-registertracelistener-f.md) | 注册应用trace捕获开关通知回调，使用callback异步回调。 |
| [startAsyncTrace](arkts-performanceanalysis-hitracemeter-startasynctrace-f.md) | 标记一个异步跟踪耗时任务的开始，分级控制跟踪输出。 |
| [startSyncTrace](arkts-performanceanalysis-hitracemeter-startsynctrace-f.md) | 标记一个同步跟踪耗时任务的开始，分级控制跟踪输出。适用于需要跟踪同步代码块执行耗时的场景，能够帮助开发者定位同步操作的耗时问题，优化应用响应速度。具体示例可参考[finishSyncTrace()](arkts-performanceanalysis-hitracemeter-finishsynctrace-f.md)中的示例。 |
| [startTrace](arkts-performanceanalysis-hitracemeter-starttrace-f.md) | 标记一个异步跟踪耗时任务的开始。调用成功后，创建一条异步跟踪记录。 |
| [traceByValue](arkts-performanceanalysis-hitracemeter-tracebyvalue-f.md) | 用来标记一个跟踪的整数变量，该变量的数值会不断变化。适用于需要实时监控数值变化（如网络请求次数、缓存命中率、内存占用等）的场景，能够帮助开发者快速发现异常波动，分析数据趋势。 |
| [traceByValue](arkts-performanceanalysis-hitracemeter-tracebyvalue-f.md) | 整数跟踪事件，分级控制跟踪输出。用来标记一个预先定义需要跟踪的整数变量名及整数值。 |
| [unregisterTraceListener](arkts-performanceanalysis-hitracemeter-unregistertracelistener-f.md) | 注销通过registerTraceListener()注册的trace捕获开关通知回调函数。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [HiTraceOutputLevel](arkts-performanceanalysis-hitracemeter-hitraceoutputlevel-e.md) | 枚举，跟踪输出级别。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [TraceEventListener](arkts-performanceanalysis-hitracemeter-traceeventlistener-t.md) | 定义应用trace捕获开关状态切换时的回调函数类型。 |
