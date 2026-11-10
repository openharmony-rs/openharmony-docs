# task.h

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1c82fe64143ca179b80fafe272ca5a84323e9159 translatedAt=2026-11-10T03:27:03.793Z pushedAt=2026-11-10T04:57:28.837Z nl=1 -->

## Overview

Declares the C APIs of FFRT tasks, providing functions such as initialization and destruction of task attributes, setting and obtaining of task QoS, task delay management, priority management of concurrent queue tasks, task stack size management, task submission and scheduled execution, task handle reference count management, and task waiting.

**File to include**: <ffrt/task.h>

**Library**: libffrt.z.so

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

## Summary

### Function

| Name| Description|
| -- | -- |
| [FFRT_C_API int ffrt_task_attr_init(ffrt_task_attr_t* attr)](#ffrt_task_attr_init) | Initializes task attributes. After a successful call, the task attributes are set to default values (for example, the default QoS is [ffrt_qos_default](capi-type-def-h.md#ffrt_qos_default_t)). After use, call [ffrt_task_attr_destroy](capi-task-h.md#ffrt_task_attr_destroy) to release the task attributes. |
| [FFRT_C_API void ffrt_task_attr_set_name(ffrt_task_attr_t* attr, const char* name)](#ffrt_task_attr_set_name) | Sets the name of the task attributes. |
| [FFRT_C_API const char* ffrt_task_attr_get_name(const ffrt_task_attr_t* attr)](#ffrt_task_attr_get_name) | Obtains the name of the task attributes. |
| [FFRT_C_API void ffrt_task_attr_destroy(ffrt_task_attr_t* attr)](#ffrt_task_attr_destroy) | Destroys task attributes. This API must be called on task attributes that have been initialized through [ffrt_task_attr_init](capi-task-h.md#ffrt_task_attr_init) to release the resources held by the attributes. After destruction, the task attributes can no longer be used. |
| [FFRT_C_API void ffrt_task_attr_set_qos(ffrt_task_attr_t* attr, ffrt_qos_t qos)](#ffrt_task_attr_set_qos) | Sets the QoS of the task attributes. QoS is used to control the scheduling priority of a task. For example, configure a high QoS for user-interactive tasks to ensure responsiveness, and configure a low QoS for background or maintenance tasks to reduce their occupation of system resources. |
| [FFRT_C_API ffrt_qos_t ffrt_task_attr_get_qos(const ffrt_task_attr_t* attr)](#ffrt_task_attr_get_qos) | Obtains the QoS of the task attributes. |
| [FFRT_C_API void ffrt_task_attr_set_delay(ffrt_task_attr_t* attr, uint64_t delay_us)](#ffrt_task_attr_set_delay) | Sets the delay of the task attributes. |
| [FFRT_C_API uint64_t ffrt_task_attr_get_delay(const ffrt_task_attr_t* attr)](#ffrt_task_attr_get_delay) | Obtains the delay of the task attributes. |
| [FFRT_C_API void ffrt_task_attr_set_queue_priority(ffrt_task_attr_t* attr, ffrt_queue_priority_t priority)](#ffrt_task_attr_set_queue_priority) | Sets the priority of the task attributes. |
| [FFRT_C_API ffrt_queue_priority_t ffrt_task_attr_get_queue_priority(const ffrt_task_attr_t* attr)](#ffrt_task_attr_get_queue_priority) | Obtains the priority of the task attributes. |
| [FFRT_C_API void ffrt_task_attr_set_stack_size(ffrt_task_attr_t* attr, uint64_t size)](#ffrt_task_attr_set_stack_size) | Sets the stack size of the task attributes. |
| [FFRT_C_API uint64_t ffrt_task_attr_get_stack_size(const ffrt_task_attr_t* attr)](#ffrt_task_attr_get_stack_size) | Obtains the stack size of the task attributes. |
| [FFRT_C_API int ffrt_this_task_update_qos(ffrt_qos_t qos)](#ffrt_this_task_update_qos) | Updates the QoS of the current task. Use this API when the scheduling priority needs to be dynamically adjusted according to the execution phase during task execution. For example, after a user triggers a related operation, a background synchronization task can use this API to raise its QoS level to speed up processing. |
| [FFRT_C_API ffrt_qos_t ffrt_this_task_get_qos(void)](#ffrt_this_task_get_qos) | Obtains the QoS of the current task. |
| [FFRT_C_API uint64_t ffrt_this_task_get_id(void)](#ffrt_this_task_get_id) | Obtains the ID of the current task. |
| [FFRT_C_API void *ffrt_alloc_auto_managed_function_storage_base(ffrt_function_kind_t kind)](#ffrt_alloc_auto_managed_function_storage_base) | Allocates memory for the function execution structure. The allocated memory is used as the task execution body packaging and is passed in when submitting a task through [ffrt_submit_base](capi-task-h.md#ffrt_submit_base) or [ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base). This memory is automatically released by the FFRT runtime after the submitted task finishes execution, and the caller does not need to release it manually. |
| [FFRT_C_API void ffrt_submit_base(ffrt_function_header_t* f, const ffrt_deps_t* in_deps, const ffrt_deps_t* out_deps, const ffrt_task_attr_t* attr)](#ffrt_submit_base) | Submits a task for scheduled execution. The task execution body, input dependencies, output dependencies, and task attributes are submitted together to the FFRT scheduler. The scheduler determines the execution timing of the task based on the dependency relationships and the task QoS, and selects a worker thread to execute the task. This API is a low-level submission API. If the task does not require a destruction callback, use the simplified API [ffrt_submit_f](capi-task-h.md#ffrt_submit_f). The difference from [ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base) is that this API does not return a task handle, and is suitable for scenarios where subsequent dependency management or waiting on the submitted task is not required. If a delay has been set in the task attributes through [ffrt_task_attr_set_delay](capi-task-h.md#ffrt_task_attr_set_delay), the input and output dependency relationships no longer take effect, and the task is scheduled after the delay ends. |
| [FFRT_C_API ffrt_task_handle_t ffrt_submit_h_base(ffrt_function_header_t* f, const ffrt_deps_t* in_deps, const ffrt_deps_t* out_deps, const ffrt_task_attr_t* attr)](#ffrt_submit_h_base) | Submits a task for scheduled execution and returns the task handle. The task execution body, input dependencies, output dependencies, and task attributes are submitted together to the FFRT scheduler. The scheduler determines the execution timing of the task based on the dependency relationships. The returned task handle can be used to wait for task completion through [ffrt_wait_deps](capi-task-h.md#ffrt_wait_deps), or used as the input dependency of other tasks to build dependency relationships between tasks. This API is a low-level submission API that returns a task handle. If the task does not require a destruction callback, use the simplified API [ffrt_submit_h_f](capi-task-h.md#ffrt_submit_h_f). The returned task handle must be destroyed through [ffrt_task_handle_destroy](capi-task-h.md#ffrt_task_handle_destroy), and its reference count can be managed through [ffrt_task_handle_inc_ref](capi-task-h.md#ffrt_task_handle_inc_ref) and [ffrt_task_handle_dec_ref](capi-task-h.md#ffrt_task_handle_dec_ref). |
| [FFRT_C_API void ffrt_submit_f(ffrt_function_t func, void* arg, const ffrt_deps_t* in_deps, const ffrt_deps_t* out_deps, const ffrt_task_attr_t* attr)](#ffrt_submit_f) | Submits a task for scheduled execution. This is a simplified form of the [ffrt_submit_base](capi-task-h.md#ffrt_submit_base) API. This API packages the given task function and its parameters into a generic task structure (`ffrt_function_kind_general`), in which the task destruction callback (after_func) used to handle post-execution cleanup is set to NULL, thereby omitting any additional cleanup actions. The packaged task structure is then submitted through the [ffrt_submit_base](capi-task-h.md#ffrt_submit_base) API. If a delay has been set in the task attributes through [ffrt_task_attr_set_delay](capi-task-h.md#ffrt_task_attr_set_delay), the input and output dependency relationships no longer take effect, and the task is scheduled after the delay ends. |
| [FFRT_C_API ffrt_task_handle_t ffrt_submit_h_f(ffrt_function_t func, void* arg, const ffrt_deps_t* in_deps, const ffrt_deps_t* out_deps, const ffrt_task_attr_t* attr)](#ffrt_submit_h_f) | Submits a task for scheduled execution and returns the task handle. This is a simplified form of the [ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base) API. This API packages the given task function and its parameters into a generic task structure (`ffrt_function_kind_general`), in which the task destruction callback (after_func) used to handle post-execution cleanup is set to NULL, thereby omitting any additional cleanup actions. The packaged task structure is then submitted through the [ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base) API. If a delay has been set in the task attributes through [ffrt_task_attr_set_delay](capi-task-h.md#ffrt_task_attr_set_delay), the input and output dependency relationships no longer take effect, and the task is scheduled after the delay ends. The returned task handle must be destroyed through [ffrt_task_handle_destroy](capi-task-h.md#ffrt_task_handle_destroy). |
| [FFRT_C_API uint32_t ffrt_task_handle_inc_ref(ffrt_task_handle_t handle)](#ffrt_task_handle_inc_ref) | Increments the reference count of the task handle. The reference count of the task handle is incremented by one, and the reference count value before the increment is returned. |
| [FFRT_C_API uint32_t ffrt_task_handle_dec_ref(ffrt_task_handle_t handle)](#ffrt_task_handle_dec_ref) | Decrements the reference count of the task handle. The reference count of the task handle is decremented by one, and the reference count value before the decrement is returned. This API should be used in pairs with [ffrt_task_handle_inc_ref](capi-task-h.md#ffrt_task_handle_inc_ref). When the handle is no longer used, it must be destroyed through [ffrt_task_handle_destroy](capi-task-h.md#ffrt_task_handle_destroy). |
| [FFRT_C_API void ffrt_task_handle_destroy(ffrt_task_handle_t handle)](#ffrt_task_handle_destroy) | Destroys the task handle. After the call, the task handle is destroyed and the associated resources are released, and the handle can no longer be used. |
| [FFRT_C_API void ffrt_wait_deps(const ffrt_deps_t* deps)](#ffrt_wait_deps) | Blocks the current task until the dependent tasks are complete, and then continues execution. |
| [FFRT_C_API void ffrt_wait(void)](#ffrt_wait) | Blocks the current task until all submitted tasks are complete, and then continues execution. |

## Function Description

### ffrt_task_attr_init()

```c
FFRT_C_API int ffrt_task_attr_init(ffrt_task_attr_t* attr)
```

**Description**

Initializes task attributes. After a successful call, the task attributes are set to default values (for example, the default QoS is [ffrt_qos_default](capi-type-def-h.md#ffrt_qos_default_t)). After use, call [ffrt_task_attr_destroy](capi-task-h.md#ffrt_task_attr_destroy) to release the task attributes.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | Pointer to the task attributes. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | Returns `0` if the task attributes are initialized successfully;<br>         otherwise returns `-1`. |

### ffrt_task_attr_set_name()

```c
FFRT_C_API void ffrt_task_attr_set_name(ffrt_task_attr_t* attr, const char* name)
```

**Description**

Sets the name of the task attributes.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | Pointer to the task attributes. |
| const char* name | Pointer to the task name. |

### ffrt_task_attr_get_name()

```c
FFRT_C_API const char* ffrt_task_attr_get_name(const ffrt_task_attr_t* attr)
```

**Description**

Obtains the name of the task attributes.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [const ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | Pointer to the task attributes. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API const char* | Non-null pointer to the task name if the task name is obtained successfully;<br>         otherwise, a null pointer. |

### ffrt_task_attr_destroy()

```c
FFRT_C_API void ffrt_task_attr_destroy(ffrt_task_attr_t* attr)
```

**Description**

Destroys task attributes. This API must be called on task attributes that have been initialized through [ffrt_task_attr_init](capi-task-h.md#ffrt_task_attr_init) to release the resources held by the attributes. After destruction, the task attributes can no longer be used.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | Pointer to the task attributes. |

### ffrt_task_attr_set_qos()

```c
FFRT_C_API void ffrt_task_attr_set_qos(ffrt_task_attr_t* attr, ffrt_qos_t qos)
```

**Description**

Sets the QoS of the task attributes. QoS is used to control the scheduling priority of a task. For example, configure a high QoS for user-interactive tasks to ensure responsiveness, and configure a low QoS for background or maintenance tasks to reduce their occupation of system resources.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | Pointer to the task attributes. |
| [ffrt_qos_t](capi-type-def-h.md#variables) qos | QoS level to set. For details, see [ffrt_qos_t](capi-type-def-h.md#variables). |

### ffrt_task_attr_get_qos()

```c
FFRT_C_API ffrt_qos_t ffrt_task_attr_get_qos(const ffrt_task_attr_t* attr)
```

**Description**

Obtains the QoS of the task attributes.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [const ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | Pointer to the task attributes. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API [ffrt_qos_t](capi-type-def-h.md#variables) | Obtains the QoS level. The default value is `ffrt_qos_default`. |

### ffrt_task_attr_set_delay()

```c
FFRT_C_API void ffrt_task_attr_set_delay(ffrt_task_attr_t* attr, uint64_t delay_us)
```

**Description**

Sets the delay of the task attributes.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | Pointer to the task attributes. |
| uint64_t delay_us | Task delay, in microseconds. |

### ffrt_task_attr_get_delay()

```c
FFRT_C_API uint64_t ffrt_task_attr_get_delay(const ffrt_task_attr_t* attr)
```

**Description**

Obtains the delay of the task attributes.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [const ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | Pointer to the task attributes. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API uint64_t | Task delay time, in microseconds. |

### ffrt_task_attr_set_queue_priority()

```c
FFRT_C_API void ffrt_task_attr_set_queue_priority(ffrt_task_attr_t* attr, ffrt_queue_priority_t priority)
```

**Description**

Sets the priority of the task attributes.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | Pointer to the task attributes. |
| [ffrt_queue_priority_t](capi-type-def-h.md#ffrt_queue_priority_t) priority | Execution priority of a task in the concurrent queue. For the value range, see [ffrt_queue_priority_t](capi-type-def-h.md#ffrt_queue_priority_t). Within the same concurrent queue, a task with a higher priority is scheduled before a task with a lower priority. Values outside the valid range are silently ignored. |

### ffrt_task_attr_get_queue_priority()

```c
FFRT_C_API ffrt_queue_priority_t ffrt_task_attr_get_queue_priority(const ffrt_task_attr_t* attr)
```

**Description**

Obtains the priority of the task attributes.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | Pointer to the task attributes. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API [ffrt_queue_priority_t](capi-type-def-h.md#ffrt_queue_priority_t) | Priority of a task in a concurrent queue. |

### ffrt_task_attr_set_stack_size()

```c
FFRT_C_API void ffrt_task_attr_set_stack_size(ffrt_task_attr_t* attr, uint64_t size)
```

**Description**

Sets the stack size of the task attributes.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | Pointer to the task attributes. |
| uint64_t size | Task stack size, in bytes. It must be greater than the minimum stack size supported by the system; otherwise, a stack overflow may occur.<br> If it is set too large, memory allocation may fail. |

### ffrt_task_attr_get_stack_size()

```c
FFRT_C_API uint64_t ffrt_task_attr_get_stack_size(const ffrt_task_attr_t* attr)
```

**Description**

Obtains the stack size of the task attributes.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | Pointer to the task attributes. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API uint64_t | Task stack size, in bytes. |

### ffrt_this_task_update_qos()

```c
FFRT_C_API int ffrt_this_task_update_qos(ffrt_qos_t qos)
```

**Description**

Updates the QoS of the current task. This API is used when the scheduling priority needs to be dynamically adjusted based on the running phase during task execution. For example, after a user triggers a related operation, a background synchronization task can use this API to raise its QoS level to speed up processing.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_qos_t](capi-type-def-h.md#variables) qos | QoS level of the task to be updated. For details, see [ffrt_qos_t](capi-type-def-h.md#variables). |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | Returns `0` if the QoS is updated successfully or the new QoS is the same as the current QoS;<br>         Returns `1` if the QoS mapping is not registered, the current task is empty, or the current task is not a generic task (that is, not a task submitted through [ffrt_submit_base](capi-task-h.md#ffrt_submit_base) or [ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base)). |

**Reference**

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
| FFRT_C_API [ffrt_qos_t](capi-type-def-h.md#variables) | Task QoS. |

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
| FFRT_C_API uint64_t | Unique task ID of the currently running task. |

### ffrt_alloc_auto_managed_function_storage_base()

```c
FFRT_C_API void *ffrt_alloc_auto_managed_function_storage_base(ffrt_function_kind_t kind)
```

**Description**

Allocates memory for the function execution structure. The allocated memory is used as the task execution body encapsulation and is passed in when submitting a task through [ffrt_submit_base](capi-task-h.md#ffrt_submit_base) or [ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base). After the submitted task is executed, this memory is automatically released by the FFRT runtime, and the caller does not need to release it manually.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_function_kind_t](capi-type-def-h.md#ffrt_function_kind_t) kind | Type of the function execution structure. The generic type applies to tasks submitted through [ffrt_submit_base](capi-task-h.md#ffrt_submit_base) or [ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base), <br>          and the queue type applies to tasks submitted through the concurrent queue submission API. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API void * | Non-null pointer if the memory is allocated successfully;<br>         otherwise, a null pointer. |

**Reference**

[ffrt_submit_base](capi-task-h.md#ffrt_submit_base)

[ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base)


### ffrt_submit_base()

```c
FFRT_C_API void ffrt_submit_base(ffrt_function_header_t* f, const ffrt_deps_t* in_deps, const ffrt_deps_t* out_deps, const ffrt_task_attr_t* attr)
```

**Description**

Submits a task for scheduled execution. The task execution body, input dependencies, output dependencies, and task attributes are submitted together to the FFRT scheduler, which determines the execution timing of the task based on the dependency relationships and task QoS, and selects a worker thread to execute the task. This API is a low-level submission API. If the task does not require a destroy callback, use the simplified API [ffrt_submit_f](capi-task-h.md#ffrt_submit_f). The difference from [ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base) is that this API does not return a task handle, and is suitable for scenarios where subsequent dependency management or waiting on the submitted task is not required. If a delay time has been set in the task attributes through [ffrt_task_attr_set_delay](capi-task-h.md#ffrt_task_attr_set_delay), the input and output dependency relationships no longer take effect, and the task is scheduled after the delay ends.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_function_header_t](capi-ffrt-ffrt-function-header-t.md)* f | Pointer to the task execution body wrapper. The memory must be allocated through [ffrt_alloc_auto_managed_function_storage_base](capi-task-h.md#ffrt_alloc_auto_managed_function_storage_base), and the task destruction callback function must be included. |
| [const ffrt_deps_t](capi-ffrt-ffrt-deps-t.md)* in_deps | Pointer to the input dependency. |
| [const ffrt_deps_t](capi-ffrt-ffrt-deps-t.md)* out_deps | Pointer to the output dependency. |
| [const ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | Pointer to the task attributes. |

**Reference**

[ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base)


### ffrt_submit_h_base()

```c
FFRT_C_API ffrt_task_handle_t ffrt_submit_h_base(ffrt_function_header_t* f, const ffrt_deps_t* in_deps, const ffrt_deps_t* out_deps, const ffrt_task_attr_t* attr)
```

**Description**

Submits a task for scheduled execution and returns a task handle. The task execution body, input dependencies, output dependencies, and task attributes are submitted together to the FFRT scheduler, which determines the execution timing of the task based on the dependency relationships. The returned task handle can be used to wait for task completion through [ffrt_wait_deps](capi-task-h.md#ffrt_wait_deps), or used as an input dependency of other tasks to build dependency relationships between tasks. This API is a low-level submission API that returns a task handle. If the task does not require a destroy callback, use the simplified API [ffrt_submit_h_f](capi-task-h.md#ffrt_submit_h_f). The returned task handle must be destroyed through [ffrt_task_handle_destroy](capi-task-h.md#ffrt_task_handle_destroy), and its reference count can be managed through [ffrt_task_handle_inc_ref](capi-task-h.md#ffrt_task_handle_inc_ref) and [ffrt_task_handle_dec_ref](capi-task-h.md#ffrt_task_handle_dec_ref).

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_function_header_t](capi-ffrt-ffrt-function-header-t.md)* f | Pointer to the task execution body wrapper. The memory must be allocated through [ffrt_alloc_auto_managed_function_storage_base](capi-task-h.md#ffrt_alloc_auto_managed_function_storage_base), and a task destruction callback function must be included. |
| [const ffrt_deps_t](capi-ffrt-ffrt-deps-t.md)* in_deps | Pointer to the input dependency. |
| [const ffrt_deps_t](capi-ffrt-ffrt-deps-t.md)* out_deps | Pointer to the output dependency. |
| [const ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | Pointer to the task attributes. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API [ffrt_task_handle_t](capi-ffrt-ffrt-task-handle-t.md) | Non-null task handle if the task is submitted successfully;<br>         otherwise, a null pointer. |

**Reference**

[ffrt_submit_base](capi-task-h.md#ffrt_submit_base)


### ffrt_submit_f()

```c
FFRT_C_API void ffrt_submit_f(ffrt_function_t func, void* arg, const ffrt_deps_t* in_deps, const ffrt_deps_t* out_deps, const ffrt_task_attr_t* attr)
```

**Description**

Submits a task for scheduled execution. It is a simplified form of the [ffrt_submit_base](capi-task-h.md#ffrt_submit_base) API. This API wraps the given task function and its parameters into a generic task structure (`ffrt_function_kind_general`), in which the task destroy callback (after_func) used to handle post-execution cleanup is set to NULL, thereby omitting any additional cleanup actions. The wrapped task structure is then submitted through the [ffrt_submit_base](capi-task-h.md#ffrt_submit_base) API. If a delay time has been set in the task attributes through [ffrt_task_attr_set_delay](capi-task-h.md#ffrt_task_attr_set_delay), the input and output dependency relationships no longer take effect, and the task is scheduled after the delay ends.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_function_t](capi-type-def-h.md#ffrt_function_t) func | Task function to be executed. |
| void* arg | Pointer to the parameter or closure data passed to the task function. |
| [const ffrt_deps_t](capi-ffrt-ffrt-deps-t.md)* in_deps | Pointer to the input dependency. |
| [const ffrt_deps_t](capi-ffrt-ffrt-deps-t.md)* out_deps | Pointer to the output dependency. |
| [const ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | Pointer to the task attributes. |

**References**

[ffrt_submit_base](capi-task-h.md#ffrt_submit_base)


### ffrt_submit_h_f()

```c
FFRT_C_API ffrt_task_handle_t ffrt_submit_h_f(ffrt_function_t func, void* arg, const ffrt_deps_t* in_deps, const ffrt_deps_t* out_deps, const ffrt_task_attr_t* attr)
```

**Description**

Submits a task for scheduled execution and returns a task handle. It is a simplified form of the [ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base) API. This API wraps the given task function and its parameters into a generic task structure (`ffrt_function_kind_general`), in which the task destroy callback (after_func) used to handle post-execution cleanup is set to NULL, thereby omitting any additional cleanup actions. The wrapped task structure is then submitted through the [ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base) API. If a delay time has been set in the task attributes through [ffrt_task_attr_set_delay](capi-task-h.md#ffrt_task_attr_set_delay), the input and output dependency relationships no longer take effect, and the task is scheduled after the delay ends. The returned task handle must be destroyed through [ffrt_task_handle_destroy](capi-task-h.md#ffrt_task_handle_destroy).

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_function_t](capi-type-def-h.md#ffrt_function_t) func | Task function to be executed. |
| void* arg | Pointer to the parameter or closure data passed to the task function. |
| [const ffrt_deps_t](capi-ffrt-ffrt-deps-t.md)* in_deps | Pointer to the input dependency. |
| [const ffrt_deps_t](capi-ffrt-ffrt-deps-t.md)* out_deps | Pointer to the output dependency. |
| [const ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | Pointer to the task attributes. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API [ffrt_task_handle_t](capi-ffrt-ffrt-task-handle-t.md) | Non-null task handle if the task is submitted successfully;<br>         null pointer otherwise. |

**References**

[ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base)


### ffrt_task_handle_inc_ref()

```c
FFRT_C_API uint32_t ffrt_task_handle_inc_ref(ffrt_task_handle_t handle)
```

**Description**

Increments the reference count of a task handle. The reference count of the task handle is incremented by one, and the reference count value before the increment is returned.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_task_handle_t](capi-ffrt-ffrt-task-handle-t.md) handle | Task handle, returned by [ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base) or [ffrt_submit_h_f](capi-task-h.md#ffrt_submit_h_f). |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API uint32_t | Reference count of the task handle before the increment; returns `UINT_MAX` if `handle` is null. |

### ffrt_task_handle_dec_ref()

```c
FFRT_C_API uint32_t ffrt_task_handle_dec_ref(ffrt_task_handle_t handle)
```

**Description**

Decrements the reference count of a task handle. The reference count of the task handle is decremented by one, and the reference count value before the decrement is returned. This API should be used in pairs with [ffrt_task_handle_inc_ref](capi-task-h.md#ffrt_task_handle_inc_ref). When the handle is no longer in use, it must be destroyed through [ffrt_task_handle_destroy](capi-task-h.md#ffrt_task_handle_destroy).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_task_handle_t](capi-ffrt-ffrt-task-handle-t.md) handle | Task handle.|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API uint32_t | Reference count of the task handle before decrementing; if `handle` is null, `UINT_MAX` is returned. |

### ffrt_task_handle_destroy()

```c
FFRT_C_API void ffrt_task_handle_destroy(ffrt_task_handle_t handle)
```

**Description**

Destroys a task handle. After the call, the task handle is destroyed and the associated resources are released, and the handle can no longer be used.

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
| [const ffrt_deps_t](capi-ffrt-ffrt-deps-t.md)* deps | Pointer to the dependency task list. Blocks the current task until all tasks referenced by the dependency list are executed. |

### ffrt_wait()

```c
FFRT_C_API void ffrt_wait(void)
```

**Description**

Blocks the current task and waits for all submitted tasks to complete before continuing execution.

**Since**: 10


