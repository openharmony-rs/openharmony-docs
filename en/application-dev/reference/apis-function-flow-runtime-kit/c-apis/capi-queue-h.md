# queue.h

## Overview

Declares the queue interfaces in C.

**Library**: libffrt.z.so

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ffrt_queue_t](capi-ffrt-ffrt-queue-t.md) | ffrt_queue_t | Queue handle, which identifies different queues. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ffrt_queue_type_t](#ffrt_queue_type_t) | ffrt_queue_type_t | Enumerates the queue types. |

### Function

| Name | Description |
| -- | -- |
| [FFRT_C_API int ffrt_queue_attr_init(ffrt_queue_attr_t* attr)](#ffrt_queue_attr_init) | Initializes a queue attribute.<br> The queue attribute must later be destroyed by [ffrt_queue_attr_destroy](capi-queue-h.md#ffrt_queue_attr_destroy). |
| [FFRT_C_API void ffrt_queue_attr_destroy(ffrt_queue_attr_t* attr)](#ffrt_queue_attr_destroy) | Destroys a queue attribute.<br> The queue attribute must have been initialized by [ffrt_queue_attr_init](capi-queue-h.md#ffrt_queue_attr_init). |
| [FFRT_C_API void ffrt_queue_attr_set_qos(ffrt_queue_attr_t* attr, ffrt_qos_t qos)](#ffrt_queue_attr_set_qos) | Sets the QoS for a queue attribute. |
| [FFRT_C_API ffrt_qos_t ffrt_queue_attr_get_qos(const ffrt_queue_attr_t* attr)](#ffrt_queue_attr_get_qos) | Gets the QoS of a queue attribute. |
| [FFRT_C_API void ffrt_queue_attr_set_timeout(ffrt_queue_attr_t* attr, uint64_t timeout_us)](#ffrt_queue_attr_set_timeout) | Sets the execution timeout of a queue attribute. |
| [FFRT_C_API uint64_t ffrt_queue_attr_get_timeout(const ffrt_queue_attr_t* attr)](#ffrt_queue_attr_get_timeout) | Gets the execution timeout of a queue attribute. |
| [FFRT_C_API void ffrt_queue_attr_set_callback(ffrt_queue_attr_t* attr, ffrt_function_header_t* f)](#ffrt_queue_attr_set_callback) | Sets the timeout callback of a queue attribute.<br> The callback is triggered when a task in the queue runs longer than the timeout duration set by [ffrt_queue_attr_set_timeout](capi-queue-h.md#ffrt_queue_attr_set_timeout). |
| [FFRT_C_API ffrt_function_header_t* ffrt_queue_attr_get_callback(const ffrt_queue_attr_t* attr)](#ffrt_queue_attr_get_callback) | Gets the timeout callback of a queue attribute. |
| [FFRT_C_API void ffrt_queue_attr_set_max_concurrency(ffrt_queue_attr_t* attr, const int max_concurrency)](#ffrt_queue_attr_set_max_concurrency) | Sets the max concurrency of a concurrent queue attribute. |
| [FFRT_C_API int ffrt_queue_attr_get_max_concurrency(const ffrt_queue_attr_t* attr)](#ffrt_queue_attr_get_max_concurrency) | Gets the max concurrency of a concurrent queue attribute. |
| [FFRT_C_API void ffrt_queue_attr_set_thread_mode(ffrt_queue_attr_t* attr, bool mode)](#ffrt_queue_attr_set_thread_mode) | Sets the execution mode of a queue attribute.<br> This interface specifies whether tasks in the queue are executed in coroutine mode or thread mode. By default, tasks are executed in coroutine mode. Set mode to `true` to enable thread-based execution. |
| [FFRT_C_API bool ffrt_queue_attr_get_thread_mode(const ffrt_queue_attr_t* attr)](#ffrt_queue_attr_get_thread_mode) | Gets the execution mode of a queue attribute. |
| [FFRT_C_API ffrt_queue_t ffrt_queue_create(ffrt_queue_type_t type, const char* name, const ffrt_queue_attr_t* attr)](#ffrt_queue_create) | Creates a queue.<br> The queue must later be destroyed by [ffrt_queue_destroy](capi-queue-h.md#ffrt_queue_destroy) when no longer needed. |
| [FFRT_C_API void ffrt_queue_destroy(ffrt_queue_t queue)](#ffrt_queue_destroy) | Destroys a queue.<br> The queue must have been created by [ffrt_queue_create](capi-queue-h.md#ffrt_queue_create). Destruction cancels tasks that have not yet started and blocks until any currently executing tasks complete. |
| [FFRT_C_API void ffrt_queue_submit(ffrt_queue_t queue, ffrt_function_header_t* f, const ffrt_task_attr_t* attr)](#ffrt_queue_submit) | Submits a task to a queue. |
| [FFRT_C_API ffrt_task_handle_t ffrt_queue_submit_h(ffrt_queue_t queue, ffrt_function_header_t* f, const ffrt_task_attr_t* attr)](#ffrt_queue_submit_h) | Submits a task to the queue, and obtains a task handle. |
| [FFRT_C_API void ffrt_queue_submit_f(ffrt_queue_t queue, ffrt_function_t func, void* arg, const ffrt_task_attr_t* attr)](#ffrt_queue_submit_f) | Submits a task to a queue, simplified from the [ffrt_queue_submit](capi-queue-h.md#ffrt_queue_submit) interface.<br> This interface wraps the provided task function and its argument into a task wrapper designed for queue submission (`ffrt_function_kind_queue`). During wrapper creation, the task destroy callback (after_func), which is intended to handle any post-execution cleanup, is set to NULL, thus omitting any additional cleanup actions. The resulting task wrapper is then submitted to the specified queue via the [ffrt_queue_submit](capi-queue-h.md#ffrt_queue_submit) interface. |
| [FFRT_C_API ffrt_task_handle_t ffrt_queue_submit_h_f(ffrt_queue_t queue, ffrt_function_t func, void* arg, const ffrt_task_attr_t* attr)](#ffrt_queue_submit_h_f) | Submits a task to a queue, and obtains a handle, simplified from the [ffrt_queue_submit_h](capi-queue-h.md#ffrt_queue_submit_h) interface.<br> This interface wraps the provided task function and its argument into a task wrapper designed for queue submission (`ffrt_function_kind_queue`). During wrapper creation, the task destroy callback (after_func), which is intended to handle any post-execution cleanup, is set to NULL, thus omitting any additional cleanup actions. The resulting task wrapper is then submitted to the specified queue via the [ffrt_queue_submit_h](capi-queue-h.md#ffrt_queue_submit_h) interface. |
| [FFRT_C_API void ffrt_queue_wait(ffrt_task_handle_t handle)](#ffrt_queue_wait) | Waits until a task in the queue is complete. |
| [FFRT_C_API int ffrt_queue_cancel(ffrt_task_handle_t handle)](#ffrt_queue_cancel) | Cancels a task in the queue.<br> Tasks that have already started executing cannot be canceled. |
| [FFRT_C_API ffrt_queue_t ffrt_get_main_queue(void)](#ffrt_get_main_queue) | Gets the application main thread queue. |
| [FFRT_C_API ffrt_queue_t ffrt_get_current_queue(void)](#ffrt_get_current_queue) | Gets the application worker (ArkTS) thread queue.(Deprecated in API18) |

### Variable

| Name | Description |
| -- | -- |
| void* ffrt_queue_t | Queue handle, which identifies different queues.<br>**Since**: 10 |

## Enum type description

### ffrt_queue_type_t

```c
enum ffrt_queue_type_t
```

**Description**

Enumerates the queue types.

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| ffrt_queue_serial | Serial queue. |
| ffrt_queue_concurrent | Concurrent queue. |
| ffrt_queue_max | Maximum valid queue type value, used as a sentinel (for example, in iteration). |


## Function description

### ffrt_queue_attr_init()

```c
FFRT_C_API int ffrt_queue_attr_init(ffrt_queue_attr_t* attr)
```

**Description**

Initializes a queue attribute.<br> The queue attribute must later be destroyed by [ffrt_queue_attr_destroy](capi-queue-h.md#ffrt_queue_attr_destroy).

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_queue_attr_t* attr | Indicates a pointer to the queue attribute. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API int | `0` if the queue attribute is initialized;          `-1` otherwise. |

### ffrt_queue_attr_destroy()

```c
FFRT_C_API void ffrt_queue_attr_destroy(ffrt_queue_attr_t* attr)
```

**Description**

Destroys a queue attribute.<br> The queue attribute must have been initialized by [ffrt_queue_attr_init](capi-queue-h.md#ffrt_queue_attr_init).

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_queue_attr_t* attr | Indicates a pointer to the queue attribute. |

### ffrt_queue_attr_set_qos()

```c
FFRT_C_API void ffrt_queue_attr_set_qos(ffrt_queue_attr_t* attr, ffrt_qos_t qos)
```

**Description**

Sets the QoS for a queue attribute.

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_queue_attr_t* attr | Indicates a pointer to the queue attribute. |
| ffrt_qos_t qos | Indicates the QoS level. See {@link ffrt_qos_t} for the value range. |

### ffrt_queue_attr_get_qos()

```c
FFRT_C_API ffrt_qos_t ffrt_queue_attr_get_qos(const ffrt_queue_attr_t* attr)
```

**Description**

Gets the QoS of a queue attribute.

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| const ffrt_queue_attr_t* attr | Indicates a pointer to the queue attribute. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API ffrt_qos_t | The QoS level. See {@link ffrt_qos_t} for the value range. |

### ffrt_queue_attr_set_timeout()

```c
FFRT_C_API void ffrt_queue_attr_set_timeout(ffrt_queue_attr_t* attr, uint64_t timeout_us)
```

**Description**

Sets the execution timeout of a queue attribute.

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_queue_attr_t* attr | Indicates a pointer to the queue attribute. |
| uint64_t timeout_us | Indicates the queue task execution timeout, in microseconds. The lower limit is 1000 microseconds (1 ms); values below 1000 are clamped to 1000. |

### ffrt_queue_attr_get_timeout()

```c
FFRT_C_API uint64_t ffrt_queue_attr_get_timeout(const ffrt_queue_attr_t* attr)
```

**Description**

Gets the execution timeout of a queue attribute.

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| const ffrt_queue_attr_t* attr | Indicates a pointer to the queue attribute. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API uint64_t | The queue task execution timeout, in microseconds. |

### ffrt_queue_attr_set_callback()

```c
FFRT_C_API void ffrt_queue_attr_set_callback(ffrt_queue_attr_t* attr, ffrt_function_header_t* f)
```

**Description**

Sets the timeout callback of a queue attribute.<br> The callback is triggered when a task in the queue runs longer than the timeout duration set by [ffrt_queue_attr_set_timeout](capi-queue-h.md#ffrt_queue_attr_set_timeout).

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_queue_attr_t* attr | Indicates a pointer to the queue attribute. |
| ffrt_function_header_t* f | Indicates the queue timeout callback function. |

### ffrt_queue_attr_get_callback()

```c
FFRT_C_API ffrt_function_header_t* ffrt_queue_attr_get_callback(const ffrt_queue_attr_t* attr)
```

**Description**

Gets the timeout callback of a queue attribute.

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| const ffrt_queue_attr_t* attr | Indicates a pointer to the queue attribute. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API ffrt_function_header_t* | The queue task timeout callback function. |

### ffrt_queue_attr_set_max_concurrency()

```c
FFRT_C_API void ffrt_queue_attr_set_max_concurrency(ffrt_queue_attr_t* attr, const int max_concurrency)
```

**Description**

Sets the max concurrency of a concurrent queue attribute.

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_queue_attr_t* attr | Indicates a pointer to the queue attribute. |
| const int max_concurrency | Indicates the maximum number of tasks that a queue can execute concurrently. |

### ffrt_queue_attr_get_max_concurrency()

```c
FFRT_C_API int ffrt_queue_attr_get_max_concurrency(const ffrt_queue_attr_t* attr)
```

**Description**

Gets the max concurrency of a concurrent queue attribute.

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const ffrt_queue_attr_t* attr | Indicates a pointer to the queue attribute. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API int | The maximum concurrency of the queue. |

### ffrt_queue_attr_set_thread_mode()

```c
FFRT_C_API void ffrt_queue_attr_set_thread_mode(ffrt_queue_attr_t* attr, bool mode)
```

**Description**

Sets the execution mode of a queue attribute.<br> This interface specifies whether tasks in the queue are executed in coroutine mode or thread mode. By default, tasks are executed in coroutine mode. Set mode to `true` to enable thread-based execution.

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_queue_attr_t* attr | Indicates a pointer to the queue attribute. |
| bool mode | Indicates whether to enable thread-based execution mode. - `true`: Tasks are executed as native threads (thread mode). - `false`: Tasks are executed as coroutines (default). |

### ffrt_queue_attr_get_thread_mode()

```c
FFRT_C_API bool ffrt_queue_attr_get_thread_mode(const ffrt_queue_attr_t* attr)
```

**Description**

Gets the execution mode of a queue attribute.

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| const ffrt_queue_attr_t* attr | Indicates a pointer to the queue attribute. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API bool | `true` if tasks are executed as native threads (thread mode);          `false` if tasks are executed as coroutines (default). |

### ffrt_queue_create()

```c
FFRT_C_API ffrt_queue_t ffrt_queue_create(ffrt_queue_type_t type, const char* name, const ffrt_queue_attr_t* attr)
```

**Description**

Creates a queue.<br> The queue must later be destroyed by [ffrt_queue_destroy](capi-queue-h.md#ffrt_queue_destroy) when no longer needed.

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ffrt_queue_type_t](capi-queue-h.md#ffrt_queue_type_t) type | Indicates the queue type. `ffrt_queue_serial` is suitable when tasks must be executed in order; `ffrt_queue_concurrent` is suitable when tasks can be executed concurrently to improve throughput. |
| const char* name | Indicates a pointer to the queue name. |
| const ffrt_queue_attr_t* attr | Indicates a pointer to the queue attribute. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API ffrt_queue_t | A non-null queue handle if the queue is created;          a null pointer otherwise. |

### ffrt_queue_destroy()

```c
FFRT_C_API void ffrt_queue_destroy(ffrt_queue_t queue)
```

**Description**

Destroys a queue.<br> The queue must have been created by [ffrt_queue_create](capi-queue-h.md#ffrt_queue_create). Destruction cancels tasks that have not yet started and blocks until any currently executing tasks complete.

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_queue_t queue | Indicates a queue handle. |

### ffrt_queue_submit()

```c
FFRT_C_API void ffrt_queue_submit(ffrt_queue_t queue, ffrt_function_header_t* f, const ffrt_task_attr_t* attr)
```

**Description**

Submits a task to a queue.

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_queue_t queue | Indicates a queue handle. |
| ffrt_function_header_t* f | Indicates a pointer to the task executor. |
| const ffrt_task_attr_t* attr | Indicates a pointer to the task attribute. |

**Reference**:

[ffrt_queue_submit_h](capi-queue-h.md#ffrt_queue_submit_h)


### ffrt_queue_submit_h()

```c
FFRT_C_API ffrt_task_handle_t ffrt_queue_submit_h(ffrt_queue_t queue, ffrt_function_header_t* f, const ffrt_task_attr_t* attr)
```

**Description**

Submits a task to the queue, and obtains a task handle.

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_queue_t queue | Indicates a queue handle. |
| ffrt_function_header_t* f | Indicates a pointer to the task executor. |
| const ffrt_task_attr_t* attr | Indicates a pointer to the task attribute. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API ffrt_task_handle_t | A non-null task handle if the task is submitted;          a null pointer otherwise. |

**Reference**:

[ffrt_queue_submit](capi-queue-h.md#ffrt_queue_submit)


### ffrt_queue_submit_f()

```c
FFRT_C_API void ffrt_queue_submit_f(ffrt_queue_t queue, ffrt_function_t func, void* arg, const ffrt_task_attr_t* attr)
```

**Description**

Submits a task to a queue, simplified from the [ffrt_queue_submit](capi-queue-h.md#ffrt_queue_submit) interface.<br> This interface wraps the provided task function and its argument into a task wrapper designed for queue submission (`ffrt_function_kind_queue`). During wrapper creation, the task destroy callback (after_func), which is intended to handle any post-execution cleanup, is set to NULL, thus omitting any additional cleanup actions. The resulting task wrapper is then submitted to the specified queue via the [ffrt_queue_submit](capi-queue-h.md#ffrt_queue_submit) interface.

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_queue_t queue | Indicates a queue handle. |
| ffrt_function_t func | Indicates a task function to be executed. |
| void* arg | Indicates a pointer to the argument or closure data that will be passed to the task function. |
| const ffrt_task_attr_t* attr | Indicates a pointer to the task attribute. |

**Reference**:

[ffrt_queue_submit](capi-queue-h.md#ffrt_queue_submit)


### ffrt_queue_submit_h_f()

```c
FFRT_C_API ffrt_task_handle_t ffrt_queue_submit_h_f(ffrt_queue_t queue, ffrt_function_t func, void* arg, const ffrt_task_attr_t* attr)
```

**Description**

Submits a task to a queue, and obtains a handle, simplified from the [ffrt_queue_submit_h](capi-queue-h.md#ffrt_queue_submit_h) interface.<br> This interface wraps the provided task function and its argument into a task wrapper designed for queue submission (`ffrt_function_kind_queue`). During wrapper creation, the task destroy callback (after_func), which is intended to handle any post-execution cleanup, is set to NULL, thus omitting any additional cleanup actions. The resulting task wrapper is then submitted to the specified queue via the [ffrt_queue_submit_h](capi-queue-h.md#ffrt_queue_submit_h) interface.

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_queue_t queue | Indicates a queue handle. |
| ffrt_function_t func | Indicates a task function to be executed. |
| void* arg | Indicates a pointer to the argument or closure data that will be passed to the task function. |
| const ffrt_task_attr_t* attr | Indicates a pointer to the task attribute. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API ffrt_task_handle_t | A non-null task handle if the task is submitted;          a null pointer otherwise. |

**Reference**:

[ffrt_queue_submit_h](capi-queue-h.md#ffrt_queue_submit_h)


### ffrt_queue_wait()

```c
FFRT_C_API void ffrt_queue_wait(ffrt_task_handle_t handle)
```

**Description**

Waits until a task in the queue is complete.

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_task_handle_t handle | Indicates a task handle. |

### ffrt_queue_cancel()

```c
FFRT_C_API int ffrt_queue_cancel(ffrt_task_handle_t handle)
```

**Description**

Cancels a task in the queue.<br> Tasks that have already started executing cannot be canceled.

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_task_handle_t handle | Indicates a task handle. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API int | `0` if the task is canceled;          `1` if the task has already been executed or removed from the queue;          `-1` if `handle` is null. |

### ffrt_get_main_queue()

```c
FFRT_C_API ffrt_queue_t ffrt_get_main_queue(void)
```

**Description**

Gets the application main thread queue.

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API ffrt_queue_t | The application main thread queue. |

### ffrt_get_current_queue()

```c
FFRT_C_API ffrt_queue_t ffrt_get_current_queue(void)
```

**Description**

Gets the application worker (ArkTS) thread queue.

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 12

**Deprecated**: 18

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API ffrt_queue_t | The application worker (ArkTS) thread queue. |


