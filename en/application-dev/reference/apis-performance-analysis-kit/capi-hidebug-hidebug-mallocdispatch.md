# HiDebug_MallocDispatch

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @leiguangyu-->
<!--Designer: @mgce1-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=e927796ba68acb42b31a64400ef3f800e94a271e translatedAt=2026-09-21T02:30:46.588Z pushedAt=2026-09-22T01:29:30.378Z -->

```c
typedef struct HiDebug_MallocDispatch {...} HiDebug_MallocDispatch
```

## Overview

Defines the HiDebug_MallocDispatch table structure type that can be replaced/restored by the application process. Through this structure, developers can customize memory management function pointers to monitor and customize process memory allocation and deallocation. Key features include: supporting dynamic replacement and restoration of memory management functions, providing comprehensive memory operation interfaces (malloc, calloc, realloc, free, mmap, munmap), and not affecting the default system memory management behavior. Use cases include: memory leak detection, memory usage performance analysis, custom memory allocation strategies, and memory safety monitoring. It helps developers promptly identify and resolve memory issues, improving application stability and performance.

**Since**: 20

**Related module**: [HiDebug](capi-hidebug.md)

**Header file**: [hidebug_type.h](capi-hidebug-type-h.md)

## Summary

### Member Function

| Name| Description|
| -- | -- |
| [void* (\*malloc)(size_t)](#malloc) | Developer-defined **malloc** function pointer. Used to replace the system default memory allocation function, recording allocation information or executing custom logic when allocating memory. It can be used for memory leak tracking and performance monitoring. |
| [void* (\*calloc)(size_t, size_t)](#calloc) | Developer-defined **calloc** function pointer. Used to replace the system default **calloc** function, recording allocation information or executing custom logic when allocating and zero-initializing memory. It can be used for tracking large-block memory allocation and monitoring memory initialization. |
| [void* (\*realloc)(void*, size_t)](#realloc) | Developer-defined **realloc** function pointer. Used to replace the system default **realloc** function, recording operation information or executing custom logic when resizing allocated memory. It can be used for monitoring memory reallocation behavior and analyzing memory fragmentation. |
| [void (\*free)(void*)](#free) | Developer-defined **free** function pointer. Used to replace the system default **free** function, recording release information or executing custom processing logic when freeing memory. Ensure that the passed pointer is valid to avoid double-freeing or freeing a wild pointer. |
| [void* (\*mmap)(void*, size_t, int, int, int, off_t)](#mmap) | Developer-defined **mmap** function pointer. Used to replace the system default **mmap** function, recording mapping information or executing custom logic during memory mapping. It can be used for monitoring large-block memory mapping operations and shared memory usage. |
| [int (\*munmap)(void*, size_t)](#munmap) | Developer-defined **munmap** function pointer. Used to replace the system default **munmap** function, recording operation information or executing custom logic when unmapping memory. It can be used together with the **mmap** function for lifecycle management of mapped memory. |

## Member Function Description

### malloc()

```c
void* (*malloc)(size_t)
```

**Description**

Developer-defined **malloc** function pointer. Used to replace the system default memory allocation function, recording allocation information or executing custom logic when allocating memory. It can be used for memory leak tracking and performance monitoring.

### calloc()

```c
void* (*calloc)(size_t, size_t)
```

**Description**

Developer-defined **calloc** function pointer. Used to replace the system default **calloc** function, recording allocation information or executing custom logic when allocating and zero-initializing memory. It can be used for tracking large-block memory allocation and monitoring memory initialization.

### realloc()

```c
void* (*realloc)(void*, size_t)
```

**Description**

Developer-defined **realloc** function pointer. Used to replace the system default **realloc** function, recording operation information or executing custom logic when resizing allocated memory. It can be used for monitoring memory reallocation behavior and analyzing memory fragmentation.

### free()

```c
void (*free)(void*)
```

**Description**

Developer-defined **free** function pointer. Used to replace the system default **free** function, recording release information or executing custom processing logic when freeing memory. Ensure that the passed pointer is valid to avoid double-freeing or freeing a wild pointer.

### mmap()

```c
void* (*mmap)(void*, size_t, int, int, int, off_t)
```

**Description**

Developer-defined **mmap** function pointer. Used to replace the system default **mmap** function, recording mapping information or executing custom logic during memory mapping. It can be used for monitoring large-block memory mapping operations and shared memory usage.

### munmap()

```c
int (*munmap)(void*, size_t)
```

**Description**

Developer-defined **munmap** function pointer. Used to replace the system default **munmap** function, recording operation information or executing custom logic when unmapping memory. It can be used together with the **mmap** function for lifecycle management of mapped memory.


