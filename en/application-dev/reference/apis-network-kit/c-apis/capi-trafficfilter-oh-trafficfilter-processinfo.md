# OH_TrafficFilter_ProcessInfo

```c
typedef struct OH_TrafficFilter_ProcessInfo {...} OH_TrafficFilter_ProcessInfo
```

## Overview

Defines the process information struct. Stores the process information returned by [OH_TrafficFilter_QueryProcess](capi-net-trafficfilter-h.md#oh_trafficfilter_queryprocess). Initialization rule: Before calling [OH_TrafficFilter_QueryProcess](capi-net-trafficfilter-h.md#oh_trafficfilter_queryprocess), the caller must clear this struct to zero (for example, using memset), and then set [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) to the actual size of the struct allocated by the caller, which is usually **sizeof(OH_TrafficFilter_ProcessInfo)**. Binary compatibility rule (ABI, that is, Application Binary Interface, which ensures that code compiled by old and new versions can recognize each other's struct layout): The system uses [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) to determine which output fields can be safely written. Only fields fully covered by [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) are written by the system. If [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) is smaller than the minimum size required to read the [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) field itself, the API returns [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode). If [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) is larger than the size known to the system, the extra fields are ignored. Output validity rule: When [OH_TrafficFilter_QueryProcess](capi-net-trafficfilter-h.md#oh_trafficfilter_queryprocess) returns [OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode), the fields covered by [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) contain valid output values. When the API returns an error, the caller must not rely on the values of output fields other than [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md).

<!--Device-struct OH_TrafficFilter_ProcessInfo {...}--><!--Device-struct OH_TrafficFilter_ProcessInfo {...}-End-->

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Since**: 26.0.0

**Related module**: [TrafficFilter](capi-network-kit-trafficfilter.md)

**Header file**: [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t size | Actual size of the struct allocated by the caller.<br>**Since**: 26.0.0<br><!--Device-uint32_t size--><!--Device-uint32_t size-End--> |
| uint32_t pid | Process ID.<br>**Since**: 26.0.0<br><!--Device-uint32_t pid--><!--Device-uint32_t pid-End--> |
| uint32_t uid | App UID.<br>**Since**: 26.0.0<br><!--Device-uint32_t uid--><!--Device-uint32_t uid-End--> |


