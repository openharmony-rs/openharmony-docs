# Http_Request

```c
typedef struct Http_Request {...} Http_Request
```

## Overview

Defines an HTTP request.

<!--Device-struct Http_Request {...}--><!--Device-struct Http_Request {...}-End-->

**System capability**: SystemCapability.Communication.NetStack

**Since**: 20

**Related module**: [netstack](capi-network-kit-netstack.md)

**Header file**: [net_http_type.h](capi-net-http-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t requestId | ID of an HTTP request.<br><!--Device-uint32_t requestId--><!--Device-uint32_t requestId-End--> |
| char *url | Pointer to the HTTP request URL.<br><!--Device-char *url--><!--Device-char *url-End--> |
| [Http_RequestOptions](capi-netstack-http-requestoptions.md) *options | Pointer to the HTTP request configuration. For details, see [Http_RequestOptions](capi-netstack-http-requestoptions.md).<br><!--Device-Http_RequestOptions *options--><!--Device-Http_RequestOptions *options-End--> |


