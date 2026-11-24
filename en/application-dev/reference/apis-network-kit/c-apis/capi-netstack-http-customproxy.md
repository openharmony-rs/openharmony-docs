# Http_CustomProxy

```c
typedef struct Http_CustomProxy {...} Http_CustomProxy
```

## Overview

Defines the custom proxy configuration.

<!--Device-struct Http_CustomProxy {...}--><!--Device-struct Http_CustomProxy {...}-End-->

**System capability**: SystemCapability.Communication.NetStack

**Since**: 20

**Related module**: [netstack](capi-network-kit-netstack.md)

**Header file**: [net_http_type.h](capi-net-http-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const char *host | Hostname of the proxy server. If no port is explicitly set, the port defaults to 1080.<br><!--Device-const char *host--><!--Device-const char *host-End--> |
| int32_t port | Host port. The value range is [0, 65535].<br><!--Device-int32_t port--><!--Device-int32_t port-End--> |
| const char *exclusionLists | List of the names of hosts that do not use the HTTP proxy server. The host name can be a domain name, IP address, or wildcard.<br><!--Device-const char *exclusionLists--><!--Device-const char *exclusionLists-End--> |


