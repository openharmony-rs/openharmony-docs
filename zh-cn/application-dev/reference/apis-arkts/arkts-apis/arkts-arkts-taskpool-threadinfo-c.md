# ThreadInfo

工作线程的内部信息。

**起始版本：** 10

<!--Device-taskpool-class ThreadInfo--><!--Device-taskpool-class ThreadInfo-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { taskpool } from '@kit.ArkTS';
```

## priority

```TypeScript
priority?: Priority
```

当前线程的优先级。如果返回为空，表示当前没有任务执行。不建议修改此值。

**类型：** Priority

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ThreadInfo-priority?: Priority--><!--Device-ThreadInfo-priority?: Priority-End-->

**系统能力：** SystemCapability.Utils.Lang

## taskIds

```TypeScript
taskIds?: number[]
```

在当前线程上运行的任务ID列表。如果返回为空，表示当前没有任务执行。不建议修改此值。

**类型：** number[]

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ThreadInfo-taskIds?: number[]--><!--Device-ThreadInfo-taskIds?: number[]-End-->

**系统能力：** SystemCapability.Utils.Lang

## tid

```TypeScript
tid: number
```

工作线程的标识符。如果返回为空，表示当前没有任务执行。不建议修改此值。

**类型：** number

**默认值：** 0

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ThreadInfo-tid: number--><!--Device-ThreadInfo-tid: number-End-->

**系统能力：** SystemCapability.Utils.Lang

