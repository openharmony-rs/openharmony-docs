# OH_TrafficFilter_PacketDesc

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=7cd2f817688c245414ad83d771260e8515966ace translatedAt=2026-11-04T06:34:44.274Z pushedAt=2026-11-04T08:04:44.861Z nl=1 -->

```c
typedef struct OH_TrafficFilter_PacketDesc {...} OH_TrafficFilter_PacketDesc
```

## Overview

Describes a packet descriptor.

**Since:** 26.0.1

**Related module:** [TrafficFilter](capi-trafficfilter.md)

**File to include:** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| uint32_t packetId | Packet ID, which is allocated by the kernel when the packet arrives at netfilter (Network Filter). |
| uint8_t protocol | Protocol type. |
| [OH_TrafficFilter_IPAddress](capi-trafficfilter-oh-trafficfilter-ipaddress.md) srcIp | Source IP address, which supports IPv4 and IPv6. |
| uint16_t srcPort | Source port. |
| [OH_TrafficFilter_IPAddress](capi-trafficfilter-oh-trafficfilter-ipaddress.md) dstIp | Destination IP address, which supports IPv4 and IPv6. |
| uint16_t dstPort | Destination port. |
| uint32_t packetLen | Packet length. |
| uint8_t* data | Pointer to the packet data. The user can modify the data, and the memory is managed by the system. **The pointer is valid only during the callback and must not be accessed after the callback returns.** |
| void* userData | User data, which is used in the callback. |
