# @ohos.resourceschedule.workScheduler

本模块提供延迟任务注册、取消、查询的能力。在开发过程中，对于实时性要求不高的任务，可以调用本模块接口注册延迟任务，在系统空闲时根据性能、功耗、热等情况进行调度执行。开发指导请参考[延迟任务开发指南](../../../../task-management/work-scheduler.md)。

**起始版本：** 9

<!--Device-unnamed-declare namespace workScheduler--><!--Device-unnamed-declare namespace workScheduler-End-->

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

## 导入模块

```TypeScript
import { workScheduler } from '@kit.BackgroundTasksKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getWorkStatus](arkts-backgroundtasks-workscheduler-getworkstatus-f.md#getworkstatus-1) | 通过workId获取延迟任务，使用Callback异步回调。 |
| [getWorkStatus](arkts-backgroundtasks-workscheduler-getworkstatus-f.md#getworkstatus-2) | 通过workId获取延迟任务，使用Promise异步回调。 |
| [isLastWorkTimeOut](arkts-backgroundtasks-workscheduler-islastworktimeout-f.md#islastworktimeout-1) | 检查延迟任务的最后一次执行是否超时，使用Callback异步回调。 |
| [isLastWorkTimeOut](arkts-backgroundtasks-workscheduler-islastworktimeout-f.md#islastworktimeout-2) | 检查延迟任务的最后一次执行是否超时，使用Callback异步回调。 |
| [isLastWorkTimeOut](arkts-backgroundtasks-workscheduler-islastworktimeout-f.md#islastworktimeout-3) | 检查延迟任务的最后一次执行是否超时，使用Promise异步回调。 |
| [obtainAllWorks](arkts-backgroundtasks-workscheduler-obtainallworks-f.md#obtainallworks-1) | 获取当前应用所有的延迟任务，使用Callback异步回调。 |
| [obtainAllWorks](arkts-backgroundtasks-workscheduler-obtainallworks-f.md#obtainallworks-2) | 获取当前应用所有的延迟任务，使用Callback异步回调。 |
| [obtainAllWorks](arkts-backgroundtasks-workscheduler-obtainallworks-f.md#obtainallworks-3) | 获取当前应用所有的延迟任务，使用Promise异步回调。 |
| [startWork](arkts-backgroundtasks-workscheduler-startwork-f.md#startwork-1) | 申请延迟任务，成功后会把任务添加到执行队列，满足触发条件后由系统调度执行。 |
| [stopAndClearWorks](arkts-backgroundtasks-workscheduler-stopandclearworks-f.md#stopandclearworks-1) | 停止和取消当前应用所有的延迟任务。 |
| [stopWork](arkts-backgroundtasks-workscheduler-stopwork-f.md#stopwork-1) | 取消延迟任务。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [WorkInfo](arkts-backgroundtasks-workscheduler-workinfo-i.md) | 延迟任务的具体信息, 用于设置延迟任务的触发条件等。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [BatteryStatus](arkts-backgroundtasks-workscheduler-batterystatus-e.md) | 触发延迟任务回调的电池状态。 |
| [ChargingType](arkts-backgroundtasks-workscheduler-chargingtype-e.md) | 触发延迟任务回调的充电类型。 |
| [NetworkType](arkts-backgroundtasks-workscheduler-networktype-e.md) | 触发延迟任务回调的网络类型。 |
| [StorageRequest](arkts-backgroundtasks-workscheduler-storagerequest-e.md) | 触发延迟任务回调的存储状态。 |

<!--Del-->
### 常量（系统接口）

| 名称 | 说明 |
| --- | --- |
| [EXECUTE_IMMEDIATE](arkts-backgroundtasks-workscheduler-con-sys.md#execute_immediate) | 请求的任务是否立即执行。 |
| [WORK_SCHEDULER_CONDITION](arkts-backgroundtasks-workscheduler-con-sys.md#work_scheduler_condition) | 当前任务触发时满足的最后一个条件。 |
<!--DelEnd-->

