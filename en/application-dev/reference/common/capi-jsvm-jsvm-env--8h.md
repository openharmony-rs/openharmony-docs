# JSVM_Env__*

<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=21434ce8d323ecbd7d67463989a2ef075be92cec translatedAt=2026-08-27T03:48:08.033Z pushedAt=2026-08-27T06:35:23.809Z -->

```c
typedef struct JSVM_Env__* JSVM_Env
```

## Overview

Defines the context of a specific VM state. It needs to be passed as a parameter when the native function is called and passed to any subsequent JSVM-API nested call.

**Usage scenario**: Used to save and pass the VM state when JSVM-API is called in a Native module, and to distinguish different VM environment instances in a multi-instance environment.

**Features**: Provides state isolation at the VM instance level and supports state passing across function calls.

**Problem solved**: Solves the state management problem when Native code interacts with the JavaScript engine, and supports state isolation among multiple VM instances.

**System capability:** SystemCapability.ArkCompiler.JSVM

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)