# OH_TrafficFilter_PacketDesc

```c
typedef struct OH_TrafficFilter_PacketDesc {...} OH_TrafficFilter_PacketDesc
```

## Overview

Packet descriptor<br> Contains five-tuple information and packet data

**Since**: 26.1.0

**Related module**: [TrafficFilter](capi-trafficfilter.md)

**Header file**: [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t packetId | Packet ID (assigned by kernel when packet arrives at netfilter)<br>**Since**: 26.1.0 |
| uint8_t protocol | Protocol type<br>**Since**: 26.1.0 |
| [OH_TrafficFilter_IPAddress](capi-trafficfilter-oh-trafficfilter-ipaddress.md) srcIp | Source IP address (supports IPv4 and IPv6)<br>**Since**: 26.1.0 |
| uint16_t srcPort | Source port<br>**Since**: 26.1.0 |
| [OH_TrafficFilter_IPAddress](capi-trafficfilter-oh-trafficfilter-ipaddress.md) dstIp | Destination IP address (supports IPv4 and IPv6)<br>**Since**: 26.1.0 |
| uint16_t dstPort | Destination port<br>**Since**: 26.1.0 |
| uint32_t packetLen | Packet length<br>**Since**: 26.1.0 |
| uint8_t* data | Packet data pointer (user can modify, memory managed by system, valid only during callback)<br>**Since**: 26.1.0 |
| void* userData | User data (used in callback)<br>**Since**: 26.1.0 |


