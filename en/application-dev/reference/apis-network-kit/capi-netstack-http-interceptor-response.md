# OH_Http_Interceptor_Response
<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
```c
typedef struct OH_Http_Interceptor_Response {
    Http_Buffer body;
    Http_ResponseCode responseCode;
    OH_Http_Interceptor_Headers *headers;
    Http_PerformanceTiming performanceTiming;
} OH_Http_Interceptor_Response;
```

## Overview

Defines a struct for the HTTP response data packet of the interceptor.

**Since**: 24

**Related module**: [netstack](capi-netstack.md)

**Header file**: [http_interceptor_type.h](capi-net-http-interceptor-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| Http_Buffer body | Response body. For details, see [Http_Buffer](capi-netstack-http-buffer.md).|
| Http_ResponseCode responseCode | Response status code. For details, see [Http_ResponseCode](capi-net-http-type-h.md#http_responsecode).|
| OH_Http_Interceptor_Headers *headers | HTTP response header. For details, see [OH_Http_Interceptor_Headers](capi-netstack-http-interceptor-headers.md).|
| Http_PerformanceTiming performanceTiming | Response performance information. For details, see [Http_PerformanceTiming](capi-netstack-http-performancetiming.md).|
