# http_interceptor_type.h
<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

## Overview

Defines the data structures for the C APIs of the global HTTP interceptor module, including the interceptor request/response header information, HTTP request/response data packet structure, interceptor configuration information, and related enum types and function pointers.

**Header file**: <network/netstack/http_interceptor_type.h>

**Library**: libhttp_interceptor.so

**System capability**: SystemCapability.Communication.NetStack

**Since**: 24

**Related module**: [netstack](capi-netstack.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_Http_Interceptor_Headers](capi-netstack-http-interceptor-headers.md) | OH_Http_Interceptor_Headers | Defines a struct for the request/response header information of the interceptor.|
| [OH_Http_Interceptor_Request](capi-netstack-http-interceptor-request.md) | OH_Http_Interceptor_Request | Defines a struct for the HTTP request data packet of the interceptor.|
| [OH_Http_Interceptor_Response](capi-netstack-http-interceptor-response.md) | OH_Http_Interceptor_Response | Defines a struct for the HTTP response data packet of the interceptor.|
| [OH_Http_Interceptor](capi-netstack-http-interceptor.md) | OH_Http_Interceptor | Defines a struct for the configuration information of the HTTP global interceptor.|

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_Interceptor_Stage](#oh_interceptor_stage) | OH_Interceptor_Stage | Defines an enum for the interceptor stages.|
| [OH_Interceptor_Type](#oh_interceptor_type) | OH_Interceptor_Type | Defines an enum for the interceptor types.|
| [OH_Interceptor_Result](#oh_interceptor_result) | OH_Interceptor_Result | Defines an enum for the interceptor results.|

### Functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [typedef OH_Interceptor_Result (*OH_Http_InterceptorHandler)(OH_Http_Interceptor_Request *request, OH_Http_Interceptor_Response *response, int32_t *isModified)](#oh_http_interceptorhandler) | OH_Http_InterceptorHandler | Pointer to the HTTP interceptor handler.|

## Enum Description

### OH_Interceptor_Stage

```c
enum OH_Interceptor_Stage
```

**Description**

Defines an enum for the interceptor stages.

**Since**: 24

**Parameters**
| Enum Item| Description|
| -- | -- |
| OH_STAGE_REQUEST | The interceptor processes the request.|
| OH_STAGE_RESPONSE | The interceptor processes the response.|

### OH_Interceptor_Type

```c
enum OH_Interceptor_Type
```

**Description**

Defines an enum for the interceptor types.

**Since**: 24

**Parameters**
| Enum Item| Description|
| -- | -- |
| OH_TYPE_READ_ONLY | Read-only interceptor.|

### OH_Interceptor_Result

```c
enum OH_Interceptor_Result
```

**Description**

Defines an enum for the interceptor results.

**Since**: 24

**Parameters**
| Enum Item| Description|
| -- | -- |
| OH_CONTINUE | The processing continues.|
| OH_ABORT | The processing is aborted.|

## Function Description

### OH_Http_InterceptorHandler()

```c
typedef OH_Interceptor_Result (*OH_Http_InterceptorHandler)(
    OH_Http_Interceptor_Request *request,
    OH_Http_Interceptor_Response *response,
    int32_t *isModified)
```

**Description**

Defines the HTTP interceptor handler function.

**Since**: 24

**Parameters**
| Name| Description|
| -- | -- |
| [OH_Http_Interceptor_Request](capi-netstack-http-interceptor-request.md) *request| Pointer to the HTTP request data packet (valid only in the request stage).|
| [OH_Http_Interceptor_Response](capi-netstack-http-interceptor-response.md) *response| Pointer to the HTTP response data packet (valid only in the response stage).|
| int32_t *isModified | Whether the interceptor has modified the data packet. This parameter is invalid for interceptors of the OH_TYPE_READ_ONLY type and can be set to nullptr.<br>- 0: The data is not modified.<br>- A non-zero value: The data is modified.|

**Returns**

| Type                                           | Description                                                        |
| ----------------------------------------------- | ------------------------------------------------------------ |
| [OH_Interceptor_Result](#oh_interceptor_result) | Interceptor processing result.<br>- OH_CONTINUE: Continue processing.<br>- OH_ABORT: Intercept the processing.|
