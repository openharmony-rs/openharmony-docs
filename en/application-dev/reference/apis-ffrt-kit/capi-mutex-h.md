# mutex.h

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1c82fe64143ca179b80fafe272ca5a84323e9159 translatedAt=2026-11-13T03:06:04.317Z pushedAt=2026-11-13T08:45:55.672Z nl=1 -->

## Overview

Declares the C APIs of mutex, which are used to provide mutually exclusive access between concurrent tasks and protect shared resources from race conditions.

**File to include**: <ffrt/mutex.h>

**Library**: libffrt.z.so

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

## Summary

### Function

| Name| Description|
| -- | -- |
| [FFRT_C_API int ffrt_mutexattr_init(ffrt_mutexattr_t* attr)](#ffrt_mutexattr_init) | Initializes the mutex attribute. After successful initialization, the mutex attribute is set to the default value. When the mutex attribute is no longer used, it must be destroyed by [ffrt_mutexattr_destroy](capi-mutex-h.md#ffrt_mutexattr_destroy). |
| [FFRT_C_API int ffrt_mutexattr_settype(ffrt_mutexattr_t* attr, int type)](#ffrt_mutexattr_settype) | Sets the type of the mutex attribute. The type can be **ffrt_mutex_normal** (normal mutex) or **ffrt_mutex_recursive** (recursive mutex, which allows the same task to acquire the lock multiple times). |
| [FFRT_C_API int ffrt_mutexattr_gettype(ffrt_mutexattr_t* attr, int* type)](#ffrt_mutexattr_gettype) | Obtains the type of the mutex attribute. After the call succeeds, the type value is returned through the output parameter **type**. |
| [FFRT_C_API int ffrt_mutexattr_destroy(ffrt_mutexattr_t* attr)](#ffrt_mutexattr_destroy) | Destroys the mutex attribute. The mutex attribute must have been initialized by [ffrt_mutexattr_init](capi-mutex-h.md#ffrt_mutexattr_init). |
| [FFRT_C_API int ffrt_mutex_init(ffrt_mutex_t* mutex, const ffrt_mutexattr_t* attr)](#ffrt_mutex_init) | Initializes the mutex. When the mutex is no longer used, it must be destroyed by [ffrt_mutex_destroy](capi-mutex-h.md#ffrt_mutex_destroy). Pass the configured mutex attribute through **attr**, or pass a null pointer to use the default value. |
| [FFRT_C_API int ffrt_mutex_lock(ffrt_mutex_t* mutex)](#ffrt_mutex_lock) | Locks the mutex. If the mutex is already held by another thread, the current thread is blocked until the mutex becomes available. On success, the calling thread holds the mutex until it is released by [ffrt_mutex_unlock](capi-mutex-h.md#ffrt_mutex_unlock). |
| [FFRT_C_API int ffrt_mutex_unlock(ffrt_mutex_t* mutex)](#ffrt_mutex_unlock) | Unlocks the mutex. The calling thread must hold the mutex, and the lock must have been acquired by [ffrt_mutex_lock](capi-mutex-h.md#ffrt_mutex_lock) or [ffrt_mutex_trylock](capi-mutex-h.md#ffrt_mutex_trylock). |
| [FFRT_C_API int ffrt_mutex_trylock(ffrt_mutex_t* mutex)](#ffrt_mutex_trylock) | Tries to lock the mutex. This API is a non-blocking operation: if the mutex is already held by another thread, an error code is returned immediately. On success, the calling thread holds the mutex until it is released by [ffrt_mutex_unlock](capi-mutex-h.md#ffrt_mutex_unlock). |
| [FFRT_C_API int ffrt_mutex_destroy(ffrt_mutex_t* mutex)](#ffrt_mutex_destroy) | Destroys the mutex. After the call succeeds, the resources occupied by the mutex are released, and the mutex object can no longer be used. The mutex must have been initialized by [ffrt_mutex_init](capi-mutex-h.md#ffrt_mutex_init), and it must not be held by any thread when this API is called. |

## Function Description

### ffrt_mutexattr_init()

```c
FFRT_C_API int ffrt_mutexattr_init(ffrt_mutexattr_t* attr)
```

**Description**

Initializes the mutex attribute. After successful initialization, the mutex attribute is set to the default value. When the mutex attribute is no longer used, it must be destroyed by [ffrt_mutexattr_destroy](capi-mutex-h.md#ffrt_mutexattr_destroy).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_mutexattr_t](capi-ffrt-ffrt-mutexattr-t.md)* attr | Pointer to the mutex attribute. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | Returns **ffrt_success** if the mutex attribute is initialized successfully.<br>         Returns **ffrt_error_inval** otherwise. |

### ffrt_mutexattr_settype()

```c
FFRT_C_API int ffrt_mutexattr_settype(ffrt_mutexattr_t* attr, int type)
```

**Description**

Sets the type of the mutex attribute. The type can be **ffrt_mutex_normal** (normal mutex) or **ffrt_mutex_recursive** (recursive mutex, which allows the same task to acquire the lock multiple times).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_mutexattr_t](capi-ffrt-ffrt-mutexattr-t.md)* attr | Pointer to the mutex attribute. |
| int type | Mutex type, which can be **ffrt_mutex_normal**, **ffrt_mutex_recursive**, or **ffrt_mutex_default** (equivalent to **ffrt_mutex_normal**). |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | Returns **ffrt_success** if the mutex attribute type is set successfully.<br>         Returns **ffrt_error_inval** if attr is a null pointer, or the mutex attribute type is neither **ffrt_mutex_normal** nor **ffrt_mutex_recursive**. |

**Reference**

[ffrt_mutex_type](capi-type-def-h.md#ffrt_mutex_type)


### ffrt_mutexattr_gettype()

```c
FFRT_C_API int ffrt_mutexattr_gettype(ffrt_mutexattr_t* attr, int* type)
```

**Description**

Obtains the type of the mutex attribute. After the call succeeds, the type value is returned through the output parameter **type**.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_mutexattr_t](capi-ffrt-ffrt-mutexattr-t.md)* attr | Pointer to the mutex attribute. |
| int* type | Pointer to the mutex type, which is used to receive the obtained type value (**ffrt_mutex_normal** or **ffrt_mutex_recursive**). |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | Returns **ffrt_success** when the mutex attribute type is obtained successfully.<br>         Returns **ffrt_error_inval** if **attr** or **type** is a null pointer. |

### ffrt_mutexattr_destroy()

```c
FFRT_C_API int ffrt_mutexattr_destroy(ffrt_mutexattr_t* attr)
```

**Description**

Destroys the mutex attribute. The mutex attribute must have been initialized by [ffrt_mutexattr_init](capi-mutex-h.md#ffrt_mutexattr_init).

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_mutexattr_t](capi-ffrt-ffrt-mutexattr-t.md)* attr | Pointer to the mutex attribute. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | Returns **ffrt_success** if the mutex attribute is destroyed successfully.<br>         Returns **ffrt_error_inval** otherwise. |

### ffrt_mutex_init()

```c
FFRT_C_API int ffrt_mutex_init(ffrt_mutex_t* mutex, const ffrt_mutexattr_t* attr)
```

**Description**

Initializes the mutex. When the mutex is no longer used, it must be destroyed by [ffrt_mutex_destroy](capi-mutex-h.md#ffrt_mutex_destroy). Pass the configured mutex attribute through **attr**, or pass a null pointer to use the default value.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_mutex_t](capi-ffrt-ffrt-mutex-t.md)* mutex | Pointer to the mutex. |
| [const ffrt_mutexattr_t](capi-ffrt-ffrt-mutexattr-t.md)* attr | Pointer to the mutex attribute, or pass a null pointer to use the default value. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | Returns **ffrt_success** if the mutex is initialized successfully.<br>         Returns **ffrt_error_inval** is if **mutex** is null, or when **attr** is not null but does not specify a valid mutex type. |

### ffrt_mutex_lock()

```c
FFRT_C_API int ffrt_mutex_lock(ffrt_mutex_t* mutex)
```

**Description**

Locks the mutex. If the mutex is already held by another thread, the current thread is blocked until the mutex becomes available. On success, the calling thread holds the mutex until it is released by [ffrt_mutex_unlock](capi-mutex-h.md#ffrt_mutex_unlock).

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_mutex_t](capi-ffrt-ffrt-mutex-t.md)* mutex | Pointer to the mutex. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | Returns **ffrt_success** if the mutex is locked successfully.<br>         Returns **ffrt_error_inval** otherwise. |

**Reference**

[ffrt_mutex_trylock](capi-mutex-h.md#ffrt_mutex_trylock)


### ffrt_mutex_unlock()

```c
FFRT_C_API int ffrt_mutex_unlock(ffrt_mutex_t* mutex)
```

**Description**

Unlocks the mutex. The calling thread must hold the mutex, and the lock must have been acquired by [ffrt_mutex_lock](capi-mutex-h.md#ffrt_mutex_lock) or [ffrt_mutex_trylock](capi-mutex-h.md#ffrt_mutex_trylock).

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_mutex_t](capi-ffrt-ffrt-mutex-t.md)* mutex | Pointer to the mutex. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | Returns **ffrt_success** if the mutex is unlocked successfully.<br>         Returns **ffrt_error_inval** otherwise. |

### ffrt_mutex_trylock()

```c
FFRT_C_API int ffrt_mutex_trylock(ffrt_mutex_t* mutex)
```

**Description**

Tries to lock the mutex. This API is a non-blocking operation: if the mutex is already held by another thread, an error code is returned immediately. On success, the calling thread holds the mutex until it is released by [ffrt_mutex_unlock](capi-mutex-h.md#ffrt_mutex_unlock).

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_mutex_t](capi-ffrt-ffrt-mutex-t.md)* mutex | Pointer to the mutex. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | Returns **ffrt_success** when the mutex is locked successfully.<br>         otherwise returns **ffrt_error_inval** or `ffrt_error_busy`. |

**Reference**

[ffrt_mutex_lock](capi-mutex-h.md#ffrt_mutex_lock)


### ffrt_mutex_destroy()

```c
FFRT_C_API int ffrt_mutex_destroy(ffrt_mutex_t* mutex)
```

**Description**

Destroys the mutex. After the call succeeds, the resources occupied by the mutex are released, and the mutex object can no longer be used. The mutex must have been initialized by [ffrt_mutex_init](capi-mutex-h.md#ffrt_mutex_init), and it must not be held by any thread when this API is called.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_mutex_t](capi-ffrt-ffrt-mutex-t.md)* mutex | Pointer to the mutex. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | Returns **ffrt_success** if the mutex is destroyed successfully.<br>         Returns **ffrt_error_inval** otherwise. |


