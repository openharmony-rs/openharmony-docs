# mutex.h

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->

## Overview

This file declares the C APIs for the mutex, providing mutual exclusion between concurrent tasks to protect shared resources from race conditions.

**File to include**: <ffrt/mutex.h>

**Library**: libffrt.z.so

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

## Summary

### Function

| Name| Description|
| -- | -- |
| [FFRT_C_API int ffrt_mutexattr_init(ffrt_mutexattr_t* attr)](#ffrt_mutexattr_init) | Initializes a mutex attribute. After the initialization is successful, the mutex attribute is set to the default value. When the mutex attribute is no longer needed, it must be destroyed via [ffrt_mutexattr_destroy](capi-mutex-h.md#ffrt_mutexattr_destroy).|
| [FFRT_C_API int ffrt_mutexattr_settype(ffrt_mutexattr_t* attr, int type)](#ffrt_mutexattr_settype) | Sets the type of the mutex attribute. The type can be `ffrt_mutex_normal` (normal mutex) or `ffrt_mutex_recursive` (recursive mutex, which allows the same task to acquire the lock multiple times).|
| [FFRT_C_API int ffrt_mutexattr_gettype(ffrt_mutexattr_t* attr, int* type)](#ffrt_mutexattr_gettype) | Obtains the type of the mutex attribute. After the API call is successful, the type is returned through the output parameter `type`.|
| [FFRT_C_API int ffrt_mutexattr_destroy(ffrt_mutexattr_t* attr)](#ffrt_mutexattr_destroy) | Destroys a mutex attribute. The mutex attribute must have been initialized via [ffrt_mutexattr_init](capi-mutex-h.md#ffrt_mutexattr_init).|
| [FFRT_C_API int ffrt_mutex_init(ffrt_mutex_t* mutex, const ffrt_mutexattr_t* attr)](#ffrt_mutex_init) | Initializes a mutex. When the mutex is no longer needed, it must be destroyed via [ffrt_mutex_destroy](capi-mutex-h.md#ffrt_mutex_destroy). Pass the configured mutex attributes through `attr`, or pass a null pointer to use the default values.|
| [FFRT_C_API int ffrt_mutex_lock(ffrt_mutex_t* mutex)](#ffrt_mutex_lock) | Locks a mutex. If the mutex is already held by another thread, the current thread is blocked until the mutex becomes available. On success, the calling thread holds the mutex until it is released via [ffrt_mutex_unlock](capi-mutex-h.md#ffrt_mutex_unlock).|
| [FFRT_C_API int ffrt_mutex_unlock(ffrt_mutex_t* mutex)](#ffrt_mutex_unlock) | Unlocks a mutex. The calling thread must already hold the mutex, and the lock must have been previously obtained via [ffrt_mutex_lock](capi-mutex-h.md#ffrt_mutex_lock) or [ffrt_mutex_trylock](capi-mutex-h.md#ffrt_mutex_trylock).|
| [FFRT_C_API int ffrt_mutex_trylock(ffrt_mutex_t* mutex)](#ffrt_mutex_trylock) | Attempts to lock a mutex. This API is non-blocking: if the mutex is already held by another thread, it immediately returns an error code. On success, the calling thread holds the mutex until it is released via [ffrt_mutex_unlock](capi-mutex-h.md#ffrt_mutex_unlock).|
| [FFRT_C_API int ffrt_mutex_destroy(ffrt_mutex_t* mutex)](#ffrt_mutex_destroy) | Destroys a mutex. After this API is successfully called, the resources occupied by the mutex are released, and the mutex object can no longer be used. The mutex must have been initialized by [ffrt_mutex_init](capi-mutex-h.md#ffrt_mutex_init) and must not be held by any thread when this API is called.|

## Function Description

### ffrt_mutexattr_init()

```c
FFRT_C_API int ffrt_mutexattr_init(ffrt_mutexattr_t* attr)
```

**Description**

Initializes a mutex attribute. After the initialization is successful, the mutex attribute is set to the default value. When the mutex attribute is no longer needed, it must be destroyed via [ffrt_mutexattr_destroy](capi-mutex-h.md#ffrt_mutexattr_destroy).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_mutexattr_t](capi-ffrt-ffrt-mutexattr-t.md)* attr | Pointer to the mutex attribute.|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | If the operation is successful, `ffrt_success` is returned.<br>         Otherwise, `ffrt_error_inval` is returned.|

### ffrt_mutexattr_settype()

```c
FFRT_C_API int ffrt_mutexattr_settype(ffrt_mutexattr_t* attr, int type)
```

**Description**

Sets the type of the mutex attribute. The type can be `ffrt_mutex_normal` (normal mutex) or `ffrt_mutex_recursive` (recursive mutex, which allows the same task to acquire the lock multiple times).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_mutexattr_t](capi-ffrt-ffrt-mutexattr-t.md)* attr | Pointer to the mutex attribute.|
| int type | Mutex type. The value can be `ffrt_mutex_normal`, `ffrt_mutex_recursive`, or `ffrt_mutex_default` (equivalent to `ffrt_mutex_normal`).|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | If the operation is successful, `ffrt_success` is returned.<br>         If `attr` is a null pointer, or if the mutex attribute type is neither `ffrt_mutex_normal` nor `ffrt_mutex_recursive`,<br>         `ffrt_error_inval` is returned.|

**Reference**

[ffrt_mutex_type](capi-type-def-h.md#ffrt_mutex_type)


### ffrt_mutexattr_gettype()

```c
FFRT_C_API int ffrt_mutexattr_gettype(ffrt_mutexattr_t* attr, int* type)
```

**Description**

Obtains the type of the mutex attribute. After the API call is successful, the type is returned through the output parameter `type`.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_mutexattr_t](capi-ffrt-ffrt-mutexattr-t.md)* attr | Pointer to the mutex attribute.|
| int* type | Pointer to the mutex type, which is used to receive the obtained type value (`ffrt_mutex_normal` or `ffrt_mutex_recursive`).|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | If the operation is successful, `ffrt_success` is returned.<br>         If `attr` or `type` is a null pointer, `ffrt_error_inval` is returned.|

### ffrt_mutexattr_destroy()

```c
FFRT_C_API int ffrt_mutexattr_destroy(ffrt_mutexattr_t* attr)
```

**Description**

Destroys a mutex attribute. The mutex attribute must have been initialized via [ffrt_mutexattr_init](capi-mutex-h.md#ffrt_mutexattr_init).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_mutexattr_t](capi-ffrt-ffrt-mutexattr-t.md)* attr | Pointer to the mutex attribute.|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | If the operation is successful, `ffrt_success` is returned.<br>         Otherwise, <idp:inline displayname="code" id="code993617296318">ffrt_error_inval</idp:inline> is returned.|

### ffrt_mutex_init()

```c
FFRT_C_API int ffrt_mutex_init(ffrt_mutex_t* mutex, const ffrt_mutexattr_t* attr)
```

**Description**

Initializes a mutex. When the mutex is no longer needed, it must be destroyed via [ffrt_mutex_destroy](capi-mutex-h.md#ffrt_mutex_destroy). Pass the configured mutex attributes through `attr`, or pass a null pointer to use the default values.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_mutex_t](capi-ffrt-ffrt-mutex-t.md)* mutex | Pointer to the mutex.|
| [const ffrt_mutexattr_t](capi-ffrt-ffrt-mutexattr-t.md)* attr | Pointer to the mutex attribute or a null pointer to use the default values.|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | If the operation is successful, `ffrt_success` is returned.<br>         If `mutex` is null, or `attr` is not null but no valid mutex type is specified, `ffrt_error_inval` is returned.|

### ffrt_mutex_lock()

```c
FFRT_C_API int ffrt_mutex_lock(ffrt_mutex_t* mutex)
```

**Description**

Locks a mutex. If the mutex is already held by another thread, the current thread is blocked until the mutex becomes available. On success, the calling thread holds the mutex until it is released via [ffrt_mutex_unlock](capi-mutex-h.md#ffrt_mutex_unlock).

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_mutex_t](capi-ffrt-ffrt-mutex-t.md)* mutex | Pointer to the mutex.|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | If the operation is successful, `ffrt_success` is returned.<br>         Otherwise, <idp:inline displayname="code" id="code59361229837">ffrt_error_inval</idp:inline> is returned.|

**Reference**

[ffrt_mutex_trylock](capi-mutex-h.md#ffrt_mutex_trylock)


### ffrt_mutex_unlock()

```c
FFRT_C_API int ffrt_mutex_unlock(ffrt_mutex_t* mutex)
```

**Description**

Unlocks a mutex. The calling thread must already hold the mutex, and the lock must have been previously obtained via [ffrt_mutex_lock](capi-mutex-h.md#ffrt_mutex_lock) or [ffrt_mutex_trylock](capi-mutex-h.md#ffrt_mutex_trylock).

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_mutex_t](capi-ffrt-ffrt-mutex-t.md)* mutex | Pointer to the mutex.|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | If the operation is successful, `ffrt_success` is returned.<br>         Otherwise, <idp:inline displayname="code" id="code1293617298310">ffrt_error_inval</idp:inline> is returned.|

### ffrt_mutex_trylock()

```c
FFRT_C_API int ffrt_mutex_trylock(ffrt_mutex_t* mutex)
```

**Description**

Attempts to lock a mutex. This API is non-blocking: if the mutex is already held by another thread, it immediately returns an error code. On success, the calling thread holds the mutex until it is released via [ffrt_mutex_unlock](capi-mutex-h.md#ffrt_mutex_unlock).

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_mutex_t](capi-ffrt-ffrt-mutex-t.md)* mutex | Pointer to the mutex.|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | If the operation is successful, `ffrt_success` is returned.<br>         Otherwise, `ffrt_error_inval` or `ffrt_error_busy` is returned.|

**Reference**

[ffrt_mutex_lock](capi-mutex-h.md#ffrt_mutex_lock)


### ffrt_mutex_destroy()

```c
FFRT_C_API int ffrt_mutex_destroy(ffrt_mutex_t* mutex)
```

**Description**

Destroys a mutex. After this API is successfully called, the resources occupied by the mutex are released, and the mutex object can no longer be used. The mutex must have been initialized by [ffrt_mutex_init](capi-mutex-h.md#ffrt_mutex_init) and must not be held by any thread when this API is called.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_mutex_t](capi-ffrt-ffrt-mutex-t.md)* mutex | Pointer to the mutex.|

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | If the operation is successful, `ffrt_success` is returned.<br>         Otherwise, <idp:inline displayname="code" id="code1293713296320">ffrt_error_inval</idp:inline> is returned.|
