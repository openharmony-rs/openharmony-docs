# OH_TrafficFilter_Config

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=55df9c11d6d7c450cc6d9d1ac7b0b998394459f6 translatedAt=2026-09-23T01:35:13.799Z pushedAt=2026-09-24T06:00:14.139Z -->

```c
typedef struct OH_TrafficFilter_Config {...} OH_TrafficFilter_Config
```

## Overview

Defines the configuration struct of an NFQueue (a packet queuing channel in the Netfilter framework).

Initialization rule: Before calling [OH_TrafficFilter_CreatePacketController](capi-net-trafficfilter-h.md#oh_trafficfilter_createpacketcontroller), the caller must clear this struct to zero (for example, using **memset**), and then set [size](#member-variables) to the actual size of the struct allocated by the caller, which is usually **sizeof(OH_TrafficFilter_Config)**.

Binary compatibility rule (ABI, that is, application binary interface, which ensures that code compiled by old and new versions can recognize each other's struct layout): The system determines which fields can be safely read based on [size](#member-variables). If [size](#member-variables) is smaller than the minimum size required by the current API, the API returns [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode). If [size](#member-variables) is larger than the size known to the system, the extra fields are ignored.

**Since:** 26.0.1

**Related module:** [TrafficFilter](capi-trafficfilter.md)

**File to include:** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| uint32_t size | Actual size of the struct allocated by the caller. |
| uint32_t packetCopyMode | Packet copy mode. For details, see [OH_TrafficFilter_PacketCopyMode](capi-trafficfilter-oh-trafficfilter-packetcopymode.md). The default value is **2**. |
| uint32_t packetCopyLen | Length (in bytes) of the packet copied by the NFQueue. The value ranges from 0 to 0xFFFF. 0xFFFF means copying the entire packet, and other values mean copying the packet header of the specified length. The default value is 0xFFFF. |
| uint32_t nfqueueMaxlen | Maximum queue length (number of packets) of the NFQueue. **0** means using the system default value (1024). |
| uint32_t nfqueueFlags | NFQueue queue flag. For details, see [OH_TRAFFICFILTER_NFQUEUE_FLAG_FAIL_OPEN](capi-net-trafficfilter-type-h.md#macros). The default value is **0x1**. |
