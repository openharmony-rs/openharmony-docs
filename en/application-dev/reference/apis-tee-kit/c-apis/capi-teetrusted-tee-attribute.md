# TEE_Attribute

```c
typedef union TEE_Attribute {...} TEE_Attribute
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
| [](capi-teetrusted---tee-objecthandle.md)s[](capi-teetrusted---tee-objecthandle.md)t[](capi-teetrusted---tee-objecthandle.md)r[](capi-teetrusted---tee-objecthandle.md)u[](capi-teetrusted---tee-objecthandle.md)c[](capi-teetrusted---tee-objecthandle.md)t[](capi-teetrusted---tee-objecthandle.md) | Reference type content.<br>**Since**: 20 |
| void *buffer | Buffer pointer. |
| size_t length;
 } ref | Length of the buffer. |
| [](capi-teetrusted---tee-objecthandle.md)s[](capi-teetrusted---tee-objecthandle.md)t[](capi-teetrusted---tee-objecthandle.md)r[](capi-teetrusted---tee-objecthandle.md)u[](capi-teetrusted---tee-objecthandle.md)c[](capi-teetrusted---tee-objecthandle.md)t[](capi-teetrusted---tee-objecthandle.md) | Value type content.<br>**Since**: 20 |
| uint32_t a | First value. |
| uint32_t b;
 } value;
 } content | Second value. |


