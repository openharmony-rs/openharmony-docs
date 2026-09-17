# applyEfficiencyResources (System API)

## Modules to Import

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
```

## applyEfficiencyResources

```TypeScript
function applyEfficiencyResources(request: EfficiencyResourcesRequest): void
```

Requests efficiency resources.

**Since:** 9

**System capability:** SystemCapability.ResourceSchedule.BackgroundTaskManager.EfficiencyResourcesApply

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| request | [EfficiencyResourcesRequest](arkts-backgroundtasks-backgroundtaskmanager-efficiencyresourcesrequest-i-sys.md) | Yes | Necessary information carried in the request, including the resource type and timeout interval. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System App. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameters types; 3. Parameter verification failed. |
| [9800001](../errorcode-backgroundTaskMgr.md#9800001-memory-operation-failure) | Memory operation failed. |
| [9800002](../errorcode-backgroundTaskMgr.md#9800002-parcel-operation-failure) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters;<br> 2. Failed to apply for memory. |
| [9800003](../errorcode-backgroundTaskMgr.md#9800003-ipc-failure) | Internal transaction failed. |
| [9800004](../errorcode-backgroundTaskMgr.md#9800004-system-service-failure) | System service operation failed. |
| [18700001](../errorcode-backgroundTaskMgr.md#18700001-caller-information-verification-failure-for-an-energy-resource-request) | Caller information verification failed for an energy resource request. |

**Examples**

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';  
import { BusinessError } from '@kit.BasicServicesKit';

let request: backgroundTaskManager.EfficiencyResourcesRequest = {
    resourceTypes: backgroundTaskManager.ResourceType.CPU,
    isApply: true,
    timeOut: 0,
    reason: "apply",
    isPersist: true,
    isProcess: false,
    cpuLevel: backgroundTaskManager.EfficiencyResourcesCpuLevel.SMALL_CPU // The application's background task runs on the small CPU core. This parameter is supported since API version 23.
};
try {
    backgroundTaskManager.applyEfficiencyResources(request);
    console.info("applyEfficiencyResources success. ");
} catch (error) {
    console.error(`applyEfficiencyResources failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
}
```
