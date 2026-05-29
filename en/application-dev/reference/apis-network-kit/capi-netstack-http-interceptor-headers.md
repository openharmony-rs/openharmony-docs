# OH_Http_Interceptor_Headers
<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
```c
typedef struct OH_Http_Interceptor_Headers {
    char *data;
    struct OH_Http_Interceptor_Headers *next;
} OH_Http_Interceptor_Headers;
```

## Overview

Defines a struct for the request/response header information of the interceptor.

**Since**: 24

**Related module**: [netstack](capi-netstack.md)

**Header file**: [http_interceptor_type.h](capi-net-http-interceptor-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| char *data | Pointer to the request/response header information of the interceptor.|
| struct OH_Http_Interceptor_Headers *next | Pointer to the next header information.|
