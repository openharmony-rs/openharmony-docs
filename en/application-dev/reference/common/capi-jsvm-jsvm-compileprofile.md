# JSVM_CompileProfile
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou; @string_sz-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

```c
typedef const struct {...} JSVM_CompileProfile
```

## Overview

Defines the compilation sampling file transferred together with **JSVM_COMPILE_COMPILE_PROFILE**.

**Since**: 12

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int *profile | Pointer to the compilation sampling file.|
| size_t length | Size of the compilation sampling file.|
