# startTrace

## startTrace

```TypeScript
function startTrace(name: string, taskId: number, expectedTime?: number): void
```

标记一个时间片跟踪任务的开始。 如果有多个相同name的任务需要追踪或者对同一个任务要追踪多次，并且这些跟踪任务会同时被执行，则每次调用startTrace的taskId必须不一致。如果 具有相同name的跟踪任务是串行执行的，则taskId可以相同。在下面bytrace.finishTrace的示例中会举例说明。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 8

**替代接口：** startTrace

<!--Device-bytrace-function startTrace(name: string, taskId: number, expectedTime?: number): void--><!--Device-bytrace-function startTrace(name: string, taskId: number, expectedTime?: number): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiTrace

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 时间片跟踪任务名称。 |
| taskId | number | 是 | 时间片跟踪任务id。 |
| expectedTime | number | 否 | 期望的耗时时间（单位：ms）。设置该值后，系统会在实际执行时间超过期望值时产生性能警告。可选，默认为空 表示不产生警告。 |

## 示例

```TypeScript
bytrace.startTrace("myTestFunc", 1);
bytrace.startTrace("myTestFunc", 1, 5); // 从startTrace到finishTrace流程的期望耗时为5ms
```

