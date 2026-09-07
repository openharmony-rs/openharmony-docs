# JSVM_ExtendedErrorInfo

<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=21434ce8d323ecbd7d67463989a2ef075be92cec translatedAt=2026-08-27T03:48:18.496Z pushedAt=2026-08-27T06:36:55.114Z -->

```c
typedef struct {...} JSVM_ExtendedErrorInfo
```

## Overview

Defines extended error information.

**Usage scenario**: Obtains detailed exception information when a JSVM API call fails, for debugging and troubleshooting JavaScript runtime errors, as well as logging and error reporting.

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
| [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) errorCode | JSVM-API status code derived from the last exception. |