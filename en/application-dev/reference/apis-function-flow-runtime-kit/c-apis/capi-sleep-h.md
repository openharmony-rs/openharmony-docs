# sleep.h

## Overview

Declares the [ffrt_usleep](capi-sleep-h.md#ffrt_usleep) and [ffrt_yield](capi-sleep-h.md#ffrt_yield) interfaces in C.

**Library**: libffrt.z.so

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 10

**Related module**: [FFRT](capi-ffrt.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [FFRT_C_API int ffrt_usleep(uint64_t usec)](#ffrt_usleep) | Suspends the calling thread for a given duration.<br> If `usec` exceeds the maximum supported value, it is clamped to that maximum. |
| [FFRT_C_API void ffrt_yield(void)](#ffrt_yield) | Passes control to other tasks so that they can be executed. |

## Function description

### ffrt_usleep()

```c
FFRT_C_API int ffrt_usleep(uint64_t usec)
```

**Description**

Suspends the calling thread for a given duration.<br> If `usec` exceeds the maximum supported value, it is clamped to that maximum.

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint64_t usec | Indicates the duration that the calling thread is suspended, in microseconds. |

**Returns**:

| Type | Description |
| -- | -- |
| FFRT_C_API int | `ffrt_success`. The function does not fail. |

### ffrt_yield()

```c
FFRT_C_API void ffrt_yield(void)
```

**Description**

Passes control to other tasks so that they can be executed.

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 10


