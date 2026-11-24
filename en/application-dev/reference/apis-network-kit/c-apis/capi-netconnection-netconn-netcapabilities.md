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
| uint32_t linkUpBandwidthKbps | Uplink bandwidth.<br><!--Device-uint32_t linkUpBandwidthKbps--><!--Device-uint32_t linkUpBandwidthKbps-End--> |
| uint32_t linkDownBandwidthKbps | Downlink bandwidth.<br><!--Device-uint32_t linkDownBandwidthKbps--><!--Device-uint32_t linkDownBandwidthKbps-End--> |
| [NetConn_NetCap](capi-net-connection-type-h.md#netconn_netcap) netCaps[NETCONN_MAX_CAP_SIZE] | Network capability list<br><!--Device-NetConn_NetCap netCaps[NETCONN_MAX_CAP_SIZE]--><!--Device-NetConn_NetCap netCaps[NETCONN_MAX_CAP_SIZE]-End--> |
| int32_t netCapsSize | Actual size of the network capability list.<br><!--Device-int32_t netCapsSize--><!--Device-int32_t netCapsSize-End--> |
| [NetConn_NetBearerType](capi-net-connection-type-h.md#netconn_netbearertype) bearerTypes[NETCONN_MAX_BEARER_TYPE_SIZE] | Bearer type list<br><!--Device-NetConn_NetBearerType bearerTypes[NETCONN_MAX_BEARER_TYPE_SIZE]--><!--Device-NetConn_NetBearerType bearerTypes[NETCONN_MAX_BEARER_TYPE_SIZE]-End--> |
| int32_t bearerTypesSize | Actual size of the bearer type list.<br><!--Device-int32_t bearerTypesSize--><!--Device-int32_t bearerTypesSize-End--> |


