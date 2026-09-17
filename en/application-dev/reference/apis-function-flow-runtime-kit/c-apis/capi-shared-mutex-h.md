# shared_mutex.h

## Overview

Declares the shared mutex interfaces in C.

**Library**: libffrt.z.so

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [FFRT_C_API int ffrt_rwlock_init(ffrt_rwlock_t* rwlock, const ffrt_rwlockattr_t* attr)](#ffrt_rwlock_init) | Initializes a rwlock.<br> The rwlock must later be destroyed by [ffrt_rwlock_destroy](capi-shared-mutex-h.md#ffrt_rwlock_destroy). |
| [FFRT_C_API int ffrt_rwlock_wrlock(ffrt_rwlock_t* rwlock)](#ffrt_rwlock_wrlock) | Locks a write lock.<br> Blocks the calling thread if the lock is unavailable. On success, the calling thread holds the exclusive write lock until a matching call to [ffrt_rwlock_unlock](capi-shared-mutex-h.md#ffrt_rwlock_unlock). The write lock is exclusive: no read locks can be held concurrently. |
| [FFRT_C_API int ffrt_rwlock_trywrlock(ffrt_rwlock_t* rwlock)](#ffrt_rwlock_trywrlock) | Attempts to lock a write lock.<br> Does not block the calling thread. On success, the calling thread holds the exclusive write lock until a matching call to [ffrt_rwlock_unlock](capi-shared-mutex-h.md#ffrt_rwlock_unlock). |
| [FFRT_C_API int ffrt_rwlock_rdlock(ffrt_rwlock_t* rwlock)](#ffrt_rwlock_rdlock) | Locks a read lock.<br> Blocks the calling thread if the lock is unavailable. On success, the calling thread holds a read lock until a matching call to [ffrt_rwlock_unlock](capi-shared-mutex-h.md#ffrt_rwlock_unlock). Multiple readers may hold the lock concurrently, but no writer may hold it. |
| [FFRT_C_API int ffrt_rwlock_tryrdlock(ffrt_rwlock_t* rwlock)](#ffrt_rwlock_tryrdlock) | Attempts to lock a read lock.<br> Does not block the calling thread. On success, the calling thread holds a read lock until a matching call to [ffrt_rwlock_unlock](capi-shared-mutex-h.md#ffrt_rwlock_unlock). |
| [FFRT_C_API int ffrt_rwlock_unlock(ffrt_rwlock_t* rwlock)](#ffrt_rwlock_unlock) | Unlocks a rwlock.<br> The rwlock must be held by the calling thread, having been previously locked by [ffrt_rwlock_rdlock](capi-shared-mutex-h.md#ffrt_rwlock_rdlock), [ffrt_rwlock_tryrdlock](capi-shared-mutex-h.md#ffrt_rwlock_tryrdlock), [ffrt_rwlock_wrlock](capi-shared-mutex-h.md#ffrt_rwlock_wrlock), or [ffrt_rwlock_trywrlock](capi-shared-mutex-h.md#ffrt_rwlock_trywrlock). |
| [FFRT_C_API int ffrt_rwlock_destroy(ffrt_rwlock_t* rwlock)](#ffrt_rwlock_destroy) | Destroys a rwlock.<br> The rwlock must have been initialized by [ffrt_rwlock_init](capi-shared-mutex-h.md#ffrt_rwlock_init) and no thread may hold a read or write lock on entry. |

## Function description

### ffrt_rwlock_init()

```c
FFRT_C_API int ffrt_rwlock_init(ffrt_rwlock_t* rwlock, const ffrt_rwlockattr_t* attr)
```

**Description**

Initializes a rwlock.<br> The rwlock must later be destroyed by [ffrt_rwlock_destroy](capi-shared-mutex-h.md#ffrt_rwlock_destroy).

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_rwlock_t* rwlock | Indicates a pointer to the rwlock. |
| const ffrt_rwlockattr_t* attr | Indicates a pointer to the rwlock attribute. Currently, only the default mode is supported, set to null pointer. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API int | `ffrt_success` if the rwlock is initialized and the attr is nullptr;          `ffrt_error_inval` otherwise. |

### ffrt_rwlock_wrlock()

```c
FFRT_C_API int ffrt_rwlock_wrlock(ffrt_rwlock_t* rwlock)
```

**Description**

Locks a write lock.<br> Blocks the calling thread if the lock is unavailable. On success, the calling thread holds the exclusive write lock until a matching call to [ffrt_rwlock_unlock](capi-shared-mutex-h.md#ffrt_rwlock_unlock). The write lock is exclusive: no read locks can be held concurrently.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_rwlock_t* rwlock | Indicates a pointer to the rwlock. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API int | `ffrt_success` if the rwlock is locked;          `ffrt_error_inval` if `rwlock` is a null pointer. |

**Reference**:

[ffrt_rwlock_rdlock](capi-shared-mutex-h.md#ffrt_rwlock_rdlock)
[ffrt_rwlock_trywrlock](capi-shared-mutex-h.md#ffrt_rwlock_trywrlock)


### ffrt_rwlock_trywrlock()

```c
FFRT_C_API int ffrt_rwlock_trywrlock(ffrt_rwlock_t* rwlock)
```

**Description**

Attempts to lock a write lock.<br> Does not block the calling thread. On success, the calling thread holds the exclusive write lock until a matching call to [ffrt_rwlock_unlock](capi-shared-mutex-h.md#ffrt_rwlock_unlock).

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_rwlock_t* rwlock | Indicates a pointer to the rwlock. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API int | `ffrt_success` if the rwlock is locked;          `ffrt_error_inval` or `ffrt_error_busy` otherwise. |

**Reference**:

[ffrt_rwlock_wrlock](capi-shared-mutex-h.md#ffrt_rwlock_wrlock)


### ffrt_rwlock_rdlock()

```c
FFRT_C_API int ffrt_rwlock_rdlock(ffrt_rwlock_t* rwlock)
```

**Description**

Locks a read lock.<br> Blocks the calling thread if the lock is unavailable. On success, the calling thread holds a read lock until a matching call to [ffrt_rwlock_unlock](capi-shared-mutex-h.md#ffrt_rwlock_unlock). Multiple readers may hold the lock concurrently, but no writer may hold it.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_rwlock_t* rwlock | Indicates a pointer to the rwlock. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API int | `ffrt_success` if the rwlock is locked;          `ffrt_error_inval` if `rwlock` is a null pointer. |

**Reference**:

[ffrt_rwlock_wrlock](capi-shared-mutex-h.md#ffrt_rwlock_wrlock)
[ffrt_rwlock_tryrdlock](capi-shared-mutex-h.md#ffrt_rwlock_tryrdlock)


### ffrt_rwlock_tryrdlock()

```c
FFRT_C_API int ffrt_rwlock_tryrdlock(ffrt_rwlock_t* rwlock)
```

**Description**

Attempts to lock a read lock.<br> Does not block the calling thread. On success, the calling thread holds a read lock until a matching call to [ffrt_rwlock_unlock](capi-shared-mutex-h.md#ffrt_rwlock_unlock).

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_rwlock_t* rwlock | Indicates a pointer to the rwlock. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API int | `ffrt_success` if the rwlock is locked;          `ffrt_error_inval` or `ffrt_error_busy` otherwise. |

**Reference**:

[ffrt_rwlock_rdlock](capi-shared-mutex-h.md#ffrt_rwlock_rdlock)


### ffrt_rwlock_unlock()

```c
FFRT_C_API int ffrt_rwlock_unlock(ffrt_rwlock_t* rwlock)
```

**Description**

Unlocks a rwlock.<br> The rwlock must be held by the calling thread, having been previously locked by [ffrt_rwlock_rdlock](capi-shared-mutex-h.md#ffrt_rwlock_rdlock), [ffrt_rwlock_tryrdlock](capi-shared-mutex-h.md#ffrt_rwlock_tryrdlock), [ffrt_rwlock_wrlock](capi-shared-mutex-h.md#ffrt_rwlock_wrlock), or [ffrt_rwlock_trywrlock](capi-shared-mutex-h.md#ffrt_rwlock_trywrlock).

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_rwlock_t* rwlock | Indicates a pointer to the rwlock. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API int | `ffrt_success` if the rwlock is unlocked;          `ffrt_error_inval` otherwise. |

### ffrt_rwlock_destroy()

```c
FFRT_C_API int ffrt_rwlock_destroy(ffrt_rwlock_t* rwlock)
```

**Description**

Destroys a rwlock.<br> The rwlock must have been initialized by [ffrt_rwlock_init](capi-shared-mutex-h.md#ffrt_rwlock_init) and no thread may hold a read or write lock on entry.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_rwlock_t* rwlock | Indicates a pointer to the rwlock. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API int | `ffrt_success` if the rwlock is destroyed;          `ffrt_error_inval` otherwise. |


