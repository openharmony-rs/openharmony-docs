# NetConn_TraceRouteOption

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=108aa11c2ceb50c68f8417aa3c60f1dcb55dabdd translatedAt=2026-09-23T01:29:45.283Z pushedAt=2026-09-24T06:00:14.118Z -->

```c
typedef struct NetConn_TraceRouteOption {...} NetConn_TraceRouteOption
```

## Overview

Defines the network trace route options.

**Since**: 20

**Related module**: [NetConnection](capi-netconnection.md)

**Header file**: [net_connection_type.h](capi-net-connection-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint8_t maxJumpNumber | Maximum number of hops in the probe result. The value must be the same as that of **TraceRouteInfo**. The maximum number of hops is 30, which is also the default value.|
| [NetConn_PacketsType](capi-net-connection-type-h.md#netconn_packetstype) packetsType | Protocol type of the probe packet. The default value is **NETCONN_PACKETS_ICMP**. |