# NetConn_ProbeResultInfo

```c
typedef struct NetConn_ProbeResultInfo {...} NetConn_ProbeResultInfo
```

## Overview

Defines the probe result.

**Since**: 20

**Related module**: [NetConnection](capi-netconnection.md)

**Header file**: [net_connection_type.h](capi-net-connection-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t lossRate | Packet loss rate, in percentage. The value **100** indicates 100% packet loss, and the value **50** indicates 50% packet loss. |
| uint32_t rtt[NETCONN_MAX_RTT_NUM] | Round-trip time in ms, including the maximum, minimum, average, and standard deviations. |


