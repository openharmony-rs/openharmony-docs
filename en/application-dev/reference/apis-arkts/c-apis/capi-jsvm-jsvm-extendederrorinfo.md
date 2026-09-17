# JSVM_ExtendedErrorInfo

```c
typedef struct JSVM_ExtendedErrorInfo {...} JSVM_ExtendedErrorInfo
```

## Overview

JSVM-API uses both return values and JavaScript exceptions for error handling

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const char* errorMessage | UTF8-encoded string containing a VM-neutral description of the error. |
| void* engineReserved | Reserved for VM-specific error details. This is currently not implemented for any VM. |
| uint32_t engineErrorCode | VM-specific error code. This is currently not implemented for any VM. |
| [JSVM_Status](capi-jsvm-types-h.md#jsvm_status) errorCode | The JSVM-API status code that originated with the last error. |


