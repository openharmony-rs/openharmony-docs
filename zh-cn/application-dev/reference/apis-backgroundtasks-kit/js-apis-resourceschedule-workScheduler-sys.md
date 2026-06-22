# @ohos.resourceschedule.workScheduler (延迟任务调度)(系统接口)

<!--Kit: Background Tasks Kit-->
<!--Subsystem: ResourceSchedule-->
<!--Owner: @xufu7-->
<!--Designer: @zhouben25-->
<!--Tester: @leetestnady-->
<!--Adviser: @HelloCrease-->

本模块提供延迟任务注册、取消、查询的能力。在开发过程中，对于实时性要求不高的任务，可以调用本模块接口注册延迟任务，在系统空闲时根据性能、功耗、热等情况进行调度执行。

>  **说明：**
> 
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

## 导入模块

```ts
import { workScheduler } from '@kit.BackgroundTasksKit';
```

## 常量

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

**系统接口：** 此接口为系统接口。

| 名称 | 类型 | 值 | 说明 |
| -------- | -------- | -------- | -------- |
| WORK_SCHEDULER_CONDITION | string | 'WORK_SCHEDULER_CONDITION' | 表示当前任务触发时满足的最后一个条件。可以作为workInfo.parameters的key值，在延迟任务调度回调接口[onWorkStart](js-apis-WorkSchedulerExtensionAbility.md#onworkstart)中使用。 |
| EXECUTE_IMMEDIATE | string | 'executeImmediate' | 表示请求的任务是否立即执行。可以作为workInfo.parameters的key值，在申请延迟任务接口[startWork](js-apis-resourceschedule-workScheduler.md#workschedulerstartwork)中使用。 |