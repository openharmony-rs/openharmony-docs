# JSVM_EscapableHandleScope__*

<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=93671cc034f483d1b8e032e6aa319b90dbbd1186 translatedAt=2026-06-18T08:21:30.951Z pushedAt=2026-06-22T03:21:12.872Z -->

```c
typedef struct JSVM_EscapableHandleScope__* JSVM_EscapableHandleScope
```

## Overview

Defines a special type of handle scope, which is used to return the value created in a specific handle scope to the parent scope.

**Usage scenario:** Creating JS objects in child functions and returning them to parent functions or outer scopes; passing locally created JS values beyond the current scope in JSVM API development.

**System capability:** SystemCapability.ArkCompiler.JSVM

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)