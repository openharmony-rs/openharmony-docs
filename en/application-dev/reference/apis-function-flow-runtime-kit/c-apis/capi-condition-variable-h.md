# condition_variable.h

## Overview

Declares the condition variable interfaces in C.

**Library**: libffrt.z.so

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [FFRT_C_API int ffrt_cond_init(ffrt_cond_t* cond, const ffrt_condattr_t* attr)](#ffrt_cond_init) | Initializes a condition variable.<br> The condition variable must later be destroyed by [ffrt_cond_destroy](capi-condition-variable-h.md#ffrt_cond_destroy) when no longer in use. |
| [FFRT_C_API int ffrt_cond_signal(ffrt_cond_t* cond)](#ffrt_cond_signal) | Unblocks at least one of the threads that are blocked on a condition variable. |
| [FFRT_C_API int ffrt_cond_broadcast(ffrt_cond_t* cond)](#ffrt_cond_broadcast) | Unblocks all threads currently blocked on a condition variable. |
| [FFRT_C_API int ffrt_cond_wait(ffrt_cond_t* cond, ffrt_mutex_t* mutex)](#ffrt_cond_wait) | Blocks the calling thread on a condition variable.<br> The mutex must be held by the calling thread on entry. It is atomically released while the thread is blocked, and re-acquired before the function returns, so the caller regains ownership of the mutex on wakeup. The thread is unblocked by a call to [ffrt_cond_signal](capi-condition-variable-h.md#ffrt_cond_signal) or [ffrt_cond_broadcast](capi-condition-variable-h.md#ffrt_cond_broadcast) from another thread. The caller is responsible for re-checking the predicate after wakeup to guard against spurious wakeups. |
| [FFRT_C_API int ffrt_cond_timedwait(ffrt_cond_t* cond, ffrt_mutex_t* mutex, const struct timespec* time_point)](#ffrt_cond_timedwait) | Blocks the calling thread until a given time point.<br> If [ffrt_cond_signal](capi-condition-variable-h.md#ffrt_cond_signal) or [ffrt_cond_broadcast](capi-condition-variable-h.md#ffrt_cond_broadcast) is not called to unblock the thread before `time_point` is reached, the thread is automatically unblocked. |
| [FFRT_C_API int ffrt_cond_destroy(ffrt_cond_t* cond)](#ffrt_cond_destroy) | Destroys a condition variable.<br> The condition variable must have been initialized by [ffrt_cond_init](capi-condition-variable-h.md#ffrt_cond_init) and must not be referenced by any thread on entry. |

## Function description

### ffrt_cond_init()

```c
FFRT_C_API int ffrt_cond_init(ffrt_cond_t* cond, const ffrt_condattr_t* attr)
```

**Description**

Initializes a condition variable.<br> The condition variable must later be destroyed by [ffrt_cond_destroy](capi-condition-variable-h.md#ffrt_cond_destroy) when no longer in use.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_cond_t* cond | Indicates a pointer to the condition variable. |
| const ffrt_condattr_t* attr | Indicates a pointer to the condition variable attribute. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API int | `ffrt_success` if the condition variable is initialized;          `ffrt_error_inval` otherwise. |

### ffrt_cond_signal()

```c
FFRT_C_API int ffrt_cond_signal(ffrt_cond_t* cond)
```

**Description**

Unblocks at least one of the threads that are blocked on a condition variable.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_cond_t* cond | Indicates a pointer to the condition variable. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API int | `ffrt_success` if the thread is unblocked;          `ffrt_error_inval` otherwise. |

**Reference**:

[ffrt_cond_wait](capi-condition-variable-h.md#ffrt_cond_wait)


### ffrt_cond_broadcast()

```c
FFRT_C_API int ffrt_cond_broadcast(ffrt_cond_t* cond)
```

**Description**

Unblocks all threads currently blocked on a condition variable.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_cond_t* cond | Indicates a pointer to the condition variable. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API int | `ffrt_success` if the threads are unblocked;          `ffrt_error_inval` otherwise. |

**Reference**:

[ffrt_cond_wait](capi-condition-variable-h.md#ffrt_cond_wait)


### ffrt_cond_wait()

```c
FFRT_C_API int ffrt_cond_wait(ffrt_cond_t* cond, ffrt_mutex_t* mutex)
```

**Description**

Blocks the calling thread on a condition variable.<br> The mutex must be held by the calling thread on entry. It is atomically released while the thread is blocked, and re-acquired before the function returns, so the caller regains ownership of the mutex on wakeup. The thread is unblocked by a call to [ffrt_cond_signal](capi-condition-variable-h.md#ffrt_cond_signal) or [ffrt_cond_broadcast](capi-condition-variable-h.md#ffrt_cond_broadcast) from another thread. The caller is responsible for re-checking the predicate after wakeup to guard against spurious wakeups.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_cond_t* cond | Indicates a pointer to the condition variable. |
| ffrt_mutex_t* mutex | Indicates a pointer to the mutex held by the calling thread. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API int | `ffrt_success` if the thread is unblocked after being blocked;          `ffrt_error_inval` otherwise. |

**Reference**:

[ffrt_cond_timedwait](capi-condition-variable-h.md#ffrt_cond_timedwait)
[ffrt_cond_signal](capi-condition-variable-h.md#ffrt_cond_signal)
[ffrt_cond_broadcast](capi-condition-variable-h.md#ffrt_cond_broadcast)


### ffrt_cond_timedwait()

```c
FFRT_C_API int ffrt_cond_timedwait(ffrt_cond_t* cond, ffrt_mutex_t* mutex, const struct timespec* time_point)
```

**Description**

Blocks the calling thread until a given time point.<br> If [ffrt_cond_signal](capi-condition-variable-h.md#ffrt_cond_signal) or [ffrt_cond_broadcast](capi-condition-variable-h.md#ffrt_cond_broadcast) is not called to unblock the thread before `time_point` is reached, the thread is automatically unblocked.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_cond_t* cond | Indicates a pointer to the condition variable. |
| ffrt_mutex_t* mutex | Indicates a pointer to the mutex. |
| const struct timespec* time_point | Indicates the absolute time point at which the wait expires. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API int | `ffrt_success` if the thread is unblocked after being blocked;          `ffrt_error_timedout` if `time_point` is reached without being signaled;          `ffrt_error_inval` if any of `cond`, `mutex`, or `time_point` is null. |

**Reference**:

[ffrt_cond_wait](capi-condition-variable-h.md#ffrt_cond_wait)
[ffrt_cond_signal](capi-condition-variable-h.md#ffrt_cond_signal)
[ffrt_cond_broadcast](capi-condition-variable-h.md#ffrt_cond_broadcast)


### ffrt_cond_destroy()

```c
FFRT_C_API int ffrt_cond_destroy(ffrt_cond_t* cond)
```

**Description**

Destroys a condition variable.<br> The condition variable must have been initialized by [ffrt_cond_init](capi-condition-variable-h.md#ffrt_cond_init) and must not be referenced by any thread on entry.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_cond_t* cond | Indicates a pointer to the condition variable. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API int | `ffrt_success` if the condition variable is destroyed;          `ffrt_error_inval` otherwise. |


