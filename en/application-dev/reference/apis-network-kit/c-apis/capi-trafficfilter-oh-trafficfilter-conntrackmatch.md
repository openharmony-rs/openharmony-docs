# OH_TrafficFilter_ConntrackMatch

```c
typedef struct OH_TrafficFilter_ConntrackMatch {...} OH_TrafficFilter_ConntrackMatch
```

## Overview

Connection tracking match condition<br> Matches packets based on connection tracking states

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Since**: 26.0.1

**Related module**: [TrafficFilter](capi-trafficfilter.md)

**Header file**: [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| bool enable | Enable conntrack matching<br>**Since**: 26.0.1 |
| uint8_t stateMask | Connection states (use OH_TRAFFICFILTER_CT_STATE_* bitmap)<br>**Since**: 26.0.1 |


