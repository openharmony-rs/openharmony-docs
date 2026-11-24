# OH_TrafficFilter_IPCidr

```c
typedef struct OH_TrafficFilter_IPCidr {...} OH_TrafficFilter_IPCidr
```

## Overview

Defines the IP match value for Classless Inter-Domain Routing (CIDR) matching.

<!--Device-struct OH_TrafficFilter_IPCidr {...}--><!--Device-struct OH_TrafficFilter_IPCidr {...}-End-->

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Since**: 26.0.0

**Related module**: [TrafficFilter](capi-network-kit-trafficfilter.md)

**Header file**: [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [OH_TrafficFilter_IPAddress](capi-trafficfilter-oh-trafficfilter-ipaddress.md) base | Base IP address of the CIDR block.<br>**Since**: 26.0.0<br><!--Device-OH_TrafficFilter_IPAddress base--><!--Device-OH_TrafficFilter_IPAddress base-End--> |
| uint8_t prefixLen | CIDR prefix length, which indicates the number of leading 1 bits in the network mask (for example, **24**<br>indicates the subnet mask 255.255.255.0).<br>**Since**: 26.0.0<br><!--Device-uint8_t prefixLen--><!--Device-uint8_t prefixLen-End--> |


