# timer.h

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1bd5d6cdd22374b2fc7c67ab365167018faf622f translatedAt=2026-07-20T02:02:40.164Z pushedAt=2026-07-20T03:19:30.191Z -->

## Overview

This file declares the C APIs of the timer. The APIs provide timer capabilities based on QoS levels, support execution of callback functions after a specified timeout, and can be used in scenarios such as delayed task scheduling.

**File to include**: <ffrt/timer.h>

**Library**: libffrt.z.so

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 12

**Related module**: [FFRT](capi-ffrt.md)

## Summary

### Function

| Name| Description|
| -- | -- |
| [FFRT_C_API ffrt_timer_t ffrt_timer_start(ffrt_qos_t qos, uint64_t timeout, void* data, ffrt_timer_cb cb, bool repeat)](#ffrt_timer_start) | Starts a timer on an FFRT worker thread. Avoid calling `exit` or [ffrt_timer_stop](capi-timer-h.md#ffrt_timer_stop) in `cb` to prevent undefined behavior or deadlock. |
| [FFRT_C_API int ffrt_timer_stop(ffrt_qos_t qos, ffrt_timer_t handle)](#ffrt_timer_stop) | Stops a timer on an FFRT worker thread. This API is a blocking API. Avoid calling this API in a callback function to prevent deadlock or synchronization issues. When the callback corresponding to `handle` is being executed, this function waits for the callback to complete before returning. |

## Function Description

### ffrt_timer_start()

```c
FFRT_C_API ffrt_timer_t ffrt_timer_start(ffrt_qos_t qos, uint64_t timeout, void* data, ffrt_timer_cb cb, bool repeat)
```

**Description**

Starts a timer on an FFRT worker thread. Avoid calling `exit` or [ffrt_timer_stop](capi-timer-h.md#ffrt_timer_stop) in `cb` to prevent undefined behavior or deadlock.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_qos_t](capi-type-def-h.md#variables) qos | QoS level of the worker thread on which the timer runs. |
| uint64_t timeout | Timeout duration, in milliseconds. |
| void* data | Pointer to the user data passed to `cb`. |
| [ffrt_timer_cb](capi-type-def-h.md#ffrt_timer_cb) cb | User callback function invoked after timeout. |
| bool repeat | Whether to repeat the timer. The value `true` means to repeat, and `false` means to execute only once. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API [ffrt_timer_t](capi-type-def-h.md#variable) | Timer handle. `-1` is returned if the callback function is a null pointer or the QoS mapping is not registered. |

**Reference:**

[ffrt_timer_stop](capi-timer-h.md#ffrt_timer_stop)

### ffrt_timer_stop()

```c
FFRT_C_API int ffrt_timer_stop(ffrt_qos_t qos, ffrt_timer_t handle)
```

**Description**

Stops a timer on an FFRT worker thread. This API is a blocking API. Avoid calling this API in a callback function to prevent deadlock or synchronization issues. When the callback corresponding to `handle` is being executed, this function waits for the callback to complete before returning.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_qos_t](capi-type-def-h.md#variable) qos | QoS level of the worker thread on which the timer runs. It must be the same as the QoS level used in [ffrt_timer_start](capi-timer-h.md#ffrt_timer_start). |
| [ffrt_timer_t](capi-type-def-h.md#variable) handle | Handle to the target timer, returned by [ffrt_timer_start](capi-timer-h.md#ffrt_timer_start). |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | Result code. If the operation is successful, `0` is returned.<br>         If the operation fails, `-1` is returned. |

**Reference:**

[ffrt_timer_start](capi-timer-h.md#ffrt_timer_start)