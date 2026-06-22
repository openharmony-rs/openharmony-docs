# JSVM_DeserializeResult

<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou; @string_sz-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=93671cc034f483d1b8e032e6aa319b90dbbd1186 translatedAt=2026-06-18T08:21:23.111Z pushedAt=2026-06-22T03:21:12.867Z -->

```c
typedef struct JSVM_DeserializeResult__* JSVM_DeserializeResult
```

## Overview

Defines a struct for the background deserialization result transferred together with **JSVM_COMPILE_BACKGROUND_DESERIALIZE_RESULT**.

**Usage scenario:** Transferring and storing the background deserialization result data in JSVM background compilation scenarios.

**Features:** A lightweight type definition, used in conjunction with **JSVM_COMPILE_BACKGROUND_DESERIALIZE_RESULT**.

**System capability:** SystemCapability.ArkCompiler.JSVM

**Since**: 24

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)