# task.h

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->

## Overview

This file declares C APIs for FFRT tasks, providing functionalities including task attribute initialization and destruction, task QoS setting and retrieval, task execution submission and scheduling, task waiting, as well as management of the task delay time, concurrent queue task priorities, task stack size, and task handle reference counting.

**File to include**: <ffrt/task.h>

**Library**: libffrt.z.so

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

## Summary

### Function

| Name| Description|
| -- | -- |
| [FFRT_C_API int ffrt_task_attr_init(ffrt_task_attr_t* attr)](#ffrt_task_attr_init) | Initializes a task attribute. After the call is successful, the task attribute is set to the default value (for example, the default QoS is [ffrt_qos_default](capi-type-def-h.md#ffrt_qos_default_t)). Call [ffrt_task_attr_destroy](capi-task-h.md#ffrt_task_attr_destroy) to release the task attribute after use.|
| [FFRT_C_API void ffrt_task_attr_set_name(ffrt_task_attr_t* attr, const char* name)](#ffrt_task_attr_set_name) | Sets the name of a task attribute.|
| [FFRT_C_API const char* ffrt_task_attr_get_name(const ffrt_task_attr_t* attr)](#ffrt_task_attr_get_name) | Obtains the name of a task attribute.|
| [FFRT_C_API void ffrt_task_attr_destroy(ffrt_task_attr_t* attr)](#ffrt_task_attr_destroy) | Destroys a task attribute. This API must be called on a task attribute that has been initialized by [ffrt_task_attr_init](capi-task-h.md#ffrt_task_attr_init) to release the resources held by the attribute. Once destroyed, the task attribute cannot be used anymore.|
| [FFRT_C_API void ffrt_task_attr_set_qos(ffrt_task_attr_t* attr, ffrt_qos_t qos)](#ffrt_task_attr_set_qos) | Sets the QoS in a task attribute. QoS is used to control the scheduling priority of a task. For example, you can configure a high QoS for user-interactive tasks to ensure responsiveness, and configure a low QoS for background or maintenance tasks to minimize their system resource usage.|
| [FFRT_C_API ffrt_qos_t ffrt_task_attr_get_qos(const ffrt_task_attr_t* attr)](#ffrt_task_attr_get_qos) | Obtains the QoS in a task attribute.|
| [FFRT_C_API void ffrt_task_attr_set_delay(ffrt_task_attr_t* attr, uint64_t delay_us)](#ffrt_task_attr_set_delay) | Sets the delay time in a task attribute.|
| [FFRT_C_API uint64_t ffrt_task_attr_get_delay(const ffrt_task_attr_t* attr)](#ffrt_task_attr_get_delay) | Obtains the delay time in a task attribute.|
| [FFRT_C_API void ffrt_task_attr_set_queue_priority(ffrt_task_attr_t* attr, ffrt_queue_priority_t priority)](#ffrt_task_attr_set_queue_priority) | Sets the priority in a task attribute.|
| [FFRT_C_API ffrt_queue_priority_t ffrt_task_attr_get_queue_priority(const ffrt_task_attr_t* attr)](#ffrt_task_attr_get_queue_priority) | Obtains the priority in a task attribute.|
| [FFRT_C_API void ffrt_task_attr_set_stack_size(ffrt_task_attr_t* attr, uint64_t size)](#ffrt_task_attr_set_stack_size) | Sets the stack size in a task attribute.|
| [FFRT_C_API uint64_t ffrt_task_attr_get_stack_size(const ffrt_task_attr_t* attr)](#ffrt_task_attr_get_stack_size) | Obtains the stack size in a task attribute.|
| [FFRT_C_API int ffrt_this_task_update_qos(ffrt_qos_t qos)](#ffrt_this_task_update_qos) | Updates the QoS of the current task. This API is used to dynamically adjust the scheduling priority based on the running phase during task execution. For example, after a user triggers a related operation for a background synchronization task, this API can be used to increase the QoS level to accelerate the processing speed.|
| [FFRT_C_API ffrt_qos_t ffrt_this_task_get_qos(void)](#ffrt_this_task_get_qos) | Obtains the QoS of the current task.|
| [FFRT_C_API uint64_t ffrt_this_task_get_id(void)](#ffrt_this_task_get_id) | Obtains the ID of the current task.|
| [FFRT_C_API void *ffrt_alloc_auto_managed_function_storage_base(ffrt_function_kind_t kind)](#ffrt_alloc_auto_managed_function_storage_base) | Allocates memory for the function execution struct. The allocated memory is used for task executor encapsulation and is passed when submitting a task via [ffrt_submit_base](capi-task-h.md#ffrt_submit_base) or [ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base). The memory is automatically released by the FFRT runtime after the submitted task completes, so the caller does not need to free it manually.|
| [FFRT_C_API void ffrt_submit_base(ffrt_function_header_t* f, const ffrt_deps_t* in_deps, const ffrt_deps_t* out_deps, const ffrt_task_attr_t* attr)](#ffrt_submit_base) | Submits a task for scheduling and execution. The task execution body, input dependencies, output dependencies, and task attribute are submitted together to the FFRT scheduler. The scheduler determines the execution timing based on dependency relationships and task QoS, and selects a worker thread to execute the task. This API is a low-level submission API. If the task does not require a destroy callback, the simplified API [ffrt_submit_f](capi-task-h.md#ffrt_submit_f) can be used instead. Unlike [ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base), this API does not return a task handle, making it suitable for scenarios where subsequent dependency management or waiting on the submitted task is not required. If a delay time has been set for the task attribute via [ffrt_task_attr_set_delay](capi-task-h.md#ffrt_task_attr_set_delay), the input and output dependencies no longer take effect, and the task will be scheduled after the delay expires.|
| [FFRT_C_API ffrt_task_handle_t ffrt_submit_h_base(ffrt_function_header_t* f, const ffrt_deps_t* in_deps, const ffrt_deps_t* out_deps, const ffrt_task_attr_t* attr)](#ffrt_submit_h_base) | Submits a task for scheduling and execution and returns the task handle. The task execution body, input dependencies, output dependencies, and task attribute are submitted together to the FFRT scheduler. The scheduler determines the execution timing based on dependency relationships. The returned task handle can be used to wait for the task to complete via [ffrt_wait_deps](capi-task-h.md#ffrt_wait_deps), or to be used as an input dependency for other tasks to build dependency relationships between tasks. This API is a low-level submission API that returns a task handle. If the task does not require a destroy callback, the simplified API [ffrt_submit_h_f](capi-task-h.md#ffrt_submit_h_f) can be used instead. The returned task handle must be destroyed via [ffrt_task_handle_destroy](capi-task-h.md#ffrt_task_handle_destroy). Its reference count can be managed using [ffrt_task_handle_inc_ref](capi-task-h.md#ffrt_task_handle_inc_ref) and [ffrt_task_handle_dec_ref](capi-task-h.md#ffrt_task_handle_dec_ref).|
| [FFRT_C_API void ffrt_submit_f(ffrt_function_t func, void* arg, const ffrt_deps_t* in_deps, const ffrt_deps_t* out_deps, const ffrt_task_attr_t* attr)](#ffrt_submit_f) | Submits a task for scheduling and execution. It is a simplified form of the [ffrt_submit_base](capi-task-h.md#ffrt_submit_base) API. This API wraps the given task function and its parameters into a general task struct (`ffrt_function_kind_general`). The task destroy callback (`after_func`), which is used for post-execution cleanup, is set to `NULL`, thereby omitting any additional cleanup actions. The wrapped task struct is then submitted via the [ffrt_submit_base](capi-task-h.md#ffrt_submit_base) API. If a delay time has been set for the task attribute via [ffrt_task_attr_set_delay](capi-task-h.md#ffrt_task_attr_set_delay), the input and output dependencies no longer take effect, and the task will be scheduled after the delay expires.|
| [FFRT_C_API ffrt_task_handle_t ffrt_submit_h_f(ffrt_function_t func, void* arg, const ffrt_deps_t* in_deps, const ffrt_deps_t* out_deps, const ffrt_task_attr_t* attr)](#ffrt_submit_h_f) | Submits a task for scheduling and execution, and returns the task handle. It is a simplified form of the [ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base) API. This API wraps the given task function and its parameters into a general task struct (<idp:inline displayname="code" id="code8234733171317">ffrt_function_kind_general</idp:inline>). The task destroy callback (`after_func`), which is used for post-execution cleanup, is set to `NULL`, thereby omitting any additional cleanup actions. The wrapped task struct is then submitted via the [ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base) API. If a delay time has been set for the task attribute via [ffrt_task_attr_set_delay](capi-task-h.md#ffrt_task_attr_set_delay), the input and output dependencies no longer take effect, and the task will be scheduled after the delay expires. The returned task handle needs to be destroyed via [ffrt_task_handle_destroy](capi-task-h.md#ffrt_task_handle_destroy).|
| [FFRT_C_API uint32_t ffrt_task_handle_inc_ref(ffrt_task_handle_t handle)](#ffrt_task_handle_inc_ref) | Increments the reference count of the task handle. The reference count of the task handle is increased by one, and the value before the increment is returned.|
| [FFRT_C_API uint32_t ffrt_task_handle_dec_ref(ffrt_task_handle_t handle)](#ffrt_task_handle_dec_ref) | Decreases the number of task handle references. The reference count of the task handle is decreased by one, and the value before the decrement is returned. This API must be used together with [ffrt_task_handle_inc_ref](capi-task-h.md#ffrt_task_handle_inc_ref). When a handle is no longer used, destroy it via [ffrt_task_handle_destroy](capi-task-h.md#ffrt_task_handle_destroy).|
| [FFRT_C_API void ffrt_task_handle_destroy(ffrt_task_handle_t handle)](#ffrt_task_handle_destroy) | Destroys a task handle. After this API is called, the task handle is destroyed and the associated resources are released. The handle can no longer be used.|
| [FFRT_C_API void ffrt_wait_deps(const ffrt_deps_t* deps)](#ffrt_wait_deps) | Blocks the current task and waits for the dependent tasks to complete before continuing execution.|
| [FFRT_C_API void ffrt_wait(void)](#ffrt_wait) | Blocks the current task and waits for all submitted tasks to complete before continuing execution.|

## Function Description

### ffrt_task_attr_init()

```c
FFRT_C_API int ffrt_task_attr_init(ffrt_task_attr_t* attr)
```

**Description**

Initializes a task attribute. After the call is successful, the task attribute is set to the default value (for example, the default QoS is [ffrt_qos_default](capi-type-def-h.md#ffrt_qos_default_t)). Call [ffrt_task_attr_destroy](capi-task-h.md#ffrt_task_attr_destroy) to release the task attribute after use.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | Pointer to the task attribute.|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | If the task attribute initialization is successful, `0` is returned.<br>         Otherwise, `-1` is returned.|

### ffrt_task_attr_set_name()

```c
FFRT_C_API void ffrt_task_attr_set_name(ffrt_task_attr_t* attr, const char* name)
```

**Description**

Sets the name of a task attribute.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | Pointer to the task attribute.|
| const char* name | Pointer to the task name.|

### ffrt_task_attr_get_name()

```c
FFRT_C_API const char* ffrt_task_attr_get_name(const ffrt_task_attr_t* attr)
```

**Description**

Obtains the name of a task attribute.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [const ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | Pointer to the task attribute.|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API const char* | If the operation is successful, a non-null pointer to the task attribute name is returned.<br>         Otherwise, a null pointer is returned.|

### ffrt_task_attr_destroy()

```c
FFRT_C_API void ffrt_task_attr_destroy(ffrt_task_attr_t* attr)
```

**Description**

Destroys a task attribute. This API must be called on a task attribute that has been initialized by [ffrt_task_attr_init](capi-task-h.md#ffrt_task_attr_init) to release the resources held by the attribute. Once destroyed, the task attribute cannot be used anymore.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | Pointer to the task attribute.|

### ffrt_task_attr_set_qos()

```c
FFRT_C_API void ffrt_task_attr_set_qos(ffrt_task_attr_t* attr, ffrt_qos_t qos)
```

**Description**

Sets the QoS in a task attribute. QoS is used to control the scheduling priority of a task. For example, you can configure a high QoS for user-interactive tasks to ensure responsiveness, and configure a low QoS for background or maintenance tasks to minimize their system resource usage.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | Pointer to the task attribute.|
| [ffrt_qos_t](capi-type-def-h.md#variables) qos| QoS level to be set. For details about the values, see [ffrt_qos_t](capi-type-def-h.md#variables).|

### ffrt_task_attr_get_qos()

```c
FFRT_C_API ffrt_qos_t ffrt_task_attr_get_qos(const ffrt_task_attr_t* attr)
```

**Description**

Obtains the QoS in a task attribute.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [const ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | Pointer to the task attribute.|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API [ffrt_qos_t](capi-type-def-h.md#variables)| QoS level. By default, `ffrt_qos_default` is returned.|

### ffrt_task_attr_set_delay()

```c
FFRT_C_API void ffrt_task_attr_set_delay(ffrt_task_attr_t* attr, uint64_t delay_us)
```

**Description**

Sets the delay time in a task attribute.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | Pointer to the task attribute.|
| uint64_t delay_us | Task delay time, in microseconds.|

### ffrt_task_attr_get_delay()

```c
FFRT_C_API uint64_t ffrt_task_attr_get_delay(const ffrt_task_attr_t* attr)
```

**Description**

Obtains the delay time in a task attribute.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [const ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | Pointer to the task attribute.|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API uint64_t | Task delay time, in microseconds.|

### ffrt_task_attr_set_queue_priority()

```c
FFRT_C_API void ffrt_task_attr_set_queue_priority(ffrt_task_attr_t* attr, ffrt_queue_priority_t priority)
```

**Description**

Sets the priority in a task attribute.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | Pointer to the task attribute.|
| [ffrt_queue_priority_t](capi-type-def-h.md#ffrt_queue_priority_t) priority | Execution priority of concurrent queue tasks. For details about the values, see [ffrt_queue_priority_t](capi-type-def-h.md#ffrt_queue_priority_t). Within the same concurrent queue, tasks with a higher priority are scheduled ahead of those with a lower priority. Values beyond the valid range will be silently ignored.|

### ffrt_task_attr_get_queue_priority()

```c
FFRT_C_API ffrt_queue_priority_t ffrt_task_attr_get_queue_priority(const ffrt_task_attr_t* attr)
```

**Description**

Obtains the priority in a task attribute.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | Pointer to the task attribute.|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API [ffrt_queue_priority_t](capi-type-def-h.md#ffrt_queue_priority_t) | Priority of a task in a queue.|

### ffrt_task_attr_set_stack_size()

```c
FFRT_C_API void ffrt_task_attr_set_stack_size(ffrt_task_attr_t* attr, uint64_t size)
```

**Description**

Sets the stack size in a task attribute.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | Pointer to the task attribute.|
| uint64_t size | Size of the task stack, in bytes. The value must be greater than the minimum stack size supported by the system. Otherwise, stack overflow may occur.<br>          If the value is too large, memory allocation may fail.|

### ffrt_task_attr_get_stack_size()

```c
FFRT_C_API uint64_t ffrt_task_attr_get_stack_size(const ffrt_task_attr_t* attr)
```

**Description**

Obtains the stack size in a task attribute.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | Pointer to the task attribute.|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API uint64_t | Size of the task stack, in bytes.|

### ffrt_this_task_update_qos()

```c
FFRT_C_API int ffrt_this_task_update_qos(ffrt_qos_t qos)
```

**Description**

Updates the QoS of the current task. This API is used to dynamically adjust the scheduling priority based on the running phase during task execution. For example, after a user triggers a related operation for a background synchronization task, this API can be used to increase the QoS level to accelerate the processing speed.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_qos_t](capi-type-def-h.md#variables) qos| QoS level to be updated. For details about the values, see [ffrt_qos_t](capi-type-def-h.md#variables).|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | If the operation is successful or the new QoS is the same as the current QoS, `0` is returned.<br>         If the QoS mapping is not registered, the current task is empty, or the current task is not a general task (that is, the task is not submitted through [ffrt_submit_base](capi-task-h.md#ffrt_submit_base) or [ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base)), `1` is returned.|

**References**

[ffrt_this_task_get_qos](capi-task-h.md#ffrt_this_task_get_qos)


### ffrt_this_task_get_qos()

```c
FFRT_C_API ffrt_qos_t ffrt_this_task_get_qos(void)
```

**Description**

Obtains the QoS of the current task.

**Since**: 12

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API [ffrt_qos_t](capi-type-def-h.md#variables)| Task QoS.|

### ffrt_this_task_get_id()

```c
FFRT_C_API uint64_t ffrt_this_task_get_id(void)
```

**Description**

Obtains the ID of the current task.

**Since**: 10

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API uint64_t | Unique ID of the current running task.|

### ffrt_alloc_auto_managed_function_storage_base()

```c
FFRT_C_API void *ffrt_alloc_auto_managed_function_storage_base(ffrt_function_kind_t kind)
```

**Description**

Allocates memory for the function execution struct. The allocated memory is used for task executor encapsulation and is passed when submitting a task via [ffrt_submit_base](capi-task-h.md#ffrt_submit_base) or [ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base). The memory is automatically released by the FFRT runtime after the submitted task completes, so the caller does not need to free it manually.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_function_kind_t](capi-type-def-h.md#ffrt_function_kind_t) kind | Function execution struct type. The general type applies to tasks submitted through [ffrt_submit_base](capi-task-h.md#ffrt_submit_base) or [ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base).<br>          The queue type applies to tasks submitted through the concurrent queue submission API.|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API void * | If the operation is successful, a non-null pointer is returned.<br>         Otherwise, a null pointer is returned.|

**References**

[ffrt_submit_base](capi-task-h.md#ffrt_submit_base)

[ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base)


### ffrt_submit_base()

```c
FFRT_C_API void ffrt_submit_base(ffrt_function_header_t* f, const ffrt_deps_t* in_deps, const ffrt_deps_t* out_deps, const ffrt_task_attr_t* attr)
```

**Description**

Submits a task for scheduling and execution. The task execution body, input dependencies, output dependencies, and task attribute are submitted together to the FFRT scheduler. The scheduler determines the execution timing based on dependency relationships and task QoS, and selects a worker thread to execute the task. This API is a low-level submission API. If the task does not require a destroy callback, the simplified API [ffrt_submit_f](capi-task-h.md#ffrt_submit_f) can be used instead. Unlike [ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base), this API does not return a task handle, making it suitable for scenarios where subsequent dependency management or waiting on the submitted task is not required. If a delay time has been set for the task attribute via [ffrt_task_attr_set_delay](capi-task-h.md#ffrt_task_attr_set_delay), the input and output dependencies no longer take effect, and the task will be scheduled after the delay expires.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_function_header_t](capi-ffrt-ffrt-function-header-t.md)* f | Pointer to the task execution body wrapper. The memory must be allocated via [ffrt_alloc_auto_managed_function_storage_base](capi-task-h.md#ffrt_alloc_auto_managed_function_storage_base), and it must contain the task destroy callback function.|
| [const ffrt_deps_t](capi-ffrt-ffrt-deps-t.md)* in_deps | Pointer to the input dependencies.|
| [const ffrt_deps_t](capi-ffrt-ffrt-deps-t.md)* out_deps | Pointer to the output dependencies.|
| [const ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | Pointer to the task attribute.|

**References**

[ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base)


### ffrt_submit_h_base()

```c
FFRT_C_API ffrt_task_handle_t ffrt_submit_h_base(ffrt_function_header_t* f, const ffrt_deps_t* in_deps, const ffrt_deps_t* out_deps, const ffrt_task_attr_t* attr)
```

**Description**

Submits a task for scheduling and execution and returns the task handle. The task execution body, input dependencies, output dependencies, and task attribute are submitted together to the FFRT scheduler. The scheduler determines the execution timing based on dependency relationships. The returned task handle can be used to wait for the task to complete via [ffrt_wait_deps](capi-task-h.md#ffrt_wait_deps), or to be used as an input dependency for other tasks to build dependency relationships between tasks. This API is a low-level submission API that returns a task handle. If the task does not require a destroy callback, the simplified API [ffrt_submit_h_f](capi-task-h.md#ffrt_submit_h_f) can be used instead. The returned task handle must be destroyed via [ffrt_task_handle_destroy](capi-task-h.md#ffrt_task_handle_destroy). Its reference count can be managed using [ffrt_task_handle_inc_ref](capi-task-h.md#ffrt_task_handle_inc_ref) and [ffrt_task_handle_dec_ref](capi-task-h.md#ffrt_task_handle_dec_ref).

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_function_header_t](capi-ffrt-ffrt-function-header-t.md)* f | Pointer to the task execution body wrapper. The memory must be allocated via [ffrt_alloc_auto_managed_function_storage_base](capi-task-h.md#ffrt_alloc_auto_managed_function_storage_base), and it must contain the task destroy callback function.|
| [const ffrt_deps_t](capi-ffrt-ffrt-deps-t.md)* in_deps | Pointer to the input dependencies.|
| [const ffrt_deps_t](capi-ffrt-ffrt-deps-t.md)* out_deps | Pointer to the output dependencies.|
| [const ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | Pointer to the task attribute.|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API [ffrt_task_handle_t](capi-ffrt-ffrt-task-handle-t.md) | If the operation is successful, a non-null task handle is returned.<br>         Otherwise, a null pointer is returned.|

**References**

[ffrt_submit_base](capi-task-h.md#ffrt_submit_base)


### ffrt_submit_f()

```c
FFRT_C_API void ffrt_submit_f(ffrt_function_t func, void* arg, const ffrt_deps_t* in_deps, const ffrt_deps_t* out_deps, const ffrt_task_attr_t* attr)
```

**Description**

Submits a task for scheduling and execution. It is a simplified form of the [ffrt_submit_base](capi-task-h.md#ffrt_submit_base) API. This API wraps the given task function and its parameters into a general task struct (<idp:inline displayname="code" id="code152351336137">ffrt_function_kind_general</idp:inline>). The task destroy callback (`after_func`), which is used for post-execution cleanup, is set to `NULL`, thereby omitting any additional cleanup actions. The wrapped task struct is then submitted via the [ffrt_submit_base](capi-task-h.md#ffrt_submit_base) API. If a delay time has been set for the task attribute via [ffrt_task_attr_set_delay](capi-task-h.md#ffrt_task_attr_set_delay), the input and output dependencies no longer take effect, and the task will be scheduled after the delay expires.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_function_t](capi-type-def-h.md#ffrt_function_t) func | Task function to be executed.|
| void* arg | Pointer to the parameter or closure data to be passed to the task function.|
| [const ffrt_deps_t](capi-ffrt-ffrt-deps-t.md)* in_deps | Pointer to the input dependencies.|
| [const ffrt_deps_t](capi-ffrt-ffrt-deps-t.md)* out_deps | Pointer to the output dependencies.|
| [const ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | Pointer to the task attribute.|

**References**

[ffrt_submit_base](capi-task-h.md#ffrt_submit_base)


### ffrt_submit_h_f()

```c
FFRT_C_API ffrt_task_handle_t ffrt_submit_h_f(ffrt_function_t func, void* arg, const ffrt_deps_t* in_deps, const ffrt_deps_t* out_deps, const ffrt_task_attr_t* attr)
```

**Description**

Submits a task for scheduling and execution, and returns the task handle. It is a simplified form of the [ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base) API. This API wraps the given task function and its parameters into a general task struct (<idp:inline displayname="code" id="code13235173319137">ffrt_function_kind_general</idp:inline>). The task destroy callback (`after_func`), which is used for post-execution cleanup, is set to `NULL`, thereby omitting any additional cleanup actions. The wrapped task struct is then submitted via the [ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base) API. If a delay time has been set for the task attribute via [ffrt_task_attr_set_delay](capi-task-h.md#ffrt_task_attr_set_delay), the input and output dependencies no longer take effect, and the task will be scheduled after the delay expires. The returned task handle needs to be destroyed via [ffrt_task_handle_destroy](capi-task-h.md#ffrt_task_handle_destroy).

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_function_t](capi-type-def-h.md#ffrt_function_t) func | Task function to be executed.|
| void* arg | Pointer to the parameter or closure data to be passed to the task function.|
| [const ffrt_deps_t](capi-ffrt-ffrt-deps-t.md)* in_deps | Pointer to the input dependencies.|
| [const ffrt_deps_t](capi-ffrt-ffrt-deps-t.md)* out_deps | Pointer to the output dependencies.|
| [const ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | Pointer to the task attribute.|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API [ffrt_task_handle_t](capi-ffrt-ffrt-task-handle-t.md) | If the operation is successful, a non-null task handle is returned.<br>         Otherwise, a null pointer is returned.|

**References**

[ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base)


### ffrt_task_handle_inc_ref()

```c
FFRT_C_API uint32_t ffrt_task_handle_inc_ref(ffrt_task_handle_t handle)
```

**Description**

Increments the reference count of the task handle. The reference count of the task handle is increased by one, and the value before the increment is returned.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_task_handle_t](capi-ffrt-ffrt-task-handle-t.md) handle | Task handle, which is returned by [ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base) or [ffrt_submit_h_f](capi-task-h.md#ffrt_submit_h_f).|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API uint32_t | Reference count value before the task handle is incremented. If the `handle` is `NULL`, `UINT_MAX` is returned.|

### ffrt_task_handle_dec_ref()

```c
FFRT_C_API uint32_t ffrt_task_handle_dec_ref(ffrt_task_handle_t handle)
```

**Description**

Decreases the number of task handle references. The reference count of the task handle is decreased by one, and the value before the decrement is returned. This API must be used together with [ffrt_task_handle_inc_ref](capi-task-h.md#ffrt_task_handle_inc_ref). When a handle is no longer used, destroy it via [ffrt_task_handle_destroy](capi-task-h.md#ffrt_task_handle_destroy).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_task_handle_t](capi-ffrt-ffrt-task-handle-t.md) handle | Task handle.|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API uint32_t | Reference count value before the task handle is incremented. If the `handle` is `NULL`, `UINT_MAX` is returned.|

### ffrt_task_handle_destroy()

```c
FFRT_C_API void ffrt_task_handle_destroy(ffrt_task_handle_t handle)
```

**Description**

Destroys a task handle. After this API is called, the task handle is destroyed and the associated resources are released. The handle can no longer be used.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_task_handle_t](capi-ffrt-ffrt-task-handle-t.md) handle | Task handle.|

### ffrt_wait_deps()

```c
FFRT_C_API void ffrt_wait_deps(const ffrt_deps_t* deps)
```

**Description**

Blocks the current task and waits for the dependent tasks to complete before continuing execution.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [const ffrt_deps_t](capi-ffrt-ffrt-deps-t.md)* deps | Pointer to the dependent task list. The current task is blocked until all tasks referenced by the dependency list have completed execution.|

### ffrt_wait()

```c
FFRT_C_API void ffrt_wait(void)
```

**Description**

Blocks the current task and waits for all submitted tasks to complete before continuing execution.

**Since**: 10
