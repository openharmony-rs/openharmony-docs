# @ohos.resourceschedule.workScheduler (延迟任务调度)

<!--Kit: Background Tasks Kit-->
<!--Subsystem: ResourceSchedule-->
<!--Owner: @xufu7-->
<!--Designer: @zhouben25-->
<!--Tester: @leetestnady-->
<!--Adviser: @HelloCrease-->

本模块提供延迟任务注册、取消、查询的能力。在开发过程中，对于实时性要求不高的任务，可以调用本模块接口注册延迟任务，在系统空闲时根据性能、功耗、热等情况进行调度执行。

>  **说明：**
>
>  本模块首批接口从API version 26.0.0开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
>  本模块接口仅可在Stage模型下使用。

## 导入模块

```ts
import { workScheduler } from '@kit.BackgroundTasksKit';
```

## 常量

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

**系统接口：** 此接口为系统接口。

| 名称 | 类型 | 值 | 说明 |
| -------- | -------- | -------- | -------- |
| WORK_SCHEDULER_CONDITION | string | 'WORK_SCHEDULER_CONDITION' | 常量字符串WORK_SCHEDULER_CONDITION，表示当前任务触发时满足的最后一个条件。可以作为workInfo.parameters的key值，在延迟任务调度回调接口onWorkStart中使用。 |
| EXECUTE_IMMEDIATE | string | 'executeImmediate' | 常量字符串executeImmediate，表示请求的任务是否立即执行。可以作为workInfo.parameters的key值，在申请延迟任务接口startWork中使用。 |