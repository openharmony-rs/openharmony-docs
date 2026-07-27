# OH_Http_Interceptor
<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
```c
typedef struct OH_Http_Interceptor {
    int32_t groupId;
    OH_Interceptor_Stage stage;
    OH_Interceptor_Type type;
    OH_Http_InterceptorHandler handler;
    int32_t enabled;
} OH_Http_Interceptor;
```

## Overview

Defines a struct for the configuration information of the global HTTP interceptor.

**Since**: 24

**Related module**: [netstack](capi-netstack.md)

**Header file**: [http_interceptor_type.h](capi-net-http-interceptor-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int32_t groupId | Interceptor group ID.|
| OH_Interceptor_Stage stage | Execution stage of the interceptor. For details, see [OH_Interceptor_Stage](capi-net-http-interceptor-type-h.md#oh_interceptor_stage).|
| OH_Interceptor_Type type | Interceptor type. For details, see [OH_Interceptor_Type](capi-net-http-interceptor-type-h.md#oh_interceptor_type).|
| OH_Http_InterceptorHandler handler | Interceptor handler. For details, see [OH_Http_InterceptorHandler](capi-net-http-interceptor-type-h.md#oh_http_interceptorhandler).|
| int32_t enabled | Enabling status of the interceptor. The value **0** indicates that the interceptor is disabled, and a non-zero value indicates the opposite.|
