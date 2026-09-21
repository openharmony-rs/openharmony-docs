# common.h

## Overview

Defines common enum types of ArkTS native module.

**Library**: libace_napi.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 10

**Related module**: [ArkTS_Napi_NativeModule](capi-arkts-napi-nativemodule.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [napi_event_mode](#napi_event_mode) | napi_event_mode | Indicates the running mode of the native event loop in an asynchronous native thread. |
| [napi_task_priority](#napi_task_priority) | napi_task_priority | Indicates the priority of a task dispatched from native thread to ArkTS thread. |

## Enum type description

### napi_event_mode

```c
enum napi_event_mode
```

**Description**

Indicates the running mode of the native event loop in an asynchronous native thread.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 12

| Enum item | Description |
| -- | -- |
| napi_event_mode_default = 0 | In this mode, the current asynchronous thread will be blocked and events of native event loop will be processed. |
| napi_event_mode_nowait = 1 | In this mode, the current asynchronous thread will not be blocked. If there are events in the event loop, only one event will be processed and then the event loop will stop. If there are no events in the loop, the event loop will stop immediately. |

### napi_task_priority

```c
enum napi_task_priority
```

**Description**

Indicates the priority of a task dispatched from native thread to ArkTS thread.

**System capability**: SystemCapability.ArkUI.ArkUI.Napi

**Since**: 12

| Enum item | Description |
| -- | -- |
| napi_priority_immediate = 0 | The immediate priority tasks should be promptly processed whenever feasible. |
| napi_priority_high = 1 | The high priority tasks, as sorted by their handle time, should be prioritized over tasks with low priority. |
| napi_priority_low = 2 | The low priority tasks, as sorted by their handle time, should be processed before idle priority tasks. |
| napi_priority_idle = 3 | The idle priority tasks should be processed immediately only if there are no other priority tasks. |


