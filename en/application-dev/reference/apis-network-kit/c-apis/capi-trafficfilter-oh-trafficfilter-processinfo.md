# OH_TrafficFilter_ProcessInfo

```c
typedef struct OH_TrafficFilter_ProcessInfo {...} OH_TrafficFilter_ProcessInfo
```

## Overview

Process information structure.<br> Stores process information returned by {@link OH_TrafficFilter_QueryProcess}.<br>Initialization rule:<br>Before calling {@link OH_TrafficFilter_QueryProcess}, the caller must clear this structure<br>to zero, for example by using memset, and then set {@link size} to the actual size of the<br>structure allocated by the caller, usually sizeof(OH_TrafficFilter_ProcessInfo).<br>ABI compatibility rule:<br>The library uses {@link size} to determine which output fields can be safely written.<br>Only fields fully covered by {@link size} are written by the library. If {@link size} is<br>smaller than the minimum size required to read the {@link size} field itself, the function<br>returns [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode). If {@link size} is larger than the<br>size known by the library, the extra fields are ignored.<br>Output validity rule:<br>When {@link OH_TrafficFilter_QueryProcess} returns [OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode), fields<br>covered by {@link size} contain valid output values. When the function returns an error,<br>the caller must not rely on the values of output fields other than {@link size}.

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


