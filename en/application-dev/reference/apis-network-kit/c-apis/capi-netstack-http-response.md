# Http_Response

```c
typedef struct Http_Response {...} Http_Response
```

## Overview

Defines the structure of HTTP responses.

<!--Device-struct Http_Response {...}--><!--Device-struct Http_Response {...}-End-->

**System capability**: SystemCapability.Communication.NetStack

**Since**: 20

**Related module**: [netstack](capi-network-kit-netstack.md)

**Header file**: [net_http_type.h](capi-net-http-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [Http_Buffer](capi-netstack-http-buffer.md) body | HTTP response data. For details, see [Http_Buffer](capi-netstack-http-buffer.md).<br><!--Device-Http_Buffer body--><!--Device-Http_Buffer body-End--> |
| [Http_ResponseCode](capi-net-http-type-h.md#http_responsecode) responseCode | HTTP response code. For details, see [Http_ResponseCode](capi-net-http-type-h.md#http_responsecode).<br><!--Device-Http_ResponseCode responseCode--><!--Device-Http_ResponseCode responseCode-End--> |
| [Http_Headers](capi-netstack-http-headers.md) *headers | Pointer to the HTTP response header. For details, see [Http_Headers](capi-netstack-http-headers.md).<br><!--Device-Http_Headers *headers--><!--Device-Http_Headers *headers-End--> |
| char *cookies | Pointer to the HTTP response cookies.<br><!--Device-char *cookies--><!--Device-char *cookies-End--> |
| [Http_PerformanceTiming](capi-netstack-http-performancetiming.md) *performanceTiming | Pointer to the HTTP response timing. For details, see [Http_PerformanceTiming](capi-netstack-http-performancetiming.md).<br><!--Device-Http_PerformanceTiming *performanceTiming--><!--Device-Http_PerformanceTiming *performanceTiming-End--> |


### Member functions

| Name | Complete quotation | Description |
| -- | -- | -- |
| [void (\*destroyResponse)(struct Http_Response **response)](#destroyresponse) | destroyResponse | Callback function for destroying an HTTP response. |

## Member function description

### destroyResponse()

```c
void (*destroyResponse)(struct Http_Response **response)
```

**Description**

Callback function for destroying an HTTP response.

<!--Device-void (*destroyResponse)(struct Http_Response **response)--><!--Device-void (*destroyResponse)(struct Http_Response **response)-End-->

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| struct [Http_Response](capi-netstack-http-response.md) **response | Pointer to the HTTP response to be destroyed. For details, see [Http_Response](capi-netstack-http-response.md). |


