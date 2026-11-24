# HiDebug_JsStackFrame

```c
typedef struct HiDebug_JsStackFrame {...} HiDebug_JsStackFrame
```

## Overview

Defines a struct for the JS stack frame content.

<!--Device-struct HiDebug_JsStackFrame {...}--><!--Device-struct HiDebug_JsStackFrame {...}-End-->

**System capability**: SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Since**: 20

**Related module**: [HiDebug](capi-performance-analysis-kit-hidebug.md)

**Header file**: [hidebug_type.h](capi-hidebug-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint64_t relativePc | Relative PC address, which is the offset of the current PC relative to the start address of its mapping area ( such as an executable file or shared library).<br><!--Device-uint64_t relativePc--><!--Device-uint64_t relativePc-End--> |
| int32_t line | Line number of the code corresponding to the current stack frame in the file.<br><!--Device-int32_t line--><!--Device-int32_t line-End--> |
| int32_t column | Column number of the code corresponding to the current stack frame in the specified line.<br><!--Device-int32_t column--><!--Device-int32_t column-End--> |
| const char* mapName | Name of the mapping area to which the current stack frame belongs.<br><!--Device-const char* mapName--><!--Device-const char* mapName-End--> |
| const char* functionName | Name of the function corresponding to the current stack frame.<br><!--Device-const char* functionName--><!--Device-const char* functionName-End--> |
| const char* url | URL of the code file corresponding to the current stack frame. It can be used to find the corresponding code file in the local path or on the remote server.<br><!--Device-const char* url--><!--Device-const char* url-End--> |
| const char* packageName | Name of the package to which the code corresponding to the current stack frame belongs.<br><!--Device-const char* packageName--><!--Device-const char* packageName-End--> |


