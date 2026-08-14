# finishTrace

## finishTrace

```TypeScript
function finishTrace(name: string, taskId: int): void
```

标记一个异步跟踪耗时任务的结束。调用成功后，完成该任务的跟踪。 finishTrace的name和taskId必须与流程开始的[startTrace()](arkts-performanceanalysis-hitracemeter-starttrace-f.md#startTrace)对应参数值一致。 从API version 19开始，建议使用[finishAsyncTrace()](arkts-performanceanalysis-hitracemeter-finishasynctrace-f.md#finishAsyncTrace)接口（需与 [startAsyncTrace()](arkts-performanceanalysis-hitracemeter-startasynctrace-f.md#startAsyncTrace)接口配套使用）。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-hiTraceMeter-function finishTrace(name: string, taskId: int): void--><!--Device-hiTraceMeter-function finishTrace(name: string, taskId: int): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiTrace

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 要跟踪的任务名称，必须与流程开始的[startTrace()](arkts-performanceanalysis-hitracemeter-starttrace-f.md#startTrace)对应参数值一致。 |
| taskId | int | 是 | 任务id，必须与流程开始的[startTrace()](arkts-performanceanalysis-hitracemeter-starttrace-f.md#startTrace)对应参数值一致。 |

## 示例

```TypeScript
// 跟踪并行执行的同名任务
hiTraceMeter.startTrace("myTestFunc", 1);
// 业务流程...... 
hiTraceMeter.startTrace("myTestFunc", 2);  // 第二个跟踪的任务开始，同时第一个跟踪的同名任务还没结束，出现了并行执行，需要不同的taskId来区分不同的任务。
// 业务流程...... 
hiTraceMeter.finishTrace("myTestFunc", 1);
// 业务流程...... 
hiTraceMeter.finishTrace("myTestFunc", 2);
```

```TypeScript
// 跟踪串行执行的同名任务
hiTraceMeter.startTrace("myTestFunc", 1);
// 业务流程...... 
hiTraceMeter.finishTrace("myTestFunc", 1);  // 第一个跟踪的任务结束
// 业务流程...... 
hiTraceMeter.startTrace("myTestFunc", 1);   // 第二个跟踪的同名任务开始，同名的待跟踪任务串行执行。
// 业务流程...... 
hiTraceMeter.finishTrace("myTestFunc", 1);
```

