# HiDebug_MemoryLimit

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @hello_harmony; @leiguangyu-->
<!--Designer: @kutcherzhou1-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct HiDebug_MemoryLimit {...} HiDebug_MemoryLimit
```

## Overview

Defines the struct for the memory limit of the application process.

**Since**: 12

**Related module**: [HiDebug](capi-hidebug.md)

**Header file**: [hidebug_type.h](capi-hidebug-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint64_t rssLimit | Limit on the physical memory size of the application process, in KB. Currently, the system does not limit the physical memory size of the process. However, the available physical memory of the process cannot exceed the maximum physical memory of the device. You can call [OH_HiDebug_GetSystemMemInfo](capi-hidebug-h.md#oh_hidebug_getsystemmeminfo) to obtain the physical memory usage of the device.|
| uint64_t vssLimit | Limit on the virtual set size, in KB.|
