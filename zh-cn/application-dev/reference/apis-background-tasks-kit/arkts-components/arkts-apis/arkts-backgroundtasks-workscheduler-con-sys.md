# 常量（系统接口）

## EXECUTE_IMMEDIATE

```TypeScript
const EXECUTE_IMMEDIATE: string
```

表示请求的任务是否立即执行。可以作为workInfo.parameters的key值，在申请延迟任务接口[startWork](arkts-backgroundtasks-workscheduler-startwork-f.md)中使用。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

**系统接口：** 此接口为系统接口。

## WORK_SCHEDULER_CONDITION

```TypeScript
const WORK_SCHEDULER_CONDITION: string
```

当前任务触发时满足的最后一个条件。可以作为workInfo.parameters的key值，在延迟任务调度回调接口[onWorkStart](arkts-backgroundtasks-workschedulerextensionability-c.md#onworkstart)中使用。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

**系统接口：** 此接口为系统接口。
