# LongTask

表示长时任务。**LongTask**继承自
[Task](arkts-arkts-taskpool-execute-f.md#execute-1)。
长时任务不设置执行时间上限，长时间运行不会触发超时异常，但不支持将同一任务多次执行或者将该任务加入任务组（TaskGroup）。
执行长时任务的线程会持续存在，直到任务完成并调用[terminateTask](arkts-arkts-taskpool-terminatetask-f.md#terminateTask-1)后，该线程在空闲时被回收。

**继承/实现关系：** LongTask extends [Task](arkts-arkts-taskpool-task-c.md#Task)

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

