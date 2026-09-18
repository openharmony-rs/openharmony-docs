# Http_CustomProxy

```c
typedef struct Http_CustomProxy {...} Http_CustomProxy
```

## Overview

Defines the custom proxy configuration.

**Since**: 20

**Related module**: [netstack](capi-netstack.md)

**Header file**: [net_http_type.h](capi-net-http-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const char *host;
 int32_t port;
 const char *exclusionLists | Host name of the proxy server. If no port is explicitly set, the port number is defaulted to **1080**. |


