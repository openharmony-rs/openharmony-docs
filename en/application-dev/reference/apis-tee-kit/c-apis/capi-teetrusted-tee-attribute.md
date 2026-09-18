# TEE_Attribute

```c
typedef struct TEE_Attribute {...} TEE_Attribute
```

## Overview

Defines an object attribute.

**Since**: 20

**Related module**: [TeeTrusted](capi-teetrusted.md)

**Header file**: [tee_defines.h](capi-tee-defines-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t attributeID | Attribute ID. |
| union | Attribute content.<br>**Since**: 20 |
| struct | Reference type content.<br>**Since**: 20 |
| void *buffer | Buffer pointer. |
| size_t length;
 } ref | Length of the buffer. |
| struct | Value type content.<br>**Since**: 20 |
| uint32_t a | First value. |
| uint32_t b;
 } value;
 } content | Second value. |


