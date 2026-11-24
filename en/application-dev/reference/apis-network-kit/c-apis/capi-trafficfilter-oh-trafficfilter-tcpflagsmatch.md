# OH_TrafficFilter_TCPFlagsMatch

```c
typedef struct OH_TrafficFilter_TCPFlagsMatch {...} OH_TrafficFilter_TCPFlagsMatch
```

## Overview

Defines the TCP flag matching condition. It is valid only for the TCP protocol.

<!--Device-struct OH_TrafficFilter_TCPFlagsMatch {...}--><!--Device-struct OH_TrafficFilter_TCPFlagsMatch {...}-End-->

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Since**: 26.0.1

**Related module**: [TrafficFilter](capi-network-kit-trafficfilter.md)

**Header file**: [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| bool enable | Whether to enable TCP flag matching. The value **true** means to enable TCP flag matching, and **false** means not to enable TCP flag matching.<br>**Since**: 26.0.1<br><!--Device-bool enable--><!--Device-bool enable-End--> |
| uint8_t flagMask | Flag mask (specifies the flags to check).<br>**Since**: 26.0.1<br><!--Device-uint8_t flagMask--><!--Device-uint8_t flagMask-End--> |
| uint8_t flagComp | Flag comparison value (value to compare against the flags).<br>**Since**: 26.0.1<br><!--Device-uint8_t flagComp--><!--Device-uint8_t flagComp-End--> |


