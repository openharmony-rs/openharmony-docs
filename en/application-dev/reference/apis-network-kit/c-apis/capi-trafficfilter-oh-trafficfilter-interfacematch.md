# OH_TrafficFilter_InterfaceMatch

```c
typedef struct OH_TrafficFilter_InterfaceMatch {...} OH_TrafficFilter_InterfaceMatch
```

## Overview

interface match condition

<!--Device-struct OH_TrafficFilter_InterfaceMatch {...}--><!--Device-struct OH_TrafficFilter_InterfaceMatch {...}-End-->

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Since**: 26.0.0

**Related module**: [TrafficFilter](capi-network-kit-trafficfilter.md)

**Header file**: [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| bool enabled | Whether interface matching is enabled<br>**Since**: 26.0.0 |
| bool invert | Whether to invert the match result<br>**Since**: 26.0.0 |
| bool isPrefix | Whether the interface name is matched by prefix<br>**Since**: 26.0.0 |
| char ifName[OH_TRAFFICFILTER_IFNAMSIZ] | Interface name.<br> The string must be encoded in UTF-8 and must be NUL-terminated. The capacity of this buffer is [OH_TRAFFICFILTER_IFNAMSIZ](capi-net-trafficfilter-type-h.md#macros) bytes, including the terminating NUL character. Therefore, the maximum length of the interface name is [OH_TRAFFICFILTER_IFNAMSIZ](capi-net-trafficfilter-type-h.md#macros) - 1 bytes, excluding the terminating NUL character.<br> If [enabled](capi-trafficfilter-oh-trafficfilter-interfacematch.md) is true, this string must not be empty. If the string is not NUL-terminated within [OH_TRAFFICFILTER_IFNAMSIZ](capi-net-trafficfilter-type-h.md#macros) bytes, or if its length exceeds [OH_TRAFFICFILTER_IFNAMSIZ](capi-net-trafficfilter-type-h.md#macros) - 1 bytes, APIs using this structure return [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode).<br> If [enabled](capi-trafficfilter-oh-trafficfilter-interfacematch.md) is false, this field is ignored. It is recommended to set this buffer to all zeros when interface matching is disabled.<br>**Since**: 26.0.0 |


