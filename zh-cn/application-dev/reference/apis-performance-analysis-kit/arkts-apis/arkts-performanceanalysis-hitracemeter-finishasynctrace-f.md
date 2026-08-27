# finishAsyncTrace

## 导入模块

```TypeScript
```

## finishAsyncTrace

```TypeScript
function finishAsyncTrace(level: HiTraceOutputLevel, name: string, taskId: number): void
```

标记一个异步跟踪耗时任务的结束，分级控制跟踪输出。finishAsyncTrace的level、name和taskId必须与流程开始的[startAsyncTrace()](arkts-performanceanalysis-hitracemeter-startasynctrace-f.md)对应参数值一致。

**起始版本：** 19

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.HiviewDFX.HiTrace

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| level | [HiTraceOutputLevel](arkts-performanceanalysis-hitracemeter-hitraceoutputlevel-e.md) | 是 | 跟踪输出级别，必须与流程开始的 [startAsyncTrace()](arkts-performanceanalysis-hitracemeter-startasynctrace-f.md)的level参数值一致。 |
| name | string | 是 | 要跟踪的任务名称，必须与流程开始的[startAsyncTrace()](arkts-performanceanalysis-hitracemeter-startasynctrace-f.md)的name 参数值一致。 |
| taskId | number | 是 | 任务id，必须与流程开始的[startAsyncTrace()](arkts-performanceanalysis-hitracemeter-startasynctrace-f.md)的taskId参数值一致。 |

**示例**

```TypeScript
const COMMERCIAL = hiTraceMeter.HiTraceOutputLevel.COMMERCIAL;
hiTraceMeter.finishAsyncTrace(COMMERCIAL, "myTestFunc", 1);
```

```TypeScript
const COMMERCIAL = hiTraceMeter.HiTraceOutputLevel.COMMERCIAL;
// 跟踪并行执行的同名任务
// 第一个跟踪的任务开始
hiTraceMeter.startAsyncTrace(COMMERCIAL, "myTestFunc", 1, "categoryTest", "key=value");
// 业务流程......
// 第二个跟踪的任务开始，同时第一个跟踪的同名任务还没结束，出现了并行执行，对应接口的taskId需要不同
hiTraceMeter.startAsyncTrace(COMMERCIAL, "myTestFunc", 2, "categoryTest", "key=value");
// 业务流程......
// 第一个跟踪的任务结束
hiTraceMeter.finishAsyncTrace(COMMERCIAL, "myTestFunc", 1);
// 业务流程......
// 第二个跟踪的任务结束
hiTraceMeter.finishAsyncTrace(COMMERCIAL, "myTestFunc", 2);
```

```TypeScript
const COMMERCIAL = hiTraceMeter.HiTraceOutputLevel.COMMERCIAL;
// 跟踪串行执行的同名任务
// 第一个跟踪的任务开始
hiTraceMeter.startAsyncTrace(COMMERCIAL, "myTestFunc", 1, "categoryTest", "key=value");
// 业务流程......
// 第一个跟踪的任务结束
hiTraceMeter.finishAsyncTrace(COMMERCIAL, "myTestFunc", 1);
// 业务流程......
// 第二个跟踪的同名任务开始，同名的待跟踪任务串行执行
hiTraceMeter.startAsyncTrace(COMMERCIAL, "myTestFunc", 1, "categoryTest", "key=value");
// 业务流程......
// 第二个跟踪的同名任务结束
hiTraceMeter.finishAsyncTrace(COMMERCIAL, "myTestFunc", 1);
```
