# OH_TrafficFilter_RedirectRule

```c
typedef struct OH_TrafficFilter_RedirectRule {...} OH_TrafficFilter_RedirectRule
```

## Overview

Traffic redirection rule.<br> Defines a TCP traffic redirection rule to redirect matched traffic to the specified proxy server.<br> Initialization rule: Before calling {@link OH_TrafficFilter_AddRedirectRule}, the caller must clear this structure<br>to zero, for example by using memset, and then set {@link size} to the actual size of the<br>structure allocated by the caller, usually sizeof(OH_TrafficFilter_RedirectRule).<br>ABI compatibility rule:<br>The library uses {@link size} to determine which fields can be safely read.<br>If {@link size} is smaller than the minimum size required by the current API, the function<br>returns {@link OH_TRAFFICFILTER_ERROR_INVALID_PARAM}. If {@link size} is larger than the<br>size known by the library, the extra fields are ignored. Newly added fields in future<br>versions should remain zero-initialized when not used.<br>Failure rule:<br>If {@link OH_TrafficFilter_AddRedirectRule} returns an error, the rule is not guaranteed to be added or applied. The caller should check the return value before assuming that the rule takes effect.

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Since**: 26.0.0

**Related module**: [TrafficFilter](capi-trafficfilter.md)

**Header file**: [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t size | the actual size of the structure allocated by the caller.<br>**Since**: 26.0.0 |
| uint32_t priority | Priority (smaller number means higher priority, same rule as packet filter)<br>**Since**: 26.0.0 |
| [OH_TrafficFilter_HookPoint](capi-net-trafficfilter-type-h.md#oh_trafficfilter_hookpoint) hookPoint | Hook point (only PREROUTING and OUTPUT are supported)<br>**Since**: 26.0.0 |
| uint8_t protocol | Protocol (fixed to TCP=6)<br>**Since**: 26.0.0 |
| [OH_TrafficFilter_IPMatch](capi-trafficfilter-oh-trafficfilter-ipmatch.md) srcIp | Source IP match condition<br>**Since**: 26.0.0 |
| [OH_TrafficFilter_PortMatch](capi-trafficfilter-oh-trafficfilter-portmatch.md) srcPort | Source port match condition<br>**Since**: 26.0.0 |
| [OH_TrafficFilter_IPMatch](capi-trafficfilter-oh-trafficfilter-ipmatch.md) dstIp | Destination IP match condition<br>**Since**: 26.0.0 |
| [OH_TrafficFilter_PortMatch](capi-trafficfilter-oh-trafficfilter-portmatch.md) dstPort | Destination port match condition<br>**Since**: 26.0.0 |
| [OH_TrafficFilter_InterfaceMatch](capi-trafficfilter-oh-trafficfilter-interfacematch.md) inInterface | Incoming interface match condition<br>**Since**: 26.0.0 |
| [OH_TrafficFilter_InterfaceMatch](capi-trafficfilter-oh-trafficfilter-interfacematch.md) outInterface | Outgoing interface match condition<br>**Since**: 26.0.0 |
| uint32_t uidStart | Application UID range start (UINT32_MAX means any)<br>**Since**: 26.0.0 |
| uint32_t uidEnd | Application UID range end (UINT32_MAX means any)<br>**Since**: 26.0.0 |
| [OH_TrafficFilter_IPAddress](capi-trafficfilter-oh-trafficfilter-ipaddress.md) proxyIp | Proxy server IP address (supports IPv4 and IPv6)<br>**Since**: 26.0.0 |
| uint16_t proxyPort | Proxy server port<br>**Since**: 26.0.0 |


