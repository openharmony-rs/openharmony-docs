# NetConn_Route

```c
typedef struct NetConn_Route {...} NetConn_Route
```

## Overview

Defines the route configuration.

<!--Device-struct NetConn_Route {...}--><!--Device-struct NetConn_Route {...}-End-->

**System capability**: SystemCapability.Communication.NetManager.Core

**Since**: 11

**Related module**: [NetConnection](capi-network-kit-netconnection.md)

**Header file**: [net_connection_type.h](capi-net-connection-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char iface[NETCONN_MAX_STR_LEN] | Network interface<br><!--Device-char iface[NETCONN_MAX_STR_LEN]--><!--Device-char iface[NETCONN_MAX_STR_LEN]-End--> |
| [NetConn_NetAddr](capi-netconnection-netconn-netaddr.md) destination | Destination address.<br><!--Device-NetConn_NetAddr destination--><!--Device-NetConn_NetAddr destination-End--> |
| [NetConn_NetAddr](capi-netconnection-netconn-netaddr.md) gateway | Gateway IP address.<br><!--Device-NetConn_NetAddr gateway--><!--Device-NetConn_NetAddr gateway-End--> |
| int32_t hasGateway | Whether a gateway exists.<br><!--Device-int32_t hasGateway--><!--Device-int32_t hasGateway-End--> |
| int32_t isDefaultRoute | Whether the default route is used.<br><!--Device-int32_t isDefaultRoute--><!--Device-int32_t isDefaultRoute-End--> |


