# sleep.h

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1c82fe64143ca179b80fafe272ca5a84323e9159 translatedAt=2026-11-10T03:21:02.264Z pushedAt=2026-11-10T04:57:25.137Z nl=1 -->

## Overview

Declares the C interfaces of [ffrt_usleep](capi-sleep-h.md#ffrt_usleep) and [ffrt_yield](capi-sleep-h.md#ffrt_yield).

**File to include**: <ffrt/sleep.h>

**Library**: libffrt.z.so

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

## Summary

### Function

| Name| Description|
| -- | -- |
| [FFRT_C_API int ffrt_usleep(uint64_t usec)](#ffrt_usleep) | Suspends the calling thread for a specified duration. If `usec` exceeds the maximum supported value, it is truncated to the maximum value. |
| [FFRT_C_API void ffrt_yield(void)](#ffrt_yield) | Yields control to other tasks so that they have a chance to be executed. |

## Function Description

### ffrt_usleep()

```c
FFRT_C_API int ffrt_usleep(uint64_t usec)
```

**Description**

Suspends the calling thread for a specified duration. If `usec` exceeds the maximum supported value, it is truncated to the maximum value.

**Since**: 10

**Parameters**

| Name| Description|
| -- | -- |
| uint64_t usec | Duration for which the calling thread is suspended, in microseconds. |

**Returns**

| Type| Description|
| -- | -- |
| FFRT_C_API int | `ffrt_success`. The function never fails. |

### ffrt_yield()

```c
FFRT_C_API void ffrt_yield(void)
```

**Description**

Yields control to other tasks so that they have a chance to be executed.

**Since**: 10


