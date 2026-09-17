# JSVM_Deferred__*

<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=21434ce8d323ecbd7d67463989a2ef075be92cec translatedAt=2026-08-27T03:47:45.136Z pushedAt=2026-08-27T06:33:45.572Z -->

```c
typedef struct JSVM_Deferred__* JSVM_Deferred
```

## Overview

Defines the deferred object.

**Usage scenario**: When a Promise object needs to be created in a JSVM native module and the result of an asynchronous operation needs to be processed in a deferred manner, this type is used in scenarios where the timing of resolving or rejecting the Promise must be manually controlled on the native layer, so that the result of the asynchronous operation on the native layer is encapsulated as a Promise and returned to the JavaScript layer.

**System capability:** SystemCapability.ArkCompiler.JSVM

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)