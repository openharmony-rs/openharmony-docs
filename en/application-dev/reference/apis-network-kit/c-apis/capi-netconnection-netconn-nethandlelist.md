# NetConn_NetHandleList

```c
typedef struct NetConn_NetHandleList {...} NetConn_NetHandleList
```

## Overview

Defines the network list.

<!--Device-struct NetConn_NetHandleList {...}--><!--Device-struct NetConn_NetHandleList {...}-End-->

**System capability**: SystemCapability.Communication.NetManager.Core

**Since**: 11

**Related module**: [NetConnection](capi-network-kit-netconnection.md)

**Header file**: [net_connection_type.h](capi-net-connection-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [NetConn_NetHandle](capi-netconnection-netconn-nethandle.md) netHandles[NETCONN_MAX_NET_SIZE] | Network handle list |
| int32_t netHandleListSize | Actual size of the network handle list. |


