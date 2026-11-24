# OH_Http_Interceptor_Response

```c
typedef struct OH_Http_Interceptor_Response {...} OH_Http_Interceptor_Response
```

## Overview

Defines a struct for the HTTP response data packet of the interceptor.

<!--Device-struct OH_Http_Interceptor_Response {...}--><!--Device-struct OH_Http_Interceptor_Response {...}-End-->

**System capability**: SystemCapability.Communication.NetStack

**Since**: 24

**Related module**: [netstack](capi-network-kit-netstack.md)

**Header file**: [http_interceptor_type.h](capi-http-interceptor-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [Http_Buffer](capi-netstack-http-buffer.md) body | Response body. For details, see [Http_Buffer](capi-netstack-http-buffer.md).<br>**Since**: 24<br><!--Device-Http_Buffer body--><!--Device-Http_Buffer body-End--> |
| [Http_ResponseCode](capi-net-http-type-h.md#http_responsecode) responseCode | Response status code. For details, see [Http_ResponseCode](capi-net-http-type-h.md#http_responsecode).<br>**Since**: 24<br><!--Device-Http_ResponseCode responseCode--><!--Device-Http_ResponseCode responseCode-End--> |
| [OH_Http_Interceptor_Headers](capi-netstack-oh-http-interceptor-headers.md) *headers | HTTP response header. For details, see [OH_Http_Interceptor_Headers](capi-netstack-oh-http-interceptor-headers.md).<br>**Since**: 24<br><!--Device-OH_Http_Interceptor_Headers *headers--><!--Device-OH_Http_Interceptor_Headers *headers-End--> |
| [Http_PerformanceTiming](capi-netstack-http-performancetiming.md) performanceTiming | Response performance information. For details, see [Http_PerformanceTiming](capi-netstack-http-performancetiming.md).<br>**Since**: 24<br><!--Device-Http_PerformanceTiming performanceTiming--><!--Device-Http_PerformanceTiming performanceTiming-End--> |


