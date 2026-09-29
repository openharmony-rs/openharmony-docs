# OH_Http_Interceptor_Request

```c
struct OH_Http_Interceptor_Request {...}
```

## Overview

Defines a struct for the HTTP request data packet of the interceptor.

**System capability**: SystemCapability.Communication.NetStack

**Since**: 24

**Related module**: [netstack](capi-netstack.md)

**Header file**: [http_interceptor_type.h](capi-http-interceptor-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [Http_Buffer](capi-netstack-http-buffer.md) url | Request URL. For details, see [Http_Buffer](capi-netstack-http-buffer.md).<br>**Since**: 24 |
| [Http_Buffer](capi-netstack-http-buffer.md) method | Request method. For details, see [Http_Buffer](capi-netstack-http-buffer.md).<br>**Since**: 24 |
| OH_Http_Interceptor_Headers *headers | HTTP request header. For details, see [OH_Http_Interceptor_Headers](capi-netstack-oh-http-interceptor-headers.md).<br>**Since**: 24 |
| [Http_Buffer](capi-netstack-http-buffer.md) body | Request body. For details, see [Http_Buffer](capi-netstack-http-buffer.md).<br>**Since**: 24 |


