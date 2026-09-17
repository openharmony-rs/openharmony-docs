# JSVM_ScriptOrigin

<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=21434ce8d323ecbd7d67463989a2ef075be92cec translatedAt=2026-08-27T03:49:26.616Z pushedAt=2026-08-27T06:46:16.573Z -->

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