# JSVM_ExtendedErrorInfo

```c
typedef struct JSVM_ExtendedErrorInfo {...} JSVM_ExtendedErrorInfo
```

## Overview

JSVM-API uses both return values and JavaScript exceptions for error handling

<!--Device-typedef struct JSVM_ExtendedErrorInfo {...} JSVM_ExtendedErrorInfo--><!--Device-typedef struct JSVM_ExtendedErrorInfo {...} JSVM_ExtendedErrorInfo-End-->

**System capability**: SystemCapability.ArkCompiler.JSVM

**Since**: 11

**Related module**: [JSVM](capi-arkts-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const char* errorMessage | UTF8-encoded string containing a VM-neutral description of the error.<br><!--Device-const char* errorMessage--><!--Device-const char* errorMessage-End--> |
| void* engineReserved | Reserved for VM-specific error details. This is currently not implemented for any VM.<br><!--Device-void* engineReserved--><!--Device-void* engineReserved-End--> |
| uint32_t engineErrorCode | VM-specific error code. This is currently not implemented for any VM.<br><!--Device-uint32_t engineErrorCode--><!--Device-uint32_t engineErrorCode-End--> |
| [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) errorCode | The JSVM-API status code that originated with the last error.<br><!--Device-JSVM_Status errorCode--><!--Device-JSVM_Status errorCode-End--> |


