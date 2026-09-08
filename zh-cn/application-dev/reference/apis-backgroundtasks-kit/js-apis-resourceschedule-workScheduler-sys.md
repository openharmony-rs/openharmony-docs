# @ohos.resourceschedule.workScheduler (延迟任务调度)(系统接口)

<!--Kit: Background Tasks Kit-->
<!--Subsystem: ResourceSchedule-->
<!--Owner: @xufu7-->
<!--Designer: @zhouben25-->
<!--Tester: @leetestnady-->
<!--Adviser: @HelloCrease-->

本模块提供延迟任务注册、取消、查询的能力。在开发过程中，对于实时性要求不高的任务，可以调用本模块接口注册延迟任务，在系统空闲时根据性能、功耗、热等情况进行调度执行。

**起始版本：** 26.0.0

## 导入模块

```ts
import { workScheduler } from '@kit.BackgroundTasksKit';
```

## 常量

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

**系统接口：** 此接口为系统接口。

| 名称 | 类型 | 值 | 说明 |
| -------- | -------- | -------- | -------- |
| WORK_SCHEDULER_CONDITION | string | 'WORK_SCHEDULER_CONDITION' | 表示当前任务触发时满足的最后一个条件。可以作为workInfo.parameters的key值，在延迟任务调度回调接口[onWorkStart](js-apis-WorkSchedulerExtensionAbility.md#onworkstart)中使用。 |
| EXECUTE_IMMEDIATE | string | 'executeImmediate' | 表示请求的任务是否立即执行。可以作为workInfo.parameters的key值，在申请延迟任务接口[startWork](js-apis-resourceschedule-workScheduler.md#workschedulerstartwork)中使用。 |

## workScheduler.setExecFrequency

setExecFrequency(info: FrequencyInfo): void

设置应用所在活跃分组的执行频率。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**需要权限：** ohos.permission.SET_WORK_SCHEDULER_PROPERTY

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------- | ------- | ---- | ---------------------------------------- |
| info | [FrequencyInfo](#frequencyinfo) | 是    | 应用所在活跃分组的执行频率信息。|

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[workScheduler错误码](errorcode-workScheduler.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201 | Permission denied. |
| 202 | Not System App. |
| 9700003 | System service operation failed. |
| 9700006 | Failed to check the execution frequency parameters. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { workScheduler } from '@kit.BackgroundTasksKit';

let frequencyInfo: workScheduler.FrequencyInfo = {
  uid: 20020220,  // 该值为示例UID，开发者需自行替换为实际应用的真实UID
  workId: 1,  // 延迟任务ID
  interval: 86400000 // 单位为毫秒
}
try {
  workScheduler.setExecFrequency(frequencyInfo);
  console.info('workschedulerLog setExecFrequency success');
} catch (error) {
  console.error(`workschedulerLog setExecFrequency failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
}
```

## workScheduler.resetExecFrequency

resetExecFrequency(uid: number): void

重置应用所在活跃分组的执行频率。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**需要权限：** ohos.permission.SET_WORK_SCHEDULER_PROPERTY

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------- | ------- | ---- | ---------------------------------------- |
| uid | number | 是    | 由系统自动分配的UID。|

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[workScheduler错误码](errorcode-workScheduler.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201 | Permission denied. |
| 202 | Not System App. |
| 9700003 | System service operation failed. |
| 9700006 | Failed to check the execution frequency parameters. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { workScheduler } from '@kit.BackgroundTasksKit';

let uid: number = 20020220;  // 该值为示例UID，开发者需自行替换为实际应用的真实UID
try {
  workScheduler.resetExecFrequency(uid);
  console.info('workschedulerLog resetExecFrequency success');
} catch (error) {
  console.error(`workschedulerLog resetExecFrequency failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
}
```

## FrequencyInfo

执行频率的具体信息，用于设置应用所在活跃分组的执行频率。

FrequencyInfo作为参数设置时，uid、workId、interval为必填项。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

**系统接口：** 此接口为系统接口。

| 名称             | 类型                              | 只读   | 可选   | 说明               |
| --------------- | --------------------------------- | ---- | ---- | ---------------- |
| uid             | number                            | 否    | 否    |由系统自动分配的uid，取值限定为整数。          |
| workId          | number                            | 否    | 否    |用于任务调度系统的延迟任务ID，取值限定为整数。          |
| interval        | number                            | 否    | 否    |活跃分组执行频率，单位：ms，取值限定为整数，取值范围[7200000, 2147483647)。        |
