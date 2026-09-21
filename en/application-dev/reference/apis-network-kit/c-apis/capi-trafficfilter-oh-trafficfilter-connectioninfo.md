# OH_TrafficFilter_ConnectionInfo

```c
typedef struct OH_TrafficFilter_ConnectionInfo {...} OH_TrafficFilter_ConnectionInfo
```

## Overview

Connection information structure<br> Describes five-tuple connection information used to query process information.<br> Initialization rule: Before calling {@link OH_TrafficFilter_QueryProcess}, the caller must clear this structure<br>to zero, for example by using memset, and then set {@link size} to the actual size of the<br>structure allocated by the caller, usually sizeof(OH_TrafficFilter_ConnectionInfo).<br>ABI compatibility rule:<br>The library uses {@link size} to determine which fields can be safely read.<br>If {@link size} is smaller than the minimum size required by the current API, the function<br>returns {@link OH_TRAFFICFILTER_ERROR_INVALID_PARAM}. If {@link size} is larger than the size known by the library, the extra fields are ignored. Newly added fields in future versions should remain zero-initialized when not used.

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Since**: 26.0.0

**Related module**: [TrafficFilter](capi-trafficfilter.md)

**Header file**: [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t size | the actual size of the structure allocated by the caller.<br>**Since**: 26.0.0 |
| [OH_TrafficFilter_IPAddress](capi-trafficfilter-oh-trafficfilter-ipaddress.md) srcIp | Source IP address, supports IPv4 and IPv6.<br>**Since**: 26.0.0 |
| uint16_t srcPort | Source port. 0 means any source port.<br>**Since**: 26.0.0 |
| [OH_TrafficFilter_IPAddress](capi-trafficfilter-oh-trafficfilter-ipaddress.md) dstIp | Destination IP address, supports IPv4 and IPv6.<br>**Since**: 26.0.0 |
| uint16_t dstPort | Destination port. 0 means any destination port.<br>**Since**: 26.0.0 |
| uint8_t protocol | Protocol type. Supported values: - OH_TRAFFICFILTER_PROTO_TCP (6) - OH_TRAFFICFILTER_PROTO_UDP (17)<br>**Since**: 26.0.0 |


