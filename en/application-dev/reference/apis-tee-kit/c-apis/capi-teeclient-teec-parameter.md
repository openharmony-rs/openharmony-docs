# TEEC_Parameter

```c
typedef union TEEC_Parameter {...} TEEC_Parameter
```

## Overview

Defines a parameter of {@code TEEC_Operation}.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeClient](capi-teeclient.md)

**Header file**: [tee_client_type.h](capi-tee-client-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [TEEC_TempMemoryReference](capi-teeclient-teec-tempmemoryreference.md) tmpref | Temporary memory reference. |
| [TEEC_RegisteredMemoryReference](capi-teeclient-teec-registeredmemoryreference.md) memref | Registered memory reference. |
| [TEEC_Value](capi-teeclient-teec-value.md) value | A value containing two 32-bit values. |
| [TEEC_IonReference](capi-teeclient-teec-ionreference.md) ionref | Ion memory reference. |


