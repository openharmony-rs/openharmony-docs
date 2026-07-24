# condition_variable.h

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->

## Overview

This file declares the C APIs for condition variables.

**File to include**: <ffrt/condition_variable.h>

**Library**: libffrt.z.so

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

## Summary

### Function

| Name| Description|
| -- | -- |
| [FFRT_C_API int ffrt_cond_init(ffrt_cond_t* cond, const ffrt_condattr_t* attr)](#ffrt_cond_init) | Initializes a condition variable. If the condition variable is no longer needed, it must be destroyed via [ffrt_cond_destroy](capi-condition-variable-h.md#ffrt_cond_destroy).|
| [FFRT_C_API int ffrt_cond_signal(ffrt_cond_t* cond)](#ffrt_cond_signal) | Unblocks at least one thread that is currently blocked on a condition variable.|
| [FFRT_C_API int ffrt_cond_broadcast(ffrt_cond_t* cond)](#ffrt_cond_broadcast) | Unblocks all threads that are currently blocked on a condition variable.|
| [FFRT_C_API int ffrt_cond_wait(ffrt_cond_t* cond, ffrt_mutex_t* mutex)](#ffrt_cond_wait) | Blocks the calling thread on a condition variable. The calling thread must hold the mutex when entering this function. While blocked, the mutex is atomically released and reacquired before the function returns, so the caller regains ownership of the mutex upon wakeup. The thread is woken by another thread calling [ffrt_cond_signal](capi-condition-variable-h.md#ffrt_cond_signal) or [ffrt_cond_broadcast](capi-condition-variable-h.md#ffrt_cond_broadcast). After waking, the caller must re-check the predicate to guard against spurious wakeups.|
| [FFRT_C_API int ffrt_cond_timedwait(ffrt_cond_t* cond, ffrt_mutex_t* mutex, const struct timespec* time_point)](#ffrt_cond_timedwait) | Blocks the calling thread until the specified time point. If [ffrt_cond_signal](capi-condition-variable-h.md#ffrt_cond_signal) or [ffrt_cond_broadcast](capi-condition-variable-h.md#ffrt_cond_broadcast) is not called to wake the thread before `time_point` is reached, the thread will be automatically unblocked.|
| [FFRT_C_API int ffrt_cond_destroy(ffrt_cond_t* cond)](#ffrt_cond_destroy) | Destroys a condition variable. The condition variable must have been initialized by [ffrt_cond_init](capi-condition-variable-h.md#ffrt_cond_init) and must not be held by any thread when this API is called.|

## Function Description

### ffrt_cond_init()

```c
FFRT_C_API int ffrt_cond_init(ffrt_cond_t* cond, const ffrt_condattr_t* attr)
```

**Description**

Initializes a condition variable. If the condition variable is no longer needed, it must be destroyed via [ffrt_cond_destroy](capi-condition-variable-h.md#ffrt_cond_destroy).

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_cond_t](capi-ffrt-ffrt-cond-t.md)* cond | Pointer to the condition variable.|
| [const ffrt_condattr_t](capi-ffrt-ffrt-condattr-t.md)* attr | Pointer to the condition variable attribute.|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | If the operation is successful, `ffrt_success` is returned.<br>         Otherwise, `ffrt_error_inval` is returned.|

### ffrt_cond_signal()

```c
FFRT_C_API int ffrt_cond_signal(ffrt_cond_t* cond)
```

**Description**

Unblocks at least one thread that is currently blocked on a condition variable.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_cond_t](capi-ffrt-ffrt-cond-t.md)* cond | Pointer to the condition variable.|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | If the operation is successful, `ffrt_success` is returned.<br>         Otherwise, <idp:inline displayname="code" id="code1737202615413">ffrt_error_inval</idp:inline> is returned.|

**Reference**

[ffrt_cond_wait](capi-condition-variable-h.md#ffrt_cond_wait)


### ffrt_cond_broadcast()

```c
FFRT_C_API int ffrt_cond_broadcast(ffrt_cond_t* cond)
```

**Description**

Unblocks all threads that are currently blocked on a condition variable.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_cond_t](capi-ffrt-ffrt-cond-t.md)* cond | Pointer to the condition variable.|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | If the operation is successful, `ffrt_success` is returned.<br>         Otherwise, <idp:inline displayname="code" id="code273872615416">ffrt_error_inval</idp:inline> is returned.|

**Reference**

[ffrt_cond_wait](capi-condition-variable-h.md#ffrt_cond_wait)


### ffrt_cond_wait()

```c
FFRT_C_API int ffrt_cond_wait(ffrt_cond_t* cond, ffrt_mutex_t* mutex)
```

**Description**

Blocks the calling thread on a condition variable. The calling thread must hold the mutex when entering this function. While blocked, the mutex is atomically released and reacquired before the function returns, so the caller regains ownership of the mutex upon wakeup. The thread is woken by another thread calling [ffrt_cond_signal](capi-condition-variable-h.md#ffrt_cond_signal) or [ffrt_cond_broadcast](capi-condition-variable-h.md#ffrt_cond_broadcast). After waking, the caller must re-check the predicate to guard against spurious wakeups.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_cond_t](capi-ffrt-ffrt-cond-t.md)* cond | Pointer to the condition variable.|
| [ffrt_mutex_t](capi-ffrt-ffrt-mutex-t.md)* mutex | Pointer to the mutex held by the calling thread.|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | If the operation is successful, `ffrt_success` is returned.<br>         Otherwise, <idp:inline displayname="code" id="code137391726040">ffrt_error_inval</idp:inline> is returned.|

**Reference**

[ffrt_cond_timedwait](capi-condition-variable-h.md#ffrt_cond_timedwait)

[ffrt_cond_signal](capi-condition-variable-h.md#ffrt_cond_signal)

[ffrt_cond_broadcast](capi-condition-variable-h.md#ffrt_cond_broadcast)


### ffrt_cond_timedwait()

```c
FFRT_C_API int ffrt_cond_timedwait(ffrt_cond_t* cond, ffrt_mutex_t* mutex, const struct timespec* time_point)
```

**Description**

Blocks the calling thread until the specified time point. If [ffrt_cond_signal](capi-condition-variable-h.md#ffrt_cond_signal) or [ffrt_cond_broadcast](capi-condition-variable-h.md#ffrt_cond_broadcast) is not called to wake the thread before `time_point` is reached, the thread will be automatically unblocked.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_cond_t](capi-ffrt-ffrt-cond-t.md)* cond | Pointer to the condition variable.|
| [ffrt_mutex_t](capi-ffrt-ffrt-mutex-t.md)* mutex | Pointer to the mutex.|
| const struct timespec* time_point | Absolute time point when the wait expires.|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | If the operation is successful, `ffrt_success` is returned.<br>         If the thread is not unblocked and `time_point` is reached, `ffrt_error_timedout` is returned.<br>         If `cond`, `mutex`, or `time_point` is null, `ffrt_error_inval` is returned.|

**Reference**

[ffrt_cond_wait](capi-condition-variable-h.md#ffrt_cond_wait)

[ffrt_cond_signal](capi-condition-variable-h.md#ffrt_cond_signal)

[ffrt_cond_broadcast](capi-condition-variable-h.md#ffrt_cond_broadcast)


### ffrt_cond_destroy()

```c
FFRT_C_API int ffrt_cond_destroy(ffrt_cond_t* cond)
```

**Description**

Destroys a condition variable. The condition variable must have been initialized by [ffrt_cond_init](capi-condition-variable-h.md#ffrt_cond_init) and must not be held by any thread when this API is called.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_cond_t](capi-ffrt-ffrt-cond-t.md)* cond | Pointer to the condition variable.|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | If the operation is successful, `ffrt_success` is returned.<br>         Otherwise, <idp:inline displayname="code" id="code157391226145">ffrt_error_inval</idp:inline> is returned.|
