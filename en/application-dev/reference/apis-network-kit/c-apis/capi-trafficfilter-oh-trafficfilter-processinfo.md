# OH_TrafficFilter_ProcessInfo

```c
struct OH_TrafficFilter_ProcessInfo {...}
```

## Overview

Process information structure.<br> Stores process information returned by OH_TrafficFilter_QueryProcess.<br> Initialization rule: Before calling OH_TrafficFilter_QueryProcess, the caller must clear this structure to zero, for example by using memset, and then set [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) to the actual size of the structure allocated by the caller, usually sizeof(OH_TrafficFilter_ProcessInfo).<br> ABI compatibility rule: The library uses [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) to determine which output fields can be safely written. Only fields fully covered by [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) are written by the library. If [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) is smaller than the minimum size required to read the [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) field itself, the function returns [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode). If [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) is larger than the size known by the library, the extra fields are ignored.<br> Output validity rule: When OH_TrafficFilter_QueryProcess returns [OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode), fields covered by [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) contain valid output values. When the function returns an error, the caller must not rely on the values of output fields other than [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md).

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Since**: 26.0.0

**Related module**: [TrafficFilter](capi-trafficfilter.md)

**Header file**: [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t size | the actual size of the structure allocated by the caller.<br>**Since**: 26.0.0 |
| uint32_t pid | Process ID<br>**Since**: 26.0.0 |
| uint32_t uid | User ID<br>**Since**: 26.0.0 |


