# JSVM_ScriptOrigin
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou; @string_sz-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

```c
typedef struct {...} JSVM_ScriptOrigin
```

## Overview

Defines the original information about a JavaScript code segment, such as the source map path, source file name, and start line/column number in the source file.

**Since**: 12

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| const char* sourceMapUrl | Source map path.|
| const char* resourceName | Source file name.|
| size_t resourceLineOffset | Start line number of the code segment in the source file.|
| size_t resourceColumnOffset | Start column number of the code segment in the source file.|
