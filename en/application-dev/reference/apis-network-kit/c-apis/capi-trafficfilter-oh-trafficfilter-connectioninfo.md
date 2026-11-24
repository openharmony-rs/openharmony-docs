# OH_TrafficFilter_ConnectionInfo

```c
typedef struct OH_TrafficFilter_ConnectionInfo {...} OH_TrafficFilter_ConnectionInfo
```

## Overview

Defines the connection information struct. It describes the five-tuple information of a network connection (source IP, destination IP, source port, destination port, and protocol type), which is used to query the process that initiates the connection. Initialization rule: Before calling [OH_TrafficFilter_QueryProcess](capi-net-trafficfilter-h.md#oh_trafficfilter_queryprocess), the caller must clear this struct to zero (for example, using **memset**), and then set [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) to the actual size of the struct allocated by the caller, which is usually **sizeof(OH_TrafficFilter_ConnectionInfo)**. Binary compatibility rule (ABI, that is, Application Binary Interface, which ensures that code compiled by old and new versions can recognize each other's struct layout): The system determines which fields can be safely read based on [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md). If [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) is smaller than the minimum size required by the current interface, the interface returns [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode). If [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) is larger than the size known to the system, the extra fields are ignored.

<!--Device-struct OH_TrafficFilter_ConnectionInfo {...}--><!--Device-struct OH_TrafficFilter_ConnectionInfo {...}-End-->

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Since**: 26.0.0

**Related module**: [TrafficFilter](capi-network-kit-trafficfilter.md)

**Header file**: [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t size | Actual size of the struct allocated by the caller.<br>**Since**: 26.0.0<br><!--Device-uint32_t size--><!--Device-uint32_t size-End--> |
| [OH_TrafficFilter_IPAddress](capi-trafficfilter-oh-trafficfilter-ipaddress.md) srcIp | Source IP address, which supports IPv4 and IPv6.<br>**Since**: 26.0.0<br><!--Device-OH_TrafficFilter_IPAddress srcIp--><!--Device-OH_TrafficFilter_IPAddress srcIp-End--> |
| uint16_t srcPort | Source port. 0 indicates any source port.<br>**Since**: 26.0.0<br><!--Device-uint16_t srcPort--><!--Device-uint16_t srcPort-End--> |
| [OH_TrafficFilter_IPAddress](capi-trafficfilter-oh-trafficfilter-ipaddress.md) dstIp | Destination IP address, which supports IPv4 and IPv6. It must be in the same address family as the source IP address.<br>**Since**: 26.0.0<br><!--Device-OH_TrafficFilter_IPAddress dstIp--><!--Device-OH_TrafficFilter_IPAddress dstIp-End--> |
| uint16_t dstPort | Destination port. **0** indicates any destination port.<br>**Since**: 26.0.0<br><!--Device-uint16_t dstPort--><!--Device-uint16_t dstPort-End--> |
| uint8_t protocol | Protocol type. Supported values: - OH_TRAFFICFILTER_PROTO_TCP (6) - OH_TRAFFICFILTER_PROTO_UDP (17)<br>**Since**: 26.0.0<br><!--Device-uint8_t protocol--><!--Device-uint8_t protocol-End--> |


