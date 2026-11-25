# queue.h

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=2958c7fca3d79723f72d09301e4f0b3e531b0233 translatedAt=2026-11-13T03:07:12.847Z pushedAt=2026-11-13T08:49:38.809Z nl=1 -->

## Overview

The **queue.h** file declares the queue APIs in C.

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
| [ffrt_queue_type_t](#ffrt_queue_type_t) | ffrt_queue_type_t | Enumerates the queue types. |

### Function

| Name| Description|
| -- | -- |
| [FFRT_C_API int ffrt_queue_attr_init(ffrt_queue_attr_t* attr)](#ffrt_queue_attr_init) | Initializes a queue attribute. When the queue attribute is no longer used, it must be destroyed by [ffrt_queue_attr_destroy](capi-queue-h.md#ffrt_queue_attr_destroy). |
| [FFRT_C_API void ffrt_queue_attr_destroy(ffrt_queue_attr_t* attr)](#ffrt_queue_attr_destroy) | Destroys a queue attribute. The queue attribute must have been initialized by [ffrt_queue_attr_init](capi-queue-h.md#ffrt_queue_attr_init). |
| [FFRT_C_API void ffrt_queue_attr_set_qos(ffrt_queue_attr_t* attr, ffrt_qos_t qos)](#ffrt_queue_attr_set_qos) | Sets the QoS of a queue attribute. |
| [FFRT_C_API ffrt_qos_t ffrt_queue_attr_get_qos(const ffrt_queue_attr_t* attr)](#ffrt_queue_attr_get_qos) | Obtains the QoS of a queue attribute. |
| [FFRT_C_API void ffrt_queue_attr_set_timeout(ffrt_queue_attr_t* attr, uint64_t timeout_us)](#ffrt_queue_attr_set_timeout) | Sets the task execution timeout of a queue attribute. |
| [FFRT_C_API uint64_t ffrt_queue_attr_get_timeout(const ffrt_queue_attr_t* attr)](#ffrt_queue_attr_get_timeout) | Obtains the task execution timeout of a queue attribute. |
| [FFRT_C_API void ffrt_queue_attr_set_callback(ffrt_queue_attr_t* attr, ffrt_function_header_t* f)](#ffrt_queue_attr_set_callback) | Sets the timeout callback function of a queue attribute. The callback is triggered when the execution time of a task in the queue exceeds the timeout set by [ffrt_queue_attr_set_timeout](capi-queue-h.md#ffrt_queue_attr_set_timeout). |
| [FFRT_C_API ffrt_function_header_t* ffrt_queue_attr_get_callback(const ffrt_queue_attr_t* attr)](#ffrt_queue_attr_get_callback) | Obtains the timeout callback function of a queue attribute. |
| [FFRT_C_API void ffrt_queue_attr_set_max_concurrency(ffrt_queue_attr_t* attr, const int max_concurrency)](#ffrt_queue_attr_set_max_concurrency) | Sets the maximum concurrency of a concurrent queue attribute. |
| [FFRT_C_API int ffrt_queue_attr_get_max_concurrency(const ffrt_queue_attr_t* attr)](#ffrt_queue_attr_get_max_concurrency) | Obtains the maximum concurrency of a concurrent queue attribute. |
| [FFRT_C_API void ffrt_queue_attr_set_thread_mode(ffrt_queue_attr_t* attr, bool mode)](#ffrt_queue_attr_set_thread_mode) | Sets the execution mode of a queue attribute. This API specifies whether tasks in the queue are executed in coroutine mode or thread mode. By default, tasks are executed in coroutine mode. Setting mode to **true** enables thread-based execution. |
| [FFRT_C_API bool ffrt_queue_attr_get_thread_mode(const ffrt_queue_attr_t* attr)](#ffrt_queue_attr_get_thread_mode) | Obtains the execution mode of a queue attribute. |
| [FFRT_C_API ffrt_queue_t ffrt_queue_create(ffrt_queue_type_t type, const char* name, const ffrt_queue_attr_t* attr)](#ffrt_queue_create) | Creates a queue. When the queue is no longer used, it must be destroyed by [ffrt_queue_destroy](capi-queue-h.md#ffrt_queue_destroy). |
| [FFRT_C_API void ffrt_queue_destroy(ffrt_queue_t queue)](#ffrt_queue_destroy) | Destroys a queue. The queue must have been created by [ffrt_queue_create](capi-queue-h.md#ffrt_queue_create). During destruction, tasks that have not started execution are canceled, and the function blocks until the tasks being executed are completed. |
| [FFRT_C_API void ffrt_queue_submit(ffrt_queue_t queue, ffrt_function_header_t* f, const ffrt_task_attr_t* attr)](#ffrt_queue_submit) | Submits a task to a queue. |
| [FFRT_C_API ffrt_task_handle_t ffrt_queue_submit_h(ffrt_queue_t queue, ffrt_function_header_t* f, const ffrt_task_attr_t* attr)](#ffrt_queue_submit_h) | Submits a task to a queue and obtains a task handle. |
| [FFRT_C_API void ffrt_queue_submit_f(ffrt_queue_t queue, ffrt_function_t func, void* arg, const ffrt_task_attr_t* attr)](#ffrt_queue_submit_f) | Submits a task to a queue. This is a simplified form of [ffrt_queue_submit](capi-queue-h.md#ffrt_queue_submit). This API wraps the given task function and its argument into a task wrapper (**ffrt_function_kind_queue**) for queue submission. The task destruction callback (**after_func**) used to handle post-execution cleanup is set to NULL, so any additional cleanup action is omitted. The generated task wrapper is then submitted to the specified queue through [ffrt_queue_submit](capi-queue-h.md#ffrt_queue_submit). |
| [FFRT_C_API ffrt_task_handle_t ffrt_queue_submit_h_f(ffrt_queue_t queue, ffrt_function_t func, void* arg, const ffrt_task_attr_t* attr)](#ffrt_queue_submit_h_f) | Submits a task to a queue and obtains a task handle. This is a simplified form of [ffrt_queue_submit_h](capi-queue-h.md#ffrt_queue_submit_h). This API wraps the given task function and its argument into a task wrapper (**ffrt_function_kind_queue**) for queue submission. The task destruction callback (**after_func**) used to handle post-execution cleanup is set to NULL, so any additional cleanup action is omitted. The generated task wrapper is then submitted to the specified queue through [ffrt_queue_submit_h](capi-queue-h.md#ffrt_queue_submit_h). |
| [FFRT_C_API void ffrt_queue_wait(ffrt_task_handle_t handle)](#ffrt_queue_wait) | Waits for the task in the queue to complete execution. |
| [FFRT_C_API int ffrt_queue_cancel(ffrt_task_handle_t handle)](#ffrt_queue_cancel) | Cancels a task in the queue. A task that has started execution cannot be canceled. |
| [FFRT_C_API ffrt_queue_t ffrt_get_main_queue(void)](#ffrt_get_main_queue) | Obtains the application main thread queue. |
| [FFRT_C_API ffrt_queue_t ffrt_get_current_queue(void)](#ffrt_get_current_queue) | Obtains the application Worker (ArkTS) thread queue. |

## Enum Description

### ffrt_queue_type_t

```c
enum ffrt_queue_type_t
```

**Description**

Enumerates the queue types.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| ffrt_queue_serial | Serial queue. |
| ffrt_queue_concurrent | Concurrent queue. |
| ffrt_queue_max | Maximum valid queue type value, used as a sentinel (for example, for iteration). |


## Function Description

### ffrt_queue_attr_init()

```c
FFRT_C_API int ffrt_queue_attr_init(ffrt_queue_attr_t* attr)
```

**Description**

Initializes a queue attribute. When the queue attribute is no longer used, it must be destroyed by [ffrt_queue_attr_destroy](capi-queue-h.md#ffrt_queue_attr_destroy).

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_queue_attr_t](capi-ffrt-ffrt-queue-attr-t.md)* attr | Pointer to the queue attribute. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | `0` is returned if the queue attribute is initialized successfully; otherwise, `-1` is returned. |

### ffrt_queue_attr_destroy()

```c
FFRT_C_API void ffrt_queue_attr_destroy(ffrt_queue_attr_t* attr)
```

**Description**

Destroys a queue attribute. The queue attribute must have been initialized by [ffrt_queue_attr_init](capi-queue-h.md#ffrt_queue_attr_init).

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_queue_attr_t](capi-ffrt-ffrt-queue-attr-t.md)* attr | Pointer to the queue attribute. |

### ffrt_queue_attr_set_qos()

```c
FFRT_C_API void ffrt_queue_attr_set_qos(ffrt_queue_attr_t* attr, ffrt_qos_t qos)
```

**Description**

Sets the QoS of a queue attribute.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_queue_attr_t](capi-ffrt-ffrt-queue-attr-t.md)* attr | Pointer to the queue attribute. |
| [ffrt_qos_t](capi-type-def-h.md#variables) qos | QoS level. For the value range, see the [ffrt_qos_t](capi-type-def-h.md#variables) enum definition. |

### ffrt_queue_attr_get_qos()

```c
FFRT_C_API ffrt_qos_t ffrt_queue_attr_get_qos(const ffrt_queue_attr_t* attr)
```

**Description**

Obtains the QoS of a queue attribute.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [const ffrt_queue_attr_t](capi-ffrt-ffrt-queue-attr-t.md)* attr | Pointer to the queue attribute. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API [ffrt_qos_t](capi-type-def-h.md#variables) | QoS level. For the value range, see the [ffrt_qos_t](capi-type-def-h.md#variables) enum definition. |

### ffrt_queue_attr_set_timeout()

```c
FFRT_C_API void ffrt_queue_attr_set_timeout(ffrt_queue_attr_t* attr, uint64_t timeout_us)
```

**Description**

Sets the task execution timeout of a queue attribute.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_queue_attr_t](capi-ffrt-ffrt-queue-attr-t.md)* attr | Pointer to the queue attribute. |
| uint64_t timeout_us | Execution timeout of the queue task, in microseconds. The lower limit is 1000 microseconds (1 millisecond). Values less than 1000 are forcibly set to 1000. |

### ffrt_queue_attr_get_timeout()

```c
FFRT_C_API uint64_t ffrt_queue_attr_get_timeout(const ffrt_queue_attr_t* attr)
```

**Description**

Obtains the task execution timeout of a queue attribute.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [const ffrt_queue_attr_t](capi-ffrt-ffrt-queue-attr-t.md)* attr | Pointer to the queue attribute. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API uint64_t | Execution timeout of a queue task, in microseconds. |

### ffrt_queue_attr_set_callback()

```c
FFRT_C_API void ffrt_queue_attr_set_callback(ffrt_queue_attr_t* attr, ffrt_function_header_t* f)
```

**Description**

Sets the timeout callback function of a queue attribute. The callback is triggered when the execution time of a task in the queue exceeds the timeout set by [ffrt_queue_attr_set_timeout](capi-queue-h.md#ffrt_queue_attr_set_timeout).

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_queue_attr_t](capi-ffrt-ffrt-queue-attr-t.md)* attr | Pointer to the queue attribute. |
| [ffrt_function_header_t](capi-ffrt-ffrt-function-header-t.md)* f | Pointer to the queue timeout callback function. |

### ffrt_queue_attr_get_callback()

```c
FFRT_C_API ffrt_function_header_t* ffrt_queue_attr_get_callback(const ffrt_queue_attr_t* attr)
```

**Description**

Obtains the timeout callback function of a queue attribute.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [const ffrt_queue_attr_t](capi-ffrt-ffrt-queue-attr-t.md)* attr | Pointer to the queue attribute. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API [ffrt_function_header_t](capi-ffrt-ffrt-function-header-t.md)* | Timeout callback function for a queue task. |

### ffrt_queue_attr_set_max_concurrency()

```c
FFRT_C_API void ffrt_queue_attr_set_max_concurrency(ffrt_queue_attr_t* attr, const int max_concurrency)
```

**Description**

Sets the maximum concurrency of a concurrent queue attribute.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_queue_attr_t](capi-ffrt-ffrt-queue-attr-t.md)* attr | Pointer to the queue attribute. |
| const int max_concurrency | Maximum number of tasks that the queue can execute concurrently. |

### ffrt_queue_attr_get_max_concurrency()

```c
FFRT_C_API int ffrt_queue_attr_get_max_concurrency(const ffrt_queue_attr_t* attr)
```

**Description**

Obtains the maximum concurrency of a concurrent queue attribute.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const ffrt_queue_attr_t](capi-ffrt-ffrt-queue-attr-t.md)* attr | Pointer to the queue attribute. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | Maximum concurrency of the queue. |

### ffrt_queue_attr_set_thread_mode()

```c
FFRT_C_API void ffrt_queue_attr_set_thread_mode(ffrt_queue_attr_t* attr, bool mode)
```

**Description**

Sets the execution mode of a queue attribute. This API specifies whether tasks in the queue are executed in coroutine mode or thread mode. By default, tasks are executed in coroutine mode. Setting mode to **true** enables thread-based execution.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_queue_attr_t](capi-ffrt-ffrt-queue-attr-t.md)* attr | Pointer to the queue attribute. |
| bool mode | Whether to enable the thread-based execution mode. - **true**: tasks are executed by native threads (thread mode). - **false**: tasks are executed by coroutines (default). |

### ffrt_queue_attr_get_thread_mode()

```c
FFRT_C_API bool ffrt_queue_attr_get_thread_mode(const ffrt_queue_attr_t* attr)
```

**Description**

Obtains the execution mode of a queue attribute.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [const ffrt_queue_attr_t](capi-ffrt-ffrt-queue-attr-t.md)* attr | Pointer to the queue attribute. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API bool | **true** if the task is executed in a native thread (thread mode);<br>         **false** if the task is executed in a coroutine (default). |

### ffrt_queue_create()

```c
FFRT_C_API ffrt_queue_t ffrt_queue_create(ffrt_queue_type_t type, const char* name, const ffrt_queue_attr_t* attr)
```

**Description**

Creates a queue. When the queue is no longer used, it must be destroyed by [ffrt_queue_destroy](capi-queue-h.md#ffrt_queue_destroy).

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_queue_type_t](capi-queue-h.md#ffrt_queue_type_t) type | Queue type. **ffrt_queue_serial** applies to scenarios where tasks must be executed in order; **ffrt_queue_concurrent** applies to scenarios where tasks can be executed concurrently to improve throughput. |
| const char* name | Pointer to the queue name. |
| [const ffrt_queue_attr_t](capi-ffrt-ffrt-queue-attr-t.md)* attr | Pointer to the queue attribute. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API [ffrt_queue_t](capi-ffrt-ffrt-queue-t.md) | A non-null queue handle is returned when the queue is created successfully;<br>         otherwise, a null pointer is returned. |

### ffrt_queue_destroy()

```c
FFRT_C_API void ffrt_queue_destroy(ffrt_queue_t queue)
```

**Description**

Destroys a queue. The queue must have been created by [ffrt_queue_create](capi-queue-h.md#ffrt_queue_create). During destruction, tasks that have not started execution are canceled, and the function blocks until the tasks being executed are completed.

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
| [ffrt_function_header_t](capi-ffrt-ffrt-function-header-t.md)* f | Pointer to the task execution body. |
| [const ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | Pointer to the task attributes. |

**Reference**

[ffrt_queue_submit_h](capi-queue-h.md#ffrt_queue_submit_h)


### ffrt_queue_submit_h()

```c
FFRT_C_API ffrt_task_handle_t ffrt_queue_submit_h(ffrt_queue_t queue, ffrt_function_header_t* f, const ffrt_task_attr_t* attr)
```

**Description**

Submits a task to a queue and obtains a task handle.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_queue_t](capi-ffrt-ffrt-queue-t.md) queue | Queue handle.|
| [ffrt_function_header_t](capi-ffrt-ffrt-function-header-t.md)* f | Pointer to the task execution body. |
| [const ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | Pointer to the task attributes. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API [ffrt_task_handle_t](capi-ffrt-ffrt-task-handle-t.md) | Non-null task handle if the task is submitted successfully;<br>         otherwise, a null pointer. |

**Reference**

[ffrt_queue_submit](capi-queue-h.md#ffrt_queue_submit)


### ffrt_queue_submit_f()

```c
FFRT_C_API void ffrt_queue_submit_f(ffrt_queue_t queue, ffrt_function_t func, void* arg, const ffrt_task_attr_t* attr)
```

**Description**

Submits a task to a queue. This is a simplified form of [ffrt_queue_submit](capi-queue-h.md#ffrt_queue_submit). This API wraps the given task function and its argument into a task wrapper (**ffrt_function_kind_queue**) for queue submission. The task destruction callback (**after_func**) used to handle post-execution cleanup is set to NULL, so any additional cleanup action is omitted. The generated task wrapper is then submitted to the specified queue through [ffrt_queue_submit](capi-queue-h.md#ffrt_queue_submit).

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_queue_t](capi-ffrt-ffrt-queue-t.md) queue | Queue handle.|
| [ffrt_function_t](capi-type-def-h.md#ffrt_function_t) func | Task function to be executed. |
| void* arg | Pointer to the parameter or closure data passed to the task function. |
| [const ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | Pointer to the task attributes. |

**References**

[ffrt_queue_submit](capi-queue-h.md#ffrt_queue_submit)


### ffrt_queue_submit_h_f()

```c
FFRT_C_API ffrt_task_handle_t ffrt_queue_submit_h_f(ffrt_queue_t queue, ffrt_function_t func, void* arg, const ffrt_task_attr_t* attr)
```

**Description**

Submits a task to a queue and obtains a task handle. This is a simplified form of [ffrt_queue_submit_h](capi-queue-h.md#ffrt_queue_submit_h). This API wraps the given task function and its argument into a task wrapper (**ffrt_function_kind_queue**) for queue submission. The task destruction callback (**after_func**) used to handle post-execution cleanup is set to NULL, so any additional cleanup action is omitted. The generated task wrapper is then submitted to the specified queue through [ffrt_queue_submit_h](capi-queue-h.md#ffrt_queue_submit_h).

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_queue_t](capi-ffrt-ffrt-queue-t.md) queue | Queue handle.|
| [ffrt_function_t](capi-type-def-h.md#ffrt_function_t) func | Task function to be executed. |
| void* arg | Pointer to the parameter or closure data passed to the task function. |
| [const ffrt_task_attr_t](capi-ffrt-ffrt-task-attr-t.md)* attr | Pointer to the task attributes. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API [ffrt_task_handle_t](capi-ffrt-ffrt-task-handle-t.md) | Non-null task handle if the task is submitted successfully;<br>         otherwise, a null pointer. |

**References**

[ffrt_queue_submit_h](capi-queue-h.md#ffrt_queue_submit_h)


### ffrt_queue_wait()

```c
FFRT_C_API void ffrt_queue_wait(ffrt_task_handle_t handle)
```

**Description**

Waits for the task in the queue to complete execution.

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

Cancels a task in the queue. A task that has started execution cannot be canceled.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_task_handle_t](capi-ffrt-ffrt-task-handle-t.md) handle | Task handle.|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | Returns `0` if the task is canceled successfully;<br>          Returns **1** if the task has been executed or removed from the queue;<br>          Returns **-1** if handle is null. |

### ffrt_get_main_queue()

```c
FFRT_C_API ffrt_queue_t ffrt_get_main_queue(void)
```

**Description**

Obtains the application main thread queue.

**Since**: 12

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API [ffrt_queue_t](capi-ffrt-ffrt-queue-t.md) | Application main thread queue. |

### ffrt_get_current_queue()

```c
FFRT_C_API ffrt_queue_t ffrt_get_current_queue(void)
```

**Description**

Obtains the application Worker (ArkTS) thread queue.

**Since**: 12

**Deprecated from**: 18

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API [ffrt_queue_t](capi-ffrt-ffrt-queue-t.md) | Application Worker (ArkTS) thread queue. |


