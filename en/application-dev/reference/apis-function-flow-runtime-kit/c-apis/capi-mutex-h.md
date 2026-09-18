# mutex.h

## Overview

Declares the mutex interfaces in C, which provide mutual exclusion between concurrent tasks to protect shared resources from race conditions.

**Library**: libffrt.z.so

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [FFRT_C_API int ffrt_mutexattr_init(ffrt_mutexattr_t* attr)](#ffrt_mutexattr_init) | Initializes a mutex attribute.<br> After successful initialization, the mutex attribute is set to its default value. The mutex attribute must later be destroyed by [ffrt_mutexattr_destroy](capi-mutex-h.md#ffrt_mutexattr_destroy). |
| [FFRT_C_API int ffrt_mutexattr_settype(ffrt_mutexattr_t* attr, int type)](#ffrt_mutexattr_settype) | Sets the type of a mutex attribute.<br> The type can be `ffrt_mutex_normal` (a regular mutex) or `ffrt_mutex_recursive` (a recursive mutex that allows the same task to acquire the lock multiple times). |
| [FFRT_C_API int ffrt_mutexattr_gettype(ffrt_mutexattr_t* attr, int* type)](#ffrt_mutexattr_gettype) | Gets the type of a mutex attribute.<br> After a successful call, the type value is written to the out parameter `type`. |
| [FFRT_C_API int ffrt_mutexattr_destroy(ffrt_mutexattr_t* attr)](#ffrt_mutexattr_destroy) | Destroys a mutex attribute.<br> The mutex attribute must have been initialized by [ffrt_mutexattr_init](capi-mutex-h.md#ffrt_mutexattr_init). |
| [FFRT_C_API int ffrt_mutex_init(ffrt_mutex_t* mutex, const ffrt_mutexattr_t* attr)](#ffrt_mutex_init) | Initializes a mutex.<br> The mutex must later be destroyed by [ffrt_mutex_destroy](capi-mutex-h.md#ffrt_mutex_destroy). Use `attr` to pass a configured mutex attribute, or a null pointer to use defaults. |
| [FFRT_C_API int ffrt_mutex_lock(ffrt_mutex_t* mutex)](#ffrt_mutex_lock) | Locks a mutex.<br> If the mutex is already held by another thread, blocks the calling thread until the mutex becomes available. On success, the calling thread holds the mutex until a matching call to [ffrt_mutex_unlock](capi-mutex-h.md#ffrt_mutex_unlock). |
| [FFRT_C_API int ffrt_mutex_unlock(ffrt_mutex_t* mutex)](#ffrt_mutex_unlock) | Unlocks a mutex.<br> The mutex must be held by the calling thread, having been previously locked by [ffrt_mutex_lock](capi-mutex-h.md#ffrt_mutex_lock) or [ffrt_mutex_trylock](capi-mutex-h.md#ffrt_mutex_trylock). |
| [FFRT_C_API int ffrt_mutex_trylock(ffrt_mutex_t* mutex)](#ffrt_mutex_trylock) | Attempts to lock a mutex.<br> This is a non-blocking operation: if the mutex is held by another thread, the function returns immediately with an error code. On success, the calling thread holds the mutex until a matching call to [ffrt_mutex_unlock](capi-mutex-h.md#ffrt_mutex_unlock). |
| [FFRT_C_API int ffrt_mutex_destroy(ffrt_mutex_t* mutex)](#ffrt_mutex_destroy) | Destroys a mutex.<br> After a successful call, the resources occupied by the mutex are released and the mutex object can no longer be used. The mutex must have been initialized by [ffrt_mutex_init](capi-mutex-h.md#ffrt_mutex_init) and no thread may hold it on entry. |

## Function description

### ffrt_mutexattr_init()

```c
FFRT_C_API int ffrt_mutexattr_init(ffrt_mutexattr_t* attr)
```

**Description**

Initializes a mutex attribute.<br> After successful initialization, the mutex attribute is set to its default value. The mutex attribute must later be destroyed by [ffrt_mutexattr_destroy](capi-mutex-h.md#ffrt_mutexattr_destroy).

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_mutexattr_t* attr | Indicates a pointer to the mutex attribute. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API int | `ffrt_success` if the mutex attribute is initialized;          `ffrt_error_inval` otherwise. |

### ffrt_mutexattr_settype()

```c
FFRT_C_API int ffrt_mutexattr_settype(ffrt_mutexattr_t* attr, int type)
```

**Description**

Sets the type of a mutex attribute.<br> The type can be `ffrt_mutex_normal` (a regular mutex) or `ffrt_mutex_recursive` (a recursive mutex that allows the same task to acquire the lock multiple times).

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_mutexattr_t* attr | Indicates a pointer to the mutex attribute. |
| int type | Indicates the mutex type, which can be `ffrt_mutex_normal`, `ffrt_mutex_recursive`, or `ffrt_mutex_default` (equivalent to `ffrt_mutex_normal`). |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API int | `ffrt_success` if the mutex attribute type is set successfully;          `ffrt_error_inval` if attr is a null pointer or          the mutex attribute type is not `ffrt_mutex_normal` or `ffrt_mutex_recursive`. |

**Reference**:

ffrt_mutex_type


### ffrt_mutexattr_gettype()

```c
FFRT_C_API int ffrt_mutexattr_gettype(ffrt_mutexattr_t* attr, int* type)
```

**Description**

Gets the type of a mutex attribute.<br> After a successful call, the type value is written to the out parameter `type`.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_mutexattr_t* attr | Indicates a pointer to the mutex attribute. |
| int* type | Indicates a pointer to the mutex type, used to receive the retrieved type value (`ffrt_mutex_normal` or `ffrt_mutex_recursive`). |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API int | `ffrt_success` if the mutex attribute type is retrieved successfully;          `ffrt_error_inval` if attr or type is a null pointer. |

### ffrt_mutexattr_destroy()

```c
FFRT_C_API int ffrt_mutexattr_destroy(ffrt_mutexattr_t* attr)
```

**Description**

Destroys a mutex attribute.<br> The mutex attribute must have been initialized by [ffrt_mutexattr_init](capi-mutex-h.md#ffrt_mutexattr_init).

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_mutexattr_t* attr | Indicates a pointer to the mutex attribute. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API int | `ffrt_success` if the mutex attribute is destroyed;          `ffrt_error_inval` otherwise. |

### ffrt_mutex_init()

```c
FFRT_C_API int ffrt_mutex_init(ffrt_mutex_t* mutex, const ffrt_mutexattr_t* attr)
```

**Description**

Initializes a mutex.<br> The mutex must later be destroyed by [ffrt_mutex_destroy](capi-mutex-h.md#ffrt_mutex_destroy). Use `attr` to pass a configured mutex attribute, or a null pointer to use defaults.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_mutex_t* mutex | Indicates a pointer to the mutex. |
| const ffrt_mutexattr_t* attr | Indicates a pointer to the mutex attribute, or a null pointer to use defaults. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API int | `ffrt_success` if the mutex is initialized;          `ffrt_error_inval` if `mutex` is null, or `attr` is non-null but does not specify          a valid mutex type. |

### ffrt_mutex_lock()

```c
FFRT_C_API int ffrt_mutex_lock(ffrt_mutex_t* mutex)
```

**Description**

Locks a mutex.<br> If the mutex is already held by another thread, blocks the calling thread until the mutex becomes available. On success, the calling thread holds the mutex until a matching call to [ffrt_mutex_unlock](capi-mutex-h.md#ffrt_mutex_unlock).

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_mutex_t* mutex | Indicates a pointer to the mutex. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API int | `ffrt_success` if the mutex is locked;          `ffrt_error_inval` otherwise. |

**Reference**:

[ffrt_mutex_trylock](capi-mutex-h.md#ffrt_mutex_trylock)


### ffrt_mutex_unlock()

```c
FFRT_C_API int ffrt_mutex_unlock(ffrt_mutex_t* mutex)
```

**Description**

Unlocks a mutex.<br> The mutex must be held by the calling thread, having been previously locked by [ffrt_mutex_lock](capi-mutex-h.md#ffrt_mutex_lock) or [ffrt_mutex_trylock](capi-mutex-h.md#ffrt_mutex_trylock).

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_mutex_t* mutex | Indicates a pointer to the mutex. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API int | `ffrt_success` if the mutex is unlocked;          `ffrt_error_inval` otherwise. |

### ffrt_mutex_trylock()

```c
FFRT_C_API int ffrt_mutex_trylock(ffrt_mutex_t* mutex)
```

**Description**

Attempts to lock a mutex.<br> This is a non-blocking operation: if the mutex is held by another thread, the function returns immediately with an error code. On success, the calling thread holds the mutex until a matching call to [ffrt_mutex_unlock](capi-mutex-h.md#ffrt_mutex_unlock).

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_mutex_t* mutex | Indicates a pointer to the mutex. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API int | `ffrt_success` if the mutex is locked;          `ffrt_error_inval` or `ffrt_error_busy` otherwise. |

**Reference**:

[ffrt_mutex_lock](capi-mutex-h.md#ffrt_mutex_lock)


### ffrt_mutex_destroy()

```c
FFRT_C_API int ffrt_mutex_destroy(ffrt_mutex_t* mutex)
```

**Description**

Destroys a mutex.<br> After a successful call, the resources occupied by the mutex are released and the mutex object can no longer be used. The mutex must have been initialized by [ffrt_mutex_init](capi-mutex-h.md#ffrt_mutex_init) and no thread may hold it on entry.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_mutex_t* mutex | Indicates a pointer to the mutex. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API int | `ffrt_success` if the mutex is destroyed;          `ffrt_error_inval` otherwise. |


