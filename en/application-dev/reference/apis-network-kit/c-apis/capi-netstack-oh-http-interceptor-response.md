# OH_Http_Interceptor_Response

```c
struct OH_Http_Interceptor_Response {...}
```

## Overview

Defines a struct for the HTTP response data packet of the interceptor.

**System capability**: SystemCapability.Communication.NetStack

**Since**: 24

**Related module**: [netstack](capi-netstack.md)

**Header file**: [http_interceptor_type.h](capi-http-interceptor-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [Http_Buffer](capi-netstack-http-buffer.md) body | Response body. For details, see [Http_Buffer](capi-netstack-http-buffer.md).<br>**Since**: 24 |
| [Http_ResponseCode](capi-net-http-type-h.md#http_responsecode) responseCode | Response status code. For details, see [Http_ResponseCode](capi-net-http-type-h.md#http_responsecode).<br>**Since**: 24 |
| OH_Http_Interceptor_Headers *headers | HTTP response header. For details, see [OH_Http_Interceptor_Headers](capi-netstack-oh-http-interceptor-headers.md).<br>**Since**: 24 |
| [Http_PerformanceTiming](capi-netstack-http-performancetiming.md) performanceTiming | Response performance information. For details, see [Http_PerformanceTiming](capi-netstack-http-performancetiming.md).<br>**Since**: 24 |


