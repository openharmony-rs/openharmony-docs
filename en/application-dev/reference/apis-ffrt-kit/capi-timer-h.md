# timer.h

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1c82fe64143ca179b80fafe272ca5a84323e9159 translatedAt=2026-11-13T03:09:58.006Z pushedAt=2026-11-13T09:02:41.324Z nl=1 -->

## Overview

Declares the C APIs of the timer. This module provides timer capabilities based on QoS levels, supports executing a callback after a specified timeout, and can be used for scenarios such as delayed task scheduling.

**File to include**: <ffrt/timer.h>

**Library**: libffrt.z.so

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 12

**Related module**: [FFRT](capi-ffrt.md)

## Summary

### Function

| Name| Description|
| -- | -- |
| [FFRT_C_API ffrt_timer_t ffrt_timer_start(ffrt_qos_t qos, uint64_t timeout, void* data, ffrt_timer_cb cb, bool repeat)](#ffrt_timer_start) | Starts a timer on the FFRT worker thread. Do not call **exit** or [ffrt_timer_stop](capi-timer-h.md#ffrt_timer_stop) in **cb** to prevent undefined behavior or deadlock. |
| [FFRT_C_API int ffrt_timer_stop(ffrt_qos_t qos, ffrt_timer_t handle)](#ffrt_timer_stop) | Stops a timer on the FFRT worker thread. This API is a blocking API. Do not call this API in the callback function to prevent deadlock or synchronization issues. When the callback corresponding to **handle** is being executed, this function waits for the callback to complete before returning. |

## Function Description

### ffrt_timer_start()

```c
FFRT_C_API ffrt_timer_t ffrt_timer_start(ffrt_qos_t qos, uint64_t timeout, void* data, ffrt_timer_cb cb, bool repeat)
```

**Description**

Starts a timer on the FFRT worker thread. Do not call **exit** or [ffrt_timer_stop](capi-timer-h.md#ffrt_timer_stop) in **cb** to prevent undefined behavior or deadlock.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_qos_t](capi-type-def-h.md#variables) qos | QoS level of the worker thread that runs the timer. |
| uint64_t timeout | Timeout duration, in milliseconds. |
| void* data | Pointer to the user data passed to **cb**. |
| [ffrt_timer_cb](capi-type-def-h.md#ffrt_timer_cb) cb | User callback function executed after the timeout. |
| bool repeat | Whether to repeat the timer. **true** indicates repeat, and **false** indicates execution only once. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API [ffrt_timer_t](capi-type-def-h.md#variables) | Timer handle. If the callback function is a null pointer or the QoS mapping is not registered, **-1** is returned. |

**Reference**

[ffrt_timer_stop](capi-timer-h.md#ffrt_timer_stop)


### ffrt_timer_stop()

```c
FFRT_C_API int ffrt_timer_stop(ffrt_qos_t qos, ffrt_timer_t handle)
```

**Description**

Stops a timer on the FFRT worker thread. This API is a blocking API. Do not call this API in the callback function to prevent deadlock or synchronization issues. When the callback corresponding to **handle** is being executed, this function waits for the callback to complete before returning.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_qos_t](capi-type-def-h.md#variables) qos | QoS level of the worker thread that runs the timer. It must be consistent with the QoS level used in [ffrt_timer_start](capi-timer-h.md#ffrt_timer_start). |
| [ffrt_timer_t](capi-type-def-h.md#variables) handle | Handle of the target timer, returned by [ffrt_timer_start](capi-timer-h.md#ffrt_timer_start). |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | Returns **0** if the operation is successful. <br>         Returns **-1** otherwise. |

**Reference**

[ffrt_timer_start](capi-timer-h.md#ffrt_timer_start)



