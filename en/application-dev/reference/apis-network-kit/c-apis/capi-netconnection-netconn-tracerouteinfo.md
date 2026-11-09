# NetConn_TraceRouteInfo

```c
struct NetConn_TraceRouteInfo {...}
```

## Overview

Defines the trace route information.

<!--Device-struct NetConn_TraceRouteInfo {...}--><!--Device-struct NetConn_TraceRouteInfo {...}-End-->

**System capability**: SystemCapability.Communication.NetManager.Core

**Since**: 20

**Related module**: [NetConnection](capi-network-kit-netconnection.md)

**Header file**: [net_connection_type.h](capi-net-connection-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t jumpNo | Number of hops. |
| char address[NETCONN_MAX_STR_LEN] | Host name or address. |
| uint32_t rtt[NETCONN_MAX_RTT_NUM] | Round-trip time in ms, including the maximum, minimum, average, and standard deviations. |


