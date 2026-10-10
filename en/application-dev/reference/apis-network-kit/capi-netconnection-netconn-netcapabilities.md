# NetConn_NetCapabilities

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=742fd8e7f742ee980eb300ddfd075065ca362dff translatedAt=2026-09-28T01:10:31.090Z pushedAt=2026-10-09T01:39:55.173Z -->

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
