# transient_task_api.h

## Overview

Declares the APIs for Transient task management.

**Library**: libtransient_task.so

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

**Since**: 13

**Related module**: [TransientTask](capi-transienttask.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [int32_t OH_BackgroundTaskManager_RequestSuspendDelay(const char* reason, TransientTask_Callback callback, TransientTask_DelaySuspendInfo *info)](#oh_backgroundtaskmanager_requestsuspenddelay) | Requests a transient task. |
| [int32_t OH_BackgroundTaskManager_GetRemainingDelayTime(int32_t requestId, int32_t *delayTime)](#oh_backgroundtaskmanager_getremainingdelaytime) | Obtains the remaining time of a transient task. |
| [int32_t OH_BackgroundTaskManager_CancelSuspendDelay(int32_t requestId)](#oh_backgroundtaskmanager_cancelsuspenddelay) | Cancels a transient task. |
| [int32_t OH_BackgroundTaskManager_GetTransientTaskInfo(TransientTask_TransientTaskInfo *transientTaskInfo)](#oh_backgroundtaskmanager_gettransienttaskinfo) | Obtains all information about a transient task, including the remaining quota of the current day. |

## Function description

### OH_BackgroundTaskManager_RequestSuspendDelay()

```c
int32_t OH_BackgroundTaskManager_RequestSuspendDelay(const char* reason, TransientTask_Callback callback, TransientTask_DelaySuspendInfo *info)
```

**Description**

Requests a transient task.

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* reason | Reason for requesting the transient task. |
| TransientTask_Callback callback | Callback used to notify the application that the transient task is about to time out. Generally, the callback is invoked 6 seconds before the timeout. |
| TransientTask_DelaySuspendInfo *info | Indicates the info of delay request. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul><li>{@link ERR_TRANSIENT_TASK_OK} 0 - Success.</li><br>    <li>{@link ERR_TRANSIENT_TASK_INVALID_PARAM} 401 - Invalid parameter.</li><br>    <li>{@link ERR_TRANSIENT_TASK_PARCEL_FAILED} 9800002 - Parcelable failed.</li><br>    <li>{@link ERR_TRANSIENT_TASK_TRANSACTION_FAILED} 9800003 - Transact failed.</li><br>    <li>{@link ERR_TRANSIENT_TASK_SYS_NOT_READY} 9800004 - System service not ready.</li><br>    <li>{@link ERR_TRANSIENT_TASK_CLIENT_INFO_VERIFICATION_FAILED} 9900001 - uid or pid info verify failed.</li><br>    <li>{@link ERR_TRANSIENT_TASK_SERVICE_VERIFICATION_FAILED} 9900002 - Transient task verification failed.</li>      </ul> |

### OH_BackgroundTaskManager_GetRemainingDelayTime()

```c
int32_t OH_BackgroundTaskManager_GetRemainingDelayTime(int32_t requestId, int32_t *delayTime)
```

**Description**

Obtains the remaining time of a transient task.

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t requestId | Request ID of the transient task. |
| int32_t *delayTime | Pointer to the remaining time of the transient task, in ms. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul><li>{@link ERR_TRANSIENT_TASK_OK} 0 - Success.</li><br>    <li>{@link ERR_TRANSIENT_TASK_INVALID_PARAM} 401 - Invalid parameter.</li><br>    <li>{@link ERR_TRANSIENT_TASK_PARCEL_FAILED} 9800002 - Parcelable failed.</li><br>    <li>{@link ERR_TRANSIENT_TASK_TRANSACTION_FAILED} 9800003 - Transact failed.</li><br>    <li>{@link ERR_TRANSIENT_TASK_SYS_NOT_READY} 9800004 - System service not ready.</li><br>    <li>{@link ERR_TRANSIENT_TASK_CLIENT_INFO_VERIFICATION_FAILED} 9900001 - uid or pid info verify failed.</li><br>    <li>{@link ERR_TRANSIENT_TASK_SERVICE_VERIFICATION_FAILED} 9900002 - Transient task verification failed.</li>      </ul> |

### OH_BackgroundTaskManager_CancelSuspendDelay()

```c
int32_t OH_BackgroundTaskManager_CancelSuspendDelay(int32_t requestId)
```

**Description**

Cancels a transient task.

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t requestId | Request ID of the transient task. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul><li>{@link ERR_TRANSIENT_TASK_OK} 0 - Success.</li><br>    <li>{@link ERR_TRANSIENT_TASK_INVALID_PARAM} 401 - Invalid parameter.</li><br>    <li>{@link ERR_TRANSIENT_TASK_PARCEL_FAILED} 9800002 - Parcelable failed.</li><br>    <li>{@link ERR_TRANSIENT_TASK_TRANSACTION_FAILED} 9800003 - Transact failed.</li><br>    <li>{@link ERR_TRANSIENT_TASK_SYS_NOT_READY} 9800004 - System service not ready.</li><br>    <li>{@link ERR_TRANSIENT_TASK_CLIENT_INFO_VERIFICATION_FAILED} 9900001 - uid or pid info verify failed.</li><br>    <li>{@link ERR_TRANSIENT_TASK_SERVICE_VERIFICATION_FAILED} 9900002 - Transient task verification failed.</li>      </ul> |

### OH_BackgroundTaskManager_GetTransientTaskInfo()

```c
int32_t OH_BackgroundTaskManager_GetTransientTaskInfo(TransientTask_TransientTaskInfo *transientTaskInfo)
```

**Description**

Obtains all information about a transient task, including the remaining quota of the current day.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TransientTask_TransientTaskInfo *transientTaskInfo | All information about a transient task. For details, see {@link TransientTask_TransientTaskInfo}. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul><li>{@link ERR_TRANSIENT_TASK_OK} 0 - Success.</li><br>    <li>{@link ERR_TRANSIENT_TASK_CLIENT_INFO_VERIFICATION_FAILED} 9900001 - uid or pid info verify failed.</li><br>    <li>{@link ERR_TRANSIENT_TASK_PARCELABLE_FAILED} 9900003 - Failed to write data into parcel.</li><br>    <li>{@link ERR_TRANSIENT_TASK_SERVICE_NOT_READY} 9900004 - System service operation failed.</li>      </ul> |


