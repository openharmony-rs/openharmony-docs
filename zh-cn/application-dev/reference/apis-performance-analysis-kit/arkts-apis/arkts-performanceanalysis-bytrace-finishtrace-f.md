# finishTrace

## finishTrace

```TypeScript
function finishTrace(name: string, taskId: number): void
```

标记一个时间片跟踪事件的结束。 > **说明：** > > finishTrace的name和taskId必须与流程开始的startTrace对应参数值一致。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 8

**替代接口：** finishTrace

<!--Device-bytrace-function finishTrace(name: string, taskId: number): void--><!--Device-bytrace-function finishTrace(name: string, taskId: number): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiTrace

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 时间片跟踪任务名称，必须与startTrace调用时的name参数值一致。 |
| taskId | number | 是 | 时间片跟踪任务id，必须与startTrace调用时的taskId参数值一致。 |

## 示例

```TypeScript
bytrace.finishTrace("myTestFunc", 1);
```

```TypeScript
// 跟踪并行执行的同名任务
bytrace.startTrace("myTestFunc", 1);
// 业务流程...... 
bytrace.startTrace("myTestFunc", 2);  // 第二个跟踪任务开始，同时第一个同名跟踪任务还没结束，出现了并行执行，对应接口的taskId需要不同
// 业务流程...... 
bytrace.finishTrace("myTestFunc", 1);
// 业务流程...... 
bytrace.finishTrace("myTestFunc", 2);
```

```TypeScript
// 跟踪串行执行的同名任务
bytrace.startTrace("myTestFunc", 1);
// 业务流程...... 
bytrace.finishTrace("myTestFunc", 1);  // 第一个跟踪任务结束
// 业务流程...... 
bytrace.startTrace("myTestFunc", 1);   // 第二个跟踪任务开始，同名跟踪任务串行执行
// 业务流程...... 
bytrace.finishTrace("myTestFunc", 1);
```

