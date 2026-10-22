# OH_TrafficFilter_FilterRule

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=55df9c11d6d7c450cc6d9d1ac7b0b998394459f6 translatedAt=2026-09-23T01:36:53.670Z pushedAt=2026-09-24T06:00:14.146Z -->

```c
typedef struct OH_TrafficFilter_FilterRule {...} OH_TrafficFilter_FilterRule
```

## Overview

Defines a packet filtering rule. The conditions within a single **OH_TrafficFilter_FilterRule** struct are in a logical AND relationship, and multiple rules added to the same **OH_TrafficFilter_PacketController** are in a logical OR relationship.

Initialization rule: Before calling [OH_TrafficFilter_AddPacketRule](capi-net-trafficfilter-h.md#oh_trafficfilter_addpacketrule), the caller must clear this struct to zero (for example, using **memset**), and then set [size](#member-variables) to the actual size of the struct allocated by the caller, usually **sizeof(OH_TrafficFilter_FilterRule)**.

Binary compatibility rule (ABI, that is, application binary interface, which ensures that code compiled by old and new versions can recognize each other's struct layout): The system determines which fields can be safely read based on [size](#member-variables). If [size](#member-variables) is smaller than the minimum size required by the current API, the API returns [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode). If [size](#member-variables) is larger than the size known to the system, the extra fields are ignored.

Failure rule: If [OH_TrafficFilter_AddPacketRule](capi-net-trafficfilter-h.md#oh_trafficfilter_addpacketrule) returns an error, it is not guaranteed that the rule has been added or taken effect. The caller should check the return value before assuming that the rule has taken effect.

**Since:** 26.0.1

**Related module:** [TrafficFilter](capi-trafficfilter.md)

**File to include:** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| uint32_t size | Actual size of the struct allocated by the caller. |
| uint32_t priority | Priority. A smaller value indicates a higher priority. |
| [OH_TrafficFilter_HookPoint](capi-net-trafficfilter-type-h.md#oh_trafficfilter_hookpoint) hookPoint | Hook point. Adds the rule to the chain of a different hook point. |
| uint8_t protocol | Protocol type. **0** indicates no restriction, **6** indicates TCP, and **17** indicates UDP. |
| [OH_TrafficFilter_IPMatch](capi-trafficfilter-oh-trafficfilter-ipmatch.md) srcIp | Source IP matching condition. |
| [OH_TrafficFilter_PortMatch](capi-trafficfilter-oh-trafficfilter-portmatch.md) srcPort | Source port matching condition. |
| [OH_TrafficFilter_IPMatch](capi-trafficfilter-oh-trafficfilter-ipmatch.md) dstIp | Destination IP matching condition. |
| [OH_TrafficFilter_PortMatch](capi-trafficfilter-oh-trafficfilter-portmatch.md) dstPort | Destination port matching condition. |
| [OH_TrafficFilter_InterfaceMatch](capi-trafficfilter-oh-trafficfilter-interfacematch.md) inInterface | Inbound interface matching condition. |
| [OH_TrafficFilter_InterfaceMatch](capi-trafficfilter-oh-trafficfilter-interfacematch.md) outInterface | Outbound interface matching condition. |
| uint32_t uidStart | Start value of the application UID range. **UINT32_MAX** indicates any value. |
| uint32_t uidEnd | End value of the application UID range. **UINT32_MAX** indicates any value. |
| [OH_TrafficFilter_MACMatch](capi-trafficfilter-oh-trafficfilter-macmatch.md) macMatch | MAC address matching condition. Applies to the source MAC address only. |
| [OH_TrafficFilter_TCPFlagsMatch](capi-trafficfilter-oh-trafficfilter-tcpflagsmatch.md) tcpFlagsMatch | TCP flag matching condition. Valid only for the TCP protocol. |
| [OH_TrafficFilter_ConntrackMatch](capi-trafficfilter-oh-trafficfilter-conntrackmatch.md) conntrackMatch | Connection tracking matching condition. |
