# JSVM_TypeTag
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou; @string_sz-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

```c
typedef struct {...} JSVM_TypeTag
```

## Overview

Defines the type tag, which is stored as a 128-bit value of two unsigned 64-bit integers. As a UUID, it can tag JavaScript objects to ensure that their types remain unchanged.

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member Variables

| Name| Description  |
|----|------|
| uint64_t lower   | Lower 64 bits.|
| uint64_t upper   | Upper 64 bits.|
