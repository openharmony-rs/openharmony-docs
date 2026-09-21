# http_interceptor_type.h

## Overview

Defines the data structures for the C APIs of the global HTTP interceptor module, including the interceptor request/response header information, HTTP request/response data packet structure, interceptor configuration information, and related enum types and function pointers.

**Library**: libhttp_interceptor.so

**System capability**: SystemCapability.Communication.NetStack

**Since**: 11

**Related module**: [netstack](capi-netstack.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_Http_Interceptor_Headers](capi-netstack-oh-http-interceptor-headers.md) | OH_Http_Interceptor_Headers | Defines a struct for the request/response header information of the interceptor. |
| [OH_Http_Interceptor_Request](capi-netstack-oh-http-interceptor-request.md) | OH_Http_Interceptor_Request | Defines a struct for the HTTP request data packet of the interceptor. |
| [OH_Http_Interceptor_Response](capi-netstack-oh-http-interceptor-response.md) | OH_Http_Interceptor_Response | Defines a struct for the HTTP response data packet of the interceptor. |
| [OH_Http_Interceptor](capi-netstack-oh-http-interceptor.md) | OH_Http_Interceptor | Defines a struct for the configuration information of the global HTTP interceptor. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_Interceptor_Stage](#oh_interceptor_stage) | OH_Interceptor_Stage | Defines an enum for the interceptor stages. |
| [OH_Interceptor_Type](#oh_interceptor_type) | OH_Interceptor_Type | Defines an enum for the interceptor types. |
| [OH_Interceptor_Result](#oh_interceptor_result) | OH_Interceptor_Result | Defines an enum for the interceptor results. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef OH_Interceptor_Result (\*OH_Http_InterceptorHandler)(OH_Http_Interceptor_Request *request, OH_Http_Interceptor_Response *response, int32_t *isModified)](#oh_http_interceptorhandler) | OH_Http_InterceptorHandler | Defines the HTTP interceptor handler function. |

### Variable

| Name | Description |
| -- | -- |
| OH_Interceptor_Result (*OH_Http_InterceptorHandler)( OH_Http_Interceptor_Request *request, OH_Http_Interceptor_Response *response, int32_t *isModified) | Defines the HTTP interceptor handler function.<br>**Since**: 24 |

## Enum type description

### OH_Interceptor_Stage

```c
enum OH_Interceptor_Stage
```

**Description**

Defines an enum for the interceptor stages.

**System capability**: SystemCapability.Communication.NetStack

**Since**: 24

| Enum item | Description |
| -- | -- |
| OH_STAGE_REQUEST | The interceptor processes the request.<br>**Since**: 24 |
| OH_STAGE_RESPONSE | The interceptor processes the response.<br>**Since**: 24 |

### OH_Interceptor_Type

```c
enum OH_Interceptor_Type
```

**Description**

Defines an enum for the interceptor types.

**System capability**: SystemCapability.Communication.NetStack

**Since**: 24

| Enum item | Description |
| -- | -- |
| OH_TYPE_READ_ONLY | Read-only interceptor.<br>**Since**: 24 |
| OH_TYPE_MODIFY_NETWORK_KIT | interceptor will modify the packet from Network Kit<br>**Since**: 26.0.0 |

### OH_Interceptor_Result

```c
enum OH_Interceptor_Result
```

**Description**

Defines an enum for the interceptor results.

**System capability**: SystemCapability.Communication.NetStack

**Since**: 24

| Enum item | Description |
| -- | -- |
| OH_CONTINUE | The processing continues.<br>**Since**: 24 |
| OH_ABORT | The processing is aborted.<br>**Since**: 24 |


## Function description

### OH_Http_InterceptorHandler()

```c
typedef OH_Interceptor_Result (*OH_Http_InterceptorHandler)(OH_Http_Interceptor_Request *request, OH_Http_Interceptor_Response *response, int32_t *isModified)
```

**Description**

Defines the HTTP interceptor handler function.

**System capability**: SystemCapability.Communication.NetStack

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Http_Interceptor_Request](capi-netstack-oh-http-interceptor-request.md) \*request | Pointer to the HTTP request data packet (valid only in the request stage). |
| [OH_Http_Interceptor_Response](capi-netstack-oh-http-interceptor-response.md) \*response | Pointer to the HTTP response data packet (valid only in the response stage). |
| int32_t \*isModified | Output parameter, which indicates whether the interceptor has modified the data packet. This parameter is invalid for the interceptor of the **OH_TYPE_READ_ONLY** type. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_Interceptor_Result](capi-http-interceptor-type-h.md#oh_interceptor_result) | Interceptor processing result. - OH_CONTINUE: The processing continues. - OH_ABORT: The processing      is aborted. |


