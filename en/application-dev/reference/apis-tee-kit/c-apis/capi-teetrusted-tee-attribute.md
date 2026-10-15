# TEE_Attribute

```c
typedef struct TEE_Attribute {...} TEE_Attribute
```

## Overview

Defines an object attribute.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeTrusted](capi-teetrusted.md)

**Header file**: [tee_defines.h](capi-tee-defines-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t attributeID | Attribute ID. |
| content.ref->buffer | Buffer pointer. |
| content.ref.length | Length of the buffer. |
| content.value.a | First value. |
| content.value.b | Second value. |


