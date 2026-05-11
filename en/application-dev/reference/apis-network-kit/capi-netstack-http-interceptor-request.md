# OH_Http_Interceptor_Request
<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
```c
typedef struct OH_Http_Interceptor_Request {
    Http_Buffer url;
    Http_Buffer method;
    OH_Http_Interceptor_Headers *headers;
    Http_Buffer body;
} OH_Http_Interceptor_Request;
```

## Overview

Defines a struct for the HTTP request data packet of the interceptor.

**Since**: 24

**Related module**: [netstack](capi-netstack.md)

**Header file**: [http_interceptor_type.h](capi-net-http-interceptor-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| Http_Buffer url | Request URL. For details, see [Http_Buffer](capi-netstack-http-buffer.md).|
| Http_Buffer method | Request method. For details, see [Http_Buffer](capi-netstack-http-buffer.md).|
| OH_Http_Interceptor_Headers *headers | HTTP request header. For details, see [OH_Http_Interceptor_Headers](capi-netstack-http-interceptor-headers.md).|
| Http_Buffer body | Request body. For details, see [Http_Buffer](capi-netstack-http-buffer.md).|
