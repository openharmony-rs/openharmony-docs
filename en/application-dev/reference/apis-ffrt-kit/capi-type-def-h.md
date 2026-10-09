# type_def.h

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1bd5d6cdd22374b2fc7c67ab365167018faf622f translatedAt=2026-07-20T02:05:47.256Z pushedAt=2026-07-20T03:01:48.882Z -->

## Overview

This file declares the common types.

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
| [ffrt_function_header_t](capi-ffrt-ffrt-function-header-t.md) | ffrt_function_header_t | Task execution struct, used to define the execution and destruction callbacks of a task. The `exec` callback is invoked when the task is scheduled, and the `destroy` callback is invoked after the task completes to release task-related resources. Together, the two callbacks manage the complete lifecycle of an FFRT task. |
| [ffrt_dependence_t](capi-ffrt-ffrt-dependence-t.md) | ffrt_dependence_t | Dependency data item struct, used to describe a single inter-task dependency. |
| [ffrt_deps_t](capi-ffrt-ffrt-deps-t.md) | ffrt_deps_t | Dependency struct, used to store the dependency list of a task. |
| [ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md) | ffrt_task_attr_t | Task attribute struct, used to store the attribute information of a task. |
| [ffrt_queue_attr_t](capi-ffrt-ffrt-queue-attr-t.md) | ffrt_queue_attr_t | Queue attribute struct, used to store the attribute information of a queue. |
| [ffrt_condattr_t](capi-ffrt-ffrt-condattr-t.md) | ffrt_condattr_t | Condition variable attribute struct, used to store the attribute information of a condition variable. |
| [ffrt_mutexattr_t](capi-ffrt-ffrt-mutexattr-t.md) | ffrt_mutexattr_t | Mutex attribute struct, used to store the attribute information of a mutex. |
| [ffrt_rwlockattr_t](capi-ffrt-ffrt-rwlockattr-t.md) | ffrt_rwlockattr_t | Read-write lock attribute struct, used to store the attribute information of a read-write lock. |
| [ffrt_mutex_t](capi-ffrt-ffrt-mutex-t.md) | ffrt_mutex_t | Mutex struct, used to store the internal data of a mutex. |
| [ffrt_rwlock_t](capi-ffrt-ffrt-rwlock-t.md) | ffrt_rwlock_t | Read-write lock struct, used to store the internal data of a read-write lock. |
| [ffrt_cond_t](capi-ffrt-ffrt-cond-t.md) | ffrt_cond_t | Condition variable struct, used to store the internal data of a condition variable. |
| [ffrt_task_handle_t](capi-ffrt-ffrt-task-handle-t.md) | ffrt_task_handle_t | Task handle, used to identify different tasks. |
| [ffrt_fiber_t](capi-ffrt-ffrt-fiber-t.md) | ffrt_fiber_t | Fiber struct, used to store the fiber execution context. |

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ffrt_queue_priority_t](#ffrt_queue_priority_t) | ffrt_queue_priority_t | Enumerates the task priority types for sorting task scheduling in concurrent queues. |
| [ffrt_qos_default_t](#ffrt_qos_default_t) | ffrt_qos_default_t | Enumerates the task QoS types. |
| [ffrt_storage_size_t](#ffrt_storage_size_t) | ffrt_storage_size_t | Enumerates the storage sizes of multiple struct types, in bytes. |
| [ffrt_function_kind_t](#ffrt_function_kind_t) | ffrt_function_kind_t | Enumerates the task types, which are used to distinguish between general concurrent tasks and queue-scheduled tasks. |
| [ffrt_dependence_type_t](#ffrt_dependence_type_t) | ffrt_dependence_type_t | Enumerates the dependency types, which are used to specify inter-task dependency relationships (data ready or task completion). |
| [ffrt_error_t](#ffrt_error_t) | ffrt_error_t | Enumerates the error codes returned by FFRT APIs. |
| [ffrt_mutex_type](#ffrt_mutex_type) | ffrt_mutex_type | Enumerates the mutex lock types. |
| [qos_default](#qos_default) | - | Enumerates the task QoS types. Each enumeration value is equivalent to the corresponding enumeration value in [ffrt_qos_default_t](capi-type-def-h.md#ffrt_qos_default_t). |

### Function

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [typedef void(\*ffrt_function_t)(void*)](#ffrt_function_t) | ffrt_function_t | Task execution function pointer type. It defines the entry point of an FFRT task. FFRT calls this function when scheduling task execution and passes the user data pointer as a parameter. |
| [typedef void (\*ffrt_poller_cb)(void* data, uint32_t event)](#ffrt_poller_cb) | ffrt_poller_cb | Poller callback function type. It is called when the poller detects a registered event. The `data` pointer carries the user data passed at registration, and the `event` value indicates the type of the triggered event. |
| [typedef void (\*ffrt_timer_cb)(void* data)](#ffrt_timer_cb) | ffrt_timer_cb | Timer callback function type. It is called when the timer expires. The `data` pointer carries the user data passed at timer registration. |

## Enum Description

### ffrt_queue_priority_t

```c
enum ffrt_queue_priority_t
```

**Description**

Enumerates the task priority types for sorting task scheduling in concurrent queues.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| ffrt_queue_priority_immediate = 0 | Highest priority. Tasks of this priority need to be scheduled as soon as possible (handle time equals submission time), and ahead of tasks with a `high` priority. |
| ffrt_queue_priority_high | High priority. Tasks of this priority are sorted by handle time, and are scheduled ahead of tasks with a `low` priority. |
| ffrt_queue_priority_low | Low priority. Tasks of this priority are sorted by handle time, and are scheduled ahead of tasks with an `idle` priority. |
| ffrt_queue_priority_idle | Lowest priority. Tasks of this priority are sorted by handle time, and are scheduled only when no tasks of other priorities exist in the queue. |

### ffrt_qos_default_t

```c
enum ffrt_qos_default_t
```

**Description**

Enumerates the task QoS types.

**Since**: 10

| Enum Item| Description|
| -- | -- |
| ffrt_qos_inherit = -1 | Inheritance. <br>It inherits from the QoS of the calling thread, and is applicable to scenarios where a task needs to adopt the priority of its creator. |
| ffrt_qos_background | Background task.<br>Lowest priority. It is applicable to tasks that are imperceptible to the user, such as background data synchronization or log flushing. |
| ffrt_qos_utility | Utility task.<br>It is applicable to long-running tasks that are perceptible to the user but not actively awaited, such as data loading or content indexing. |
| ffrt_qos_default | Default type.<br>The default QoS is used when there are no special QoS requirements. It is applicable to most general tasks. |
| ffrt_qos_user_initiated | User-initiated task.<br>It is applicable to tasks that are actively triggered by the user and require quick response but do not block the UI, such as opening a document or performing a search. |
| ffrt_qos_deadline_request | Deadline request task.<br>It is applicable to tasks with explicit deadlines, where the system prioritizes their scheduling resources.<br>**Since:** 23 |
| ffrt_qos_user_interactive | User interaction task.<br>It is applicable to operations that require immediate interaction with the user, such as UI responses.<br>**Since:** 23 |
| ffrt_qos_max = ffrt_qos_user_interactive | Highest QoS level.<br>It is equivalent to ffrt_qos_user_interactive.<br>**Since:** 23 |

### ffrt_storage_size_t

```c
enum ffrt_storage_size_t
```

**Description**

Enumerates the storage sizes of multiple struct types, in bytes.

**Since**: 10

| Value | Description |
| -- | -- |
| ffrt_task_attr_storage_size = 128 | Task attribute storage size, in bytes. |
| ffrt_auto_managed_function_storage_size = 64 + sizeof(ffrt_function_header_t) | Task execution body storage size, in bytes. |
| ffrt_mutex_storage_size = 64 | Mutex storage size, in bytes. |
| ffrt_cond_storage_size = 64 | Condition variable storage size, in bytes. |
| ffrt_queue_attr_storage_size = 128 | Queue attribute storage size, in bytes. |
| ffrt_rwlock_storage_size = 64 | Read-write lock storage size, in bytes.<br>**Since:** 18 |
| ffrt_fiber_storage_size| Fiber storage size, in bytes. This constant defines the fiber storage size. The actual value depends on the target architecture: AArch64: 22 bytes; Arm: 64 bytes; x86_64: 8 bytes; other platforms: not supported.<br>**Since:** 20  |

### ffrt_function_kind_t

```c
enum ffrt_function_kind_t
```

**Description**

Enumerates the task types, which are used to distinguish between general concurrent tasks and queue-scheduled tasks.

**Since**: 10

| Enum Item| Description|
| -- | -- |
| ffrt_function_kind_general | General task. Tasks can be submitted to the FFRT scheduler for concurrent execution. |
| ffrt_function_kind_queue | Queue task. Tasks are executed sequentially in the order of submission through the queue. |

### ffrt_dependence_type_t

```c
enum ffrt_dependence_type_t
```

**Description**

Enumerates the dependency types, which are used to specify inter-task dependency relationships (data ready or task completion). 

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
| ffrt_success = 0 | Success. |
| ffrt_error_nomem = ENOMEM | Insufficient memory error. |
| ffrt_error_timedout = ETIMEDOUT | Timeout error. |
| ffrt_error_busy = EBUSY | Resource busy error. The resource is busy. Try again later. |
| ffrt_error_inval = EINVAL | Invalid value error. |

### ffrt_mutex_type

```c
enum ffrt_mutex_type
```

**Description**

Enumerates the mutex lock types.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| ffrt_mutex_normal = 0 | Normal mutex type. |
| ffrt_mutex_recursive = 2 | Recursive mutex type. This type allows the same thread to lock the same mutex multiple times. |
| ffrt_mutex_default = ffrt_mutex_normal | Default mutex type, equivalent to `ffrt_mutex_normal`. |

### qos_default

```c
enum qos_default
```

**Description**

Enumerates the task QoS types. Each enumeration value is equivalent to the corresponding enumeration value in [ffrt_qos_default_t](capi-type-def-h.md#ffrt_qos_default_t).

**Since**: 10

| Enum Item| Description|
| -- | -- |
| qos_inherit = ffrt_qos_inherit | Inheritance. <br>It inherits from the QoS of the calling thread, and is applicable to scenarios where a task needs to adopt the priority of its creator. |
| qos_background = ffrt_qos_background | Background task.<br>Lowest priority. It is applicable to tasks that are imperceptible to the user, such as background data synchronization or log flushing. |
| qos_utility = ffrt_qos_utility | Utility task.<br>It is applicable to long-running tasks that are perceptible to the user but not actively awaited, such as data loading or content indexing. |
| qos_default = ffrt_qos_default | Default type.<br>The default QoS is used when there are no special QoS requirements. It is applicable to most general tasks. |
| qos_user_initiated = ffrt_qos_user_initiated | User-initiated task.<br>It is applicable to tasks that are actively triggered by the user and require quick response but do not block the UI, such as opening a document or performing a search. |
| qos_deadline_request = ffrt_qos_deadline_request | Deadline request task.<br>It is applicable to tasks with explicit deadlines, where the system prioritizes their scheduling resources.<br>**Since:** 23 |
| qos_user_interactive = ffrt_qos_user_interactive | User interaction task.<br>It is applicable to operations that require immediate interaction with the user, such as UI responses.<br>**Since:** 23 |
| qos_max = ffrt_qos_user_interactive | Highest QoS level.<br>It is equivalent to ffrt_qos_user_interactive.<br>**Since:** 23 |

## Function Description

### ffrt_function_t()

```c
typedef void(*ffrt_function_t)(void*)
```

**Description**

Task execution function pointer type. It defines the entry point of an FFRT task. FFRT calls this function when scheduling task execution and passes the user data pointer as a parameter.

**Since**: 10

### ffrt_poller_cb()

```c
typedef void (*ffrt_poller_cb)(void* data, uint32_t event)
```

**Description**

Poller callback function type. It is called when the poller detects a registered event. The `data` pointer carries the user data passed at registration, and the `event` value indicates the type of the triggered event. 

**Since**: 12

**Parameters**

| Parameter Item | Description |
| -- | -- |
| void\* data | Pointer to the user data passed at poller registration. |
| uint32_t event | Type of event that triggered the callback. |

### ffrt_timer_cb()

```c
typedef void (*ffrt_timer_cb)(void* data)
```

**Description**

Timer callback function type. It is called when the timer expires. The `data` pointer carries the user data passed at timer registration.

**Since**: 12

**Parameters**

| Parameter Item | Description |
| -- | -- |
| void\* data | Pointer to the user data passed at timer registration. |