# @ohos.resourceschedule.workScheduler (Deferred Task Scheduling) (System API)

<!--Kit: Background Tasks Kit-->
<!--Subsystem: ResourceSchedule-->
<!--Owner: @xufu7-->
<!--Designer: @zhouben25-->
<!--Tester: @leetestnady-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=289448f9e8c34d626462a3c44c66800818efaf3a translatedAt=2026-09-15T13:37:52.112Z pushedAt=2026-09-17T08:49:03.601Z -->

This module provides the APIs for registering, canceling, and querying deferred tasks. You can use the APIs to register tasks that do not have high requirements on real-time performance as deferred tasks. The system schedules and executes the deferred tasks when the system is idle, based on performance, power consumption, temperature, and other conditions.

**Since:** 26.0.0

## Modules to Import

```ts
import { workScheduler } from '@kit.BackgroundTasksKit';
```

## Constants

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.ResourceSchedule.WorkScheduler

**System API:** This is a system API.

| Name| Type| Value| Description|
| -------- | -------- | -------- | -------- |
| WORK_SCHEDULER_CONDITION | string | 'WORK_SCHEDULER_CONDITION' | Last condition that must be met to trigger the current task. This parameter can be used in [onWorkStart](js-apis-WorkSchedulerExtensionAbility.md#onworkstart) as a key of **workInfo.parameters**.|
| EXECUTE_IMMEDIATE | string | 'executeImmediate' | Whether the requested task is executed immediately. This parameter can be used in [startWork](js-apis-resourceschedule-workScheduler.md#workschedulerstartwork) as a key of **workInfo.parameters**.|

## workScheduler.setExecFrequency

setExecFrequency(info: FrequencyInfo): void

Sets the execution frequency based on the app activity group.

**Since:** 26.0.1

**Model restriction**: This API can be used only in the stage model.

**Required permissions:** ohos.permission.SET_WORK_SCHEDULER_PROPERTY

**System capability**: SystemCapability.ResourceSchedule.WorkScheduler

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| ------- | ------- | ---- | ---------------------------------------- |
| info | [FrequencyInfo](#frequencyinfo) | Yes | Execution frequency information based on the app activity group. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [workScheduler Error Codes](errorcode-workScheduler.md).

| ID  | Error Message             |
| ---- | --------------------- |
| 201 | Permission denied. |
| 202 | Not System App. |
| 9700003 | System service operation failed. |
| 9700006 | Failed to check the execution frequency parameters. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { workScheduler } from '@kit.BackgroundTasksKit';

let frequencyInfo: workScheduler.FrequencyInfo = {
  uid: 20020220,  // This value is an example UID. Replace it with the actual UID of your app.
  workId: 1,  // ID of the deferred task
  interval: 86400000 // The unit is millisecond.
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

Resets the execution frequency based on the app activity group.

**Since:** 26.0.1

**Model restriction**: This API can be used only in the stage model.

**Required permissions:** ohos.permission.SET_WORK_SCHEDULER_PROPERTY

**System capability**: SystemCapability.ResourceSchedule.WorkScheduler

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| ------- | ------- | ---- | ---------------------------------------- |
| uid | number | Yes    | UID automatically allocated by the system.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [workScheduler Error Codes](errorcode-workScheduler.md).

| ID  | Error Message             |
| ---- | --------------------- |
| 201 | Permission denied. |
| 202 | Not System App. |
| 9700003 | System service operation failed. |
| 9700006 | Failed to check the execution frequency parameters. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { workScheduler } from '@kit.BackgroundTasksKit';

let uid: number = 20020220;  // This value is an example UID. Replace it with the actual UID of your app.
try {
  workScheduler.resetExecFrequency(uid);
  console.info('workschedulerLog resetExecFrequency success');
} catch (error) {
  console.error(`workschedulerLog resetExecFrequency failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
}
```

## FrequencyInfo

Describes the specific information used to set the execution frequency based on the app activity group.

When **FrequencyInfo** is used to set the execution frequency, **uid**, **workId**, and **interval** are mandatory.





**Since:** 26.0.1

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ResourceSchedule.WorkScheduler

**System API**: This is a system API.

| Name             | Type                              | Read-Only   | Optional   | Description               |
| --------------- | --------------------------------- | ---- | ---- | ---------------- |
| uid             | number                            | No    | No    | UID automatically allocated by the system. The value is an integer.          |
| workId          | number                            | No    | No    | ID of the deferred task in the task scheduling system. The value is an integer.         |
| interval        | number                            | No    | No    | Execution frequency of an active group, in milliseconds. The value is an integer within the range of [7200000, 2147483647).        |
