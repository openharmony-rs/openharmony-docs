# malloc.h

## Overview

Includes some memory-related methods and structures, such as: malloc, calloc, realloc, and so on.

**Library**: libc.so

**Since**: 12

**Related module**: [MuslMalloc](capi-muslmalloc.md)

## Summary

### Struct

| Name | Description |
| -- | -- |
| [mallinfo](capi-muslmalloc-mallinfo.md) |  |
| [mallinfo2](capi-muslmalloc-mallinfo2.md) |  |

### Function

| Name | Description |
| -- | -- |
| [int malloc_check_from_ptr(void *ptr)

struct mallinfo 

struct mallinfo2](#malloc_check_from_ptr) | This function determines whether a given memory block was allocated using Standard C library Memory Allocator. This function is MT-Safe(multi-thread safe) but not signal-safe. |
| [struct mallinfo mallinfo(void)](#mallinfo) | Obtains the memory information allocated by malloc-related operations. |
| [struct mallinfo2 mallinfo2(void)](#mallinfo2) | Obtains the memory information allocated by malloc-related operations. |

## Function description

### malloc_check_from_ptr()

```c
int malloc_check_from_ptr(void *ptr)

struct mallinfo {int arenaint ordblksint smblksint hblksint hblkhdint usmblksint fsmblksint uordblksint fordblksint keepcost
}

struct mallinfo2 {size_t arenasize_t ordblkssize_t smblkssize_t hblkssize_t hblkhdsize_t usmblkssize_t fsmblkssize_t uordblkssize_t fordblkssize_t keepcost
}
```

**Description**

This function determines whether a given memory block was allocated using Standard C library Memory Allocator. This function is MT-Safe(multi-thread safe) but not signal-safe.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| {void | *} ptr A pointer to the memory block to be checked. |

**Returns**:

| Type | Description |
| -- | -- |
| int | 1 - The memory block was allocated using Standard C library Memory Allocator.           0 - The memory block was not allocated using Standard C library Memory Allocator.           -1 - The function is not implemented or other error. |

### mallinfo()

```c
struct mallinfo mallinfo(void)
```

**Description**

Obtains the memory information allocated by malloc-related operations.

**Since**: 20

**Returns**:

| Type | Description |
| -- | -- |
| [struct mallinfo](capi-muslmalloc-mallinfo.md) | A mallinfo struct containing details about memory allocation. |

### mallinfo2()

```c
struct mallinfo2 mallinfo2(void)
```

**Description**

Obtains the memory information allocated by malloc-related operations.

**Since**: 20

**Returns**:

| Type | Description |
| -- | -- |
| [struct mallinfo2](capi-muslmalloc-mallinfo2.md) | A mallinfo2 struct containing details about memory allocation. Unlike mallinfo, this struct uses  size_t for its counters, providing a larger range. |


