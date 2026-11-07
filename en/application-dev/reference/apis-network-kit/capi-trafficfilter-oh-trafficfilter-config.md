# OH_TrafficFilter_Config

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=7cd2f817688c245414ad83d771260e8515966ace translatedAt=2026-11-04T06:29:21.795Z pushedAt=2026-11-04T08:04:44.842Z nl=1 -->

```c
typedef struct OH_TrafficFilter_Config {...} OH_TrafficFilter_Config
```

## Overview

Configuration struct of NFQueue (a packet queuing channel in the Netfilter framework).

Initialization rule: Before calling [OH_TrafficFilter_CreatePacketController](capi-net-trafficfilter-h.md#oh_trafficfilter_createpacketcontroller), the caller must clear this struct to zero (for example, using memset), and then set [size](#member-variables) to the actual size of the struct allocated by the caller, which is usually sizeof(OH_TrafficFilter_Config).

Binary compatibility rule (ABI, that is, application binary interface, which ensures that code compiled by old and new versions can recognize each other's struct layout): The system determines which fields can be safely read based on [size](#member-variables). If [size](#member-variables) is smaller than the minimum size required by the current API, the API returns [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode). If [size](#member-variables) is larger than the size known to the system, the extra fields are ignored.

**Since:** 26.0.1

**Related module:** [TrafficFilter](capi-trafficfilter.md)

**File to include:** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| uint32_t size | Actual size of the struct allocated by the caller. |
| uint32_t packetCopyMode | Packet copy mode. For details, see [OH_TrafficFilter_PacketCopyMode](capi-trafficfilter-oh-trafficfilter-packetcopymode.md). Default value (2) |
| uint32_t packetCopyLen | Length (in bytes) of the packet copied by NFQueue. The value ranges from 0 to 0xFFFF. 0xFFFF indicates copying the entire packet, and other values indicate copying the packet header of the specified length. Default value (0xFFFF) |
| uint32_t nfqueueMaxlen | Maximum queue length (number of packets) of NFQueue. 0 indicates using the system default value (1024). |
| uint32_t nfqueueFlags | NFQueue queue flag. For details, see [OH_TRAFFICFILTER_NFQUEUE_FLAG_FAIL_OPEN](capi-net-trafficfilter-type-h.md#macros). Default value (1) |
