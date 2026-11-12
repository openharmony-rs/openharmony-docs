# NetConn_NetAddr

```c
typedef struct NetConn_NetAddr {...} NetConn_NetAddr
```

## Overview

Defines network addresses.

<!--Device-struct NetConn_NetAddr {...}--><!--Device-struct NetConn_NetAddr {...}-End-->

**System capability**: SystemCapability.Communication.NetManager.Core

**Since**: 11

**Related module**: [NetConnection](capi-network-kit-netconnection.md)

**Header file**: [net_connection_type.h](capi-net-connection-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t family | Network address family. |
| uint8_t prefixlen | Prefix length. |
| uint8_t port | Port number. |
| char address[NETCONN_MAX_STR_LEN] | Address |


