# OH_TrafficFilter_MACMatch

```c
typedef struct OH_TrafficFilter_MACMatch {...} OH_TrafficFilter_MACMatch
```

## Overview

MAC address match condition<br> Matches packets based on MAC address Only source MAC is supported

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Since**: 26.0.1

**Related module**: [TrafficFilter](capi-trafficfilter.md)

**Header file**: [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| bool enable | Enable MAC address matching<br>**Since**: 26.0.1 |
| bool invert | Whether to invert the match result<br>**Since**: 26.0.1 |
| char srcMac[OH_TRAFFICFILTER_MAC_ADDRSTRLEN] | Source MAC address in "XX:XX:XX:XX:XX:XX" format. ASCII/UTF-8 encoded, must be null-terminated. OH_TRAFFICFILTER_MAC_ADDRSTRLEN includes the null terminator; maximum valid string length is 17 characters. Invalid format will cause the rule-setting API to return OH_TRAFFICFILTER_ERROR_INVALID_PARAM.<br>**Since**: 26.0.1 |


