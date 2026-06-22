# JSVM_ScriptOrigin
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=93671cc034f483d1b8e032e6aa319b90dbbd1186 translatedAt=2026-06-18T08:22:19.738Z pushedAt=2026-06-22T03:21:12.886Z -->

```c
typedef struct {...} JSVM_ScriptOrigin
```

## Overview

Defines the original information about a JavaScript code segment, such as the source map path, source file name, and start line/column number in the source file.

**System capability:** SystemCapability.ArkCompiler.JSVM

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