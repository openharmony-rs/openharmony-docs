# queue.h

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->

## Overview

This file declares the C APIs for queues.

**File to include**: <ffrt/queue.h>

**Library**: libffrt.z.so

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

## Summary

### Structs

| Name              | Description|
|------------------|--|
| [ffrt_queue_t](capi-ffrt-ffrt-queue-t.md) | Queue handle. |

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ffrt_queue_type_t](#ffrt_queue_type_t) | ffrt_queue_type_t | Enumerates queue types.|

### Function

| Name| Description|
| -- | -- |
| [FFRT_C_API int ffrt_queue_attr_init(ffrt_queue_attr_t* attr)](#ffrt_queue_attr_init) | Initializes a queue attribute. When the queue attribute is no longer needed, it must be destroyed via [ffrt_queue_attr_destroy](capi-queue-h.md#ffrt_queue_attr_destroy).|
| [FFRT_C_API void ffrt_queue_attr_destroy(ffrt_queue_attr_t* attr)](#ffrt_queue_attr_destroy) | Destroys a queue attribute. The queue attribute must have been initialized via [ffrt_queue_attr_init](capi-queue-h.md#ffrt_queue_attr_init).|
| [FFRT_C_API void ffrt_queue_attr_set_qos(ffrt_queue_attr_t* attr, ffrt_qos_t qos)](#ffrt_queue_attr_set_qos) | Sets the QoS in a queue attribute.|
| [FFRT_C_API ffrt_qos_t ffrt_queue_attr_get_qos(const ffrt_queue_attr_t* attr)](#ffrt_queue_attr_get_qos) | Obtains the QoS in a queue attribute.|
| [FFRT_C_API void ffrt_queue_attr_set_timeout(ffrt_queue_attr_t* attr, uint64_t timeout_us)](#ffrt_queue_attr_set_timeout) | Sets the task execution timeout interval in a queue attribute.|
| [FFRT_C_API uint64_t ffrt_queue_attr_get_timeout(const ffrt_queue_attr_t* attr)](#ffrt_queue_attr_get_timeout) | Obtains the task execution timeout interval in a queue attribute.|
| [FFRT_C_API void ffrt_queue_attr_set_callback(ffrt_queue_attr_t* attr, ffrt_function_header_t* f)](#ffrt_queue_attr_set_callback) | Sets the timeout callback in a queue attribute. This callback is triggered when the execution time of a task in the queue exceeds the timeout interval set via [ffrt_queue_attr_set_timeout](capi-queue-h.md#ffrt_queue_attr_set_timeout).|
| [FFRT_C_API ffrt_function_header_t* ffrt_queue_attr_get_callback(const ffrt_queue_attr_t* attr)](#ffrt_queue_attr_get_callback) | Obtains the timeout callback in a queue attribute.|
| [FFRT_C_API void ffrt_queue_attr_set_max_concurrency(ffrt_queue_attr_t* attr, const int max_concurrency)](#ffrt_queue_attr_set_max_concurrency) | Sets the maximum concurrency in a concurrent queue attribute.|
| [FFRT_C_API int ffrt_queue_attr_get_max_concurrency(const ffrt_queue_attr_t* attr)](#ffrt_queue_attr_get_max_concurrency) | Obtains the maximum concurrency in a concurrent queue attribute.|
| [FFRT_C_API void ffrt_queue_attr_set_thread_mode(ffrt_queue_attr_t* attr, bool mode)](#ffrt_queue_attr_set_thread_mode) | Sets the execution mode in a queue attribute. This API specifies whether tasks in the queue are executed in coroutine mode or thread mode. By default, the coroutine mode is used. Set `mode` to `true` to enable thread-based execution.|
| [FFRT_C_API bool ffrt_queue_attr_get_thread_mode(const ffrt_queue_attr_t* attr)](#ffrt_queue_attr_get_thread_mode) | Obtains the execution mode in a queue attribute.|
| [FFRT_C_API ffrt_queue_t ffrt_queue_create(ffrt_queue_type_t type, const char* name, const ffrt_queue_attr_t* attr)](#ffrt_queue_create) | Creates a queue. When the queue is no longer needed, it must be destroyed via [ffrt_queue_destroy](capi-queue-h.md#ffrt_queue_destroy).|
| [FFRT_C_API void ffrt_queue_destroy(ffrt_queue_t queue)](#ffrt_queue_destroy) | Destroys a queue. The queue must have been created via [ffrt_queue_create](capi-queue-h.md#ffrt_queue_create). During the destruction, pending tasks are canceled, and the API call blocks until all running tasks complete.|
| [FFRT_C_API void ffrt_queue_submit(ffrt_queue_t queue, ffrt_function_header_t* f, const ffrt_task_attr_t* attr)](#ffrt_queue_submit) | Submits a task to a queue.|
| [FFRT_C_API ffrt_task_handle_t ffrt_queue_submit_h(ffrt_queue_t queue, ffrt_function_header_t* f, const ffrt_task_attr_t* attr)](#ffrt_queue_submit_h) | Submits a task to a queue and obtains the task handle.|
| [FFRT_C_API void ffrt_queue_submit_f(ffrt_queue_t queue, ffrt_function_t func, void* arg, const ffrt_task_attr_t* attr)](#ffrt_queue_submit_f) | Submits a task to a queue. It is a simplified form of the [ffrt_queue_submit](capi-queue-h.md#ffrt_queue_submit) API. This API wraps the given task function and its parameters into a task wrapper for queue submission (`ffrt_function_kind_queue`). The task destroy callback (`after_func`), which is used for post-execution cleanup, is set to `NULL`, thereby omitting any additional cleanup actions. The generated task wrapper is then submitted to the specified queue via the [ffrt_queue_submit](capi-queue-h.md#ffrt_queue_submit) API.|
| [FFRT_C_API ffrt_task_handle_t ffrt_queue_submit_h_f(ffrt_queue_t queue, ffrt_function_t func, void* arg, const ffrt_task_attr_t* attr)](#ffrt_queue_submit_h_f) | Submits a task to a queue and obtains the task handle. It is a simplified form of the [ffrt_queue_submit_h](capi-queue-h.md#ffrt_queue_submit_h) API. This API wraps the given task function and its parameters into a task wrapper for queue submission (<idp:inline displayname="code" id="code16324747161913">ffrt_function_kind_queue</idp:inline>). The task destroy callback (`after_func`), which is used for post-execution cleanup, is set to `NULL`, thereby omitting any additional cleanup actions. The generated task wrapper is then submitted to the specified queue via the [ffrt_queue_submit_h](capi-queue-h.md#ffrt_queue_submit_h) API.|
| [FFRT_C_API void ffrt_queue_wait(ffrt_task_handle_t handle)](#ffrt_queue_wait) | Waits for the tasks in the queue to complete execution.|
| [FFRT_C_API int ffrt_queue_cancel(ffrt_task_handle_t handle)](#ffrt_queue_cancel) | Cancels a task in the queue. A task that has started cannot be canceled.|
| [FFRT_C_API ffrt_queue_t ffrt_get_main_queue(void)](#ffrt_get_main_queue) | Obtains the main thread queue of an application.|
| [FFRT_C_API ffrt_queue_t ffrt_get_current_queue(void)](#ffrt_get_current_queue) | Obtains the worker (ArkTS) thread queue of an application. (It is deprecated since API version 18.)|

## Enum Description

### ffrt_queue_type_t

```c
enum ffrt_queue_type_t
```

**Description**

Enumerates queue types.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| ffrt_queue_serial | Serial queue.|
| ffrt_queue_concurrent | Concurrent queue.|
| ffrt_queue_max | Maximum valid queue type value. It is used as a sentinel value (for example, for iteration).|


## Function Description

### ffrt_queue_attr_init()

```c
FFRT_C_API int ffrt_queue_attr_init(ffrt_queue_attr_t* attr)
```

**Description**

Initializes a queue attribute. When the queue attribute is no longer needed, it must be destroyed via [ffrt_queue_attr_destroy](capi-queue-h.md#ffrt_queue_attr_destroy).

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_queue_attr_t](capi-ffrt-ffrt-queue-attr-t.md)* attr | Pointer to the queue attribute.|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | If the queue attribute initialization is successful, `0` is returned.<br>         Otherwise, `-1` is returned.|

### ffrt_queue_attr_destroy()

```c
FFRT_C_API void ffrt_queue_attr_destroy(ffrt_queue_attr_t* attr)
```

**Description**

Destroys a queue attribute. The queue attribute must have been initialized via [ffrt_queue_attr_init](capi-queue-h.md#ffrt_queue_attr_init).

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_queue_attr_t](capi-ffrt-ffrt-queue-attr-t.md)* attr | Pointer to the queue attribute.|

### ffrt_queue_attr_set_qos()

```c
FFRT_C_API void ffrt_queue_attr_set_qos(ffrt_queue_attr_t* attr, ffrt_qos_t qos)
```

**Description**

Sets the QoS in a queue attribute.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_queue_attr_t](capi-ffrt-ffrt-queue-attr-t.md)* attr | Pointer to the queue attribute.|
| [ffrt_qos_t](capi-type-def-h.md#variables) qos| QoS level. For details about the value range, see the enumeration definition in [ffrt_qos_t](capi-type-def-h.md#variables).|

### ffrt_queue_attr_get_qos()

```c
FFRT_C_API ffrt_qos_t ffrt_queue_attr_get_qos(const ffrt_queue_attr_t* attr)
```

**Description**

Obtains the QoS in a queue attribute.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [const ffrt_queue_attr_t](capi-ffrt-ffrt-queue-attr-t.md)* attr | Pointer to the queue attribute.|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API [ffrt_qos_t](capi-type-def-h.md#variables)| QoS level. For details about the value range, see the enumeration definition in [ffrt_qos_t](capi-type-def-h.md#variables).|

### ffrt_queue_attr_set_timeout()

```c
FFRT_C_API void ffrt_queue_attr_set_timeout(ffrt_queue_attr_t* attr, uint64_t timeout_us)
```

**Description**

Sets the task execution timeout interval in a queue attribute.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_queue_attr_t](capi-ffrt-ffrt-queue-attr-t.md)* attr | Pointer to the queue attribute.|
| uint64_t timeout_us | Timeout duration for queue task execution, in microseconds. The minimum value is 1000 microseconds (1 ms). Values below 1000 are clamped to 1000.|

### ffrt_queue_attr_get_timeout()

```c
FFRT_C_API uint64_t ffrt_queue_attr_get_timeout(const ffrt_queue_attr_t* attr)
```

**Description**

Obtains the task execution timeout interval in a queue attribute.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [const ffrt_queue_attr_t](capi-ffrt-ffrt-queue-attr-t.md)* attr | Pointer to the queue attribute.|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API uint64_t | Timeout duration for queue task execution, in microseconds.|

### ffrt_queue_attr_set_callback()

```c
FFRT_C_API void ffrt_queue_attr_set_callback(ffrt_queue_attr_t* attr, ffrt_function_header_t* f)
```

**Description**

Sets the timeout callback in a queue attribute. This callback is triggered when the execution time of a task in the queue exceeds the timeout interval set via [ffrt_queue_attr_set_timeout](capi-queue-h.md#ffrt_queue_attr_set_timeout).

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_queue_attr_t](capi-ffrt-ffrt-queue-attr-t.md)* attr | Pointer to the queue attribute.|
| [ffrt_function_header_t](capi-ffrt-ffrt-function-header-t.md)* f | Queue task timeout callback function.|

### ffrt_queue_attr_get_callback()

```c
FFRT_C_API ffrt_function_header_t* ffrt_queue_attr_get_callback(const ffrt_queue_attr_t* attr)
```

**Description**

Obtains the timeout callback in a queue attribute.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [const ffrt_queue_attr_t](capi-ffrt-ffrt-queue-attr-t.md)* attr | Pointer to the queue attribute.|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API [ffrt_function_header_t](capi-ffrt-ffrt-function-header-t.md)* | Queue task timeout callback function.|

### ffrt_queue_attr_set_max_concurrency()

```c
FFRT_C_API void ffrt_queue_attr_set_max_concurrency(ffrt_queue_attr_t* attr, const int max_concurrency)
```

**Description**

Sets the maximum concurrency in a concurrent queue attribute.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_queue_attr_t](capi-ffrt-ffrt-queue-attr-t.md)* attr | Pointer to the queue attribute.|
| const int max_concurrency | Maximum number of tasks that can be concurrently executed in a queue.|

### ffrt_queue_attr_get_max_concurrency()

```c
FFRT_C_API int ffrt_queue_attr_get_max_concurrency(const ffrt_queue_attr_t* attr)
```

**Description**

Obtains the maximum concurrency in a concurrent queue attribute.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const ffrt_queue_attr_t](capi-ffrt-ffrt-queue-attr-t.md)* attr | Pointer to the queue attribute.|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | Maximum concurrency of a queue.|

### ffrt_queue_attr_set_thread_mode()

```c
FFRT_C_API void ffrt_queue_attr_set_thread_mode(ffrt_queue_attr_t* attr, bool mode)
```

**Description**

Sets the execution mode in a queue attribute. This API specifies whether tasks in the queue are executed in coroutine mode or thread mode. By default, the coroutine mode is used. Set `mode` to `true` to enable thread-based execution.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_queue_attr_t](capi-ffrt-ffrt-queue-attr-t.md)* attr | Pointer to the queue attribute.|
| bool mode | Whether to enable thread-based execution. - `true`: Tasks are executed on native threads (thread mode). - `false` (default value): Tasks are executed in coroutine mode.|

### ffrt_queue_attr_get_thread_mode()

```c
FFRT_C_API bool ffrt_queue_attr_get_thread_mode(const ffrt_queue_attr_t* attr)
```

**Description**

Obtains the execution mode in a queue attribute.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [const ffrt_queue_attr_t](capi-ffrt-ffrt-queue-attr-t.md)* attr | Pointer to the queue attribute.|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API bool | If tasks are executed on native threads (thread mode), `true` is returned.<br>         If tasks are executed in coroutine mode (default), `false` is returned.|

### ffrt_queue_create()

```c
FFRT_C_API ffrt_queue_t ffrt_queue_create(ffrt_queue_type_t type, const char* name, const ffrt_queue_attr_t* attr)
```

**Description**

Creates a queue. When the queue is no longer needed, it must be destroyed via [ffrt_queue_destroy](capi-queue-h.md#ffrt_queue_destroy).

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_queue_type_t](capi-queue-h.md#ffrt_queue_type_t) type | Enumerates the queue types. `ffrt_queue_serial` is applicable to scenarios where tasks need to be executed in sequence, and `ffrt_queue_concurrent` is applicable to scenarios where tasks can be executed concurrently to improve throughput.|
| const char* name | Pointer to the queue name.|
| [const ffrt_queue_attr_t](capi-ffrt-ffrt-queue-attr-t.md)* attr | Pointer to the queue attribute.|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API [ffrt_queue_t](capi-ffrt-ffrt-queue-t.md) | If the operation is successful, a non-null queue handle is returned.<br>         Otherwise, a null pointer is returned.|

### ffrt_queue_destroy()

```c
FFRT_C_API void ffrt_queue_destroy(ffrt_queue_t queue)
```

**Description**

Destroys a queue. The queue must have been created via [ffrt_queue_create](capi-queue-h.md#ffrt_queue_create). During the destruction, pending tasks are canceled, and the API call blocks until all running tasks complete.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_queue_t](capi-ffrt-ffrt-queue-t.md) queue | Queue handle.|

### ffrt_queue_submit()

```c
FFRT_C_API void ffrt_queue_submit(ffrt_queue_t queue, ffrt_function_header_t* f, const ffrt_task_attr_t* attr)
```

**Description**

Submits a task to a queue.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_queue_t](capi-ffrt-ffrt-queue-t.md) queue | Queue handle.|
| [ffrt_function_header_t](capi-ffrt-ffrt-function-header-t.md)* f | Pointer to the task executor.|
| [const ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | Pointer to the task attribute.|

**References**

[ffrt_queue_submit_h](capi-queue-h.md#ffrt_queue_submit_h)


### ffrt_queue_submit_h()

```c
FFRT_C_API ffrt_task_handle_t ffrt_queue_submit_h(ffrt_queue_t queue, ffrt_function_header_t* f, const ffrt_task_attr_t* attr)
```

**Description**

Submits a task to a queue and obtains the task handle.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_queue_t](capi-ffrt-ffrt-queue-t.md) queue | Queue handle.|
| [ffrt_function_header_t](capi-ffrt-ffrt-function-header-t.md)* f | Pointer to the task executor.|
| [const ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | Pointer to the task attribute.|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API [ffrt_task_handle_t](capi-ffrt-ffrt-task-handle-t.md) | If the operation is successful, a non-null task handle is returned.<br>         Otherwise, a null pointer is returned.|

**References**

[ffrt_queue_submit](capi-queue-h.md#ffrt_queue_submit)


### ffrt_queue_submit_f()

```c
FFRT_C_API void ffrt_queue_submit_f(ffrt_queue_t queue, ffrt_function_t func, void* arg, const ffrt_task_attr_t* attr)
```

**Description**

Submits a task to a queue. It is a simplified form of the [ffrt_queue_submit](capi-queue-h.md#ffrt_queue_submit) API. This API wraps the given task function and its parameters into a task wrapper for queue submission (`ffrt_function_kind_queue`). The task destroy callback (`after_func`), which is used for post-execution cleanup, is set to `NULL`, thereby omitting any additional cleanup actions. The generated task wrapper is then submitted to the specified queue via the [ffrt_queue_submit](capi-queue-h.md#ffrt_queue_submit) API.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_queue_t](capi-ffrt-ffrt-queue-t.md) queue | Queue handle.|
| [ffrt_function_t](capi-type-def-h.md#ffrt_function_t) func | Task function to be executed.|
| void* arg | Pointer to the parameter or closure data to be passed to the task function.|
| [const ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | Pointer to the task attribute.|

**References**

[ffrt_queue_submit](capi-queue-h.md#ffrt_queue_submit)


### ffrt_queue_submit_h_f()

```c
FFRT_C_API ffrt_task_handle_t ffrt_queue_submit_h_f(ffrt_queue_t queue, ffrt_function_t func, void* arg, const ffrt_task_attr_t* attr)
```

**Description**

Submits a task to a queue and obtains the task handle. It is a simplified form of the [ffrt_queue_submit_h](capi-queue-h.md#ffrt_queue_submit_h) API. This API wraps the given task function and its parameters into a task wrapper for queue submission (<idp:inline displayname="code" id="code13665856690">ffrt_function_kind_queue</idp:inline>). The task destroy callback (`after_func`), which is used for post-execution cleanup, is set to `NULL`, thereby omitting any additional cleanup actions. The generated task wrapper is then submitted to the specified queue via the [ffrt_queue_submit_h](capi-queue-h.md#ffrt_queue_submit_h) API.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_queue_t](capi-ffrt-ffrt-queue-t.md) queue | Queue handle.|
| [ffrt_function_t](capi-type-def-h.md#ffrt_function_t) func | Task function to be executed.|
| void* arg | Pointer to the parameter or closure data to be passed to the task function.|
| [const ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | Pointer to the task attribute.|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API [ffrt_task_handle_t](capi-ffrt-ffrt-task-handle-t.md) | If the operation is successful, a non-null task handle is returned.<br>         Otherwise, a null pointer is returned.|

**References**

[ffrt_queue_submit_h](capi-queue-h.md#ffrt_queue_submit_h)


### ffrt_queue_wait()

```c
FFRT_C_API void ffrt_queue_wait(ffrt_task_handle_t handle)
```

**Description**

Waits for the tasks in the queue to complete execution.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_task_handle_t](capi-ffrt-ffrt-task-handle-t.md) handle | Task handle.|

### ffrt_queue_cancel()

```c
FFRT_C_API int ffrt_queue_cancel(ffrt_task_handle_t handle)
```

**Description**

Cancels a task in the queue. A task that has started cannot be canceled.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_task_handle_t](capi-ffrt-ffrt-task-handle-t.md) handle | Task handle.|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | If the task is canceled successfully, `0` is returned.<br>          If the task has been executed or removed from the queue, `1` is returned.<br>          If `handle` is null, `-1` is returned.|

### ffrt_get_main_queue()

```c
FFRT_C_API ffrt_queue_t ffrt_get_main_queue(void)
```

**Description**

Obtains the main thread queue of an application.

**Since**: 12

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API [ffrt_queue_t](capi-ffrt-ffrt-queue-t.md) | Main thread queue of an application.|

### ffrt_get_current_queue()

```c
FFRT_C_API ffrt_queue_t ffrt_get_current_queue(void)
```

**Description**

Obtains the worker (ArkTS) thread queue of an application.

**Since**: 12

**Deprecated from**: 18

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API [ffrt_queue_t](capi-ffrt-ffrt-queue-t.md) | Worker (ArkTS) thread queue of an application.|
