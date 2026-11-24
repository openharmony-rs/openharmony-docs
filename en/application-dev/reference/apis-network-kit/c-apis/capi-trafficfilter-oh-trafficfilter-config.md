# OH_TrafficFilter_Config

```c
typedef struct OH_TrafficFilter_Config {...} OH_TrafficFilter_Config
```

## Overview

Defines the configuration struct of an NFQueue (a packet queuing channel in the Netfilter framework). Initialization rule: Before calling [OH_TrafficFilter_CreatePacketController](capi-net-trafficfilter-h.md#oh_trafficfilter_createpacketcontroller), the caller must clear this struct to zero (for example, using **memset**), and then set [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) to the actual size of the struct allocated by the caller, which is usually **sizeof(OH_TrafficFilter_Config)**. Binary compatibility rule (ABI, that is, application binary interface, which ensures that code compiled by old and new versions can recognize each other's struct layout): The system determines which fields can be safely read based on [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md). If [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) is smaller than the minimum size required by the current API, the API returns [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode). If [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) is larger than the size known to the system, the extra fields are ignored.

<!--Device-struct OH_TrafficFilter_Config {...}--><!--Device-struct OH_TrafficFilter_Config {...}-End-->

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Since**: 26.0.1

**Related module**: [TrafficFilter](capi-network-kit-trafficfilter.md)

**Header file**: [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t size | Actual size of the struct allocated by the caller.<br>**Since**: 26.0.1<br><!--Device-uint32_t size--><!--Device-uint32_t size-End--> |
| uint32_t packetCopyMode | Packet copy mode. For details, see [OH_TrafficFilter_PacketCopyMode](capi-net-trafficfilter-type-h.md#oh_trafficfilter_packetcopymode). The default value is **2**.<br>**Since**: 26.0.1<br><!--Device-uint32_t packetCopyMode--><!--Device-uint32_t packetCopyMode-End--> |
| uint32_t packetCopyLen | Length (in bytes) of the packet copied by the NFQueue. The value ranges from 0 to 0xFFFF. 0xFFFF means copying the entire packet, and other values mean copying the packet header of the specified length. The default value is 0xFFFF.<br>**Since**: 26.0.1<br><!--Device-uint32_t packetCopyLen--><!--Device-uint32_t packetCopyLen-End--> |
| uint32_t nfqueueMaxlen | Maximum queue length (number of packets) of the NFQueue. **0** means using the system default value (1024).<br>**Since**: 26.0.1<br><!--Device-uint32_t nfqueueMaxlen--><!--Device-uint32_t nfqueueMaxlen-End--> |
| uint32_t nfqueueFlags | NFQueue queue flag. For details, see [OH_TRAFFICFILTER_NFQUEUE_FLAG_FAIL_OPEN](capi-net-trafficfilter-type-h.md#macros). The default value is **0x1**.<br>**Since**: 26.0.1<br><!--Device-uint32_t nfqueueFlags--><!--Device-uint32_t nfqueueFlags-End--> |


