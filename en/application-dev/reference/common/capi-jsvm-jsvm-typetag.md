# JSVM_TypeTag

<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=93671cc034f483d1b8e032e6aa319b90dbbd1186 translatedAt=2026-06-18T08:22:25.988Z pushedAt=2026-06-22T03:21:12.887Z -->

```c
typedef struct {...} JSVM_TypeTag
```

## Overview

Defines the type tag, which is stored as a 128-bit value of two unsigned 64-bit integers. As a UUID, it can tag JavaScript objects to ensure that their types remain unchanged.

**Use scenario:** Identifying the type of JavaScript objects in cross-language interaction scenarios, such as C/C++ and JavaScript interaction.

**Features:** A 128-bit unique identifier composed of two 64-bit integers is provided, ensuring uniqueness and accuracy of identification. It can be attached to JavaScript objects to implement type tagging and verification.

**Problem solved:** The type confusion or misidentification problem of JavaScript objects in cross-language interaction.

**Benefits:** Ensuring the type consistency of JavaScript objects and improving type safety in cross-language interaction.

**System capability:** SystemCapability.ArkCompiler.JSVM

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member Variables

| Name| Description  |
|----|------|
| uint64_t lower   | Lower 64 bits.|
| uint64_t upper   | Upper 64 bits.|