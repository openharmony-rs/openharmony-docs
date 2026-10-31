# fiber.h

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1bd5d6cdd22374b2fc7c67ab365167018faf622f translatedAt=2026-07-20T01:59:40.814Z pushedAt=2026-07-20T09:57:14.641Z -->

## Overview

This file declares the C APIs of fibers. A fiber is a lightweight user-mode thread used to implement efficient task scheduling and context switching in the user space.

**File to include**: <ffrt/fiber.h>

**Library**: libffrt.z.so

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 20

**Related module**: [FFRT](capi-ffrt.md)

## Summary

### Function

| Name| Description|
| -- | -- |
| [FFRT_C_API int ffrt_fiber_init(ffrt_fiber_t* fiber, void(\*func)(void*), void* arg, void* stack, size_t stack_size)](#ffrt_fiber_init) | Initializes a fiber. This API initializes the fiber structure so that it is ready for execution. The caller is responsible for allocating the stack memory pointed to by `stack` and ensuring that the memory remains valid throughout the entire lifecycle of the fiber. |
| [FFRT_C_API void ffrt_fiber_switch(ffrt_fiber_t* from, ffrt_fiber_t* to)](#ffrt_fiber_switch) | Switches the execution context between two fibers. This API saves the current execution context to the fiber specified by `from`, and restores the execution context from the fiber specified by `to`. Both `from` and `to` must point to a fiber instance that has been initialized by [ffrt_fiber_init](capi-fiber-h.md#ffrt_fiber_init). Otherwise, the behavior is undefined. |

## Function Description

### ffrt_fiber_init()

```c
FFRT_C_API int ffrt_fiber_init(ffrt_fiber_t* fiber, void(*func)(void*), void* arg, void* stack, size_t stack_size)
```

**Description**

Initializes a fiber. This API initializes the fiber structure so that it is ready for execution. The caller is responsible for allocating the stack memory pointed to by `stack` and ensuring that the memory remains valid throughout the entire lifecycle of the fiber. 

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_fiber_t](capi-ffrt-ffrt-fiber-t.md)\* fiber | Pointer to the fiber structure to initialize. |
| void(\*func)(void\*) | Entry function to be executed by the fiber. |
| void\* arg | Parameters passed to the entry function. |
| void\* stack | Pointer to the memory region used for the fiber stack. |
| size_t stack_size | Stack size, in bytes. It must be large enough to accommodate the fiber context. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | If the operation is successful, `ffrt_success` is returned.<br>         If `stack_size` is too small to accommodate the fiber context, `ffrt_error_inval` is returned. |

### ffrt_fiber_switch()

```c
FFRT_C_API void ffrt_fiber_switch(ffrt_fiber_t* from, ffrt_fiber_t* to)
```

**Description**

Switches the execution context between two fibers. This API saves the current execution context to the fiber specified by `from`, and restores the execution context from the fiber specified by `to`. Both `from` and `to` must point to a fiber instance that has been initialized by [ffrt_fiber_init](capi-fiber-h.md#ffrt_fiber_init). Otherwise, the behavior is undefined.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_fiber_t](capi-ffrt-ffrt-fiber-t.md)* from | Pointer to the fiber used to save the current context. |
| [ffrt_fiber_t](capi-ffrt-ffrt-fiber-t.md)* to | Pointer to the fiber used to restore the execution context. |

**See also:**

[ffrt_fiber_init](capi-fiber-h.md#ffrt_fiber_init)