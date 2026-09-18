# fiber.h

## Overview

Declares the fiber interfaces in C.<br> A fiber is a lightweight user-mode thread that enables efficient task scheduling and context switching in user space.

**Library**: libffrt.z.so

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [FFRT_C_API int ffrt_fiber_init(ffrt_fiber_t* fiber, void(\*func)(void*), void* arg, void* stack, size_t stack_size)](#ffrt_fiber_init) | Initializes a fiber.<br> This function initializes a fiber structure, preparing it for execution. The caller is responsible for allocating the stack memory pointed to by `stack` and keeping it valid for the entire lifetime of the fiber. |
| [FFRT_C_API void ffrt_fiber_switch(ffrt_fiber_t* from, ffrt_fiber_t* to)](#ffrt_fiber_switch) | Switches execution context between two fibers.<br> Switches the execution context by saving the current context into the fiber specified by `from` and restoring the context from the fiber specified by `to`.<br> Both `from` and `to` must point to fiber instances that have been initialized by [ffrt_fiber_init](capi-fiber-h.md#ffrt_fiber_init); otherwise the behavior is undefined. |

## Function description

### ffrt_fiber_init()

```c
FFRT_C_API int ffrt_fiber_init(ffrt_fiber_t* fiber, void(*func)(void*), void* arg, void* stack, size_t stack_size)
```

**Description**

Initializes a fiber.<br> This function initializes a fiber structure, preparing it for execution. The caller is responsible for allocating the stack memory pointed to by `stack` and keeping it valid for the entire lifetime of the fiber.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| frt_fiber_t\* fiber | Indicates the pointer to the fiber structure to be initialized. |
| void(\*func)(void\*) | Indicates the entry point function that the fiber will execute. |
| void\* arg | Indicates the argument to be passed to the entry point function. |
| void\* stack | Indicates the pointer to the memory region to be used as the fiber's stack. |
| size_t stack_size | Indicates the size of the stack in bytes. Must be large enough to hold the fiber context. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API int | `ffrt_success` if the fiber is initialized;          `ffrt_error_inval` if `stack_size` is too small to hold the fiber context. |

### ffrt_fiber_switch()

```c
FFRT_C_API void ffrt_fiber_switch(ffrt_fiber_t* from, ffrt_fiber_t* to)
```

**Description**

Switches execution context between two fibers.<br> Switches the execution context by saving the current context into the fiber specified by `from` and restoring the context from the fiber specified by `to`.<br> Both `from` and `to` must point to fiber instances that have been initialized by [ffrt_fiber_init](capi-fiber-h.md#ffrt_fiber_init); otherwise the behavior is undefined.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| ffrt_fiber_t* from | Indicates the pointer to the fiber into which the current context will be saved. |
| ffrt_fiber_t* to | Indicates the pointer to the fiber from which the context will be restored. |

**Reference**:

[ffrt_fiber_init](capi-fiber-h.md#ffrt_fiber_init)



