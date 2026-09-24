# loop.h

## Overview

Declares the event loop interfaces in C.

**Library**: libffrt.z.so

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ffrt_loop_t](capi-ffrt-ffrt-loop-t.md) | ffrt_loop_t | Loop handle, which identifies different loops. |

### Function

| Name | Description |
| -- | -- |
| [FFRT_C_API ffrt_loop_t ffrt_loop_create(ffrt_queue_t queue)](#ffrt_loop_create) | Creates a loop on the specified queue for running an event loop. |
| [FFRT_C_API int ffrt_loop_destroy(ffrt_loop_t loop)](#ffrt_loop_destroy) | Destroys a loop.<br> Call this interface to release the resources associated with the loop. |
| [FFRT_C_API int ffrt_loop_run(ffrt_loop_t loop)](#ffrt_loop_run) | Starts a loop run.<br> This function occupies the calling thread, running the event loop synchronously on the current thread until [ffrt_loop_stop](capi-loop-h.md#ffrt_loop_stop) is invoked. |
| [FFRT_C_API void ffrt_loop_stop(ffrt_loop_t loop)](#ffrt_loop_stop) | Stops a loop run.<br> After this call, the thread executing [ffrt_loop_run](capi-loop-h.md#ffrt_loop_run) stops the loop and returns. |
| [FFRT_C_API int ffrt_loop_epoll_ctl(ffrt_loop_t loop, int op, int fd, uint32_t events, void* data, ffrt_poller_cb cb)](#ffrt_loop_epoll_ctl) | Controls an epoll file descriptor on ffrt loop.<br> Adds, modifies, or deletes the monitored events on the target file descriptor. |
| [FFRT_C_API ffrt_timer_t ffrt_loop_timer_start(ffrt_loop_t loop, uint64_t timeout, void* data, ffrt_timer_cb cb, bool repeat)](#ffrt_loop_timer_start) | Starts a timer on ffrt loop.<br> The callback is invoked after the timeout elapses, and is repeated if `repeat` is `true`. |
| [FFRT_C_API int ffrt_loop_timer_stop(ffrt_loop_t loop, ffrt_timer_t handle)](#ffrt_loop_timer_stop) | Stops a timer on ffrt loop.<br> After this call, the timer no longer fires. |

### Variable

| Name | Description |
| -- | -- |
| void* ffrt_loop_t | Loop handle, which identifies different loops.<br>**Since**: 12 |

## Function description

### ffrt_loop_create()

```c
FFRT_C_API ffrt_loop_t ffrt_loop_create(ffrt_queue_t queue)
```

**Description**

Creates a loop on the specified queue for running an event loop.

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_queue_t queue | Indicates a queue. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API ffrt_loop_t | A non-null loop handle if the loop is created;          a null pointer otherwise. |

### ffrt_loop_destroy()

```c
FFRT_C_API int ffrt_loop_destroy(ffrt_loop_t loop)
```

**Description**

Destroys a loop.<br> Call this interface to release the resources associated with the loop.

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_loop_t loop | Indicates a loop handle. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API int | `0` if the loop is destroyed;          `-1` otherwise. |

### ffrt_loop_run()

```c
FFRT_C_API int ffrt_loop_run(ffrt_loop_t loop)
```

**Description**

Starts a loop run.<br> This function occupies the calling thread, running the event loop synchronously on the current thread until [ffrt_loop_stop](capi-loop-h.md#ffrt_loop_stop) is invoked.

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_loop_t loop | Indicates a loop handle. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API int | `0` if the loop run succeeds;          `-1` otherwise. |

**Reference**:

[ffrt_loop_stop](capi-loop-h.md#ffrt_loop_stop)


### ffrt_loop_stop()

```c
FFRT_C_API void ffrt_loop_stop(ffrt_loop_t loop)
```

**Description**

Stops a loop run.<br> After this call, the thread executing [ffrt_loop_run](capi-loop-h.md#ffrt_loop_run) stops the loop and returns.

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_loop_t loop | Indicates a loop handle. |

**Reference**:

[ffrt_loop_run](capi-loop-h.md#ffrt_loop_run)


### ffrt_loop_epoll_ctl()

```c
FFRT_C_API int ffrt_loop_epoll_ctl(ffrt_loop_t loop, int op, int fd, uint32_t events, void* data, ffrt_poller_cb cb)
```

**Description**

Controls an epoll file descriptor on ffrt loop.<br> Adds, modifies, or deletes the monitored events on the target file descriptor.

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_loop_t loop | Indicates a loop handle. |
| int op | Indicates the operation type on the target file descriptor, such as add, modify, or delete. |
| int fd | Indicates the target file descriptor on which to perform the operation. |
| uint32_t events | Indicates the event type to monitor on the target file descriptor (such as readable, writable, and so on), and can be combined by bitwise OR. |
| void* data | Indicates user data used in cb. |
| ffrt_poller_cb cb | Indicates user cb which will be executed when the target fd is polled. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API int | `0` if the operation succeeds;          `-1` otherwise. |

### ffrt_loop_timer_start()

```c
FFRT_C_API ffrt_timer_t ffrt_loop_timer_start(ffrt_loop_t loop, uint64_t timeout, void* data, ffrt_timer_cb cb, bool repeat)
```

**Description**

Starts a timer on ffrt loop.<br> The callback is invoked after the timeout elapses, and is repeated if `repeat` is `true`.

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_loop_t loop | Indicates a loop handle. |
| uint64_t timeout | Indicates the number of milliseconds that specifies timeout. The value range is [0, +∞). |
| void* data | Indicates user data used in cb. |
| ffrt_timer_cb cb | Indicates user cb which will be executed when timeout. |
| bool repeat | Indicates whether to repeat this timer. `true` to repeat the timer, `false` to run it once. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API ffrt_timer_t | The timer handle; `-1` if `loop` or `cb` is null. |

**Reference**:

[ffrt_loop_timer_stop](capi-loop-h.md#ffrt_loop_timer_stop)


### ffrt_loop_timer_stop()

```c
FFRT_C_API int ffrt_loop_timer_stop(ffrt_loop_t loop, ffrt_timer_t handle)
```

**Description**

Stops a timer on ffrt loop.<br> After this call, the timer no longer fires.

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_loop_t loop | Indicates a loop handle. |
| ffrt_timer_t handle | Indicates the timer handle returned by [ffrt_loop_timer_start](capi-loop-h.md#ffrt_loop_timer_start). |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API int | `0` if the operation succeeds;          `-1` otherwise. |

**Reference**:

[ffrt_loop_timer_start](capi-loop-h.md#ffrt_loop_timer_start)



