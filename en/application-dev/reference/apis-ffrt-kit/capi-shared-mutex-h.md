# shared_mutex.h

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1c82fe64143ca179b80fafe272ca5a84323e9159 translatedAt=2026-11-10T03:21:52.791Z pushedAt=2026-11-10T04:57:19.518Z nl=1 -->

## Overview

Declares the C APIs of the read-write lock (rwlock).

**File to include**: <ffrt/shared_mutex.h>

**Library**: libffrt.z.so

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 18

**Related module**: [FFRT](capi-ffrt.md)

## Summary

### Function

| Name| Description|
| -- | -- |
| [FFRT_C_API int ffrt_rwlock_init(ffrt_rwlock_t* rwlock, const ffrt_rwlockattr_t* attr)](#ffrt_rwlock_init) | Initializes an rwlock. When the rwlock is no longer used, it must be destroyed by [ffrt_rwlock_destroy](capi-shared-mutex-h.md#ffrt_rwlock_destroy). |
| [FFRT_C_API int ffrt_rwlock_wrlock(ffrt_rwlock_t* rwlock)](#ffrt_rwlock_wrlock) | Acquires a write lock. Blocks the current thread when the lock is unavailable. On success, the calling thread holds an exclusive write lock until it is released by [ffrt_rwlock_unlock](capi-shared-mutex-h.md#ffrt_rwlock_unlock). A write lock is exclusive and cannot be held simultaneously with any read lock. |
| [FFRT_C_API int ffrt_rwlock_trywrlock(ffrt_rwlock_t* rwlock)](#ffrt_rwlock_trywrlock) | Attempts to acquire a write lock. Does not block the current thread. On success, the calling thread holds an exclusive write lock until it is released by [ffrt_rwlock_unlock](capi-shared-mutex-h.md#ffrt_rwlock_unlock). |
| [FFRT_C_API int ffrt_rwlock_rdlock(ffrt_rwlock_t* rwlock)](#ffrt_rwlock_rdlock) | Acquires a read lock. Blocks the current thread when the lock is unavailable. On success, the calling thread holds a read lock until it is released by [ffrt_rwlock_unlock](capi-shared-mutex-h.md#ffrt_rwlock_unlock). Multiple readers can hold the lock simultaneously, but it cannot be held simultaneously with a write lock. |
| [FFRT_C_API int ffrt_rwlock_tryrdlock(ffrt_rwlock_t* rwlock)](#ffrt_rwlock_tryrdlock) | Attempts to acquire a read lock. Does not block the current thread. On success, the calling thread holds a read lock until it is released by [ffrt_rwlock_unlock](capi-shared-mutex-h.md#ffrt_rwlock_unlock). |
| [FFRT_C_API int ffrt_rwlock_unlock(ffrt_rwlock_t* rwlock)](#ffrt_rwlock_unlock) | Unlocks an rwlock. The calling thread must already hold the rwlock, and the lock must have been acquired by [ffrt_rwlock_rdlock](capi-shared-mutex-h.md#ffrt_rwlock_rdlock), [ffrt_rwlock_tryrdlock](capi-shared-mutex-h.md#ffrt_rwlock_tryrdlock), [ffrt_rwlock_wrlock](capi-shared-mutex-h.md#ffrt_rwlock_wrlock), or [ffrt_rwlock_trywrlock](capi-shared-mutex-h.md#ffrt_rwlock_trywrlock). |
| [FFRT_C_API int ffrt_rwlock_destroy(ffrt_rwlock_t* rwlock)](#ffrt_rwlock_destroy) | Destroys an rwlock. The rwlock must have been initialized by [ffrt_rwlock_init](capi-shared-mutex-h.md#ffrt_rwlock_init), and it must not be held by any thread as a read lock or write lock when this API is called. |

## Function Description

### ffrt_rwlock_init()

```c
FFRT_C_API int ffrt_rwlock_init(ffrt_rwlock_t* rwlock, const ffrt_rwlockattr_t* attr)
```

**Description**

Initializes an rwlock. When the rwlock is no longer used, it must be destroyed by calling [ffrt_rwlock_destroy](capi-shared-mutex-h.md#ffrt_rwlock_destroy).

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_rwlock_t](capi-ffrt-ffrt-rwlock-t.md)* rwlock | Pointer to the rwlock. |
| [const ffrt_rwlockattr_t](capi-ffrt-ffrt-rwlockattr-t.md)* attr | Pointer to the rwlock attribute. Currently only the default mode is supported, and it must be set to a null pointer. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | Returns `ffrt_success` if the rwlock is initialized successfully and attr is a null pointer;<br>         returns `ffrt_error_inval` otherwise. |

### ffrt_rwlock_wrlock()

```c
FFRT_C_API int ffrt_rwlock_wrlock(ffrt_rwlock_t* rwlock)
```

**Description**

Acquires a write lock. Blocks the current thread when the lock is unavailable. On success, the calling thread holds the exclusive write lock until it is released by calling [ffrt_rwlock_unlock](capi-shared-mutex-h.md#ffrt_rwlock_unlock). The write lock is exclusive and cannot be held simultaneously with any read lock.

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_rwlock_t](capi-ffrt-ffrt-rwlock-t.md)* rwlock | Pointer to the rwlock. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | Returns `ffrt_success` if the rwlock is locked successfully;<br>         Returns `ffrt_error_inval` if `rwlock` is a null pointer. |

**Reference**

[ffrt_rwlock_rdlock](capi-shared-mutex-h.md#ffrt_rwlock_rdlock)

[ffrt_rwlock_trywrlock](capi-shared-mutex-h.md#ffrt_rwlock_trywrlock)


### ffrt_rwlock_trywrlock()

```c
FFRT_C_API int ffrt_rwlock_trywrlock(ffrt_rwlock_t* rwlock)
```

**Description**

Attempts to acquire a write lock. Does not block the current thread. On success, the calling thread holds the exclusive write lock until it is released by calling [ffrt_rwlock_unlock](capi-shared-mutex-h.md#ffrt_rwlock_unlock).

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_rwlock_t](capi-ffrt-ffrt-rwlock-t.md)* rwlock | Pointer to the rwlock. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | Returns `ffrt_success` if the rwlock is locked successfully;<br>         otherwise, returns `ffrt_error_inval` or `ffrt_error_busy`. |

**Reference**

[ffrt_rwlock_wrlock](capi-shared-mutex-h.md#ffrt_rwlock_wrlock)


### ffrt_rwlock_rdlock()

```c
FFRT_C_API int ffrt_rwlock_rdlock(ffrt_rwlock_t* rwlock)
```

**Description**

Acquires a read lock. Blocks the current thread when the lock is unavailable. On success, the calling thread holds the read lock until it is released by calling [ffrt_rwlock_unlock](capi-shared-mutex-h.md#ffrt_rwlock_unlock). Multiple readers can hold the lock simultaneously, but it cannot be held simultaneously with a write lock.

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_rwlock_t](capi-ffrt-ffrt-rwlock-t.md)* rwlock | Pointer to the rwlock. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | Returns `ffrt_success` if the rwlock is locked successfully;<br>         Returns `ffrt_error_inval` if `rwlock` is a null pointer. |

**Reference**

[ffrt_rwlock_wrlock](capi-shared-mutex-h.md#ffrt_rwlock_wrlock)

[ffrt_rwlock_tryrdlock](capi-shared-mutex-h.md#ffrt_rwlock_tryrdlock)


### ffrt_rwlock_tryrdlock()

```c
FFRT_C_API int ffrt_rwlock_tryrdlock(ffrt_rwlock_t* rwlock)
```

**Description**

Attempts to acquire a read lock. This API does not block the current thread. On success, the calling thread holds the read lock until it is released by [ffrt_rwlock_unlock](capi-shared-mutex-h.md#ffrt_rwlock_unlock).

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_rwlock_t](capi-ffrt-ffrt-rwlock-t.md)* rwlock | Pointer to the rwlock. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | Returns `ffrt_success` if the rwlock is locked successfully;<br>         otherwise returns `ffrt_error_inval` or `ffrt_error_busy`. |

**Reference**

[ffrt_rwlock_rdlock](capi-shared-mutex-h.md#ffrt_rwlock_rdlock)


### ffrt_rwlock_unlock()

```c
FFRT_C_API int ffrt_rwlock_unlock(ffrt_rwlock_t* rwlock)
```

**Description**

Unlocks the rwlock. The calling thread must already hold the rwlock, and the lock must have been acquired by [ffrt_rwlock_rdlock](capi-shared-mutex-h.md#ffrt_rwlock_rdlock), [ffrt_rwlock_tryrdlock](capi-shared-mutex-h.md#ffrt_rwlock_tryrdlock), [ffrt_rwlock_wrlock](capi-shared-mutex-h.md#ffrt_rwlock_wrlock), or [ffrt_rwlock_trywrlock](capi-shared-mutex-h.md#ffrt_rwlock_trywrlock).

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_rwlock_t](capi-ffrt-ffrt-rwlock-t.md)* rwlock | Pointer to the rwlock. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | Returns `ffrt_success` if the rwlock is unlocked successfully;<br>         otherwise returns `ffrt_error_inval`. |

### ffrt_rwlock_destroy()

```c
FFRT_C_API int ffrt_rwlock_destroy(ffrt_rwlock_t* rwlock)
```

**Description**

Destroys the rwlock. The rwlock must have been initialized by [ffrt_rwlock_init](capi-shared-mutex-h.md#ffrt_rwlock_init), and it must not be held by any thread as a read lock or write lock when this API is called.

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_rwlock_t](capi-ffrt-ffrt-rwlock-t.md)* rwlock | Pointer to the rwlock. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | Returns `ffrt_success` if the rwlock is destroyed successfully;<br>         otherwise returns `ffrt_error_inval`. |


