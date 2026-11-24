# HiDebug_NativeStackFrame

```c
typedef struct HiDebug_NativeStackFrame {...} HiDebug_NativeStackFrame
```

## Overview

Defines the native stack frame content.

<!--Device-struct HiDebug_NativeStackFrame {...}--><!--Device-struct HiDebug_NativeStackFrame {...}-End-->

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 20

**Related module**: [HiDebug](capi-performance-analysis-kit-hidebug.md)

**Header file**: [hidebug_type.h](capi-hidebug-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint64_t relativePc | Relative PC address, which is the offset of the current PC relative to the start address of its mapping area ( such as an executable file or shared library).<br><!--Device-uint64_t relativePc--><!--Device-uint64_t relativePc-End--> |
| uint64_t funcOffset | Offset of the function corresponding to the current stack frame in its mapping area (such as an executable file or shared library).<br><!--Device-uint64_t funcOffset--><!--Device-uint64_t funcOffset-End--> |
| const char* mapName | Name of the mapping area to which the current stack frame belongs.<br><!--Device-const char* mapName--><!--Device-const char* mapName-End--> |
| const char* functionName | Name of the function corresponding to the current stack frame.<br><!--Device-const char* functionName--><!--Device-const char* functionName-End--> |
| const char* buildId | Build ID that uniquely identifies the current mapping area (such as an executable file or shared library). During debugging and symbol parsing, **buildId** ensures that the symbol file version matches the actual binary file version.<br><!--Device-const char* buildId--><!--Device-const char* buildId-End--> |
| const char* reserved | Reserved field for future extension.<br><!--Device-const char* reserved--><!--Device-const char* reserved-End--> |


