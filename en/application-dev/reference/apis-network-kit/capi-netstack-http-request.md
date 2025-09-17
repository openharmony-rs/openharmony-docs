# Http_Request
<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
## Overview

Defines an HTTP request.

**Since**: 20

**Related module**: [netstack](capi-netstack.md)

**Header file**: [net_http_type.h](capi-net-http-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t requestId | HTTP request ID.|
| char *url | Pointer to the HTTP request URL.|
| [Http_RequestOptions](capi-netstack-http-requestoptions.md) *options | Pointer to the HTTP request configuration. For details, see [Http_RequestOptions](capi-netstack-http-requestoptions.md).|
