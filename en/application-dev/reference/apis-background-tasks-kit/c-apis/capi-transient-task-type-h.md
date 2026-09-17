# transient_task_type.h

## Overview

Defines the data structures for the C APIs of transient task.

**Library**: libtransient_task.so

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

**Since**: 13

**Related module**: [TransientTask](capi-transienttask.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [TransientTask_DelaySuspendInfo](capi-transienttask-transienttask-delaysuspendinfo.md) | TransientTask_DelaySuspendInfo | A struct that describes the returned information about a transient task. The struct returns the ID and remaining time of the transient task. |
| [TransientTask_TransientTaskInfo](capi-transienttask-transienttask-transienttaskinfo.md) | TransientTask_TransientTaskInfo | A struct that describes all transient task information. The struct returns all transient task information, including the remaining quota of the current day. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [TransientTask_ErrorCode](#transienttask_errorcode) | TransientTask_ErrorCode | Enumerates the error codes available for a transient task. |

### Macro

| Name | Description |
| -- | -- |
| TRANSIENT_TASK_MAX_NUM 3 | Defines the maximum number of transient tasks at the same time.<br>**Since**: 20 |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*TransientTask_Callback)(void)](#transienttask_callback) | TransientTask_Callback | Defines a callback for transient task timeout. |

### Variable

| Name | Description |
| -- | -- |
| void (*TransientTask_Callback)(void) | Defines a callback for transient task timeout.<br>**Since**: 13 |

## Enum type description

### TransientTask_ErrorCode

```c
enum TransientTask_ErrorCode
```

**Description**

Enumerates the error codes available for a transient task.

**Since**: 13

| Enum item | Description |
| -- | -- |
| ERR_TRANSIENT_TASK_OK = 0 | Operation successful.<br>**Since**: 13 |
| ERR_TRANSIENT_TASK_INVALID_PARAM = 401 | Parameter check failed. Possible causes: 1. Mandatory parameters are not passed. 2. Incorrect parameter types.<br>**Since**: 13 |
| ERR_TRANSIENT_TASK_PARCEL_FAILED = 9800002 | Parcel read/write operation failed.<br>**Since**: 13 |
| ERR_TRANSIENT_TASK_TRANSACTION_FAILED = 9800003 | IPC failed.<br>**Since**: 13 |
| ERR_TRANSIENT_TASK_SYS_NOT_READY = 9800004 | System service failed.<br>**Since**: 13 |
| ERR_TRANSIENT_TASK_CLIENT_INFO_VERIFICATION_FAILED = 9900001 | Failed to verify the client information of the transient task.<br>**Since**: 13 |
| ERR_TRANSIENT_TASK_SERVICE_VERIFICATION_FAILED = 9900002 | Failed to verify the server information of the transient task.<br>**Since**: 13 |
| ERR_TRANSIENT_TASK_PARCELABLE_FAILED = 9900003 | Parcel read/write operation failed for the transient task. Possible causes: 1. The parameter is invalid. 2. Memory allocation fails.<br>**Since**: 13 |
| ERR_TRANSIENT_TASK_SERVICE_NOT_READY = 9900004 |  |


## Function description

### TransientTask_Callback()

```c
typedef void (*TransientTask_Callback)(void)
```

**Description**

Defines a callback for transient task timeout.

**Since**: 13


