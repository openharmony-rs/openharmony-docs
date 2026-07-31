# shared_mutex.h

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1bd5d6cdd22374b2fc7c67ab365167018faf622f translatedAt=2026-07-20T02:02:17.319Z pushedAt=2026-07-20T08:01:07.046Z -->

## Overview

This file declares the C APIs of the read-write lock (`rwlock`).

**File to include**: <ffrt/shared_mutex.h>

**Library**: libffrt.z.so

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 18

**Related module**: [FFRT](capi-ffrt.md)

## Summary

### Function

| Name| Description|
| -- | -- |
| [FFRT_C_API int ffrt_rwlock_init(ffrt_rwlock_t* rwlock, const ffrt_rwlockattr_t* attr)](#ffrt_rwlock_init) | Initializes a `rwlock`. It must be destroyed via [ffrt_rwlock_destroy](capi-shared-mutex-h.md#ffrt_rwlock_destroy) when no longer needed. |
| [FFRT_C_API int ffrt_rwlock_wrlock(ffrt_rwlock_t* rwlock)](#ffrt_rwlock_wrlock) | Acquires a write lock. It blocks the current thread if the lock is unavailable. On success, the calling thread holds the exclusive write lock until the lock is released via [ffrt_rwlock_unlock](capi-shared-mutex-h.md#ffrt_rwlock_unlock). The write lock is exclusive and cannot be held concurrently with any read lock. |
| [FFRT_C_API int ffrt_rwlock_trywrlock(ffrt_rwlock_t* rwlock)](#ffrt_rwlock_trywrlock) | Attempts to acquire a write lock. It does not block the current thread. On success, the calling thread holds the write lock until the lock is released via [ffrt_rwlock_unlock](capi-shared-mutex-h.md#ffrt_rwlock_unlock). |
| [FFRT_C_API int ffrt_rwlock_rdlock(ffrt_rwlock_t* rwlock)](#ffrt_rwlock_rdlock) | Acquires a read lock. It blocks the current thread if the lock is unavailable. On success, the calling thread holds the read lock until the lock is released via [ffrt_rwlock_unlock](capi-shared-mutex-h.md#ffrt_rwlock_unlock). Multiple readers can hold the lock simultaneously, but the lock cannot be held concurrently with a write lock. |
| [FFRT_C_API int ffrt_rwlock_tryrdlock(ffrt_rwlock_t* rwlock)](#ffrt_rwlock_tryrdlock) | Attempts to acquire a read lock. It does not block the current thread. On success, the calling thread holds the read lock until the lock is released via [ffrt_rwlock_unlock](capi-shared-mutex-h.md#ffrt_rwlock_unlock). |
| [FFRT_C_API int ffrt_rwlock_unlock(ffrt_rwlock_t* rwlock)](#ffrt_rwlock_unlock) | Unlocks a `rwlock`. The calling thread must hold the read-write lock, which must have been previously acquired via [ffrt_rwlock_rdlock](capi-shared-mutex-h.md#ffrt_rwlock_rdlock), [ffrt_rwlock_tryrdlock](capi-shared-mutex-h.md#ffrt_rwlock_tryrdlock), [ffrt_rwlock_wrlock](capi-shared-mutex-h.md#ffrt_rwlock_wrlock), or [ffrt_rwlock_trywrlock](capi-shared-mutex-h.md#ffrt_rwlock_trywrlock). |
| [FFRT_C_API int ffrt_rwlock_destroy(ffrt_rwlock_t* rwlock)](#ffrt_rwlock_destroy) | Destroys a `rwlock`. The read-write lock must have been initialized via [ffrt_rwlock_init](capi-shared-mutex-h.md#ffrt_rwlock_init) and must not be held by any thread, either as a read lock or a write lock, when this API is called. |

## Function Description

### ffrt_rwlock_init()

```c
FFRT_C_API int ffrt_rwlock_init(ffrt_rwlock_t* rwlock, const ffrt_rwlockattr_t* attr)
```

**Description**

Initializes a `rwlock`. It must be destroyed via [ffrt_rwlock_destroy](capi-shared-mutex-h.md#ffrt_rwlock_destroy) when no longer needed.

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_rwlock_t](capi-ffrt-ffrt-rwlock-t.md)* rwlock | Pointer to the `rwlock`. |
| [const ffrt_rwlockattr_t](capi-ffrt-ffrt-rwlockattr-t.md)* attr | Pointer to the `rwlock` attribute. Currently, only the default mode is supported, and this parameter must be set to a null pointer. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | If the `rwlock` is initialized successfully and `attr` is a null pointer, `ffrt_success` is returned.<br>         Otherwise, `ffrt_error_inval` is returned. |

### ffrt_rwlock_wrlock()

```c
FFRT_C_API int ffrt_rwlock_wrlock(ffrt_rwlock_t* rwlock)
```

**Description**

Obtains a write lock. It blocks the current thread if the lock is unavailable. Upon success, the calling thread holds the exclusive write lock until the lock is released via [ffrt_rwlock_unlock](capi-shared-mutex-h.md#ffrt_rwlock_unlock). The write lock is exclusive and cannot be held concurrently with any read lock.

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_rwlock_t](capi-ffrt-ffrt-rwlock-t.md)* rwlock | Pointer to the `rwlock`. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | If the `rwlock` is acquired successfully, `ffrt_success` is returned.<br>         If `rwlock`is a null pointer, `ffrt_error_inval` is returned.  |

**Reference**

[ffrt_rwlock_rdlock](capi-shared-mutex-h.md#ffrt_rwlock_rdlock)

[ffrt_rwlock_trywrlock](capi-shared-mutex-h.md#ffrt_rwlock_trywrlock)

### ffrt_rwlock_trywrlock()

```c
FFRT_C_API int ffrt_rwlock_trywrlock(ffrt_rwlock_t* rwlock)
```

**Description**

Attempts to obtain a write lock. It does not block the current thread. Upon success, the calling thread holds the exclusive write lock until the lock is released via [ffrt_rwlock_unlock](capi-shared-mutex-h.md#ffrt_rwlock_unlock).

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_rwlock_t](capi-ffrt-ffrt-rwlock-t.md)* rwlock | Pointer to the `rwlock`. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | If the `rwlock` is acquired successfully, `ffrt_success` is returned.<br>         Otherwise, `ffrt_error_inval` or `ffrt_error_busy` is returned. |

**Reference**

[ffrt_rwlock_wrlock](capi-shared-mutex-h.md#ffrt_rwlock_wrlock)

### ffrt_rwlock_rdlock()

```c
FFRT_C_API int ffrt_rwlock_rdlock(ffrt_rwlock_t* rwlock)
```

**Description**

Obtains a read lock. It blocks the current thread if the lock is unavailable. Upon success, the calling thread holds the read lock until the lock is released via [ffrt_rwlock_unlock](capi-shared-mutex-h.md#ffrt_rwlock_unlock). Multiple readers can hold the lock concurrently, but the lock cannot be held simultaneously with a write lock.

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_rwlock_t](capi-ffrt-ffrt-rwlock-t.md)* rwlock | Pointer to the `rwlock`. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | If the `rwlock` is acquired successfully, `ffrt_success` is returned.<br>         If `rwlock`is a null pointer, `ffrt_error_inval` is returned. |

**Reference**

[ffrt_rwlock_wrlock](capi-shared-mutex-h.md#ffrt_rwlock_wrlock)

[ffrt_rwlock_tryrdlock](capi-shared-mutex-h.md#ffrt_rwlock_tryrdlock)

### ffrt_rwlock_tryrdlock()

```c
FFRT_C_API int ffrt_rwlock_tryrdlock(ffrt_rwlock_t* rwlock)
```

**Description**

Attempts to obtain a read lock. It does not block the current thread. Upon success, the calling thread holds the read lock until the lock is released via [ffrt_rwlock_unlock](capi-shared-mutex-h.md#ffrt_rwlock_unlock).

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_rwlock_t](capi-ffrt-ffrt-rwlock-t.md)* rwlock | Pointer to the `rwlock`. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | If the `rwlock` is acquired successfully, `ffrt_success` is returned.<br>         Otherwise, `ffrt_error_inval` or `ffrt_error_busy` is returned. |

**Reference**

[ffrt_rwlock_rdlock](capi-shared-mutex-h.md#ffrt_rwlock_rdlock)

### ffrt_rwlock_unlock()

```c
FFRT_C_API int ffrt_rwlock_unlock(ffrt_rwlock_t* rwlock)
```

**Description**

Unlocks a `rwlock`. The calling thread must already hold the rwlock, and the lock must have been previously obtained by [ffrt_rwlock_rdlock](capi-shared-mutex-h.md#ffrt_rwlock_rdlock), [ffrt_rwlock_tryrdlock](capi-shared-mutex-h.md#ffrt_rwlock_tryrdlock), [ffrt_rwlock_wrlock](capi-shared-mutex-h.md#ffrt_rwlock_wrlock), or [ffrt_rwlock_trywrlock](capi-shared-mutex-h.md#ffrt_rwlock_trywrlock).

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_rwlock_t](capi-ffrt-ffrt-rwlock-t.md)* rwlock | Pointer to the `rwlock`. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | If the `rwlock` is successfully unlocked, `ffrt_success` is returned.<br>         Otherwise, `ffrt_error_inval` is returned. |

### ffrt_rwlock_destroy()

```c
FFRT_C_API int ffrt_rwlock_destroy(ffrt_rwlock_t* rwlock)
```

**Description**

Destroys a `rwlock`. The `rwlock` must have been initialized by [ffrt_rwlock_init](capi-shared-mutex-h.md#ffrt_rwlock_init) and must not be held by any thread, either as a read lock or a write lock, when this API is called.

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_rwlock_t](capi-ffrt-ffrt-rwlock-t.md)* rwlock | Pointer to the `rwlock`. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | If the `rwlock` is successfully destroyed, `ffrt_success` is returned.<br>         Otherwise, `ffrt_error_inval` is returned. |