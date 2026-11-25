# NetConn_Route

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=4e51b85a4547edffa9339ec0d60d3cf87f258a4a translatedAt=2026-09-23T01:28:56.366Z pushedAt=2026-09-24T06:00:14.115Z -->

```c
typedef struct NetConn_Route {...} NetConn_Route
```

## Overview

Defines the route configuration.

**Since**: 11

**Related module**: [NetConnection](capi-netconnection.md)

**Header file**: [net_connection_type.h](capi-net-connection-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| char iface[[NETCONN_MAX_STR_LEN](capi-net-connection-type-h.md#macros)] | Network interface. |
| [NetConn_NetAddr](capi-netconnection-netconn-netaddr.md) destination | Destination address. |
| [NetConn_NetAddr](capi-netconnection-netconn-netaddr.md) gateway | Gateway address. |
| int32_t hasGateway | Whether a gateway exists. |
| int32_t isDefaultRoute | Whether it is the default route. |


