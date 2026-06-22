# JSVM_CompileProfile

<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=93671cc034f483d1b8e032e6aa319b90dbbd1186 translatedAt=2026-06-18T08:21:05.361Z pushedAt=2026-06-22T03:21:12.861Z -->

```c
typedef const struct {...} JSVM_CompileProfile
```

## Overview

Defines the compilation sampling file transferred together with **JSVM_COMPILE_COMPILE_PROFILE**.

**Use scenario:** Pre-compilation optimization during the secondary startup of an application, which can improve application startup speed and runtime performance; application scenarios that require startup performance optimization.

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