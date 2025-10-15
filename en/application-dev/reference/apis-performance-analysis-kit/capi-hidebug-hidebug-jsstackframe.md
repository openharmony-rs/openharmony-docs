# HiDebug_JsStackFrame

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @hello_harmony; @yu_haoqiaida-->
<!--Designer: @kutcherzhou1-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

## Overview

Defines the JS stack frame content.

**Since**: 20

**Related module**: [HiDebug](capi-hidebug.md)

**Header file**: [hidebug_type.h](capi-hidebug-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint64_t relativePc | Relative PC address. Offset of the current PC address to the start address of the mapping area (for example, an executable file or shared library) to which the PC address belongs.|
| int32_t line |  Line number of the code corresponding to the current stack frame in the file.|
| int32_t column |  Column number of the code corresponding to the current stack frame in the specified line.|
| const char* mapName |  Name of the mapping area to which the current stack frame belongs.|
| const char* functionName |  Name of the function corresponding to the current stack frame.|
| const char* url |  URL of the file of the code corresponding to the current stack frame. The code file can be found through the URL, regardless of whether the file is a local file or a file on a remote server.|
| const char* packageName |  Name of the package to which the code corresponding to the current stack frame belongs.|
