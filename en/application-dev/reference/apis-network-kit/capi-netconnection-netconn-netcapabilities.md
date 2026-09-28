# NetConn_NetCapabilities

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=c33290f86c4a896f90eff1ee86d78748f13424d1 translatedAt=2026-09-23T01:27:08.631Z pushedAt=2026-09-24T06:00:14.109Z -->

```c
typedef struct NetConn_NetCapabilities {...} NetConn_NetCapabilities
```

## Overview

Defines network capability sets.

**Since**: 11

**Related module**: [NetConnection](capi-netconnection.md)

**Header file**: [net_connection_type.h](capi-net-connection-type-h.md)

## Summary

### Member Variables

| Name                                                                                                                  | Description|
|------------------------------------------------------------------------------------------------------------------------| -- |
| uint32_t linkUpBandwidthKbps                                                                                           | Uplink bandwidth.|
| uint32_t linkDownBandwidthKbps                                                                                         | Downlink bandwidth.|
| [NetConn_NetCap](capi-net-connection-type-h.md#netconn_netcap) netCaps[[NETCONN_MAX_CAP_SIZE](capi-net-connection-type-h.md#macros)]                           | List of network capabilities. |
| int32_t netCapsSize                                                                                                    | Actual size of the network capability list.|
| [NetConn_NetBearerType](capi-net-connection-type-h.md#netconn_netbearertype) bearerTypes[[NETCONN_MAX_BEARER_TYPE_SIZE](capi-net-connection-type-h.md#macros)] | List of bearer types. |
| int32_t bearerTypesSize                                                                                                | Actual size of the bearer type list. |
