# OH_TrafficFilter_FilterRule

```c
typedef struct OH_TrafficFilter_FilterRule {...} OH_TrafficFilter_FilterRule
```

## Overview

Defines a packet filtering rule. The conditions within a single **OH_TrafficFilter_FilterRule** struct are in a logical AND relationship, and multiple rules added to the same **OH_TrafficFilter_PacketController** are in a logical OR relationship. Initialization rule: Before calling [OH_TrafficFilter_AddPacketRule](capi-net-trafficfilter-h.md#oh_trafficfilter_addpacketrule), the caller must clear this struct to zero (for example, using **memset**), and then set [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) to the actual size of the struct allocated by the caller, usually **sizeof(OH_TrafficFilter_FilterRule)**. Binary compatibility rule (ABI, that is, application binary interface, which ensures that code compiled by old and new versions can recognize each other's struct layout): The system determines which fields can be safely read based on [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md). If [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) is smaller than the minimum size required by the current API, the API returns [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode). If [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) is larger than the size known to the system, the extra fields are ignored. Failure rule: If [OH_TrafficFilter_AddPacketRule](capi-net-trafficfilter-h.md#oh_trafficfilter_addpacketrule) returns an error, it is not guaranteed that the rule has been added or taken effect. The caller should check the return value before assuming that the rule has taken effect.

<!--Device-struct OH_TrafficFilter_FilterRule {...}--><!--Device-struct OH_TrafficFilter_FilterRule {...}-End-->

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Since**: 26.0.1

**Related module**: [TrafficFilter](capi-network-kit-trafficfilter.md)

**Header file**: [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t size | Actual size of the struct allocated by the caller.<br>**Since**: 26.0.1<br><!--Device-uint32_t size--><!--Device-uint32_t size-End--> |
| uint32_t priority | Priority. A smaller value indicates a higher priority.<br>**Since**: 26.0.1<br><!--Device-uint32_t priority--><!--Device-uint32_t priority-End--> |
| [OH_TrafficFilter_HookPoint](capi-net-trafficfilter-type-h.md#oh_trafficfilter_hookpoint) hookPoint | Hook point. Adds the rule to the chain of a different hook point.<br>**Since**: 26.0.1<br><!--Device-OH_TrafficFilter_HookPoint hookPoint--><!--Device-OH_TrafficFilter_HookPoint hookPoint-End--> |
| uint8_t protocol | Protocol type. **0** indicates no restriction, **6** indicates TCP, and **17** indicates UDP.<br>**Since**: 26.0.1<br><!--Device-uint8_t protocol--><!--Device-uint8_t protocol-End--> |
| [OH_TrafficFilter_IPMatch](capi-trafficfilter-oh-trafficfilter-ipmatch.md) srcIp | Source IP matching condition.<br>**Since**: 26.0.1<br><!--Device-OH_TrafficFilter_IPMatch srcIp--><!--Device-OH_TrafficFilter_IPMatch srcIp-End--> |
| [OH_TrafficFilter_PortMatch](capi-trafficfilter-oh-trafficfilter-portmatch.md) srcPort | Source port matching condition.<br>**Since**: 26.0.1<br><!--Device-OH_TrafficFilter_PortMatch srcPort--><!--Device-OH_TrafficFilter_PortMatch srcPort-End--> |
| [OH_TrafficFilter_IPMatch](capi-trafficfilter-oh-trafficfilter-ipmatch.md) dstIp | Destination IP matching condition.<br>**Since**: 26.0.1<br><!--Device-OH_TrafficFilter_IPMatch dstIp--><!--Device-OH_TrafficFilter_IPMatch dstIp-End--> |
| [OH_TrafficFilter_PortMatch](capi-trafficfilter-oh-trafficfilter-portmatch.md) dstPort | Destination port matching condition.<br>**Since**: 26.0.1<br><!--Device-OH_TrafficFilter_PortMatch dstPort--><!--Device-OH_TrafficFilter_PortMatch dstPort-End--> |
| [OH_TrafficFilter_InterfaceMatch](capi-trafficfilter-oh-trafficfilter-interfacematch.md) inInterface | Inbound interface matching condition.<br>**Since**: 26.0.1<br><!--Device-OH_TrafficFilter_InterfaceMatch inInterface--><!--Device-OH_TrafficFilter_InterfaceMatch inInterface-End--> |
| [OH_TrafficFilter_InterfaceMatch](capi-trafficfilter-oh-trafficfilter-interfacematch.md) outInterface | Outbound interface matching condition.<br>**Since**: 26.0.1<br><!--Device-OH_TrafficFilter_InterfaceMatch outInterface--><!--Device-OH_TrafficFilter_InterfaceMatch outInterface-End--> |
| uint32_t uidStart | Start value of the application UID range. **UINT32_MAX** indicates any value.<br>**Since**: 26.0.1<br><!--Device-uint32_t uidStart--><!--Device-uint32_t uidStart-End--> |
| uint32_t uidEnd | End value of the application UID range. **UINT32_MAX** indicates any value.<br>**Since**: 26.0.1<br><!--Device-uint32_t uidEnd--><!--Device-uint32_t uidEnd-End--> |
| [OH_TrafficFilter_MACMatch](capi-trafficfilter-oh-trafficfilter-macmatch.md) macMatch | MAC address matching condition. Applies to the source MAC address only.<br>**Since**: 26.0.1<br><!--Device-OH_TrafficFilter_MACMatch macMatch--><!--Device-OH_TrafficFilter_MACMatch macMatch-End--> |
| [OH_TrafficFilter_TCPFlagsMatch](capi-trafficfilter-oh-trafficfilter-tcpflagsmatch.md) tcpFlagsMatch | TCP flag matching condition. Valid only for the TCP protocol.<br>**Since**: 26.0.1<br><!--Device-OH_TrafficFilter_TCPFlagsMatch tcpFlagsMatch--><!--Device-OH_TrafficFilter_TCPFlagsMatch tcpFlagsMatch-End--> |
| [OH_TrafficFilter_ConntrackMatch](capi-trafficfilter-oh-trafficfilter-conntrackmatch.md) conntrackMatch | Connection tracking matching condition.<br>**Since**: 26.0.1<br><!--Device-OH_TrafficFilter_ConntrackMatch conntrackMatch--><!--Device-OH_TrafficFilter_ConntrackMatch conntrackMatch-End--> |


