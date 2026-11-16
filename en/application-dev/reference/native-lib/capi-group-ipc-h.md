# group_ipc.h

<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @da_wei_li11-->
<!--Designer: @liyiming13-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=a8391144300860d9588d1e0a358570a1d246ae2f translatedAt=2026-11-03T13:39:24.693Z pushedAt=2026-11-04T07:06:59.578Z nl=1 -->

## Overview

Provides interfaces for organizing shared memory and named semaphores by business group identifier, supporting multiple processes to access the same shared object and perform synchronization. It is suitable for scenarios where cross-process data sharing and synchronization are organized by business group. Different business groups use different paths, and the actual access permission is determined by the system permission configuration. These interfaces are OpenHarmony extension interfaces.

**Header file:** `<sys/group_ipc.h>`

**Library:** libc.so

**System capability:** SystemCapability.Base

**Since:** 26.1.0

**Related module:** [libc standard library](musl.md)

## Usage

The four interfaces use the same path rule: format `gid` as a decimal directory name, remove all leading slashes from `name`, and then access `/dev/group/shm/<gid>/<name>`. For example, when `gid` is 1001 and `name` is `/shared-state`, the actual path is `/dev/group/shm/1001/shared-state`.

- Before calling, `/dev/group/shm/<gid>` must already exist, and the calling process must have the required directory and file access permissions. The interfaces do not create the parent directory, modify the directory's owner or permissions, or fall back to `/dev/shm`. When the parent directory does not exist, they return failure with `errno` set to `ENOENT`.
- `gid` is agreed upon by the business side and is used to select the directory. The interfaces do not require it to equal the calling process's real or effective group ID, nor do they switch the process identity. The same `gid` does not automatically grant access permission, and different UIDs do not necessarily mean access is denied; the access result is determined by the system permission control.
- Multiple processes with access permission that use the same `gid` and `name` can open the same object that has not yet been deleted. Different `gid` values correspond to different paths. Shared memory and named semaphores share this path space and should use different names.

  The following diagram shows how the path space is organized. The connecting lines indicate opening an object when the required access permission is available, and do not mean that the same `gid` automatically grants permission.

  ```mermaid
  flowchart LR
      A["Process A"] -->|"gid=1001, name=/shared-state"| SHM
      B["Process B"] -->|"gid=1001, name=/shared-state"| SHM
      A -->|"gid=1001, name=/ready"| SEM
      B -->|"gid=1001, name=/ready"| SEM
      C["Process C"] -->|"gid=1002, name=/shared-state"| OTHER
      subgraph ROOT["/dev/group/shm/"]
          subgraph G1001["1001/"]
              SHM["shared-state: shared memory object"]
              SEM["ready: named semaphore object"]
          end
          subgraph G1002["1002/"]
              OTHER["shared-state: another shared memory object"]
          end
      end
  ```

- `name` must be a valid null-terminated string. After removing the leading slash, the name length is 1 to `NAME_MAX` bytes (currently 255). It cannot be `.` or `..`, and cannot contain a slash. An empty string, a string of all slashes, and a name containing a subpath are all invalid.
- Data synchronization of shared memory requires the `MAP_SHARED` mapping. The order of concurrent access is coordinated by the business side using mechanisms such as semaphores.

The interface first removes the leading slash from `name` and then verifies the length of the remaining name. If the remaining name exceeds `NAME_MAX`, or if the path after symbolic link expansion during group directory path resolution exceeds the system length limit, the interface returns failure and sets `errno` to `ENAMETOOLONG`.

## Function Summary

| Name | Description |
| --- | --- |
| [group_sem_open()](#group_sem_open) | Creates or opens the named semaphore under the specified `gid`. |
| [group_sem_unlink()](#group_sem_unlink) | Deletes the named semaphore name under the specified `gid`. |
| [group_shm_open()](#group_shm_open) | Creates or opens the shared memory object under the specified `gid`. |
| [group_shm_unlink()](#group_shm_unlink) | Deletes the shared memory object name under the specified `gid`. |

## Function Description

### group_sem_open()

```c
sem_t *group_sem_open(const char *name, int flags, gid_t gid, ...);
```

Creates or opens a named semaphore, suitable for scenarios where multiple processes synchronize and coordinate through semaphores. Except for the additional `gid` parameter and the changed access path, the usage is the same as `sem_open()`. The returned handle can be passed to interfaces such as `sem_wait()`, `sem_trywait()`, and `sem_post()`, and closed with `sem_close()`. Shared memory and named semaphores share the same path space, so different names should be used to avoid conflicts. After a name is deleted by `group_sem_unlink()`, the already-opened semaphore handle remains valid until it is closed through `sem_close()`.

**Since:** 26.1.0

**Parameters**

| Name | Description |
| --- | --- |
| `name` | Semaphore name, following the name rules in [Usage](#usage). |
| `flags` | Open flags. `0` means only open an existing object; `O_CREAT` means create if it does not exist; `O_CREAT \| O_EXCL` means exclusive creation, failing if the object already exists. `O_EXCL` should be used together with `O_CREAT`. |
| `gid` | Business group identifier used to select the parent directory, with a value range representable by `gid_t`; 0 is valid. The directory must still pre-exist. |
| `...` | When `O_CREAT` is specified, pass `mode_t mode` (creation permission parameter) and `unsigned int value` (semaphore initial value parameter) in sequence. `mode` only uses the read/write permission bits included in `0666` and is affected by the process `umask`. `value` ranges from 0 to `SEM_VALUE_MAX` (currently 2147483647). Opening an existing object does not modify its permission or count value; these two parameters are read and validated only when the object is actually created. |

**Returns**

Returns the semaphore pointer on success; returns `SEM_FAILED` and sets `errno` on failure.

**Error codes**

| errno | Cause | Handling measures |
| --- | --- | --- |
| EACCES | Lacks the permission required to access the parent directory or the semaphore object. | Verify the calling process identity and directory access permission. Creating an object requires write and search permission on the parent directory; opening an existing semaphore requires read/write permission on the object, and the environment manager adjusts the permission when necessary. |
| EEXIST | `O_CREAT \| O_EXCL` is specified, but the object already exists. | Confirm that the existing object is the semaphore agreed upon by the business and has been initialized; set `flags` to `0` when reuse is needed, and have the business side coordinate the cleanup timing of the original object when a new one is needed. |
| EINTR | During the open or create process, the underlying operation was interrupted by a signal and reported this error. | Check the signal handling requirements; call the interface again if the business still needs to continue, and end the operation if the signal is used to terminate the task. The case where the object already exists must still be handled on retry. |
| EINVAL | The name is invalid, or the initial value at creation exceeds `SEM_VALUE_MAX`. | Check `name` according to [Usage](#usage); set `value` to a value within the range of 0 to `SEM_VALUE_MAX` at creation. |
| EMFILE | The process's file descriptors or named semaphore references have reached the upper limit. | Close file descriptors that are no longer used, release named semaphore references that are no longer used through `sem_close()`, and then retry. |
| ENAMETOOLONG | The name after removing the leading slash exceeds `NAME_MAX`, or the length after underlying path resolution exceeds the system limit. | Shorten the name after removing the leading slash to within `NAME_MAX` bytes; have the environment manager check the symbolic link expansion results in the group directory and its parent paths. |
| ENFILE | The system has opened too many semaphores or files and can no longer allocate system-level open resources. | Have the environment manager investigate system resource usage, coordinate related processes to close semaphore references or files that are no longer used, and then retry. |
| ENOENT | The parent directory does not exist, or `O_CREAT` is not specified and the object does not exist. | Verify `gid` and the group directory; have the environment manager prepare the directory when it does not exist. When only the object does not exist and creation is needed, specify `O_CREAT` and pass `mode` and `value`. |
| ENOSPC | There is not enough space or file system resources to create the semaphore object or write its initial state. | Check the available space and inode resources of the file system where the group directory resides, clean up objects confirmed to be no longer used, or have the environment manager expand resources and then retry. |

The application should read and save `errno` promptly after a failure to avoid subsequent calls overwriting the error information. See [Semaphore Example](#semaphore-example) for an example.

When handling `EEXIST`, the business side should confirm that the original object is no longer used before cleaning it up, and coordinate the lifecycle of all participating processes. Directly deleting the name of an object still in use by other processes and then recreating it will cause existing handles and new handles to point to different objects.

### group_sem_unlink()

```c
int group_sem_unlink(const char *name, gid_t gid);
```

Deletes the name of a named semaphore without deleting its parent directory. After the name is deleted, other processes can no longer open the original object by that name; semaphores that are already open remain valid until the corresponding references are closed through `sem_close()`. A semaphore recreated with the same name is a new object.

**Since:** 26.1.0

**Parameters**

| Name | Description |
| --- | --- |
| `name` | Name of the semaphore to delete, following the naming rules in [Usage](#usage). |
| `gid` | Business group identifier of the directory where the object resides, consistent with the `gid` used when creating or opening it. The directory must still pre-exist. |

**Returns**

Returns 0 on success; returns -1 on failure and sets `errno`.

**Error codes**

| errno | Cause | Handling measures |
| --- | --- | --- |
| EACCES | The permission required to delete the specified object name is missing, for example, the write or search permission on the parent directory is lacking. | Verify the calling process identity and parent directory permissions, and have the environment manager handle the permission issue; the object's own read/write permission cannot independently determine whether deletion is allowed. |
| EINVAL | The name is invalid. | Check `name` according to [Usage](#usage), and use a valid name corresponding to the one used when creating the object. |
| ENAMETOOLONG | The name after removing the leading slash exceeds `NAME_MAX`, or the length after underlying path resolution exceeds the system limit. | Verify the name used at creation time, and ensure that the length after removing the leading slash does not exceed `NAME_MAX` bytes; have the environment manager check the result of symbolic link expansion in the parent path. |
| ENOENT | The parent directory or the object with the specified name does not exist. | Verify `gid`, the name, and the parent directory; if the business only requires that the name no longer exist, this result can be treated as cleanup completion. |
| EPERM | System permission control does not allow deleting the object. | Have the environment manager verify the calling process identity, the parent directory, and the object's permission restrictions; the object's own read/write permission cannot independently determine whether deletion is allowed. |

The application should read and save `errno` promptly after a failure. For an example, see [Semaphore Example](#semaphore-example).

### group_shm_open()

```c
int group_shm_open(const char *name, int flag, mode_t mode, gid_t gid);
```

Creates or opens a shared memory object, suitable for scenarios where data is shared among multiple processes. Returns a file descriptor. The initial length of a newly created object is 0. You should first use `ftruncate()` to set the length, and then use `mmap()` with `MAP_SHARED` to establish the mapping. The file descriptor is closed with `close()`, and the mapping is removed with `munmap()`. Shared memory and named semaphores share the same path space, so different names should be used to avoid conflicts. After a name is removed by `group_shm_unlink()`, the already opened file descriptor and mapping remain valid until released through `close()` and `munmap()`.

**Since:** 26.1.0

**Parameters**

| Name | Description |
| --- | --- |
| `name` | Name of the shared memory object, following the naming rules in [Usage](#usage). |
| `flag` | The access mode is `O_RDONLY` or `O_RDWR`, and can be combined with `O_CREAT`, `O_EXCL`, and `O_TRUNC` as needed. `O_CREAT` creates the object when it does not exist; `O_CREAT \| O_EXCL` fails when the object already exists; `O_EXCL` should be used together with `O_CREAT`; `O_TRUNC` truncates the object length to 0 and is recommended to be used with `O_RDWR`. |
| `mode` | Creation permission parameter. Common values are `0600` (owner read/write only) or `0660` (owner and group read/write), affected by the process `umask`. Opening an existing object does not change its permissions. This parameter must be passed; 0 can be passed when no object is created. |
| `gid` | The business group identifier used to select the parent directory. The value range is the values representable by `gid_t`, and 0 is valid. The directory must still be pre-existing. |

When opening, the interface attaches the `O_NOFOLLOW`, `O_CLOEXEC`, and `O_NONBLOCK` flags, which are respectively used to refuse to follow a symbolic link in the final path component, to close the file descriptor when executing a new program, and to open in non-blocking mode.

**Returns**

Returns a non-negative file descriptor on success; returns -1 and sets `errno` on failure.

**Error codes**

| errno | Cause | Handling measures |
| --- | --- | --- |
| EACCES | Lacks the permission required to access the parent directory, open or create the object, or `O_TRUNC` is specified but there is no write permission on the object. | Verify the calling process identity, directory permissions, and object permissions. Creating an object requires write and search permission on the parent directory; opening an existing object requires the access permission corresponding to `O_RDONLY` or `O_RDWR`, and truncating the object also requires write permission. |
| EEXIST | `O_CREAT \| O_EXCL` is specified, but the object already exists. | Confirm the type, data format, and initialization state of the existing object; when reuse is needed, open it with `O_RDONLY` or `O_RDWR` according to the access requirement, and do not specify `O_TRUNC` when data must be preserved. When a new object is needed, coordinate the lifecycle of the original object according to the cleanup principles in [group_sem_open()](#group_sem_open). |
| EINTR | During opening or creation, the underlying operation was interrupted by a signal and reported this error. | Check the signal handling requirements; re-invoke the interface when the business still needs to continue, and end the operation if the signal is used to terminate the task. When retrying, the case where the object already exists must still be handled. |
| EINVAL | The name is invalid. | Check `name` according to [Usage](#usage), and correct empty names, `.`, `..`, or names containing subpaths. |
| EMFILE | The number of file descriptors of the process has reached the upper limit. | Close the file descriptors that the process no longer uses, check for file descriptor leaks and process resource limits, and then retry. |
| ENAMETOOLONG | The name after removing the leading slash exceeds `NAME_MAX`, or the length after underlying path resolution exceeds the system limit. | Shorten the name after removing the leading slash to within `NAME_MAX` bytes; the environment manager checks the symbolic link expansion results in the group directory and its parent paths. |
| ENFILE | The system has opened too many shared memory objects or files and can no longer allocate system-level open resources. | The environment manager investigates system file resource usage, coordinates related processes to close file descriptors that are no longer used, and then retries. |
| ENOENT | The parent directory does not exist, or `O_CREAT` is not specified and the object does not exist. | Verify `gid` and the group directory; when the directory does not exist, the environment manager prepares it. When only the object does not exist and creation is needed, specify `O_CREAT` and set the creation permission. |
| ENOSPC | There is not enough space or file system resources to create the shared memory object. | Check the available space and inode resources of the file system where the group directory resides, clean up objects confirmed to be no longer used, or have the environment manager expand resources and then retry. |

The application should read and save `errno` promptly after a failure. When subsequent `ftruncate()` and `mmap()` calls fail, they should be handled according to the error codes of the corresponding interfaces. See [Shared Memory Example](#shared-memory-example) for an example.

### group_shm_unlink()

```c
int group_shm_unlink(const char *name, gid_t gid);
```

Deletes the name of a shared memory object without deleting its parent directory. Already-open file descriptors and mappings remain valid; after the name is deleted and all references are released, the object's resources are reclaimed. An object recreated with the same name is independent of the old object.

**Since:** 26.1.0

**Parameters**

| Name | Description |
| --- | --- |
| `name` | Name of the shared memory object to delete, following the name rules in [Usage](#usage). |
| `gid` | Business group identifier of the directory where the object resides, consistent with the `gid` used when creating or opening it. The directory must still pre-exist. |

**Returns**

Returns 0 on success; returns -1 on failure and sets `errno`.

**Error codes**

| errno | Cause | Handling measures |
| --- | --- | --- |
| EACCES | No permission to delete the specified object name, for example, missing write or search permission on the parent directory. | Verify the calling process identity and parent directory permission, and have the environment manager handle the permission issue; the object's own read/write permission cannot independently determine whether to allow deletion. |
| EINVAL | The name is invalid. | Check `name` according to [Usage](#usage), and use a valid name corresponding to the one used when creating the object. |
| ENAMETOOLONG | The name after removing the leading slash exceeds `NAME_MAX`, or the length after underlying path resolution exceeds the system limit. | Verify the name used at creation, ensuring that the length after removing the leading slash does not exceed `NAME_MAX` bytes; have the environment manager check the symbolic link expansion result in the parent path. |
| ENOENT | The parent directory or the object with the specified name does not exist. | Verify `gid`, the name, and the parent directory; if the business only requires that the name no longer exist, this result can be treated as cleanup completion. |
| EPERM | System permission control does not allow deleting the object. | Have the environment manager verify the calling process identity, the parent directory, and the object's permission restrictions; the object's own read/write permission cannot independently determine whether to allow deletion. |

The application should read and save `errno` promptly after a failure. See [Shared Memory Example](#shared-memory-example) for an example.

## Example

The following two examples respectively demonstrate the complete lifecycle of creating or opening, operating, closing, and deleting a name. Before running, the environment manager with the appropriate permissions prepares `/dev/group/shm/1001` and grants the calling process the required access permission; the interface does not create the directory on its behalf. The `gid` in the examples is only a business-agreed value.

The examples use exclusive creation; if an object with the same name already exists, an error is reported and the existing object is not overwritten. When used across processes, each process should agree on the same `gid`, name, and shared data format, and the business side should coordinate the timing of initialization completion and the final deletion of the object name.

### Semaphore Example

```c
#include <fcntl.h>
#include <stdio.h>
#include <sys/group_ipc.h>

int main(void)
{
    const gid_t gid = 1001;
    const char *name = "/example-ready";
    int result = 0;
    sem_t *sem = group_sem_open(name, O_CREAT | O_EXCL, gid, (mode_t)0660, 0U);
    if (sem == SEM_FAILED) {
        perror("group_sem_open");
        return 1;
    }
    if (sem_post(sem) == -1 || sem_wait(sem) == -1) {
        perror("sem_post/sem_wait");
        result = 1;
    }
    if (sem_close(sem) == -1) {
        perror("sem_close");
        result = 1;
    }
    if (group_sem_unlink(name, gid) == -1) {
        perror("group_sem_unlink");
        result = 1;
    }
    return result;
}
```

### Shared Memory Example

```c
#include <fcntl.h>
#include <stdio.h>
#include <sys/group_ipc.h>
#include <unistd.h>
#include <sys/mman.h>

int main(void)
{
    const gid_t gid = 1001;
    const char *name = "/example-state";
    int result = 1;
    int *state;
    int fd = group_shm_open(name, O_CREAT | O_EXCL | O_RDWR, 0660, gid);
    if (fd == -1) {
        perror("group_shm_open");
        return 1;
    }
    if (ftruncate(fd, sizeof(*state)) == -1) {
        perror("ftruncate");
        goto cleanup;
    }
    state = mmap(NULL, sizeof(*state), PROT_READ | PROT_WRITE, MAP_SHARED, fd, 0);
    if (state == MAP_FAILED) {
        perror("mmap");
        goto cleanup;
    }
    *state = 42;
    result = 0;
    if (munmap(state, sizeof(*state)) == -1) {
        perror("munmap");
        result = 1;
    }
cleanup:
    if (close(fd) == -1) {
        perror("close");
        result = 1;
    }
    if (group_shm_unlink(name, gid) == -1) {
        perror("group_shm_unlink");
        result = 1;
    }
    return result;
}
```
