# NetConn_ProbeResultInfo

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=824f364f144656e22b90cfa1d73b03b48377f225 translatedAt=2026-09-28T01:11:20.282Z pushedAt=2026-10-09T01:40:01.951Z -->

```c
typedef struct NetConn_ProbeResultInfo {...} NetConn_ProbeResultInfo
```

## Overview

Defines the probe result.

**Since**: 20

**Related module**: [NetConnection](capi-netconnection.md)

**Header file**: [net_connection_type.h](capi-net-connection-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint8_t lossRate |Packet loss rate, in percentage. The value **100** indicates 100% packet loss, and the value **50** indicates 50% packet loss.|
| uint32_t rtt[NETCONN_MAX_RTT_NUM](capi-net-connection-type-h.md#macros) | Latency result (in ms), including the minimum, maximum, average, and standard deviation. |