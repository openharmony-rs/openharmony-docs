# @ohos.hiTraceMeter(性能打点)

本模块提供了跟踪进程轨迹，度量程序执行性能的打点能力，支持异步耗时任务跟踪、同步耗时任务跟踪、整数变量跟踪等多种性能分析场景。本模块打点的数据供 HiTraceMeter工具分析使用，能够帮助开发者快速定位性能瓶颈，优化应用性能。详细开发流程请参考：[使用HiTraceMeter跟踪性能（ArkTS）](../../../dfx/hitracemeter-guidelines-arkts.md)。建议使用API version 19的性能打点接口，后续性能打点接口[startTrace()](arkts-performanceanalysis-hitracemeter-starttrace-f.md)、 [finishTrace()](arkts-performanceanalysis-hitracemeter-finishtrace-f.md)、[traceByValue()](arkts-performanceanalysis-hitracemeter-tracebyvalue-f.md)将逐步废弃。性能打点接口[startTrace()](arkts-performanceanalysis-hitracemeter-starttrace-f.md)、[finishTrace()](arkts-performanceanalysis-hitracemeter-finishtrace-f.md)、 [traceByValue()](arkts-performanceanalysis-hitracemeter-tracebyvalue-f.md)固定使用COMMERCIAL级别。  
[用户态trace格式](../../../dfx/hitracemeter-view.md#用户态trace格式说明)使用竖线 `|` 作为分隔符，所以通过性能打点接口传递的字符串 类型参数应避免包含该字符，防止trace解析异常。  
[用户态trace](../../../dfx/hitracemeter-view.md#用户态trace格式说明)总长度限制512字符，超过的部分将会被截断。

**起始版本：** 8

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## 导入模块

```TypeScript
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [finishAsyncTrace(性能打点)](arkts-performanceanalysis-hitracemeter-finishasynctrace-f.md) | 标记一个异步跟踪耗时任务的结束，分级控制跟踪输出。finishAsyncTrace的level、name和taskId必须与流程开始的[startAsyncTrace()](arkts-performanceanalysis-hitracemeter-startasynctrace-f.md)对应参数值一致。 |
| [finishSyncTrace(性能打点)](arkts-performanceanalysis-hitracemeter-finishsynctrace-f.md) | 标记一个同步跟踪耗时任务的结束，分级控制跟踪输出。finishSyncTrace的level必须与流程开始的[startSyncTrace()](arkts-performanceanalysis-hitracemeter-startsynctrace-f.md)对应参数值一致。 |
| [finishTrace(性能打点)](arkts-performanceanalysis-hitracemeter-finishtrace-f.md) | 标记一个异步跟踪耗时任务的结束。调用成功后，完成该任务的跟踪。finishTrace的name和taskId必须与流程开始的[startTrace()](arkts-performanceanalysis-hitracemeter-starttrace-f.md)对应参数值一致。从API version 19开始，建议使用[finishAsyncTrace()](arkts-performanceanalysis-hitracemeter-finishasynctrace-f.md)接口（需与 [startAsyncTrace()](arkts-performanceanalysis-hitracemeter-startasynctrace-f.md)接口配套使用）。 |
| [isTraceEnabled(性能打点)](arkts-performanceanalysis-hitracemeter-istraceenabled-f.md) | 判断当前是否开启应用trace捕获。 |
| [registerTraceListener(性能打点)](arkts-performanceanalysis-hitracemeter-registertracelistener-f.md) | 注册应用trace捕获开关通知回调，使用callback异步回调。注册成功后，立即执行一次回调函数，后续回调函数由应用trace捕获开关状态变化触发执行。回调函数保存在应用进程内，一个进程最多可以注册10个回调函数。若注册的回调包含耗时操作，当回调被执行时，注册或注销行为会被阻塞 （等待回调执行完成）。因此，建议不要在应用主线程中注册或注销包含耗时操作的回调，避免发生应用冻屏。 |
| [startAsyncTrace(性能打点)](arkts-performanceanalysis-hitracemeter-startasynctrace-f.md) | 标记一个异步跟踪耗时任务的开始，分级控制跟踪输出。如果有多个相同name的任务需要跟踪或者对同一个任务要跟踪多次，并且任务同时被执行，则开发者每次调用startAsyncTrace传入的taskId需不同。如果具有相同name的任务是串行执行的，则taskId可以相同。具体示例可参考[finishAsyncTrace()](arkts-performanceanalysis-hitracemeter-finishasynctrace-f.md) 中的示例。 |
| [startSyncTrace(性能打点)](arkts-performanceanalysis-hitracemeter-startsynctrace-f.md) | 标记一个同步跟踪耗时任务的开始，分级控制跟踪输出。适用于需要跟踪同步代码块执行耗时的场景，能够帮助开发者定位同步操作的耗时问题，优化应用响应 速度。具体示例可参考[finishSyncTrace()](arkts-performanceanalysis-hitracemeter-finishsynctrace-f.md)中的示例。 |
| [startTrace(性能打点)](arkts-performanceanalysis-hitracemeter-starttrace-f.md) | 标记一个异步跟踪耗时任务的开始。调用成功后，创建一条异步跟踪记录。如果有多个相同name的任务需要跟踪或者对同一个任务要跟踪多次，并且任务同时被执行，则开发者每次调用startTrace传入的taskId需不同。如果具有相同name的任务是串行执行的，则taskId可以相同。具体示例可参考[finishTrace()](arkts-performanceanalysis-hitracemeter-finishtrace-f.md)中的示例。从API version 19开始，建议使用[startAsyncTrace()](arkts-performanceanalysis-hitracemeter-startasynctrace-f.md)接口（需与 [finishAsyncTrace()](arkts-performanceanalysis-hitracemeter-finishasynctrace-f.md)接口配套使用），以便分级控制跟踪输出与跟踪聚类。 |
| [traceByValue(性能打点)](arkts-performanceanalysis-hitracemeter-tracebyvalue-f.md) | 用来标记一个跟踪的整数变量，该变量的数值会不断变化。适用于需要实时监控数值变化（如网络请求次数、缓存命中率、内存占用等）的场景，能够帮助开发者 快速发现异常波动，分析数据趋势。从API version 19开始，建议使用 [traceByValue](arkts-performanceanalysis-hitracemeter-tracebyvalue-f.md)接口，以便分级控 制跟踪输出。 |
| [traceByValue(性能打点)](arkts-performanceanalysis-hitracemeter-tracebyvalue-f.md) | 整数跟踪事件，分级控制跟踪输出。用来标记一个预先定义需要跟踪的整数变量名及整数值。 |
| [unregisterTraceListener(性能打点)](arkts-performanceanalysis-hitracemeter-unregistertracelistener-f.md) | 注销通过registerTraceListener()注册的trace捕获开关通知回调函数。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [HiTraceOutputLevel(性能打点)](arkts-performanceanalysis-hitracemeter-hitraceoutputlevel-e.md) | 枚举，跟踪输出级别。低于系统跟踪输出级别阈值的打点将不会生效。log版本阈值为INFO；nolog版本阈值为COMMERCIAL。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [TraceEventListener(性能打点)](arkts-performanceanalysis-hitracemeter-traceeventlistener-t.md) | 定义应用trace捕获开关状态切换时的回调函数类型。 |
