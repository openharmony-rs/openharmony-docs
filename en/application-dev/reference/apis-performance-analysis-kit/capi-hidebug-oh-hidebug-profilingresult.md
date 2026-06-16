# OH_HiDebug_ProfilingResult

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @leiguangyu-->
<!--Designer: @mgce1-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct OH_HiDebug_ProfilingResult {...} OH_HiDebug_ProfilingResult
```

## Overview

Defines a struct for encapsulating the result of a single resource collection.

**Since**: 24

**Related module**: [HiDebug](capi-hidebug.md)

**Header file**: [hidebug_type.h](capi-hidebug-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [OH_HiDebug_ResourceType](capi-hidebug-type-h.md#oh_hidebug_resourcetype) resourceType | Resource collection type<br> **Since**: 24|
| const char* filePath | Pointer to the file path of the resource collection result. If the collection fails, the value is empty.<br> **Since**: 24|
