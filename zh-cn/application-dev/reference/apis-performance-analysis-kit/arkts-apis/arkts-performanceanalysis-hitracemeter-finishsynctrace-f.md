# finishSyncTrace

## finishSyncTrace

```TypeScript
function finishSyncTrace(level: HiTraceOutputLevel): void
```

标记一个同步跟踪耗时任务的结束，分级控制跟踪输出。 finishSyncTrace的level必须与流程开始的[startSyncTrace()](arkts-performanceanalysis-hitracemeter-startsynctrace-f.md#startSyncTrace)对应参数值一致。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-hiTraceMeter-function finishSyncTrace(level: HiTraceOutputLevel): void--><!--Device-hiTraceMeter-function finishSyncTrace(level: HiTraceOutputLevel): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiTrace

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| level | [HiTraceOutputLevel](arkts-performanceanalysis-hitracemeter-hitraceoutputlevel-e.md) | 是 | 跟踪输出级别。 |

## 示例

```TypeScript
const COMMERCIAL = hiTraceMeter.HiTraceOutputLevel.COMMERCIAL;
hiTraceMeter.finishSyncTrace(COMMERCIAL);
```

```TypeScript
const COMMERCIAL = hiTraceMeter.HiTraceOutputLevel.COMMERCIAL;
// 可嵌套使用，相邻的startSyncTrace与finishSyncTrace匹配
// 第一个跟踪的任务开始
hiTraceMeter.startSyncTrace(COMMERCIAL, "myTestFunc1", "key=value");
// 业务流程......
// 第二个跟踪的任务开始
hiTraceMeter.startSyncTrace(COMMERCIAL, "myTestFunc2", "key=value");
// 业务流程......
// 第二个跟踪的任务结束
hiTraceMeter.finishSyncTrace(COMMERCIAL);
// 业务流程......
// 第一个跟踪的任务结束
hiTraceMeter.finishSyncTrace(COMMERCIAL);
```

