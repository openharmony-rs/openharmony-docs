# JSVM_VMInfo

<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=21434ce8d323ecbd7d67463989a2ef075be92cec translatedAt=2026-08-27T03:49:48.130Z pushedAt=2026-08-27T06:46:54.385Z -->

```c
typedef struct {...} JSVM_VMInfo
```

## Overview

Defines the JavaScript VM information.

**System capability:** SystemCapability.ArkCompiler.JSVM

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t apiVersion | The latest API version supported by the VM.|
| const char* engine | Name of the engine that implements the VM.|
| const char* version | VM version.|
| uint32_t cachedDataVersionTag | Cache data version tag.|