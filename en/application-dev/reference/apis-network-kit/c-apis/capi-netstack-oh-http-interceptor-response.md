# OH_Http_Interceptor_Response

```c
typedef struct OH_Http_Interceptor_Response {...} OH_Http_Interceptor_Response
```

## Overview

Defines a struct for the HTTP response data packet of the interceptor.

**Since**: 24

**Related module**: [netstack](capi-netstack.md)

**Header file**: [http_interceptor_type.h](capi-http-interceptor-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| Http_Buffer body | Response body. For details, see {@link Http_Buffer}.<br>**Since**: 24 |
| Http_ResponseCode responseCode | Response status code. For details, see {@link Http_ResponseCode}.<br>**Since**: 24 |
| [OH_Http_Interceptor_Headers](capi-netstack-oh-http-interceptor-headers.md) *headers | HTTP response header. For details, see [OH_Http_Interceptor_Headers](capi-netstack-oh-http-interceptor-headers.md).<br>**Since**: 24 |
| Http_PerformanceTiming performanceTiming | Response performance information. For details, see {@link Http_PerformanceTiming}.<br>**Since**: 24 |


