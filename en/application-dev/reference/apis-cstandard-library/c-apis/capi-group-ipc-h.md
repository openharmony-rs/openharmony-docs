# group_ipc.h

## Overview

Declares interfaces for shared memory and named semaphores in group-specific directories.

**Include**: <sys/group_ipc.h>

**Library**: libc.so

**Since**: 26.2.0

**Related module**: [MuslGroupIPC](capi-muslgroupipc.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [sem_t *group_sem_open(const char *name, int flags, gid_t gid, ...)](#group_sem_open) | Creates or opens a named semaphore in the directory selected by gid.<br> When O_CREAT is specified, the variadic arguments must be a mode_t mode followed by an unsigned int value. These creation attributes are ignored when opening an existing semaphore. This function is a POSIX handle-returning function, not a status-code function: the return value is a semaphore handle, and SEM_FAILED is the sentinel failure value. It uses the common errno error model; the return type matches the POSIX sem_open declaration. |
| [int group_sem_unlink(const char *name, gid_t gid)](#group_sem_unlink) | Removes the name of a group-scoped semaphore.<br> This function is a POSIX status-style function and uses the common errno error model: the return type matches the POSIX sem_unlink declaration, success is 0, and failure is -1 with errno set. No dedicated module error-code enum or module-specific error codes are defined. |
| [int group_shm_open(const char *name, int flag, mode_t mode, gid_t gid)](#group_shm_open) | Creates or opens a shared memory object in the directory selected by gid.<br> This function is a POSIX handle-returning function, not a status-code function: the nonnegative return value is a file descriptor and -1 is the sentinel failure value. It uses the common errno error model; the return type matches the POSIX shm_open declaration. |
| [int group_shm_unlink(const char *name, gid_t gid)](#group_shm_unlink) | Removes the name of a group-scoped shared memory object.<br> This function is a POSIX status-style function and uses the common errno error model: the return type matches the POSIX shm_unlink declaration, success is 0, and failure is -1 with errno set. No dedicated module error-code enum or module-specific error codes are defined. |

## Function description

### group_sem_open()

```c
sem_t *group_sem_open(const char *name, int flags, gid_t gid, ...)
```

**Description**

Creates or opens a named semaphore in the directory selected by gid.<br> When O_CREAT is specified, the variadic arguments must be a mode_t mode followed by an unsigned int value. These creation attributes are ignored when opening an existing semaphore. This function is a POSIX handle-returning function, not a status-code function: the return value is a semaphore handle, and SEM_FAILED is the sentinel failure value. It uses the common errno error model; the return type matches the POSIX sem_open declaration.

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *name | [in] Name of the semaphore. Cannot be NULL. Must be a NUL-terminated string of 1 to NAME_MAX (255) bytes after leading slashes are removed; must not contain '/', and must not be '.' or '..'. The string is not modified and remains owned by the caller. |
| int flags | [in] Open flags. Supports O_CREAT and O_EXCL. |
| gid_t gid | [in] Application-supplied group identifier used to select the directory. |

**Returns**:

| Type | Description |
| -- | -- |
| sem_t * | <ul> <li>A valid semaphore handle if the semaphore is created or opened successfully.</li> <li>SEM_FAILED if the operation fails. errno is set to a common error code such as EACCES, EEXIST, EINVAL, ENAMETOOLONG, ENOENT, ENOTDIR, EMFILE, or ENOMEM. No module-specific error codes are defined.</li> </ul> |

### group_sem_unlink()

```c
int group_sem_unlink(const char *name, gid_t gid)
```

**Description**

Removes the name of a group-scoped semaphore.<br> This function is a POSIX status-style function and uses the common errno error model: the return type matches the POSIX sem_unlink declaration, success is 0, and failure is -1 with errno set. No dedicated module error-code enum or module-specific error codes are defined.

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *name | [in] Name of the semaphore. Cannot be NULL. Must be a NUL-terminated string of 1 to NAME_MAX (255) bytes after leading slashes are removed; must not contain '/', and must not be '.' or '..'. The string is not modified and remains owned by the caller. |
| gid_t gid | [in] Application-supplied group identifier used to select the directory. |

**Returns**:

| Type | Description |
| -- | -- |
| int | <ul> <li>0 if the name is removed successfully.</li> <li>-1 if the operation fails. errno is set to a common error code such as EACCES, EPERM, EINVAL, ENAMETOOLONG, ENOENT, ENOTDIR, or EROFS. No module-specific error codes are defined.</li> </ul> |

### group_shm_open()

```c
int group_shm_open(const char *name, int flag, mode_t mode, gid_t gid)
```

**Description**

Creates or opens a shared memory object in the directory selected by gid.<br> This function is a POSIX handle-returning function, not a status-code function: the nonnegative return value is a file descriptor and -1 is the sentinel failure value. It uses the common errno error model; the return type matches the POSIX shm_open declaration.

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *name | [in] Name of the shared memory object. Cannot be NULL. Must be a NUL-terminated string of 1 to NAME_MAX (255) bytes after leading slashes are removed; must not contain '/', and must not be '.' or '..'. The string is not modified and remains owned by the caller. |
| int flag | [in] Open flags, such as O_RDONLY, O_RDWR, O_CREAT, O_EXCL and O_TRUNC. |
| mode_t mode | [in] Access permissions for a newly created object, subject to umask. |
| gid_t gid | [in] Application-supplied group identifier used to select the directory. |

**Returns**:

| Type | Description |
| -- | -- |
| int | <ul> <li>A nonnegative file descriptor for the shared memory object if the operation succeeds.</li> <li>-1 if the operation fails. errno is set to a common error code such as EACCES, EEXIST, EINVAL, ENAMETOOLONG, ENOENT, ENOTDIR, ELOOP, EMFILE, or ENFILE. No module-specific error codes are defined.</li> </ul> |

### group_shm_unlink()

```c
int group_shm_unlink(const char *name, gid_t gid)
```

**Description**

Removes the name of a group-scoped shared memory object.<br> This function is a POSIX status-style function and uses the common errno error model: the return type matches the POSIX shm_unlink declaration, success is 0, and failure is -1 with errno set. No dedicated module error-code enum or module-specific error codes are defined.

**Since**: 26.2.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *name | [in] Name of the shared memory object. Cannot be NULL. Must be a NUL-terminated string of 1 to NAME_MAX (255) bytes after leading slashes are removed; must not contain '/', and must not be '.' or '..'. The string is not modified and remains owned by the caller. |
| gid_t gid | [in] Application-supplied group identifier used to select the directory. |

**Returns**:

| Type | Description |
| -- | -- |
| int | <ul> <li>0 if the name is removed successfully.</li> <li>-1 if the operation fails. errno is set to a common error code such as EACCES, EPERM, EINVAL, ENAMETOOLONG, ENOENT, ENOTDIR, or EROFS. No module-specific error codes are defined.</li> </ul> |


