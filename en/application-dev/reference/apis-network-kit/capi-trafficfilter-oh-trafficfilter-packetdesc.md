# OH_TrafficFilter_PacketDesc

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=55df9c11d6d7c450cc6d9d1ac7b0b998394459f6 translatedAt=2026-09-23T01:40:48.104Z pushedAt=2026-09-24T06:00:14.157Z -->

```c
typedef struct OH_TrafficFilter_PacketDesc {...} OH_TrafficFilter_PacketDesc
```

## Overview

Defines the packet descriptor.

**Since:** 26.0.1

**Related module:** [TrafficFilter](capi-trafficfilter.md)

**File to include:** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| uint32_t packetId | Packet ID (assigned by the kernel when the packet arrives at netfilter (Network Filter)). |
| uint8_t protocol | Protocol type. |
| [OH_TrafficFilter_IPAddress](capi-trafficfilter-oh-trafficfilter-ipaddress.md) srcIp | Source IP address (supports IPv4 and IPv6). |
| uint16_t srcPort | Source port. |
| [OH_TrafficFilter_IPAddress](capi-trafficfilter-oh-trafficfilter-ipaddress.md) dstIp | Destination IP address (supports IPv4 and IPv6). |
| uint16_t dstPort | Destination port. |
| uint32_t packetLen | Packet length. |
| uint8_t* data | Pointer to the packet data (modifiable by the user; the memory is managed by the system, and **it is valid only during the callback. Do not access this pointer after the callback returns**). |
| void* userData | Pointer to the user data (used in the callback). |
