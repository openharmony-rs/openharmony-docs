# OH_TrafficFilter_RedirectRule

```c
typedef struct OH_TrafficFilter_RedirectRule {...} OH_TrafficFilter_RedirectRule
```

## Overview

Defines the traffic redirection rule. Defines a TCP traffic redirection rule to redirect matching traffic to a specified proxy server. Initialization rule: Before calling [OH_TrafficFilter_AddRedirectRule](capi-net-trafficfilter-h.md#oh_trafficfilter_addredirectrule), the caller must clear this struct to zero (for example, using **memset**), and then set [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) to the actual size of the struct allocated by the caller, usually **sizeof(OH_TrafficFilter_RedirectRule)**. Binary compatibility rule (ABI, that is, application binary interface, which ensures that code compiled by old and new versions can recognize each other's struct layout): The system determines which fields can be safely read based on [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md). If [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) is smaller than the minimum size required by the current API, the API returns [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode). If [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) is larger than the size known to the system, the extra fields are ignored. Failure rule: If [OH_TrafficFilter_AddRedirectRule](capi-net-trafficfilter-h.md#oh_trafficfilter_addredirectrule) returns an error, it is not guaranteed that the rule has been added or taken effect. The caller should check the return value before assuming that the rule has taken effect.

<!--Device-struct OH_TrafficFilter_RedirectRule {...}--><!--Device-struct OH_TrafficFilter_RedirectRule {...}-End-->

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Since**: 26.0.0

**Related module**: [TrafficFilter](capi-network-kit-trafficfilter.md)

**Header file**: [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t size | Actual size of the struct allocated by the caller.<br>**Since**: 26.0.0<br><!--Device-uint32_t size--><!--Device-uint32_t size-End--> |
| uint32_t priority | Priority. A smaller value indicates a higher priority. The rule is the same as that of the packet filter.<br>**Since**: 26.0.0<br><!--Device-uint32_t priority--><!--Device-uint32_t priority-End--> |
| [OH_TrafficFilter_HookPoint](capi-net-trafficfilter-type-h.md#oh_trafficfilter_hookpoint) hookPoint | Hook point, which specifies where the rule takes effect in the network protocol stack. Only **PREROUTING** and **OUTPUT** are supported. For details, see [OH_TrafficFilter_HookPoint](capi-net-trafficfilter-type-h.md#oh_trafficfilter_hookpoint).<br>**Since**: 26.0.0<br><!--Device-OH_TrafficFilter_HookPoint hookPoint--><!--Device-OH_TrafficFilter_HookPoint hookPoint-End--> |
| uint8_t protocol | Protocol, fixed to TCP=6.<br>**Since**: 26.0.0<br><!--Device-uint8_t protocol--><!--Device-uint8_t protocol-End--> |
| [OH_TrafficFilter_IPMatch](capi-trafficfilter-oh-trafficfilter-ipmatch.md) srcIp | Source IP matching condition.<br>**Since**: 26.0.0<br><!--Device-OH_TrafficFilter_IPMatch srcIp--><!--Device-OH_TrafficFilter_IPMatch srcIp-End--> |
| [OH_TrafficFilter_PortMatch](capi-trafficfilter-oh-trafficfilter-portmatch.md) srcPort | Source port matching condition.<br>**Since**: 26.0.0<br><!--Device-OH_TrafficFilter_PortMatch srcPort--><!--Device-OH_TrafficFilter_PortMatch srcPort-End--> |
| [OH_TrafficFilter_IPMatch](capi-trafficfilter-oh-trafficfilter-ipmatch.md) dstIp | Destination IP matching condition.<br>**Since**: 26.0.0<br><!--Device-OH_TrafficFilter_IPMatch dstIp--><!--Device-OH_TrafficFilter_IPMatch dstIp-End--> |
| [OH_TrafficFilter_PortMatch](capi-trafficfilter-oh-trafficfilter-portmatch.md) dstPort | Destination port matching condition.<br>**Since**: 26.0.0<br><!--Device-OH_TrafficFilter_PortMatch dstPort--><!--Device-OH_TrafficFilter_PortMatch dstPort-End--> |
| [OH_TrafficFilter_InterfaceMatch](capi-trafficfilter-oh-trafficfilter-interfacematch.md) inInterface | Inbound interface matching condition.<br>**Since**: 26.0.0<br><!--Device-OH_TrafficFilter_InterfaceMatch inInterface--><!--Device-OH_TrafficFilter_InterfaceMatch inInterface-End--> |
| [OH_TrafficFilter_InterfaceMatch](capi-trafficfilter-oh-trafficfilter-interfacematch.md) outInterface | Outbound interface matching condition.<br>**Since**: 26.0.0<br><!--Device-OH_TrafficFilter_InterfaceMatch outInterface--><!--Device-OH_TrafficFilter_InterfaceMatch outInterface-End--> |
| uint32_t uidStart | Start value of the app UID range. The value range is [0, UINT32_MAX], where **UINT32_MAX** indicates any UID.<br>**Since**: 26.0.0<br><!--Device-uint32_t uidStart--><!--Device-uint32_t uidStart-End--> |
| uint32_t uidEnd | End value of the app UID range. The value range is [0, UINT32_MAX], where **UINT32_MAX** indicates any UID. Generally, this value must be greater than or equal to **uidStart** (the start value of the app UID range).<br>**Since**: 26.0.0<br><!--Device-uint32_t uidEnd--><!--Device-uint32_t uidEnd-End--> |
| [OH_TrafficFilter_IPAddress](capi-trafficfilter-oh-trafficfilter-ipaddress.md) proxyIp | IP address of the proxy server. Both IPv4 and IPv6 are supported.<br>**Since**: 26.0.0<br><!--Device-OH_TrafficFilter_IPAddress proxyIp--><!--Device-OH_TrafficFilter_IPAddress proxyIp-End--> |
| uint16_t proxyPort | Port of the proxy server.<br>**Since**: 26.0.0<br><!--Device-uint16_t proxyPort--><!--Device-uint16_t proxyPort-End--> |


