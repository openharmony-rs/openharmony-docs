# JSVM_Ref__*

<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=21434ce8d323ecbd7d67463989a2ef075be92cec translatedAt=2026-08-27T03:49:07.517Z pushedAt=2026-08-27T06:46:01.413Z -->

```c
typedef struct JSVM_Ref__* JSVM_Ref
```

## Overview

Defines the reference to the JavaScript value.

**Use scenario**: Used when a reference to a JavaScript object needs to be held in Native and JavaScript interaction scenarios.

**Features**: Provides a stable reference to a JavaScript value to prevent it from being garbage collected. Supports passing JavaScript values across functions and scopes.

**System capability:** SystemCapability.ArkCompiler.JSVM

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)