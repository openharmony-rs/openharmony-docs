# fiber.h

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1c82fe64143ca179b80fafe272ca5a84323e9159 translatedAt=2026-11-13T03:05:34.558Z pushedAt=2026-11-13T08:30:11.837Z nl=1 -->

## Overview

Declares the C APIs of fibers. A fiber is a lightweight user-space thread used to implement efficient task scheduling and context switching in user space.

**File to include**: <ffrt/fiber.h>

**Library**: libffrt.z.so

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 20

**Related module**: [FFRT](capi-ffrt.md)

## Summary

### Function

| Name| Description|
| -- | -- |
| [FFRT_C_API int ffrt_fiber_init(ffrt_fiber_t* fiber, void(\*func)(void*), void* arg, void* stack, size_t stack_size)](#ffrt_fiber_init) | Initializes a fiber. Initializes the fiber structure so that it is ready to be executed. The caller is responsible for allocating the stack memory pointed to by `stack` and ensuring that the memory remains valid throughout the entire lifecycle of the fiber. |
| [FFRT_C_API void ffrt_fiber_switch(ffrt_fiber_t* from, ffrt_fiber_t* to)](#ffrt_fiber_switch) | Switches the execution context between two fibers. Saves the current execution context to the fiber specified by `from`, and restores the execution context from the fiber specified by `to`. Both `from` and `to` must point to fiber instances that have been initialized by [ffrt_fiber_init](capi-fiber-h.md#ffrt_fiber_init); otherwise, the behavior is undefined. |

## Function Description

### ffrt_fiber_init()

```c
FFRT_C_API int ffrt_fiber_init(ffrt_fiber_t* fiber, void(*func)(void*), void* arg, void* stack, size_t stack_size)
```

**Description**

Initializes a fiber. Initializes the fiber structure so that it is ready to be executed. The caller is responsible for allocating the stack memory pointed to by `stack` and ensuring that the memory remains valid throughout the entire lifecycle of the fiber.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_fiber_t](capi-ffrt-ffrt-fiber-t.md)\* fiber | Pointer to the fiber structure to be initialized. |
| void(\*func)(void\*) | Entry function to be executed by the fiber. |
| void\* arg | Argument passed to the entry function. |
| void\* stack | Pointer to the memory area used by the fiber stack. |
| size_t stack_size | Size of the stack, in bytes. It must be large enough to accommodate the fiber context. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | Returns `ffrt_success` if the fiber is initialized successfully;<br>         Returns `ffrt_error_inval` if `stack_size` is too small (insufficient to hold the fiber context). |

### ffrt_fiber_switch()

```c
FFRT_C_API void ffrt_fiber_switch(ffrt_fiber_t* from, ffrt_fiber_t* to)
```

**Description**

Switches the execution context between two fibers. Saves the current execution context to the fiber specified by `from`, and restores the execution context from the fiber specified by `to`. Both `from` and `to` must point to fiber instances that have been initialized by [ffrt_fiber_init](capi-fiber-h.md#ffrt_fiber_init); otherwise, the behavior is undefined.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [ffrt_fiber_t](capi-ffrt-ffrt-fiber-t.md)* from | Pointer to the fiber used to save the current context. |
| [ffrt_fiber_t](capi-ffrt-ffrt-fiber-t.md)* to | Pointer to the fiber used to restore the execution context. |

**Reference**

[ffrt_fiber_init](capi-fiber-h.md#ffrt_fiber_init)



