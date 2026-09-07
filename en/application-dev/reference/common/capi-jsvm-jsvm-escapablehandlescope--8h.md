# JSVM_EscapableHandleScope__*

<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=21434ce8d323ecbd7d67463989a2ef075be92cec translatedAt=2026-08-27T03:48:09.850Z pushedAt=2026-08-27T06:36:19.359Z -->

```c
typedef struct JSVM_EscapableHandleScope__* JSVM_EscapableHandleScope
```

## Overview

Defines a special type of handle scope, which is used to return the value created in a specific handle scope to the parent scope.

**Usage scenario**: Used when a JS object needs to be created in a child function and returned to the parent function or a higher-level scope. In JSVM API development, it is used in scenarios where a locally created JS value needs to be passed out of the current scope.

**System capability:** SystemCapability.ArkCompiler.JSVM

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)