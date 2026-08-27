# JSVM_CompileProfile

<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=21434ce8d323ecbd7d67463989a2ef075be92cec translatedAt=2026-08-27T03:47:21.467Z pushedAt=2026-08-27T06:26:02.619Z -->

```c
typedef const struct {...} JSVM_CompileProfile
```

## Overview

Defines the compilation sampling file transferred together with **JSVM_COMPILE_COMPILE_PROFILE**.

**Use scenario**: Used for pre-compilation optimization during the second launch of an app to improve app startup speed and runtime performance. It applies to app scenarios that require startup performance optimization.

**System capability:** SystemCapability.ArkCompiler.JSVM

**Since**: 12

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int *profile | Pointer to the compilation sampling file.|
| size_t length | Size of the compilation sampling file.|