# OH_Http_Interceptor_Request

```c
typedef struct OH_Http_Interceptor_Request {...} OH_Http_Interceptor_Request
```

## Overview

Defines a struct for the HTTP request data packet of the interceptor.

**Since**: 24

**Related module**: [netstack](capi-netstack.md)

**Header file**: [http_interceptor_type.h](capi-http-interceptor-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| Http_Buffer url | Request URL. For details, see {@link Http_Buffer}.<br>**Since**: 24 |
| Http_Buffer method | Request method. For details, see {@link Http_Buffer}.<br>**Since**: 24 |
| [OH_Http_Interceptor_Headers](capi-netstack-oh-http-interceptor-headers.md) *headers | HTTP request header. For details, see [OH_Http_Interceptor_Headers](capi-netstack-oh-http-interceptor-headers.md).<br>**Since**: 24 |
| Http_Buffer body | Request body. For details, see {@link Http_Buffer}.<br>**Since**: 24 |


