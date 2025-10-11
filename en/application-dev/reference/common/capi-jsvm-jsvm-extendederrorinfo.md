# JSVM_ExtendedErrorInfo
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou; @string_sz-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

## Overview

Extended error information.

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| const char* errorMessage | UTF-8-encoded string, which contains exception information.|
| void* engineReserved | Detailed error message specific to a VM. This function is not implemented for any VM yet.|
| uint32_t engineErrorCode | Error code specific to a VM. This function is not implemented for any VM yet.|
| JSVM_Status errorCode | JSVM-API status code derived from the last error.|
