# NetConn_NetHandleList

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=c69deb80f49add35805a3310c87e79c46b0431d7 translatedAt=2026-09-23T01:28:38.707Z pushedAt=2026-09-24T06:00:14.114Z -->

```c
typedef struct NetConn_NetHandleList {...} NetConn_NetHandleList
```

## Overview

Defines the network list.

**Since**: 11

**Related module**: [NetConnection](capi-netconnection.md)

**Header file**: [net_connection_type.h](capi-net-connection-type-h.md)

## Summary

### Member Variables

| Name                                                    | Description|
|--------------------------------------------------------| -- |
| [NetConn_NetHandle](capi-netconnection-netconn-nethandle.md) netHandles[[NETCONN_MAX_NET_SIZE](capi-net-connection-type-h.md#macros)] | List of network handles. |
| int32_t netHandleListSize                              | Actual size of the network handle list.|
