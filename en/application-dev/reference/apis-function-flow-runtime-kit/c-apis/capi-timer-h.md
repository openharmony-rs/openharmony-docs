# timer.h

## Overview

Declares the timer interfaces in C.<br> Provides timer capabilities based on QoS levels, supporting callback execution after a specified timeout. It can be used for delayed task scheduling and other scenarios.

**Library**: libffrt.z.so

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [FFRT_C_API ffrt_timer_t ffrt_timer_start(ffrt_qos_t qos, uint64_t timeout, void* data, ffrt_timer_cb cb, bool repeat)](#ffrt_timer_start) | Starts a timer on an FFRT worker.<br> Avoid calling `exit` or [ffrt_timer_stop](capi-timer-h.md#ffrt_timer_stop) in `cb` to prevent undefined behavior or deadlock. |
| [FFRT_C_API int ffrt_timer_stop(ffrt_qos_t qos, ffrt_timer_t handle)](#ffrt_timer_stop) | Stops a timer on an FFRT worker.<br> This is a blocking interface. Avoid calling it inside the callback function to prevent deadlock or synchronization issues. If the callback associated with `handle` is currently running, this function waits for the callback to complete before returning. |

## Function description

### ffrt_timer_start()

```c
FFRT_C_API ffrt_timer_t ffrt_timer_start(ffrt_qos_t qos, uint64_t timeout, void* data, ffrt_timer_cb cb, bool repeat)
```

**Description**

Starts a timer on an FFRT worker.<br> Avoid calling `exit` or [ffrt_timer_stop](capi-timer-h.md#ffrt_timer_stop) in `cb` to prevent undefined behavior or deadlock.

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_qos_t qos | Indicates the QoS of the worker that runs timer. |
| uint64_t timeout | Indicates the number of milliseconds that specifies timeout. |
| void* data | Indicates user data used in cb. |
| ffrt_timer_cb cb | Indicates user cb which will be executed when timeout. |
| bool repeat | Indicates whether to repeat this timer. `true` to repeat the timer, `false` to run it once. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API ffrt_timer_t | A timer handle; `-1` if the callback function is a null pointer or the QoS mapping is not registered. |

**Reference**:

[ffrt_timer_stop](capi-timer-h.md#ffrt_timer_stop)


### ffrt_timer_stop()

```c
FFRT_C_API int ffrt_timer_stop(ffrt_qos_t qos, ffrt_timer_t handle)
```

**Description**

Stops a timer on an FFRT worker.<br> This is a blocking interface. Avoid calling it inside the callback function to prevent deadlock or synchronization issues. If the callback associated with `handle` is currently running, this function waits for the callback to complete before returning.

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_qos_t qos | Indicates the QoS of the worker that runs the timer. Must match the QoS used in [ffrt_timer_start](capi-timer-h.md#ffrt_timer_start). |
| ffrt_timer_t handle | Indicates the target timer handle returned by [ffrt_timer_start](capi-timer-h.md#ffrt_timer_start). |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API int | `0` if success;          `-1` otherwise. |

**Reference**:

[ffrt_timer_start](capi-timer-h.md#ffrt_timer_start)



