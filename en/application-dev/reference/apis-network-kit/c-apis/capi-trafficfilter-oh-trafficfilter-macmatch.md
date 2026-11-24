# OH_TrafficFilter_MACMatch

```c
typedef struct OH_TrafficFilter_MACMatch {...} OH_TrafficFilter_MACMatch
```

## Overview

Defines the MAC address matching condition.

<!--Device-struct OH_TrafficFilter_MACMatch {...}--><!--Device-struct OH_TrafficFilter_MACMatch {...}-End-->

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Since**: 26.0.1

**Related module**: [TrafficFilter](capi-network-kit-trafficfilter.md)

**Header file**: [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| bool enable | Whether to enable MAC address matching. The value **true** means to enable MAC address matching, and **false** means the opposite.<br>**Since**: 26.0.1<br><!--Device-bool enable--><!--Device-bool enable-End--> |
| bool invert | Whether to invert the matching result. The value **true** means to invert the matching result, and **false** means the opposite.<br>**Since**: 26.0.1<br><!--Device-bool invert--><!--Device-bool invert-End--> |
| char srcMac[OH_TRAFFICFILTER_MAC_ADDRSTRLEN] | Source MAC address (in the XX:XX:XX:XX:XX:XX format).<br>**Since**: 26.0.1<br><!--Device-char srcMac[OH_TRAFFICFILTER_MAC_ADDRSTRLEN]--><!--Device-char srcMac[OH_TRAFFICFILTER_MAC_ADDRSTRLEN]-End--> |


