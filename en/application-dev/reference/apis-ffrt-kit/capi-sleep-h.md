# sleep.h

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1bd5d6cdd22374b2fc7c67ab365167018faf622f translatedAt=2026-07-20T02:00:35.758Z pushedAt=2026-07-20T02:22:03.629Z -->

## Overview

This file declares the C APIs [ffrt_usleep](capi-sleep-h.md#ffrt_usleep) and [ffrt_yield](capi-sleep-h.md#ffrt_yield).

**File to include**: <ffrt/sleep.h>

**Library**: libffrt.z.so

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

## Summary

### Function

| Name| Description|
| -- | -- |
| [FFRT_C_API int ffrt_usleep(uint64_t usec)](#ffrt_usleep) | Suspends the calling thread for a specified duration. If `usec` exceeds the maximum value supported, the maximum value will be used. |
| [FFRT_C_API void ffrt_yield(void)](#ffrt_yield) | Yields control to other tasks, giving them an opportunity to execute. |

## Function Description

### ffrt_usleep()

```c
FFRT_C_API int ffrt_usleep(uint64_t usec)
```

**Description**

Suspends the calling thread for a specified duration. If `usec` exceeds the maximum value supported, the maximum value will be used.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| uint64_t usec | Duration for which the calling thread is suspended, in microseconds. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | `ffrt_success`. This function never fails. |

### ffrt_yield()

```c
FFRT_C_API void ffrt_yield(void)
```

**Description**

Yields control to other tasks, giving them an opportunity to be executed.

**Since**: 10