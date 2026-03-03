# JSVM_CodeCache
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou; @string_sz-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

```c
typedef struct {...} JSVM_CodeCache
```

## Overview

Defines a struct that represents the code cache when **id** is **JSVM_COMPILE_CODE_CACHE**.

**Since**: 12

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member Variables

| Name             | Description         |
|------------------|---------------|
| uint8_t* cache   | Cache address.    |
| size_t length    | Cache size.    |
