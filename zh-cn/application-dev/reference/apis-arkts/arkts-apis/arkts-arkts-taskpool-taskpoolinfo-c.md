# TaskPoolInfo

任务池的内部信息。

**起始版本：** 10

<!--Device-taskpool-class TaskPoolInfo--><!--Device-taskpool-class TaskPoolInfo-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { taskpool } from '@kit.ArkTS';
```

## taskInfos

```TypeScript
taskInfos: TaskInfo[]
```

任务的内部信息。不建议修改此值。

**类型：** TaskInfo[]

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TaskPoolInfo-taskInfos: TaskInfo[]--><!--Device-TaskPoolInfo-taskInfos: TaskInfo[]-End-->

**系统能力：** SystemCapability.Utils.Lang

## threadInfos

```TypeScript
threadInfos: ThreadInfo[]
```

工作线程的内部信息。不建议修改此值。

**类型：** ThreadInfo[]

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TaskPoolInfo-threadInfos: ThreadInfo[]--><!--Device-TaskPoolInfo-threadInfos: ThreadInfo[]-End-->

**系统能力：** SystemCapability.Utils.Lang

