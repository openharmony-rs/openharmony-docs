# JSVM_CodeCache
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=93671cc034f483d1b8e032e6aa319b90dbbd1186 translatedAt=2026-06-18T08:20:47.134Z pushedAt=2026-06-18T09:01:39.267Z -->

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