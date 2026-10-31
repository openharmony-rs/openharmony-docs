# loop.h

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->

## Overview

This file declares the loop APIs in C.

**File to include**: <ffrt/loop.h>

**Library**: libffrt.z.so

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 12

**Related module**: [FFRT](capi-ffrt.md)

## Summary

### Structs

| Name             | Description|
|-----------------|----|
| [ffrt_loop_t](capi-ffrt-ffrt-loop-t.md) | Loop handle, which is used to identify different loops.  |

### Function

| Name| Description|
| -- | -- |
| [FFRT_C_API ffrt_loop_t ffrt_loop_create(ffrt_queue_t queue)](#ffrt_loop_create) | Creates a loop on a specified queue to run the event loop.|
| [FFRT_C_API int ffrt_loop_destroy(ffrt_loop_t loop)](#ffrt_loop_destroy) | Destroys a loop. This API can release resources associated with the loop.|
| [FFRT_C_API int ffrt_loop_run(ffrt_loop_t loop)](#ffrt_loop_run) | Runs one iteration of a loop. This function exclusively occupies the calling thread and synchronously runs the event loop in the current calling thread until [ffrt_loop_stop](capi-loop-h.md#ffrt_loop_stop) is called.|
| [FFRT_C_API void ffrt_loop_stop(ffrt_loop_t loop)](#ffrt_loop_stop) | Stops a loop. After this function is called, the thread that is executing [ffrt_loop_run](capi-loop-h.md#ffrt_loop_run) stops the loop and returns.|
| [FFRT_C_API int ffrt_loop_epoll_ctl(ffrt_loop_t loop, int op, int fd, uint32_t events, void *data, ffrt_poller_cb cb)](#ffrt_loop_epoll_ctl) | Controls the epoll file descriptor on an FFRT loop. It adds, modifies, or deletes listening events on the target file descriptor.|
| [FFRT_C_API ffrt_timer_t ffrt_loop_timer_start(ffrt_loop_t loop, uint64_t timeout, void* data, ffrt_timer_cb cb, bool repeat)](#ffrt_loop_timer_start) | Starts the timer on an FFRT loop. After the timer expires, the callback function is called. If `repeat` is `true`, the timer is triggered periodically.|
| [FFRT_C_API int ffrt_loop_timer_stop(ffrt_loop_t loop, ffrt_timer_t handle)](#ffrt_loop_timer_stop) | Stops the timer on an FFRT loop. After this function is called, the timer will not be triggered.|

## Function Description

### ffrt_loop_create()

```c
FFRT_C_API ffrt_loop_t ffrt_loop_create(ffrt_queue_t queue)
```

**Description**

Creates a loop on a specified queue to run the event loop.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_queue_t](capi-ffrt-ffrt-queue-t.md) queue | Queue.|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API [ffrt_loop_t](capi-ffrt-ffrt-loop-t.md) | If the operation is successful, a non-null loop handle is returned.<br>         Otherwise, a null pointer is returned.|

### ffrt_loop_destroy()

```c
FFRT_C_API int ffrt_loop_destroy(ffrt_loop_t loop)
```

**Description**

Destroys a loop. This API can release resources associated with the loop.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_loop_t](capi-ffrt-ffrt-loop-t.md) loop | Loop handle.|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | If the operation is successful, `0` is returned.<br>         Otherwise, `-1` is returned.|

### ffrt_loop_run()

```c
FFRT_C_API int ffrt_loop_run(ffrt_loop_t loop)
```

**Description**

Runs one iteration of a loop. This function exclusively occupies the calling thread and synchronously runs the event loop in the current calling thread until [ffrt_loop_stop](capi-loop-h.md#ffrt_loop_stop) is called.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_loop_t](capi-ffrt-ffrt-loop-t.md) loop | Loop handle.|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | If the operation is successful, `0` is returned.<br>         Otherwise, <idp:inline displayname="code" id="code718621153317">-1</idp:inline> is returned.|

**Reference**

[ffrt_loop_stop](capi-loop-h.md#ffrt_loop_stop)


### ffrt_loop_stop()

```c
FFRT_C_API void ffrt_loop_stop(ffrt_loop_t loop)
```

**Description**

Stops a loop. After this function is called, the thread that is executing [ffrt_loop_run](capi-loop-h.md#ffrt_loop_run) stops the loop and returns.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_loop_t](capi-ffrt-ffrt-loop-t.md) loop | Loop handle.|

**Reference**

[ffrt_loop_run](capi-loop-h.md#ffrt_loop_run)


### ffrt_loop_epoll_ctl()

```c
FFRT_C_API int ffrt_loop_epoll_ctl(ffrt_loop_t loop, int op, int fd, uint32_t events, void *data, ffrt_poller_cb cb)
```

**Description**

Controls the epoll file descriptor on an FFRT loop. It adds, modifies, or deletes listening events on the target file descriptor.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_loop_t](capi-ffrt-ffrt-loop-t.md) loop | Loop handle.|
| int op | Type of operation to be performed on the target file descriptor, such as adding, modifying, or deleting.|
| int fd | Target file descriptor on which an operation is to be performed.|
| uint32_t events | Type of the event to be listened for (such as readable or writable). Bitwise OR combination is supported.|
| void *data | User data passed to `cb`.|
| [ffrt_poller_cb](capi-type-def-h.md#ffrt_poller_cb) cb | User callback function executed when the target file descriptor is polled.|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | If the operation is successful, `0` is returned.<br>         Otherwise, <idp:inline displayname="code" id="code318182103317">-1</idp:inline> is returned.|

### ffrt_loop_timer_start()

```c
FFRT_C_API ffrt_timer_t ffrt_loop_timer_start(ffrt_loop_t loop, uint64_t timeout, void* data, ffrt_timer_cb cb, bool repeat)
```

**Description**

Starts the timer on an FFRT loop. After the timer expires, the callback function is called. If `repeat` is `true`, the timer is triggered periodically.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_loop_t](capi-ffrt-ffrt-loop-t.md) loop | Loop handle.|
| uint64_t timeout | Timeout interval, in milliseconds. The value range is [0, +∞).|
| void* data | User data passed to <idp:inline displayname="code" id="code1340912552363">cb</idp:inline>.|
| [ffrt_timer_cb](capi-type-def-h.md#ffrt_timer_cb) cb | User callback function invoked upon a timeout.|
| bool repeat | Whether to repeat the timer. The value `true` indicates that the timer is repeated, and the value `false` indicates that the timer is executed only once.|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API [ffrt_timer_t](capi-type-def-h.md#variables)| Timer handle. If `loop` or `cb` is null, `-1` is returned.|

**Reference**

[ffrt_loop_timer_stop](capi-loop-h.md#ffrt_loop_timer_stop)


### ffrt_loop_timer_stop()

```c
FFRT_C_API int ffrt_loop_timer_stop(ffrt_loop_t loop, ffrt_timer_t handle)
```

**Description**

Stops the timer on an FFRT loop. After this function is called, the timer will not be triggered.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_loop_t](capi-ffrt-ffrt-loop-t.md) loop | Loop handle.|
| [ffrt_timer_t](capi-type-def-h.md#variables) handle| Timer handle, which is returned by [ffrt_loop_timer_start](capi-loop-h.md#ffrt_loop_timer_start).|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | If the operation is successful, `0` is returned.<br>         Otherwise, <idp:inline displayname="code" id="code1181721143314">-1</idp:inline> is returned.|

**Reference**

[ffrt_loop_timer_start](capi-loop-h.md#ffrt_loop_timer_start)
