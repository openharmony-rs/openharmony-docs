# NetConn_NetCapabilities

```c
typedef struct NetConn_NetCapabilities {...} NetConn_NetCapabilities
```

## Overview

Defines network capability sets.

<!--Device-struct NetConn_NetCapabilities {...}--><!--Device-struct NetConn_NetCapabilities {...}-End-->

**System capability**: SystemCapability.Communication.NetManager.Core

**Since**: 11

**Related module**: [NetConnection](capi-network-kit-netconnection.md)

**Header file**: [net_connection_type.h](capi-net-connection-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t linkUpBandwidthKbps | Uplink bandwidth. |
| uint32_t linkDownBandwidthKbps | Downlink bandwidth. |
| [NetConn_NetCap](capi-net-connection-type-h.md#netconn_netcap) netCaps[NETCONN_MAX_CAP_SIZE] | Network capability list |
| int32_t netCapsSize | Actual size of the network capability list. |
| [NetConn_NetBearerType](capi-net-connection-type-h.md#netconn_netbearertype) bearerTypes[NETCONN_MAX_BEARER_TYPE_SIZE] | Bearer type list |
| int32_t bearerTypesSize | Actual size of the bearer type list. |


