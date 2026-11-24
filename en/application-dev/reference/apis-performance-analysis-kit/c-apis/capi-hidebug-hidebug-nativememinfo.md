# HiDebug_NativeMemInfo

```c
typedef struct HiDebug_NativeMemInfo {...} HiDebug_NativeMemInfo
```

## Overview

Defines the struct for the local memory information of the application process.

<!--Device-struct HiDebug_NativeMemInfo {...}--><!--Device-struct HiDebug_NativeMemInfo {...}-End-->

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 12

**Related module**: [HiDebug](capi-performance-analysis-kit-hidebug.md)

**Header file**: [hidebug_type.h](capi-hidebug-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t pss | Proportional set size, in KB.<br><!--Device-uint32_t pss--><!--Device-uint32_t pss-End--> |
| uint32_t vss | Virtual memory size, in KB.<br><!--Device-uint32_t vss--><!--Device-uint32_t vss-End--> |
| uint32_t rss | Resident set size, in KB.<br><!--Device-uint32_t rss--><!--Device-uint32_t rss-End--> |
| uint32_t sharedDirty | Size of the shared dirty memory, in KB.<br><!--Device-uint32_t sharedDirty--><!--Device-uint32_t sharedDirty-End--> |
| uint32_t privateDirty | Size of the private dirty memory, in KB.<br><!--Device-uint32_t privateDirty--><!--Device-uint32_t privateDirty-End--> |
| uint32_t sharedClean | Size of the shared clean memory, in KB.<br><!--Device-uint32_t sharedClean--><!--Device-uint32_t sharedClean-End--> |
| uint32_t privateClean | Size of the private clean memory, in KB.<br><!--Device-uint32_t privateClean--><!--Device-uint32_t privateClean-End--> |


