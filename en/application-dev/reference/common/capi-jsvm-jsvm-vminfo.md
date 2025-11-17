# JSVM_VMInfo
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou; @string_sz-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

## Overview

Defines the JavaScript VM information.

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t apiVersion | The latest API version supported by the VM.|
| const char* engine | Name of the engine that implements the VM.|
| const char* version | VM version.|
| uint32_t cachedDataVersionTag | Cache data version tag.|
