# transient_task_api.h

<!--Kit: Background Tasks Kit-->
<!--Subsystem: ResourceSchedule-->
<!--Owner: @xufu7-->
<!--Designer: @zhouben25-->
<!--Tester: @leetestnady-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=520f9a32cdb2e9a005e54fc92b1c491413781b64 translatedAt=2026-09-15T12:42:52.103Z pushedAt=2026-09-17T01:54:22.813Z -->

## Overview

The **transient_task_api.h** file declares the APIs for requesting, querying, and canceling transient tasks. A transient task allows an app to obtain a limited time extension in the background to complete critical operations. The system allocates a daily quota to each app. Before the quota is exhausted, the system notifies the app through a callback. After the quota is exhausted, the system suspends the app. For details about the development guidelines, see [Transient Task (C/C++)](../../task-management/native-transient-task.md).

**File to include**: <transient_task/transient_task_api.h>

**Library**: libtransient_task.so

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

**Since**: 13

**Related module**: [TransientTask](capi-transienttask.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [int32_t OH_BackgroundTaskManager_RequestSuspendDelay(const char* reason, TransientTask_Callback callback, TransientTask_DelaySuspendInfo *info)](#oh_backgroundtaskmanager_requestsuspenddelay) | Requests a transient task.|
| [int32_t OH_BackgroundTaskManager_GetRemainingDelayTime(int32_t requestId, int32_t *delayTime)](#oh_backgroundtaskmanager_getremainingdelaytime) | Obtains the remaining time of this transient task.|
| [int32_t OH_BackgroundTaskManager_CancelSuspendDelay(int32_t requestId)](#oh_backgroundtaskmanager_cancelsuspenddelay) | Cancels a transient task.|
| [int32_t OH_BackgroundTaskManager_GetTransientTaskInfo(TransientTask_TransientTaskInfo *transientTaskInfo)](#oh_backgroundtaskmanager_gettransienttaskinfo) | Obtains information about all transient tasks, such as the remaining total quota of the current day.|

## Function Description

### OH_BackgroundTaskManager_RequestSuspendDelay()

```c
int32_t OH_BackgroundTaskManager_RequestSuspendDelay(const char* reason, TransientTask_Callback callback, TransientTask_DelaySuspendInfo *info)
```

**Description**

Requests a transient task. This method is used to continue some short-time operations in the background when an app enters the background or is suspended, such as data synchronization and status saving.

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

**Since**: 13


**Parameters**

| Name                                                                                         | Description|
|----------------------------------------------------------------------------------------------| -- |
| const char* reason                                                                           | Reason for requesting the transient task.|
| [TransientTask_Callback](capi-transient-task-type-h.md#transienttask_callback) callback      | Callback used to notify the application that the transient task is about to time out. Generally, the callback is invoked 6 seconds before the timeout.|
| [TransientTask_DelaySuspendInfo](capi-transienttask-transienttask-delaysuspendinfo.md) *info | Information about the transient task.|

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Returns 0 if the request is successful.<br>Returns 401 if the input parameter is incorrect.<br>Returns 9800002 if the Parcel read/write operation fails.<br>Returns 9800003 if IPC fails.<br>Returns 9800004 if the system service fails.<br>Returns 9900001 if the client information of the transient task fails to be verified.<br>Returns 9900002 if the server information of the transient task fails to be verified.<br>For details about the error codes, see [TransientTask_ErrorCode](capi-transient-task-type-h.md#transienttask_errorcode). |

### OH_BackgroundTaskManager_GetRemainingDelayTime()

```c
int32_t OH_BackgroundTaskManager_GetRemainingDelayTime(int32_t requestId, int32_t *delayTime)
```

**Description**

Obtains the remaining time of a transient task.

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| int32_t requestId | Request ID of the transient task, which is the value of **requestId** returned by [OH_BackgroundTaskManager_RequestSuspendDelay](#oh_backgroundtaskmanager_requestsuspenddelay). |
| int32_t *delayTime | Remaining time of the transient task, in ms. |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Returns 0 if the query is successful.<br>Returns 401 if the input parameter is incorrect.<br>Returns 9800002 if the Parcel read/write operation fails.<br>Returns 9800003 if IPC fails.<br>Returns 9800004 if the system service fails.<br>Returns 9900001 if the client information of the transient task fails to be verified. <br>Returns 9900002 if the server information of the transient task fails to be verified.<br>For details about the error codes, see [TransientTask_ErrorCode](capi-transient-task-type-h.md#transienttask_errorcode). |

### OH_BackgroundTaskManager_CancelSuspendDelay()

```c
int32_t OH_BackgroundTaskManager_CancelSuspendDelay(int32_t requestId)
```

**Description**

Cancels a transient task. This method is used to release system resources when background execution is no longer required, for example, when a task is complete or an app is switched to the foreground.

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| int32_t requestId | Request ID of the transient task, which is the value of **requestId** returned by [OH_BackgroundTaskManager_RequestSuspendDelay](#oh_backgroundtaskmanager_requestsuspenddelay). |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Returns 0 if the cancellation is successful.<br>Returns 401 if the input parameter is incorrect.<br>Returns 9800002 if the Parcel read/write operation fails.<br>Returns 9800003 if IPC fails.<br>Returns 9800004 if the system service fails. <br>Returns 9900001 if the client information of the transient task fails to be verified.<br>Returns 9900002 if the server information of the transient task fails to be verified.<br>For details about the error codes, see [TransientTask_ErrorCode](capi-transient-task-type-h.md#transienttask_errorcode). |

### OH_BackgroundTaskManager_GetTransientTaskInfo()

```c
int32_t OH_BackgroundTaskManager_GetTransientTaskInfo(TransientTask_TransientTaskInfo *transientTaskInfo)
```

**Description**

Obtains information about all transient tasks, including the remaining quota of the current day.

**Since**: 20


**Parameters**

| Name                                                                                                         | Description                                                                                                     |
|--------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| [TransientTask_TransientTaskInfo](capi-transienttask-transienttask-transienttaskinfo.md) *transientTaskInfo | All information about a transient task. For details, see [TransientTask_TransientTaskInfo](capi-transienttask-transienttask-transienttaskinfo.md). |

**Return value**

| Type| Description|
| -- | -- |
| int32_t | Returns 0 if the transient task is obtained successfully.<br>Returns 9900001 if the client information of the transient task fails to be verified.<br>Returns 9900003 if the Parcel read/write operation fails.<br>Returns 9900004 if the system service fails. <br>For details about the error codes, see [TransientTask_ErrorCode](capi-transient-task-type-h.md#transienttask_errorcode). |


