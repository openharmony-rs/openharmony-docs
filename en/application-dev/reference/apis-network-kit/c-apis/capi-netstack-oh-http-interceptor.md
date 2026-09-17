# OH_Http_Interceptor

```c
typedef struct OH_Http_Interceptor {...} OH_Http_Interceptor
```

## Overview

Defines a struct for the configuration information of the global HTTP interceptor.

**Since**: 24

**Related module**: [netstack](capi-netstack.md)

**Header file**: [http_interceptor_type.h](capi-http-interceptor-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t groupId | Interceptor group ID.<br>**Since**: 24 |
| [OH_Interceptor_Stage](capi-http-interceptor-type-h.md#oh_interceptor_stage) stage | Execution stage of the interceptor. For details, see [OH_Interceptor_Stage](capi-http-interceptor-type-h.md#oh_interceptor_stage).<br>**Since**: 24 |
| [OH_Interceptor_Type](capi-http-interceptor-type-h.md#oh_interceptor_type) type | Interceptor type. For details, see [OH_Interceptor_Type](capi-http-interceptor-type-h.md#oh_interceptor_type).<br>**Since**: 24 |
| [OH_Http_InterceptorHandler](capi-http-interceptor-type-h.md#oh_http_interceptorhandler) handler | Interceptor handler. For details, see [OH_Http_InterceptorHandler](capi-http-interceptor-type-h.md#oh_http_interceptorhandler).<br>**Since**: 24 |
| int32_t enabled | Enabling status of the interceptor. The value **0** indicates that the interceptor is disabled, and a non- zero value indicates the opposite.<br>**Since**: 24 |


