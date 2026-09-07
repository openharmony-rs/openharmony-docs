# JSVM_EnvScope__*

<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=21434ce8d323ecbd7d67463989a2ef075be92cec translatedAt=2026-08-27T03:48:07.592Z pushedAt=2026-08-27T06:35:49.173Z -->

```c
typedef struct JSVM_EnvScope__* JSVM_EnvScope
```

## Overview

Defines the environment scope of the current VM instance. The environment is available to the VM instance of the thread only after the thread enters **JSVM_EnvScope** of the environment through **OH_JSVM_OpenEnvScope**.

**Use scenario**: Used to manage and switch the environment scope when the JavaScript environment needs to be accessed and operated in a multi-threaded environment.

**Problem solved**: Solves the problem of environment access and isolation for the same VM instance in a multi-threaded environment.

**Benefit**: Provides developers with a thread-safe environment management mechanism, ensuring the correctness and isolation of multi-threaded access.

**System capability:** SystemCapability.ArkCompiler.JSVM

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)