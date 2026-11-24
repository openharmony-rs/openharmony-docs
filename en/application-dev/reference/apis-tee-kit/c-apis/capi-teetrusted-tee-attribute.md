# TEE_Attribute

```c
typedef struct TEE_Attribute {...} TEE_Attribute
```

## Overview

Defines an object attribute.

<!--Device-typedef struct TEE_Attribute {...} TEE_Attribute--><!--Device-typedef struct TEE_Attribute {...} TEE_Attribute-End-->

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeTrusted](capi-tee-kit-teetrusted.md)

**Header file**: [tee_defines.h](capi-tee-defines-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t attributeID | Attribute ID.<br><!--Device-uint32_t attributeID--><!--Device-uint32_t attributeID-End--> |
| content.ref.buffer | Buffer pointer.<br><!--Device-content.ref.buffer--><!--Device-content.ref.buffer-End--> |
| content.ref.length | Length of the buffer.<br><!--Device-content.ref.length--><!--Device-content.ref.length-End--> |
| content.value.a | First value.<br><!--Device-content.value.a--><!--Device-content.value.a-End--> |
| content.value.b | Second value.<br><!--Device-content.value.b--><!--Device-content.value.b-End--> |


