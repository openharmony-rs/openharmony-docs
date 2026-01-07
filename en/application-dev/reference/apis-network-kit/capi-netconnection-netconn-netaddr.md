# NetConn_NetAddr

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

```c
typedef struct NetConn_NetAddr {...} NetConn_NetAddr
```

## Overview

Defines network addresses.

**Since**: 11

**Related module**: [NetConnection](capi-netconnection.md)

**Header file**: [net_connection_type.h](capi-net-connection-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint8_t family | Network address family.|
| uint8_t prefixlen | Prefix length.|
| uint8_t port | Port number.|
| char address[[NETCONN_MAX_STR_LEN]](capi-net-connection-type-h.md#macros)| Network address.|
