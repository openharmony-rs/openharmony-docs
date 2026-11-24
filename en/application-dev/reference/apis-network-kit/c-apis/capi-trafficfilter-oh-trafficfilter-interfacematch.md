# OH_TrafficFilter_InterfaceMatch

```c
typedef struct OH_TrafficFilter_InterfaceMatch {...} OH_TrafficFilter_InterfaceMatch
```

## Overview

Defines the interface match condition.

<!--Device-struct OH_TrafficFilter_InterfaceMatch {...}--><!--Device-struct OH_TrafficFilter_InterfaceMatch {...}-End-->

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Since**: 26.0.0

**Related module**: [TrafficFilter](capi-network-kit-trafficfilter.md)

**Header file**: [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| bool enabled | Whether to enable interface match. The value **true** means to enable interface match,and **false** means not to enable interface match.<br>**Since**: 26.0.0<br><!--Device-bool enabled--><!--Device-bool enabled-End--> |
| bool invert | Whether to invert the match result. The value **true** means to invert the match result, and **false** means not to invert the match result.<br>**Since**: 26.0.0<br><!--Device-bool invert--><!--Device-bool invert-End--> |
| bool isPrefix | Whether to match the interface name by prefix. The value **true** means to match by prefix, and **false** means not to match by prefix.<br>**Since**: 26.0.0<br><!--Device-bool isPrefix--><!--Device-bool isPrefix-End--> |
| char ifName[OH_TRAFFICFILTER_IFNAMSIZ] | Interface name. The string must be UTF-8 encoded and NULL-terminated. The buffer capacity is [OH_TRAFFICFILTER_IFNAMSIZ](capi-net-trafficfilter-type-h.md#macros) bytes, including the terminating NULL character. Therefore, the maximum length of the interface name is [OH_TRAFFICFILTER_IFNAMSIZ](capi-net-trafficfilter-type-h.md#macros) - 1 bytes, excluding the terminating NULL character. If [enabled](capi-trafficfilter-oh-trafficfilter-interfacematch.md) is **true**, the string cannot be empty. If the string is not NULL-terminated within [OH_TRAFFICFILTER_IFNAMSIZ](capi-net-trafficfilter-type-h.md#macros) bytes, or its length exceeds [OH_TRAFFICFILTER_IFNAMSIZ](capi-net-trafficfilter-type-h.md#macros) - 1 bytes, the API that uses this struct returns [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode). If [enabled](capi-trafficfilter-oh-trafficfilter-interfacematch.md) is **false**, this field is ignored. It is recommended to set the entire buffer to zero when interface match is disabled.<br>**Since**: 26.0.0<br><!--Device-char ifName[OH_TRAFFICFILTER_IFNAMSIZ]--><!--Device-char ifName[OH_TRAFFICFILTER_IFNAMSIZ]-End--> |


