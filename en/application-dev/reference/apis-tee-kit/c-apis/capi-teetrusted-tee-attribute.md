# TEE_Attribute

```c
typedef struct TEE_Attribute {...} TEE_Attribute
```

## Overview

Defines an object attribute.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeTrusted](capi-others-teetrusted.md)

**Header file**: [tee_defines.h](capi-tee-defines-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t attributeID | Attribute ID. |
| content | Attribute content.<br>**Since**: 20 |
| TEE_Attribute.ref | Reference type content.<br>**Since**: 20 |
| content.ref.buffer | Buffer pointer. |
| content.ref.length | Length of the buffer. |
| TEE_Attribute.value | Value type content.<br>**Since**: 20 |
| content.value.a | First value. |
| content.value.b | Second value. |


