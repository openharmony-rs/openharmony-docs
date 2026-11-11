# condition_variable.h

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1c82fe64143ca179b80fafe272ca5a84323e9159 translatedAt=2026-11-10T03:16:44.027Z pushedAt=2026-11-10T04:54:54.971Z nl=1 -->

## Overview

The **condition_variable.h** file declares the condition variable APIs in C.

**File to include**: <ffrt/condition_variable.h>

**Library**: libffrt.z.so

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

## Summary

### Function

| Name| Description|
| -- | -- |
| [FFRT_C_API int ffrt_cond_init(ffrt_cond_t* cond, const ffrt_condattr_t* attr)](#ffrt_cond_init) | Initializes a condition variable. When the condition variable is no longer used, it must be destroyed by [ffrt_cond_destroy](capi-condition-variable-h.md#ffrt_cond_destroy). |
| [FFRT_C_API int ffrt_cond_signal(ffrt_cond_t* cond)](#ffrt_cond_signal) | Wakes up at least one thread blocked on the condition variable. |
| [FFRT_C_API int ffrt_cond_broadcast(ffrt_cond_t* cond)](#ffrt_cond_broadcast) | Wakes up all threads currently blocked on the condition variable. |
| [FFRT_C_API int ffrt_cond_wait(ffrt_cond_t* cond, ffrt_mutex_t* mutex)](#ffrt_cond_wait) | Blocks the calling thread on the condition variable. The calling thread must hold the mutex when entering. During blocking, the mutex is atomically released and reacquired before the function returns, so that the caller regains ownership of the mutex upon wakeup. The thread is woken up by another thread calling [ffrt_cond_signal](capi-condition-variable-h.md#ffrt_cond_signal) or [ffrt_cond_broadcast](capi-condition-variable-h.md#ffrt_cond_broadcast). The caller must recheck the predicate after wakeup to guard against spurious wakeup. |
| [FFRT_C_API int ffrt_cond_timedwait(ffrt_cond_t* cond, ffrt_mutex_t* mutex, const struct timespec* time_point)](#ffrt_cond_timedwait) | Blocks the calling thread until the given time point. If [ffrt_cond_signal](capi-condition-variable-h.md#ffrt_cond_signal) or [ffrt_cond_broadcast](capi-condition-variable-h.md#ffrt_cond_broadcast) is not called to wake up the thread before `time_point` is reached, the thread is woken up automatically. |
| [FFRT_C_API int ffrt_cond_destroy(ffrt_cond_t* cond)](#ffrt_cond_destroy) | Destroys a condition variable. The condition variable must have been initialized by [ffrt_cond_init](capi-condition-variable-h.md#ffrt_cond_init) and must not be referenced by any thread when this API is called. |

## Function Description

### ffrt_cond_init()

```c
FFRT_C_API int ffrt_cond_init(ffrt_cond_t* cond, const ffrt_condattr_t* attr)
```

**Description**

Initializes a condition variable. When the condition variable is no longer used, it must be destroyed by [ffrt_cond_destroy](capi-condition-variable-h.md#ffrt_cond_destroy).

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_cond_t](capi-ffrt-ffrt-cond-t.md)* cond | Pointer to the condition variable. |
| [const ffrt_condattr_t](capi-ffrt-ffrt-condattr-t.md)* attr | Pointer to the condition variable attribute. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | Returns `ffrt_success` if the condition variable is initialized successfully;<br>         otherwise returns `ffrt_error_inval`. |

### ffrt_cond_signal()

```c
FFRT_C_API int ffrt_cond_signal(ffrt_cond_t* cond)
```

**Description**

Wakes up at least one thread that is blocked on the condition variable.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_cond_t](capi-ffrt-ffrt-cond-t.md)* cond | Pointer to the condition variable. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | Returns `ffrt_success` when the thread is woken up;<br>         otherwise, returns `ffrt_error_inval`. |

**Reference**

[ffrt_cond_wait](capi-condition-variable-h.md#ffrt_cond_wait)


### ffrt_cond_broadcast()

```c
FFRT_C_API int ffrt_cond_broadcast(ffrt_cond_t* cond)
```

**Description**

Wakes up all threads that are currently blocked on the condition variable.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_cond_t](capi-ffrt-ffrt-cond-t.md)* cond | Pointer to the condition variable. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | Returns `ffrt_success` when the thread is woken up;<br>         otherwise, returns `ffrt_error_inval`. |

**Reference**

[ffrt_cond_wait](capi-condition-variable-h.md#ffrt_cond_wait)


### ffrt_cond_wait()

```c
FFRT_C_API int ffrt_cond_wait(ffrt_cond_t* cond, ffrt_mutex_t* mutex)
```

**Description**

Blocks the calling thread on the condition variable. The calling thread must hold the mutex when entering. During blocking, the mutex is atomically released and reacquired before the function returns, so the caller regains ownership of the mutex upon wakeup. The thread is woken up by another thread calling [ffrt_cond_signal](capi-condition-variable-h.md#ffrt_cond_signal) or [ffrt_cond_broadcast](capi-condition-variable-h.md#ffrt_cond_broadcast). The caller must recheck the predicate after wakeup to guard against spurious wakeup.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_cond_t](capi-ffrt-ffrt-cond-t.md)* cond | Pointer to the condition variable. |
| [ffrt_mutex_t](capi-ffrt-ffrt-mutex-t.md)* mutex | Pointer to the mutex held by the calling thread. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | Returns `ffrt_success` if the thread is successfully woken up after being blocked;<br>         otherwise returns `ffrt_error_inval`. |

**Reference**

[ffrt_cond_timedwait](capi-condition-variable-h.md#ffrt_cond_timedwait)

[ffrt_cond_signal](capi-condition-variable-h.md#ffrt_cond_signal)

[ffrt_cond_broadcast](capi-condition-variable-h.md#ffrt_cond_broadcast)


### ffrt_cond_timedwait()

```c
FFRT_C_API int ffrt_cond_timedwait(ffrt_cond_t* cond, ffrt_mutex_t* mutex, const struct timespec* time_point)
```

**Description**

Blocks the calling thread until the given time point. If [ffrt_cond_signal](capi-condition-variable-h.md#ffrt_cond_signal) or [ffrt_cond_broadcast](capi-condition-variable-h.md#ffrt_cond_broadcast) is not called to wake up the thread before `time_point` is reached, the thread is woken up automatically.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_cond_t](capi-ffrt-ffrt-cond-t.md)* cond | Pointer to the condition variable. |
| [ffrt_mutex_t](capi-ffrt-ffrt-mutex-t.md)* mutex | Pointer to the mutex. |
| const struct timespec* time_point | Absolute time point at which the wait expires. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | Returns `ffrt_success` when it is successfully woken up after being blocked;<br>         Returns `ffrt_error_timedout` when it is not woken up and the `time_point` expires;<br>         Returns `ffrt_error_inval` if any of `cond`, `mutex`, or `time_point` is null. |

**Reference**

[ffrt_cond_wait](capi-condition-variable-h.md#ffrt_cond_wait)

[ffrt_cond_signal](capi-condition-variable-h.md#ffrt_cond_signal)

[ffrt_cond_broadcast](capi-condition-variable-h.md#ffrt_cond_broadcast)


### ffrt_cond_destroy()

```c
FFRT_C_API int ffrt_cond_destroy(ffrt_cond_t* cond)
```

**Description**

Destroys a condition variable. The condition variable must have been initialized by [ffrt_cond_init](capi-condition-variable-h.md#ffrt_cond_init) and must not be referenced by any thread when this API is called.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_cond_t](capi-ffrt-ffrt-cond-t.md)* cond | Pointer to the condition variable. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | Returns `ffrt_success` if the condition variable is destroyed successfully;<br>         otherwise returns `ffrt_error_inval`. |


