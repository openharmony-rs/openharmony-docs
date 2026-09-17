# task.h

## Overview

Declares the FFRT task C APIs, including task attribute initialization and destruction, task QoS configuration, task delay time management, concurrent queue task priority management, task stack size management, task submission and scheduling, task handle reference counting, and task wait operations.

**Library**: libffrt.z.so

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [FFRT_C_API int ffrt_task_attr_init(ffrt_task_attr_t* attr)](#ffrt_task_attr_init) | Initializes a task attribute.<br> After the call, the task attribute is set to its default values (for example, the QoS defaults to {@link ffrt_qos_default}). The caller is expected to invoke [ffrt_task_attr_destroy](capi-task-h.md#ffrt_task_attr_destroy) to release the attribute when it is no longer needed. |
| [FFRT_C_API void ffrt_task_attr_set_name(ffrt_task_attr_t* attr, const char* name)](#ffrt_task_attr_set_name) | Sets the name of a task attribute. |
| [FFRT_C_API const char* ffrt_task_attr_get_name(const ffrt_task_attr_t* attr)](#ffrt_task_attr_get_name) | Gets the name of a task attribute. |
| [FFRT_C_API void ffrt_task_attr_destroy(ffrt_task_attr_t* attr)](#ffrt_task_attr_destroy) | Destroys a task attribute.<br> This interface must be called on a task attribute that was previously initialized with [ffrt_task_attr_init](capi-task-h.md#ffrt_task_attr_init), and is used to release the resources held by the attribute. The attribute must not be used again after destruction. |
| [FFRT_C_API void ffrt_task_attr_set_qos(ffrt_task_attr_t* attr, ffrt_qos_t qos)](#ffrt_task_attr_set_qos) | Sets the QoS of a task attribute.<br> The QoS controls the scheduling priority of the task. For example, assign a higher QoS to user-facing work to keep the response time low, and a lower QoS to background or housekeeping work to reduce its impact on system resources. |
| [FFRT_C_API ffrt_qos_t ffrt_task_attr_get_qos(const ffrt_task_attr_t* attr)](#ffrt_task_attr_get_qos) | Gets the QoS of a task attribute. |
| [FFRT_C_API void ffrt_task_attr_set_delay(ffrt_task_attr_t* attr, uint64_t delay_us)](#ffrt_task_attr_set_delay) | Sets the delay time of a task attribute. |
| [FFRT_C_API uint64_t ffrt_task_attr_get_delay(const ffrt_task_attr_t* attr)](#ffrt_task_attr_get_delay) | Gets the delay time of a task attribute. |
| [FFRT_C_API void ffrt_task_attr_set_queue_priority(ffrt_task_attr_t* attr, ffrt_queue_priority_t priority)](#ffrt_task_attr_set_queue_priority) | Sets the priority of a task attribute. |
| [FFRT_C_API ffrt_queue_priority_t ffrt_task_attr_get_queue_priority(const ffrt_task_attr_t* attr)](#ffrt_task_attr_get_queue_priority) | Gets the priority of a task attribute. |
| [FFRT_C_API void ffrt_task_attr_set_stack_size(ffrt_task_attr_t* attr, uint64_t size)](#ffrt_task_attr_set_stack_size) | Sets the stack size of a task attribute. |
| [FFRT_C_API uint64_t ffrt_task_attr_get_stack_size(const ffrt_task_attr_t* attr)](#ffrt_task_attr_get_stack_size) | Gets the stack size of a task attribute. |
| [FFRT_C_API int ffrt_this_task_update_qos(ffrt_qos_t qos)](#ffrt_this_task_update_qos) | Updates the QoS of this task.<br> Use this interface to adjust the scheduling priority of the currently running task when its priority needs to change during execution, for example when a background task starts to handle a user-initiated operation and requires faster response. |
| [FFRT_C_API ffrt_qos_t ffrt_this_task_get_qos(void)](#ffrt_this_task_get_qos) | Gets the QoS of this task. |
| [FFRT_C_API uint64_t ffrt_this_task_get_id(void)](#ffrt_this_task_get_id) | Gets the ID of this task. |
| [FFRT_C_API void* ffrt_alloc_auto_managed_function_storage_base(ffrt_function_kind_t kind)](#ffrt_alloc_auto_managed_function_storage_base) | Allocates memory for the function execution structure.<br> The allocated memory is used as the task executor wrapper passed to [ffrt_submit_base](capi-task-h.md#ffrt_submit_base) or [ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base) when submitting a task. The memory is automatically released by the FFRT runtime after the submitted task finishes execution, so the caller does not need to free it manually. |
| [FFRT_C_API void ffrt_submit_base(ffrt_function_header_t* f, const ffrt_deps_t* in_deps, const ffrt_deps_t* out_deps, const ffrt_task_attr_t* attr)](#ffrt_submit_base) | Submits a task.<br> The task is submitted to the FFRT scheduler together with its input and output dependencies and the task attribute. The scheduler uses the dependencies and the task QoS to determine when the task becomes ready to run and which worker executes it. This is the underlying submission interface; the simplified wrapper [ffrt_submit_f](capi-task-h.md#ffrt_submit_f) can be used when no task destroy callback is required. Unlike [ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base), this interface does not return a task handle and should be used when the caller does not need to track the task after submission.<br> If a task delay has been set on the attribute with [ffrt_task_attr_set_delay](capi-task-h.md#ffrt_task_attr_set_delay), the input and output dependencies are ignored and the task is scheduled after the delay elapses. |
| [FFRT_C_API ffrt_task_handle_t ffrt_submit_h_base(ffrt_function_header_t* f, const ffrt_deps_t* in_deps, const ffrt_deps_t* out_deps, const ffrt_task_attr_t* attr)](#ffrt_submit_h_base) | Submits a task, and obtains a task handle.<br> The task is submitted to the FFRT scheduler together with its input and output dependencies and the task attribute. The scheduler uses the dependencies to determine when the task becomes ready to run. The returned handle can be used with [ffrt_wait_deps](capi-task-h.md#ffrt_wait_deps) to wait for the task, or passed as an input dependency to other submitted tasks to build a dependency chain. This is the underlying submission interface that returns a task handle; the simplified wrapper [ffrt_submit_h_f](capi-task-h.md#ffrt_submit_h_f) can be used when no task destroy callback is required. The returned handle should be released with [ffrt_task_handle_destroy](capi-task-h.md#ffrt_task_handle_destroy) when it is no longer needed, and its reference count can be managed with [ffrt_task_handle_inc_ref](capi-task-h.md#ffrt_task_handle_inc_ref) and [ffrt_task_handle_dec_ref](capi-task-h.md#ffrt_task_handle_dec_ref). |
| [FFRT_C_API void ffrt_submit_f(ffrt_function_t func, void* arg, const ffrt_deps_t* in_deps, const ffrt_deps_t* out_deps, const ffrt_task_attr_t* attr)](#ffrt_submit_f) | Submits a task, simplified from the [ffrt_submit_base](capi-task-h.md#ffrt_submit_base) interface.<br> This interface wraps the provided task function and its argument into a task wrapper designated as a general task (`ffrt_function_kind_general`). During wrapper creation, the task destroy callback (after_func), which is intended to handle any post-execution cleanup, is set to NULL, thus omitting any additional cleanup actions. The resulting task wrapper is then submitted using the underlying [ffrt_submit_base](capi-task-h.md#ffrt_submit_base) interface.<br> If a task delay has been set on the attribute with [ffrt_task_attr_set_delay](capi-task-h.md#ffrt_task_attr_set_delay), the input and output dependencies are ignored and the task is scheduled after the delay elapses. |
| [FFRT_C_API ffrt_task_handle_t ffrt_submit_h_f(ffrt_function_t func, void* arg, const ffrt_deps_t* in_deps, const ffrt_deps_t* out_deps, const ffrt_task_attr_t* attr)](#ffrt_submit_h_f) | Submits a task, and obtains a handle, simplified from the [ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base) interface.<br> This interface wraps the provided task function and its argument into a task wrapper designated as a general task (`ffrt_function_kind_general`). During wrapper creation, the task destroy callback (after_func), which is intended to handle any post-execution cleanup, is set to NULL, thus omitting any additional cleanup actions. The resulting task wrapper is then submitted using the underlying [ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base) interface.<br> If a task delay has been set on the attribute with [ffrt_task_attr_set_delay](capi-task-h.md#ffrt_task_attr_set_delay), the input and output dependencies are ignored and the task is scheduled after the delay elapses. The returned task handle should be released with [ffrt_task_handle_destroy](capi-task-h.md#ffrt_task_handle_destroy) when it is no longer needed. |
| [FFRT_C_API uint32_t ffrt_task_handle_inc_ref(ffrt_task_handle_t handle)](#ffrt_task_handle_inc_ref) | Increases the reference count of a task handle.<br> The reference count of the task handle is incremented by one, and the value of the reference count before the increment is returned. |
| [FFRT_C_API uint32_t ffrt_task_handle_dec_ref(ffrt_task_handle_t handle)](#ffrt_task_handle_dec_ref) | Decreases the reference count of a task handle.<br> The reference count of the task handle is decremented by one, and the value of the reference count before the decrement is returned. Pair this call with [ffrt_task_handle_inc_ref](capi-task-h.md#ffrt_task_handle_inc_ref) and use [ffrt_task_handle_destroy](capi-task-h.md#ffrt_task_handle_destroy) to release the handle when it is no longer needed. |
| [FFRT_C_API void ffrt_task_handle_destroy(ffrt_task_handle_t handle)](#ffrt_task_handle_destroy) | Destroys a task handle.<br> After the call, the task handle is destroyed and the resources associated with it are released. The handle must not be used again after destruction. |
| [FFRT_C_API void ffrt_wait_deps(const ffrt_deps_t* deps)](#ffrt_wait_deps) | Waits until the dependent tasks are complete. |
| [FFRT_C_API void ffrt_wait(void)](#ffrt_wait) | Waits until all submitted tasks are complete. |

## Function description

### ffrt_task_attr_init()

```c
FFRT_C_API int ffrt_task_attr_init(ffrt_task_attr_t* attr)
```

**Description**

Initializes a task attribute.<br> After the call, the task attribute is set to its default values (for example, the QoS defaults to {@link ffrt_qos_default}). The caller is expected to invoke [ffrt_task_attr_destroy](capi-task-h.md#ffrt_task_attr_destroy) to release the attribute when it is no longer needed.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_task_attr_t* attr | Indicates a pointer to the task attribute. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API int | `0` if the task attribute is initialized;          `-1` otherwise. |

### ffrt_task_attr_set_name()

```c
FFRT_C_API void ffrt_task_attr_set_name(ffrt_task_attr_t* attr, const char* name)
```

**Description**

Sets the name of a task attribute.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_task_attr_t* attr | Indicates a pointer to the task attribute. |
| const char* name | Indicates a pointer to the task name. |

### ffrt_task_attr_get_name()

```c
FFRT_C_API const char* ffrt_task_attr_get_name(const ffrt_task_attr_t* attr)
```

**Description**

Gets the name of a task attribute.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| const ffrt_task_attr_t* attr | Indicates a pointer to the task attribute. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API const char* | A non-null pointer to the task name if the name is obtained;          a null pointer otherwise. |

### ffrt_task_attr_destroy()

```c
FFRT_C_API void ffrt_task_attr_destroy(ffrt_task_attr_t* attr)
```

**Description**

Destroys a task attribute.<br> This interface must be called on a task attribute that was previously initialized with [ffrt_task_attr_init](capi-task-h.md#ffrt_task_attr_init), and is used to release the resources held by the attribute. The attribute must not be used again after destruction.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_task_attr_t* attr | Indicates a pointer to the task attribute. |

### ffrt_task_attr_set_qos()

```c
FFRT_C_API void ffrt_task_attr_set_qos(ffrt_task_attr_t* attr, ffrt_qos_t qos)
```

**Description**

Sets the QoS of a task attribute.<br> The QoS controls the scheduling priority of the task. For example, assign a higher QoS to user-facing work to keep the response time low, and a lower QoS to background or housekeeping work to reduce its impact on system resources.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_task_attr_t* attr | Indicates a pointer to the task attribute. |
| ffrt_qos_t qos | Indicates the QoS level to set. The available levels are defined by {@link ffrt_qos_t}. |

### ffrt_task_attr_get_qos()

```c
FFRT_C_API ffrt_qos_t ffrt_task_attr_get_qos(const ffrt_task_attr_t* attr)
```

**Description**

Gets the QoS of a task attribute.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| const ffrt_task_attr_t* attr | Indicates a pointer to the task attribute. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API ffrt_qos_t | The QoS, which is `ffrt_qos_default` by default. |

### ffrt_task_attr_set_delay()

```c
FFRT_C_API void ffrt_task_attr_set_delay(ffrt_task_attr_t* attr, uint64_t delay_us)
```

**Description**

Sets the delay time of a task attribute.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_task_attr_t* attr | Indicates a pointer to the task attribute. |
| uint64_t delay_us | Indicates the delay time, in microseconds. |

### ffrt_task_attr_get_delay()

```c
FFRT_C_API uint64_t ffrt_task_attr_get_delay(const ffrt_task_attr_t* attr)
```

**Description**

Gets the delay time of a task attribute.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| const ffrt_task_attr_t* attr | Indicates a pointer to the task attribute. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API uint64_t | The delay time, in microseconds. |

### ffrt_task_attr_set_queue_priority()

```c
FFRT_C_API void ffrt_task_attr_set_queue_priority(ffrt_task_attr_t* attr, ffrt_queue_priority_t priority)
```

**Description**

Sets the priority of a task attribute.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_task_attr_t* attr | Indicates a pointer to the task attribute. |
| ffrt_queue_priority_t priority | Indicates the priority of a concurrent queue task. The available priorities are defined by {@link ffrt_queue_priority_t}; higher priorities are scheduled before lower priorities within the same concurrent queue. Values outside the valid range are silently ignored. |

### ffrt_task_attr_get_queue_priority()

```c
FFRT_C_API ffrt_queue_priority_t ffrt_task_attr_get_queue_priority(const ffrt_task_attr_t* attr)
```

**Description**

Gets the priority of a task attribute.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const ffrt_task_attr_t* attr | Indicates a pointer to the task attribute. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API ffrt_queue_priority_t | The priority of a concurrent queue task. |

### ffrt_task_attr_set_stack_size()

```c
FFRT_C_API void ffrt_task_attr_set_stack_size(ffrt_task_attr_t* attr, uint64_t size)
```

**Description**

Sets the stack size of a task attribute.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_task_attr_t* attr | Indicates a pointer to the task attribute. |
| uint64_t size | Indicates the task stack size, in bytes. The value must be greater than the minimum stack size supported by the system, or stack overflow may occur. Setting it too large may result in memory allocation failure. |

### ffrt_task_attr_get_stack_size()

```c
FFRT_C_API uint64_t ffrt_task_attr_get_stack_size(const ffrt_task_attr_t* attr)
```

**Description**

Gets the stack size of a task attribute.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const ffrt_task_attr_t* attr | Indicates a pointer to the task attribute. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API uint64_t | The task stack size, in bytes. |

### ffrt_this_task_update_qos()

```c
FFRT_C_API int ffrt_this_task_update_qos(ffrt_qos_t qos)
```

**Description**

Updates the QoS of this task.<br> Use this interface to adjust the scheduling priority of the currently running task when its priority needs to change during execution, for example when a background task starts to handle a user-initiated operation and requires faster response.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_qos_t qos | Indicates the new QoS level for this task. The available levels are defined by {@link ffrt_qos_t}. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API int | `0` if the QoS is updated, or if the new QoS is the same as the current QoS;          `1` if the QoS map is not registered, the current task is null, or the          current task is not a general-type task (i.e., not submitted through          [ffrt_submit_base](capi-task-h.md#ffrt_submit_base) or [ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base)). |

**Reference**:

[ffrt_this_task_get_qos](capi-task-h.md#ffrt_this_task_get_qos)


### ffrt_this_task_get_qos()

```c
FFRT_C_API ffrt_qos_t ffrt_this_task_get_qos(void)
```

**Description**

Gets the QoS of this task.

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API ffrt_qos_t | The task QoS. |

### ffrt_this_task_get_id()

```c
FFRT_C_API uint64_t ffrt_this_task_get_id(void)
```

**Description**

Gets the ID of this task.

**Since**: 10

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API uint64_t | The unique task ID of the currently running task. |

### ffrt_alloc_auto_managed_function_storage_base()

```c
FFRT_C_API void* ffrt_alloc_auto_managed_function_storage_base(ffrt_function_kind_t kind)
```

**Description**

Allocates memory for the function execution structure.<br> The allocated memory is used as the task executor wrapper passed to [ffrt_submit_base](capi-task-h.md#ffrt_submit_base) or [ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base) when submitting a task. The memory is automatically released by the FFRT runtime after the submitted task finishes execution, so the caller does not need to free it manually.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_function_kind_t kind | Indicates the type of the function execution structure. Use a common (general) kind for tasks submitted through [ffrt_submit_base](capi-task-h.md#ffrt_submit_base) or [ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base), and a queue kind for tasks submitted through the concurrent queue submit interface. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API void* | A non-null pointer if the memory is allocated;          a null pointer otherwise. |

**Reference**:

[ffrt_submit_base](capi-task-h.md#ffrt_submit_base)
[ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base)


### ffrt_submit_base()

```c
FFRT_C_API void ffrt_submit_base(ffrt_function_header_t* f, const ffrt_deps_t* in_deps, const ffrt_deps_t* out_deps, const ffrt_task_attr_t* attr)
```

**Description**

Submits a task.<br> The task is submitted to the FFRT scheduler together with its input and output dependencies and the task attribute. The scheduler uses the dependencies and the task QoS to determine when the task becomes ready to run and which worker executes it. This is the underlying submission interface; the simplified wrapper [ffrt_submit_f](capi-task-h.md#ffrt_submit_f) can be used when no task destroy callback is required. Unlike [ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base), this interface does not return a task handle and should be used when the caller does not need to track the task after submission.<br> If a task delay has been set on the attribute with [ffrt_task_attr_set_delay](capi-task-h.md#ffrt_task_attr_set_delay), the input and output dependencies are ignored and the task is scheduled after the delay elapses.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_function_header_t* f | Indicates a pointer to the task executor wrapper. The wrapper must be allocated with [ffrt_alloc_auto_managed_function_storage_base](capi-task-h.md#ffrt_alloc_auto_managed_function_storage_base) and must include a task destroy callback. |
| const ffrt_deps_t* in_deps | Indicates a pointer to the input dependencies. |
| const ffrt_deps_t* out_deps | Indicates a pointer to the output dependencies. |
| const ffrt_task_attr_t* attr | Indicates a pointer to the task attribute. |

**Reference**:

[ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base)


### ffrt_submit_h_base()

```c
FFRT_C_API ffrt_task_handle_t ffrt_submit_h_base(ffrt_function_header_t* f, const ffrt_deps_t* in_deps, const ffrt_deps_t* out_deps, const ffrt_task_attr_t* attr)
```

**Description**

Submits a task, and obtains a task handle.<br> The task is submitted to the FFRT scheduler together with its input and output dependencies and the task attribute. The scheduler uses the dependencies to determine when the task becomes ready to run. The returned handle can be used with [ffrt_wait_deps](capi-task-h.md#ffrt_wait_deps) to wait for the task, or passed as an input dependency to other submitted tasks to build a dependency chain. This is the underlying submission interface that returns a task handle; the simplified wrapper [ffrt_submit_h_f](capi-task-h.md#ffrt_submit_h_f) can be used when no task destroy callback is required. The returned handle should be released with [ffrt_task_handle_destroy](capi-task-h.md#ffrt_task_handle_destroy) when it is no longer needed, and its reference count can be managed with [ffrt_task_handle_inc_ref](capi-task-h.md#ffrt_task_handle_inc_ref) and [ffrt_task_handle_dec_ref](capi-task-h.md#ffrt_task_handle_dec_ref).

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_function_header_t* f | Indicates a pointer to the task executor wrapper. The wrapper must be allocated with [ffrt_alloc_auto_managed_function_storage_base](capi-task-h.md#ffrt_alloc_auto_managed_function_storage_base) and must include a task destroy callback. |
| const ffrt_deps_t* in_deps | Indicates a pointer to the input dependencies. |
| const ffrt_deps_t* out_deps | Indicates a pointer to the output dependencies. |
| const ffrt_task_attr_t* attr | Indicates a pointer to the task attribute. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API ffrt_task_handle_t | A non-null task handle if the task is submitted;          a null pointer otherwise. |

**Reference**:

[ffrt_submit_base](capi-task-h.md#ffrt_submit_base)


### ffrt_submit_f()

```c
FFRT_C_API void ffrt_submit_f(ffrt_function_t func, void* arg, const ffrt_deps_t* in_deps, const ffrt_deps_t* out_deps, const ffrt_task_attr_t* attr)
```

**Description**

Submits a task, simplified from the [ffrt_submit_base](capi-task-h.md#ffrt_submit_base) interface.<br> This interface wraps the provided task function and its argument into a task wrapper designated as a general task (`ffrt_function_kind_general`). During wrapper creation, the task destroy callback (after_func), which is intended to handle any post-execution cleanup, is set to NULL, thus omitting any additional cleanup actions. The resulting task wrapper is then submitted using the underlying [ffrt_submit_base](capi-task-h.md#ffrt_submit_base) interface.<br> If a task delay has been set on the attribute with [ffrt_task_attr_set_delay](capi-task-h.md#ffrt_task_attr_set_delay), the input and output dependencies are ignored and the task is scheduled after the delay elapses.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_function_t func | Indicates a task function to be executed. |
| void* arg | Indicates a pointer to the argument or closure data that will be passed to the task function. |
| const ffrt_deps_t* in_deps | Indicates a pointer to the input dependencies. |
| const ffrt_deps_t* out_deps | Indicates a pointer to the output dependencies. |
| const ffrt_task_attr_t* attr | Indicates a pointer to the task attribute. |

**Reference**:

[ffrt_submit_base](capi-task-h.md#ffrt_submit_base)


### ffrt_submit_h_f()

```c
FFRT_C_API ffrt_task_handle_t ffrt_submit_h_f(ffrt_function_t func, void* arg, const ffrt_deps_t* in_deps, const ffrt_deps_t* out_deps, const ffrt_task_attr_t* attr)
```

**Description**

Submits a task, and obtains a handle, simplified from the [ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base) interface.<br> This interface wraps the provided task function and its argument into a task wrapper designated as a general task (`ffrt_function_kind_general`). During wrapper creation, the task destroy callback (after_func), which is intended to handle any post-execution cleanup, is set to NULL, thus omitting any additional cleanup actions. The resulting task wrapper is then submitted using the underlying [ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base) interface.<br> If a task delay has been set on the attribute with [ffrt_task_attr_set_delay](capi-task-h.md#ffrt_task_attr_set_delay), the input and output dependencies are ignored and the task is scheduled after the delay elapses. The returned task handle should be released with [ffrt_task_handle_destroy](capi-task-h.md#ffrt_task_handle_destroy) when it is no longer needed.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_function_t func | Indicates a task function to be executed. |
| void* arg | Indicates a pointer to the argument or closure data that will be passed to the task function. |
| const ffrt_deps_t* in_deps | Indicates a pointer to the input dependencies. |
| const ffrt_deps_t* out_deps | Indicates a pointer to the output dependencies. |
| const ffrt_task_attr_t* attr | Indicates a pointer to the task attribute. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API ffrt_task_handle_t | A non-null task handle if the task is submitted;          a null pointer otherwise. |

**Reference**:

[ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base)


### ffrt_task_handle_inc_ref()

```c
FFRT_C_API uint32_t ffrt_task_handle_inc_ref(ffrt_task_handle_t handle)
```

**Description**

Increases the reference count of a task handle.<br> The reference count of the task handle is incremented by one, and the value of the reference count before the increment is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_task_handle_t handle | Indicates a task handle, obtained from [ffrt_submit_h_base](capi-task-h.md#ffrt_submit_h_base) or [ffrt_submit_h_f](capi-task-h.md#ffrt_submit_h_f). |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API uint32_t | The task handle reference count value before the increment;          `UINT_MAX` if `handle` is null. |

### ffrt_task_handle_dec_ref()

```c
FFRT_C_API uint32_t ffrt_task_handle_dec_ref(ffrt_task_handle_t handle)
```

**Description**

Decreases the reference count of a task handle.<br> The reference count of the task handle is decremented by one, and the value of the reference count before the decrement is returned. Pair this call with [ffrt_task_handle_inc_ref](capi-task-h.md#ffrt_task_handle_inc_ref) and use [ffrt_task_handle_destroy](capi-task-h.md#ffrt_task_handle_destroy) to release the handle when it is no longer needed.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_task_handle_t handle | Indicates a task handle. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API uint32_t | The task handle reference count value before the decrement;          `UINT_MAX` if `handle` is null. |

### ffrt_task_handle_destroy()

```c
FFRT_C_API void ffrt_task_handle_destroy(ffrt_task_handle_t handle)
```

**Description**

Destroys a task handle.<br> After the call, the task handle is destroyed and the resources associated with it are released. The handle must not be used again after destruction.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_task_handle_t handle | Indicates a task handle. |

### ffrt_wait_deps()

```c
FFRT_C_API void ffrt_wait_deps(const ffrt_deps_t* deps)
```

**Description**

Waits until the dependent tasks are complete.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| const ffrt_deps_t* deps | Indicates a pointer to the list of dependent tasks. The calling task is blocked until all tasks referenced by this dependency list have finished executing. |

### ffrt_wait()

```c
FFRT_C_API void ffrt_wait(void)
```

**Description**

Waits until all submitted tasks are complete.

**Since**: 10


