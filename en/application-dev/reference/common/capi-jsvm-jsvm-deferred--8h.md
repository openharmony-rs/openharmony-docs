# JSVM_Deferred__*

<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=93671cc034f483d1b8e032e6aa319b90dbbd1186 translatedAt=2026-06-18T08:21:10.360Z pushedAt=2026-06-22T03:21:12.865Z -->

```c
typedef struct JSVM_Deferred__* JSVM_Deferred
```

## Overview

Defines the deferred object.

**Use scenario:** Creating Promise objects in JSVM native modules to defer handling asynchronous operation results; manually controlling over Promise resolve/reject timing in the native layer; encapsulating native layer asynchronous operation results as Promises to return to the JavaScript layer.

**System capability:** SystemCapability.ArkCompiler.JSVM

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)