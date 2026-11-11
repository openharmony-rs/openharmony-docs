# loop.h

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1c82fe64143ca179b80fafe272ca5a84323e9159 translatedAt=2026-11-10T03:20:17.725Z pushedAt=2026-11-10T04:57:05.490Z nl=1 -->

## Overview

Declares the C APIs of the event loop.

**File to include**: <ffrt/loop.h>

**Library**: libffrt.z.so

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 12

**Related module**: [FFRT](capi-ffrt.md)

## Summary

### Structs

| Name             | Description|
|-----------------|----|
| [ffrt_loop_t](capi-ffrt-ffrt-loop-t.md) | Loop handle used to identify different loops. |

### Function

| Name| Description|
| -- | -- |
| [FFRT_C_API ffrt_loop_t ffrt_loop_create(ffrt_queue_t queue)](#ffrt_loop_create) | Creates a loop on the specified queue to run an event loop. |
| [FFRT_C_API int ffrt_loop_destroy(ffrt_loop_t loop)](#ffrt_loop_destroy) | Destroys a loop. Calling this API releases the resources associated with the loop. |
| [FFRT_C_API int ffrt_loop_run(ffrt_loop_t loop)](#ffrt_loop_run) | Starts a loop iteration. This function exclusively occupies the calling thread and runs the event loop synchronously on the current calling thread until [ffrt_loop_stop](capi-loop-h.md#ffrt_loop_stop) is called. |
| [FFRT_C_API void ffrt_loop_stop(ffrt_loop_t loop)](#ffrt_loop_stop) | Stops the loop. After this API is called, the thread running [ffrt_loop_run](capi-loop-h.md#ffrt_loop_run) stops the loop and returns. |
| [FFRT_C_API int ffrt_loop_epoll_ctl(ffrt_loop_t loop, int op, int fd, uint32_t events, void *data, ffrt_poller_cb cb)](#ffrt_loop_epoll_ctl) | Controls the epoll file descriptor on the ffrt loop. Adds, modifies, or removes the events to listen for on the target file descriptor. |
| [FFRT_C_API ffrt_timer_t ffrt_loop_timer_start(ffrt_loop_t loop, uint64_t timeout, void* data, ffrt_timer_cb cb, bool repeat)](#ffrt_loop_timer_start) | Starts a timer on the ffrt loop. Invokes the callback after the timeout. If `repeat` is `true`, the timer is triggered periodically. |
| [FFRT_C_API int ffrt_loop_timer_stop(ffrt_loop_t loop, ffrt_timer_t handle)](#ffrt_loop_timer_stop) | Stops a timer on the ffrt loop. After this API is called, the timer is no longer triggered. |

## Function Description

### ffrt_loop_create()

```c
FFRT_C_API ffrt_loop_t ffrt_loop_create(ffrt_queue_t queue)
```

**Description**

Creates a loop on the specified queue to run the event loop.

**Since**: 12

**Parameters**

| Name                   | Description|
|------------------------| -- |
| [ffrt_queue_t](capi-ffrt-ffrt-queue-t.md) queue | Queue. |

**Returns**

| Type                        | Description|
|----------------------------| -- |
| FFRT_C_API [ffrt_loop_t](capi-ffrt-ffrt-loop-t.md) | Non-null loop handle if the loop is created successfully;<br>         null pointer otherwise. |

### ffrt_loop_destroy()

```c
FFRT_C_API int ffrt_loop_destroy(ffrt_loop_t loop)
```

**Description**

Destroys a loop. Calling this API releases the resources associated with the loop.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_loop_t](capi-ffrt-ffrt-loop-t.md) loop | Loop handle. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | `0` if the loop is destroyed successfully;<br>         otherwise `-1`. |

### ffrt_loop_run()

```c
FFRT_C_API int ffrt_loop_run(ffrt_loop_t loop)
```

**Description**

Starts a loop iteration. This function exclusively occupies the calling thread and runs the event loop synchronously on the current calling thread until [ffrt_loop_stop](capi-loop-h.md#ffrt_loop_stop) is called.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_loop_t](capi-ffrt-ffrt-loop-t.md) loop | Loop handle. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | Returns `0` if the loop runs successfully;<br>         otherwise returns `-1`. |

**Reference**

[ffrt_loop_stop](capi-loop-h.md#ffrt_loop_stop)


### ffrt_loop_stop()

```c
FFRT_C_API void ffrt_loop_stop(ffrt_loop_t loop)
```

**Description**

Stops a loop. After this API is called, the thread that is running [ffrt_loop_run](capi-loop-h.md#ffrt_loop_run) stops the loop and returns.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_loop_t](capi-ffrt-ffrt-loop-t.md) loop | Loop handle. |

**Reference**

[ffrt_loop_run](capi-loop-h.md#ffrt_loop_run)


### ffrt_loop_epoll_ctl()

```c
FFRT_C_API int ffrt_loop_epoll_ctl(ffrt_loop_t loop, int op, int fd, uint32_t events, void *data, ffrt_poller_cb cb)
```

**Description**

Controls the epoll file descriptor on the FFRT loop. Adds, modifies, or removes the monitored events on the target file descriptor.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_loop_t](capi-ffrt-ffrt-loop-t.md) loop | Loop handle. |
| int op | Type of the operation to perform on the target file descriptor, such as add, modify, or delete. |
| int fd | Target file descriptor on which the operation is performed. |
| uint32_t events | Type of the events to listen for (for example, readable or writable). Bitwise OR combination is supported. |
| void *data | User data passed to `cb`. |
| [ffrt_poller_cb](capi-type-def-h.md#ffrt_poller_cb) cb | Callback invoked when the target fd is polled. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | Returns `0` if the operation is successful;<br>         otherwise, returns `-1`. |

### ffrt_loop_timer_start()

```c
FFRT_C_API ffrt_timer_t ffrt_loop_timer_start(ffrt_loop_t loop, uint64_t timeout, void* data, ffrt_timer_cb cb, bool repeat)
```

**Description**

Starts a timer on the FFRT loop. The callback is invoked after a timeout; if `repeat` is `true`, the timer is triggered periodically.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_loop_t](capi-ffrt-ffrt-loop-t.md) loop | Loop handle. |
| uint64_t timeout | Timeout duration, in milliseconds. The value ranges from 0 to +∞. |
| void* data | Pointer to the user data passed to `cb`. |
| [ffrt_timer_cb](capi-type-def-h.md#ffrt_timer_cb) cb | Callback invoked when the timeout expires. |
| bool repeat | Whether to execute the timer repeatedly. The value `true` means to repeat, and `false` means to execute only once. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API [ffrt_timer_t](capi-type-def-h.md#variables) | Timer handle. If `loop` or `cb` is null, `-1` is returned. |

**Reference**

[ffrt_loop_timer_stop](capi-loop-h.md#ffrt_loop_timer_stop)


### ffrt_loop_timer_stop()

```c
FFRT_C_API int ffrt_loop_timer_stop(ffrt_loop_t loop, ffrt_timer_t handle)
```

**Description**

Stops a timer on the ffrt loop. After this API is called, the timer will no longer be triggered.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_loop_t](capi-ffrt-ffrt-loop-t.md) loop | Loop handle. |
| [ffrt_timer_t](capi-type-def-h.md#variables) handle | Timer handle, returned by [ffrt_loop_timer_start](capi-loop-h.md#ffrt_loop_timer_start). |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | Returns `0` if the operation is successful;<br>         otherwise returns `-1`. |

**Reference**

[ffrt_loop_timer_start](capi-loop-h.md#ffrt_loop_timer_start)



