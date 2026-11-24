# OH_TrafficFilter_PacketDesc

```c
typedef struct OH_TrafficFilter_PacketDesc {...} OH_TrafficFilter_PacketDesc
```

## Overview

Defines the packet descriptor.

<!--Device-struct OH_TrafficFilter_PacketDesc {...}--><!--Device-struct OH_TrafficFilter_PacketDesc {...}-End-->

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Since**: 26.0.1

**Related module**: [TrafficFilter](capi-network-kit-trafficfilter.md)

**Header file**: [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t packetId | Packet ID (assigned by the kernel when the packet arrives at netfilter (Network Filter)).<br>**Since**: 26.0.1<br><!--Device-uint32_t packetId--><!--Device-uint32_t packetId-End--> |
| uint8_t protocol | Protocol type.<br>**Since**: 26.0.1<br><!--Device-uint8_t protocol--><!--Device-uint8_t protocol-End--> |
| [OH_TrafficFilter_IPAddress](capi-trafficfilter-oh-trafficfilter-ipaddress.md) srcIp | Source IP address (supports IPv4 and IPv6).<br>**Since**: 26.0.1<br><!--Device-OH_TrafficFilter_IPAddress srcIp--><!--Device-OH_TrafficFilter_IPAddress srcIp-End--> |
| uint16_t srcPort | Source port.<br>**Since**: 26.0.1<br><!--Device-uint16_t srcPort--><!--Device-uint16_t srcPort-End--> |
| [OH_TrafficFilter_IPAddress](capi-trafficfilter-oh-trafficfilter-ipaddress.md) dstIp | Destination IP address (supports IPv4 and IPv6).<br>**Since**: 26.0.1<br><!--Device-OH_TrafficFilter_IPAddress dstIp--><!--Device-OH_TrafficFilter_IPAddress dstIp-End--> |
| uint16_t dstPort | Destination port.<br>**Since**: 26.0.1<br><!--Device-uint16_t dstPort--><!--Device-uint16_t dstPort-End--> |
| uint32_t packetLen | Packet length.<br>**Since**: 26.0.1<br><!--Device-uint32_t packetLen--><!--Device-uint32_t packetLen-End--> |
| uint8_t* data | Pointer to the packet data (modifiable by the user; the memory is managed by the system, and **it is valid only during the callback. Do not access this pointer after the callback returns**).<br>**Since**: 26.0.1<br><!--Device-uint8_t* data--><!--Device-uint8_t* data-End--> |
| void* userData | Pointer to the user data (used in the callback).<br>**Since**: 26.0.1<br><!--Device-void* userData--><!--Device-void* userData-End--> |


