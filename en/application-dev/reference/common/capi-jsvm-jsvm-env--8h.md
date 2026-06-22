# JSVM_Env__*

<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=93671cc034f483d1b8e032e6aa319b90dbbd1186 translatedAt=2026-06-18T08:21:27.616Z pushedAt=2026-06-22T03:21:12.869Z -->

```c
typedef struct JSVM_Env__* JSVM_Env
```

## Overview

Defines the context of a specific VM state. It needs to be passed as a parameter when the native function is called and passed to any subsequent JSVM-API nested call.

**Usage scenario:** Saving and passing virtual machine states when JSVM-API is called in a native module; distinguishing between different VM environment instances in a multi-instance environment.

**Features:** State isolation at the VM instance level and state passing across function calls.

**Problem solved:** State management issue when native code interacts with the JavaScript engine; supporting state isolation among multiple VM instances.

**System capability:** SystemCapability.ArkCompiler.JSVM

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)