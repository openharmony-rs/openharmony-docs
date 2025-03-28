# sleep.h


## Overview

The **sleep.h** file declares the sleep and yield interfaces in C.

**File to include**: &lt;ffrt/sleep.h&gt;

**Library**: libffrt.z.so

**System capability**: SystemCapability.Resourceschedule.Ffrt.Core

**Since**: 10

**Related module**: [FFRT](_f_f_r_t.md)


## Summary


### Functions

| Name| Description| 
| -------- | -------- |
| FFRT_C_API int [ffrt_usleep](_f_f_r_t.md#ffrt_usleep) (uint64_t usec) | Sets the fixed sleep time. | 
| FFRT_C_API void [ffrt_yield](_f_f_r_t.md#ffrt_yield) (void) | Passes control to other tasks so that they can be executed. | 
