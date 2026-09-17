# OH_TrafficFilter_FilterRule

```c
typedef struct OH_TrafficFilter_FilterRule {...} OH_TrafficFilter_FilterRule
```

## Overview

Packet filter rule<br> Defines conditions for matching packets. 1. **Initialization Contract (Caller Side)**: - The caller must **zero-initialize** the entire structure (e.g., via `memset`) before use. - The `size` field **must** be explicitly set to `sizeof(OH_TrafficFilter_FilterRule)`. - If `size` is less than `sizeof(OH_TrafficFilter_FilterRule)`, the implementation will only read the stable prefix fields up to `size`, ignoring subsequent bytes.<br> 2. **Read Contract (Implementation Side)**: - The implementation strictly determines the valid field range based on the `size` value. - If `size` < `sizeof(OH_TrafficFilter_FilterRule)`, the implementation treats it as an older version and reads only the prefix fields compatible with that size. - If `size` is 0 or the pointer is NULL, the implementation must return an error.

**Since**: 26.1.0

**Related module**: [TrafficFilter](capi-trafficfilter.md)

**Header file**: [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t size | Must be set to `sizeof(OH_TrafficFilter_FilterRule)` by the caller. The caller is required to zero-initialize the structure first, then set this field. The implementation uses this value to determine the valid data range for binary compatibility.<br>**Since**: 26.1.0 |
| uint32_t priority | Priority (smaller number means higher priority)<br>**Since**: 26.1.0 |
| [OH_TrafficFilter_HookPoint](capi-net-trafficfilter-type-h.md#oh_trafficfilter_hookpoint) hookPoint | Hook point<br>**Since**: 26.1.0 |
| uint8_t protocol | Protocol (0=any, 6=TCP, 17=UDP)<br>**Since**: 26.1.0 |
| [OH_TrafficFilter_IPMatch](capi-trafficfilter-oh-trafficfilter-ipmatch.md) srcIp | Source IP match condition<br>**Since**: 26.1.0 |
| [OH_TrafficFilter_PortMatch](capi-trafficfilter-oh-trafficfilter-portmatch.md) srcPort | Source port match condition<br>**Since**: 26.1.0 |
| [OH_TrafficFilter_IPMatch](capi-trafficfilter-oh-trafficfilter-ipmatch.md) dstIp | Destination IP match condition<br>**Since**: 26.1.0 |
| [OH_TrafficFilter_PortMatch](capi-trafficfilter-oh-trafficfilter-portmatch.md) dstPort | Destination port match condition<br>**Since**: 26.1.0 |
| [OH_TrafficFilter_InterfaceMatch](capi-trafficfilter-oh-trafficfilter-interfacematch.md) inInterface | Incoming interface match condition<br>**Since**: 26.1.0 |
| [OH_TrafficFilter_InterfaceMatch](capi-trafficfilter-oh-trafficfilter-interfacematch.md) outInterface | Outgoing interface match condition<br>**Since**: 26.1.0 |
| uint32_t uidStart | Application UID range start (inclusive). Valid range: 0 to UINT32_MAX. To match any UID, set both uidStart and uidEnd to UINT32_MAX. If uidStart > uidEnd, the rule-setting API returns OH_TRAFFICFILTER_ERROR_INVALID_PARAM. After zero-initialization, uidStart=0 and uidEnd=0, which matches UID 0 only.<br>**Since**: 26.1.0 |
| uint32_t uidEnd | Application UID range end (inclusive). Valid range: 0 to UINT32_MAX. See uidStart for usage details.<br>**Since**: 26.1.0 |
| [OH_TrafficFilter_MACMatch](capi-trafficfilter-oh-trafficfilter-macmatch.md) macMatch | MAC address match condition (only source MAC)<br>**Since**: 26.1.0 |
| [OH_TrafficFilter_TCPFlagsMatch](capi-trafficfilter-oh-trafficfilter-tcpflagsmatch.md) tcpFlagsMatch | TCP flags match condition (valid only for TCP protocol)<br>**Since**: 26.1.0 |
| [OH_TrafficFilter_ConntrackMatch](capi-trafficfilter-oh-trafficfilter-conntrackmatch.md) conntrackMatch | Connection tracking match condition<br>**Since**: 26.1.0 |


