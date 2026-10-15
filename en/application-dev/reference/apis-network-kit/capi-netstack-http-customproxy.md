# Http_CustomProxy
<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=742fd8e7f742ee980eb300ddfd075065ca362dff translatedAt=2026-09-28T01:12:10.750Z pushedAt=2026-10-09T01:40:08.459Z -->

```c
typedef struct Http_CustomProxy {...} Http_CustomProxy
```

## Overview

Defines the custom proxy configuration.

**Since**: 20

**Related module**: [netstack](capi-netstack.md)

**Header file**: [net_http_type.h](capi-net-http-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| const char *host | Hostname of the proxy server. If no port is explicitly set, the port defaults to 1080. |
| int32_t port | Host port. The value range is [0, 65535].|
| const char *exclusionLists | List of the names of hosts that do not use the HTTP proxy server. The host name can be a domain name, IP address, or wildcard.|


