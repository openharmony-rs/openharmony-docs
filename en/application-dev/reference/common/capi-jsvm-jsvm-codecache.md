# JSVM_CodeCache

<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=21434ce8d323ecbd7d67463989a2ef075be92cec translatedAt=2026-08-27T03:46:30.318Z pushedAt=2026-08-27T06:24:19.311Z -->

```c
typedef struct {...} JSVM_CodeCache
```

## Overview

Defines a struct that represents the code cache when **id** is **JSVM_COMPILE_CODE_CACHE**.

**System capability:** SystemCapability.ArkCompiler.JSVM

**Since**: 12

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member Variables

| Name             | Description         |
|------------------|---------------|
| uint8_t* cache   | Cache address.    |
| size_t length    | Cache size.    |