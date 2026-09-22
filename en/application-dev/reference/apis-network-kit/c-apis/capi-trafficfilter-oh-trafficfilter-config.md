# OH_TrafficFilter_Config

```c
typedef struct OH_TrafficFilter_Config {...} OH_TrafficFilter_Config
```

## Overview

NFQueue configuration structure - If `config` is **NULL**, the implementation applies the following default values: - `packetCopyLen` = 0xFFFF (copy entire packet) - `nfqueueMaxlen` = 0 (use system default, which is 1024) - `nfqueueFlags` = OH_TRAFFICFILTER_NFQUEUE_FLAG_FAIL_OPEN - If `config` is **non-NULL**, the caller **must**: 1. Zero-initialize the entire structure (e.g., `memset(&cfg, 0, sizeof(cfg))`). 2. Set `size` = `sizeof(OH_TrafficFilter_Config)`. 3. Set all other fields to valid values within the defined ranges (see below). - **Failure** to follow this contract (e.g., incorrect `size`, out-of-range field values) will cause the API to return `OH_TRAFFICFILTER_ERROR_INVALID_PARAM`.

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Since**: 26.0.1

**Related module**: [TrafficFilter](capi-trafficfilter.md)

**Header file**: [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t size | Must be set to `sizeof(OH_TrafficFilter_Config)` by the caller. The caller is required to zero-initialize the structure first, then set this field. The implementation uses this value to determine the valid data range for binary compatibility.<br>**Since**: 26.0.1 |
| uint32_t packetCopyMode | NFQueue packet copy mode, see OH_TrafficFilter_PacketCopyMode<br>**Since**: 26.0.1 |
| uint32_t packetCopyLen | NFQueue packet copy length in bytes, 0xFFFF means entire packet, smaller values copy only header<br>**Since**: 26.0.1 |
| uint32_t nfqueueMaxlen | NFQueue maximum queue length (number of packets), 0 means system default (1024)<br>**Since**: 26.0.1 |
| uint32_t nfqueueFlags | NFQueue queue flags, see OH_TRAFFICFILTER_NFQUEUE_FLAG_* definitions<br>**Since**: 26.0.1 |


