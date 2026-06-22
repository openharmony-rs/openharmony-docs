# JSVM_EnvScope__*

<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=93671cc034f483d1b8e032e6aa319b90dbbd1186 translatedAt=2026-06-18T08:21:28.447Z pushedAt=2026-06-22T03:21:12.870Z -->

```c
typedef struct JSVM_EnvScope__* JSVM_EnvScope
```

## Overview

Defines the environment scope of the current VM instance. The environment is available to the VM instance of the thread only after the thread enters **JSVM_EnvScope** of the environment through **OH_JSVM_OpenEnvScope**.

**Use scenario:** Managing and switching environment scopes when accessing and operating JavaScript environments in multi-threaded scenarios.

**Problem solved:** Environment access and isolation for the same VM instance in multi-threaded scenarios.

**Benefits:** A thread-safe environment management mechanism is provided, ensuring correctness and isolation in multi-threaded access.

**System capability:** SystemCapability.ArkCompiler.JSVM

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)