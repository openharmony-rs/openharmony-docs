# OH_Http_Interceptor_Headers

```c
typedef struct OH_Http_Interceptor_Headers {...} OH_Http_Interceptor_Headers
```

## Overview

Defines a struct for the request/response header information of the interceptor.

**Since**: 24

**Related module**: [netstack](capi-netstack.md)

**Header file**: [http_interceptor_type.h](capi-http-interceptor-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char *data | Pointer to the request/response header information of the interceptor.<br>**Since**: 24 |
| struct [OH_Http_Interceptor_Headers](capi-netstack-oh-http-interceptor-headers.md) *next | Pointer to the next header information.<br>**Since**: 24 |


