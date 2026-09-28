# JSVM_TypeTag

<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=21434ce8d323ecbd7d67463989a2ef075be92cec translatedAt=2026-08-27T03:49:31.841Z pushedAt=2026-08-27T06:46:32.263Z -->

```c
typedef struct {...} JSVM_TypeTag
```

## Overview

Defines the type tag, which is stored as a 128-bit value of two unsigned 64-bit integers. As a UUID, it can tag JavaScript objects to ensure that their types remain unchanged.

**Use scenario**: Used to tag and identify the type of JavaScript objects in cross-language interaction scenarios, such as C/C++ and JavaScript interaction.

**Features**: Provides a 128-bit unique identifier composed of two 64-bit integers, ensuring the uniqueness and accuracy of the identifier. It can be attached to JavaScript objects to implement type tagging and verification.

**Problem solved**: Solves the type identification problem of JavaScript objects in cross-language interaction. Prevents object type confusion or misidentification.

**Benefits**: Ensures that the type of JavaScript objects remains consistent, improving the type safety of cross-language interaction.

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