# JSVM_ExtendedErrorInfo

<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=93671cc034f483d1b8e032e6aa319b90dbbd1186 translatedAt=2026-06-18T08:21:43.034Z pushedAt=2026-06-22T03:21:12.873Z -->

```c
typedef struct {...} JSVM_ExtendedErrorInfo
```

## Overview

Defines extended error information.

**Use scenario:** Obtaining detailed exception information when a JSVM API call fails; debugging and troubleshooting JavaScript runtime errors; logging and error reporting.

**System capability:** SystemCapability.ArkCompiler.JSVM

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| const char* errorMessage | UTF-8-encoded string, which contains error messages.|
| void* engineReserved | Detailed error message specific to a VM. This feature is not implemented for any VM yet.|
| uint32_t engineErrorCode | Error code specific to a VM. This feature is not implemented for any VM yet.|
| [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) errorCode | JSVM-API status code from the last exception. |