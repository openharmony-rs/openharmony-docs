# NetConn_TraceRouteInfo

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=c33290f86c4a896f90eff1ee86d78748f13424d1 translatedAt=2026-09-23T01:29:32.177Z pushedAt=2026-09-24T06:00:14.117Z -->

```c
typedef struct NetConn_TraceRouteInfo {...} NetConn_TraceRouteInfo
```

## Overview

Defines the trace route information.

**Since**: 20

**Related module**: [NetConnection](capi-netconnection.md)

**Header file**: [net_connection_type.h](capi-net-connection-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint8_t jumpNo | Number of hops.|
| char address[[NETCONN_MAX_STR_LEN](capi-net-connection-type-h.md#macros)] | Host name or address. |
| uint32_t rtt[[NETCONN_MAX_RTT_NUM](capi-net-connection-type-h.md#macros)] | Round-trip time (in ms), including the maximum, minimum, average, and standard deviation. |