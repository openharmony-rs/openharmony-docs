# type_def.h

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=528f79113a49f66de1d5ef6860690f10b63b035e translatedAt=2026-11-13T03:10:46.582Z pushedAt=2026-11-13T09:09:09.431Z nl=1 -->

## Overview

The **type_def.h** file declares the common types.

**File to include**: <ffrt/type_def.h>

**Library**: libffrt.z.so

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

## Summary

### Variables

| Name | typedef Keyword| Description                    |
|-----|------------|------------------------|
| int | ffrt_qos_t | QoS type, used to set the QoS level of a task. |
| int | ffrt_timer_t | Timer handle, used to identify a created timer. |
| using qos = int | - | QoS type.<br>**Since**: 10|

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ffrt_function_header_t](capi-ffrt-ffrt-function-header-t.md) | ffrt_function_header_t | Task execution body, which is used to define the execution and destruction callbacks of a task. The **exec** callback is invoked when the task is scheduled, and the **destroy** callback is invoked after the task is completed to release task-related resources. Together, they manage the complete lifecycle of an FFRT task. |
| [ffrt_dependence_t](capi-ffrt-ffrt-dependence-t.md) | ffrt_dependence_t | Dependency data item structure, used to describe a single dependency relationship between tasks. |
| [ffrt_deps_t](capi-ffrt-ffrt-deps-t.md) | ffrt_deps_t | Dependency structure, used to store the dependency list of a task. |
| [ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md) | ffrt_task_attr_t | Task attribute structure, used to store the attribute information of a task. |
| [ffrt_queue_attr_t](capi-ffrt-ffrt-queue-attr-t.md) | ffrt_queue_attr_t | Queue attribute structure, used to store the attribute information of a queue. |
| [ffrt_condattr_t](capi-ffrt-ffrt-condattr-t.md) | ffrt_condattr_t | Condition variable attribute structure, used to store the attribute information of a condition variable. |
| [ffrt_mutexattr_t](capi-ffrt-ffrt-mutexattr-t.md) | ffrt_mutexattr_t | Mutex attribute structure, used to store the attribute information of a mutex. |
| [ffrt_rwlockattr_t](capi-ffrt-ffrt-rwlockattr-t.md) | ffrt_rwlockattr_t | Read-write lock attribute structure, used to store the attribute information of a read-write lock. |
| [ffrt_mutex_t](capi-ffrt-ffrt-mutex-t.md) | ffrt_mutex_t | Mutex structure, used to store the internal data of a mutex. |
| [ffrt_rwlock_t](capi-ffrt-ffrt-rwlock-t.md) | ffrt_rwlock_t | Read-write lock structure, used to store the internal data of a read-write lock. |
| [ffrt_cond_t](capi-ffrt-ffrt-cond-t.md) | ffrt_cond_t | Condition variable structure, used to store the internal data of a condition variable. |
| [ffrt_task_handle_t](capi-ffrt-ffrt-task-handle-t.md) | ffrt_task_handle_t | Task handle, used to identify different tasks. |
| [ffrt_fiber_t](capi-ffrt-ffrt-fiber-t.md) | ffrt_fiber_t | Fiber structure, used to store the fiber execution context. |

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ffrt_queue_priority_t](#ffrt_queue_priority_t) | ffrt_queue_priority_t | Enumerates the task priority types used to order task scheduling in a concurrent queue. |
| [ffrt_qos_default_t](#ffrt_qos_default_t) | ffrt_qos_default_t | Enumerates the task QoS types. |
| [ffrt_storage_size_t](#ffrt_storage_size_t) | ffrt_storage_size_t | Defines the storage size of various types of structures, in bytes. |
| [ffrt_function_kind_t](#ffrt_function_kind_t) | ffrt_function_kind_t | Enumerates the task types, used to distinguish general concurrent tasks from queue-scheduled tasks. |
| [ffrt_dependence_type_t](#ffrt_dependence_type_t) | ffrt_dependence_type_t | Enumerates the dependency types, used to specify the dependency relationship between tasks (data ready or task completion). |
| [ffrt_error_t](#ffrt_error_t) | ffrt_error_t | Enumerates the error codes returned by FFRT APIs. |
| [ffrt_mutex_type](#ffrt_mutex_type) | ffrt_mutex_type | Enumerates the mutex types. |
| [qos_default](#qos_default) | - | Enumerates the task QoS types. Each enum value is equivalent to the corresponding enum value in [ffrt_qos_default_t](capi-type-def-h.md#ffrt_qos_default_t). |

### Function

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [typedef void(\*ffrt_function_t)(void*)](#ffrt_function_t) | ffrt_function_t | Task execution function pointer type. The function pointer defines the entry point of an FFRT task. FFRT invokes this function when scheduling task execution, and passes the user data pointer through the parameter. |
| [typedef void (\*ffrt_poller_cb)(void* data, uint32_t event)](#ffrt_poller_cb) | ffrt_poller_cb | Poller callback function type. This callback is invoked when the poller detects a registered event. The **data** pointer carries the user data passed at registration, and the **event** value identifies the type of the triggered event. |
| [typedef void (\*ffrt_timer_cb)(void* data)](#ffrt_timer_cb) | ffrt_timer_cb | Timer callback function type. This callback is invoked when the timer expires. The **data** pointer carries the user data passed at timer registration. |

## Enum Description

### ffrt_queue_priority_t

```c
enum ffrt_queue_priority_t
```

**Description**

Enumerates the task priority types used to order task scheduling in a concurrent queue.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| ffrt_queue_priority_immediate = 0 | Highest priority. The task is scheduled as soon as possible (the handle time equals the submission time); it takes precedence over **high** in scheduling. |
| ffrt_queue_priority_high | High priority. Tasks are ordered by handle time; it takes precedence over **low** in scheduling. |
| ffrt_queue_priority_low | Low priority. Tasks are ordered by handle time; it takes precedence over **idle** in scheduling. |
| ffrt_queue_priority_idle | Lowest priority. Tasks are ordered by handle time; it is scheduled only when no tasks of other priorities exist in the queue. |

### ffrt_qos_default_t

```c
enum ffrt_qos_default_t
```

**Description**

Enumerates the task QoS types.

**Since**: 10

| Enum Item| Description|
| -- | -- |
| ffrt_qos_inherit = -1 | Inherit.<br>Inherits the QoS of the calling thread. It is used for tasks that need to adopt the creator's priority. |
| ffrt_qos_background | Background task.<br>Lowest priority. It is used for work that is imperceptible to users, such as background data synchronization or log refresh. |
| ffrt_qos_utility | Utility task.<br>It is used for long-running tasks that are perceptible to users but not actively awaited, such as data loading or content indexing. |
| ffrt_qos_default | Default type.<br>Default QoS used when no special QoS requirement exists, applicable to most general tasks. |
| ffrt_qos_user_initiated | User-initiated task.<br>It is used for tasks triggered by users that require quick response but do not block the UI, such as opening a document or performing a search. |
| ffrt_qos_deadline_request | Deadline request task.<br>It is used for tasks with an explicit deadline, for which the system prioritizes scheduling resources.<br>**Since:** 23 |
| ffrt_qos_user_interactive | User interactive task.<br>It is applicable to operations that require immediate interaction with users, such as UI responses.<br>**Since:** 23 |
| ffrt_qos_max = ffrt_qos_user_interactive | Highest QoS level.<br>Equivalent to **ffrt_qos_user_interactive**.<br>**Since:** 23 |

### ffrt_storage_size_t

```c
enum ffrt_storage_size_t
```

**Description**

Defines the storage size of various types of structures, in bytes.

**Since**: 10

| Enum Item| Description|
| -- | -- |
| ffrt_task_attr_storage_size = 128 | Storage size of the task attribute, in bytes. |
| ffrt_auto_managed_function_storage_size = 64 + sizeof(ffrt_function_header_t) | Storage size of the task execution body, in bytes. |
| ffrt_mutex_storage_size = 64 | Storage size of the mutex, in bytes. |
| ffrt_cond_storage_size = 64 | Storage size of the condition variable, in bytes. |
| ffrt_queue_attr_storage_size = 128 | Storage size of the queue attribute, in bytes. |
| ffrt_rwlock_storage_size = 64 | Storage size of the read-write lock, in bytes.<br>**Since:** 18 |
| ffrt_fiber_storage_size| Storage size of the fiber, in bytes. This constant defines the storage size of a fiber. The actual value depends on the target architecture: aarch64: 22 bytes; arm: 64 bytes; x86_64: 8 bytes; other platforms: not supported.<br>**Since:** 20  |
### ffrt_function_kind_t

```c
enum ffrt_function_kind_t
```

**Description**

Enumerates the task types, used to distinguish general concurrent tasks from queue-scheduled tasks.

**Since**: 10

| Enum Item| Description|
| -- | -- |
| ffrt_function_kind_general | General task. The task can be submitted to the FFRT scheduler for concurrent execution. |
| ffrt_function_kind_queue | Queue task. Tasks are executed sequentially in submission order through a queue. |

### ffrt_dependence_type_t

```c
enum ffrt_dependence_type_t
```

**Description**

Enumerates the dependency types, used to specify the dependency relationship between tasks (data ready or task completion).

**Since**: 10

| Enum Item| Description|
| -- | -- |
| ffrt_dependence_data | Data dependency type. A task is scheduled only after the referenced data is ready. |
| ffrt_dependence_task | Task dependency type. A task is scheduled only after the referenced task is complete. |

### ffrt_error_t

```c
enum ffrt_error_t
```

**Description**

Enumerates the error codes returned by FFRT APIs.

**Since**: 10

| Enum Item| Description|
| -- | -- |
| ffrt_error = -1 | General error. |
| ffrt_success = 0 | Operation successful. |
| ffrt_error_nomem = ENOMEM | Insufficient memory error. |
| ffrt_error_timedout = ETIMEDOUT | Timeout error. |
| ffrt_error_busy = EBUSY | Resource busy error. The resource is busy. Try again later. |
| ffrt_error_inval = EINVAL | Invalid value error. |

### ffrt_mutex_type

```c
enum ffrt_mutex_type
```

**Description**

Enumerates the mutex types.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| ffrt_mutex_normal = 0 | Normal mutex type. |
| ffrt_mutex_recursive = 2 | Recursive mutex type, which allows the same thread to lock the same mutex multiple times. |
| ffrt_mutex_default = ffrt_mutex_normal | Default mutex type, equivalent to `ffrt_mutex_normal`. |

### qos_default

```c
enum qos_default
```

**Description**

Enumerates the task QoS types. Each enum value is equivalent to the corresponding enum value in [ffrt_qos_default_t](capi-type-def-h.md#ffrt_qos_default_t).

**Since**: 10

| Enum Item| Description|
| -- | -- |
| qos_inherit = ffrt_qos_inherit | Inherit.<br>Inherits the QoS of the calling thread. It is used for tasks that need to adopt the creator's priority. |
| qos_background = ffrt_qos_background | Background task.<br>Lowest priority. It is used for work that is imperceptible to users, such as background data synchronization or log refresh. |
| qos_utility = ffrt_qos_utility | Utility task.<br>It is used for long-running tasks that are perceptible to users but not actively awaited, such as data loading or content indexing. |
| qos_default = ffrt_qos_default | Default type.<br>Default QoS used when no special QoS requirement exists, applicable to most general tasks. |
| qos_user_initiated = ffrt_qos_user_initiated | User-initiated task.<br>It is used for tasks triggered by users that require quick response but do not block the UI, such as opening a document or performing a search. |
| qos_deadline_request = ffrt_qos_deadline_request | Deadline request task.<br>It is used for tasks with an explicit deadline, for which the system prioritizes scheduling resources.<br>**Since:** 23 |
| qos_user_interactive = ffrt_qos_user_interactive | User interactive task.<br>Applicable to operations that require immediate interaction with users, such as UI responses.<br>**Since:** 23 |
| qos_max = ffrt_qos_user_interactive | Highest QoS level.<br>Equivalent to ffrt_qos_user_interactive.<br>**Since:** 23 |


## Function Description

### ffrt_function_t()

```c
typedef void(*ffrt_function_t)(void*)
```

**Description**

Task execution function pointer type. The function pointer defines the entry point of an FFRT task. FFRT invokes this function when scheduling task execution, and passes the user data pointer through the parameter.

**Since**: 10

### ffrt_poller_cb()

```c
typedef void (*ffrt_poller_cb)(void* data, uint32_t event)
```

**Description**

Poller callback function type. This callback is invoked when the poller detects a registered event. The **data** pointer carries the user data passed at registration, and the **event** value identifies the type of the triggered event.

**Since**: 12

**Parameters:**

| Name | Description |
| -- | -- |
| void\* data | Pointer to the user data passed at poller registration. |
| uint32_t event | Type of the event that triggers the callback. |

### ffrt_timer_cb()

```c
typedef void (*ffrt_timer_cb)(void* data)
```

**Description**

Timer callback function type. This callback is invoked when the timer expires. The **data** pointer carries the user data passed at timer registration.

**Since**: 12

**Parameters:**

| Name | Description |
| -- | -- |
| void\* data | Pointer to the user data passed at timer registration. |


