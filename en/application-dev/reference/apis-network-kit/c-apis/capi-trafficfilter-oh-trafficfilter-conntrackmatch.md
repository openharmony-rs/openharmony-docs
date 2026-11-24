# OH_TrafficFilter_ConntrackMatch

```c
typedef struct OH_TrafficFilter_ConntrackMatch {...} OH_TrafficFilter_ConntrackMatch
```

## Overview

Defines the connection tracking match condition.

<!--Device-struct OH_TrafficFilter_ConntrackMatch {...}--><!--Device-struct OH_TrafficFilter_ConntrackMatch {...}-End-->

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Since**: 26.0.1

**Related module**: [TrafficFilter](capi-network-kit-trafficfilter.md)

**Header file**: [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| bool enable | Whether to enable connection tracking match. The value **true** means to enable connection tracking match, and **false** means not to enable it.<br>**Since**: 26.0.1<br><!--Device-bool enable--><!--Device-bool enable-End--> |
| uint8_t stateMask | Connection state.<br>**Since**: 26.0.1<br><!--Device-uint8_t stateMask--><!--Device-uint8_t stateMask-End--> |


