# setExecFrequency (System API)

## Modules to Import

```TypeScript
import { workScheduler } from '@kit.BackgroundTasksKit';
```

## setExecFrequency

```TypeScript
function setExecFrequency(info: FrequencyInfo): void
```

Set the execution frequency.

**Since:** 26.0.1

**Required permissions:** ohos.permission.SET_WORK_SCHEDULER_PROPERTY

**Model restriction:** This API can be used only in the stage model.

<!--Device-workScheduler-function setExecFrequency(info: FrequencyInfo): void--><!--Device-workScheduler-function setExecFrequency(info: FrequencyInfo): void-End-->

**System capability:** SystemCapability.ResourceSchedule.WorkScheduler

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [FrequencyInfo](arkts-backgroundtasks-workscheduler-frequencyinfo-i-sys.md) | Yes | Execution frequency information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [9700003](../errorcode-workScheduler.md#9700003-system-service-failure) | System service operation failed. |
| [9700006](../errorcode-workScheduler.md#9700006-failed-to-verify-the-execution-frequency-parameters) | Failed to check the execution frequency parameters. |
