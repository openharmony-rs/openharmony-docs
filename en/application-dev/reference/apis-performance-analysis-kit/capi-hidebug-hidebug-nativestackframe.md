# HiDebug_NativeStackFrame

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @hello_harmony; @yu_haoqiaida-->
<!--Designer: @kutcherzhou1-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

## Overview

Defines the native stack frame content.

**Since**: 20

**Related module**: [HiDebug](capi-hidebug.md)

**Header file**: [hidebug_type.h](capi-hidebug-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint64_t relativePc |  Offset of the current PC address from the start address of the mapping area (for example, an executable file or shared library) where the PC address is located.|
| uint64_t funcOffset |  Offset of the function corresponding to the current stack frame in the mapping area (for example, an executable file or shared library) where the function is located.|
| const char* mapName |  Name of the mapping area to which the current stack frame belongs.|
| const char* functionName |  Name of the function corresponding to the current stack frame.|
| const char* buildId |  Unique identifier related to the current mapping area (for example, an executable file or shared library). During debugging and symbol parsing, **buildId** ensures that the symbol file version matches the actual binary file version.|
| const char* reserved |  Reserved field for future extension.|
