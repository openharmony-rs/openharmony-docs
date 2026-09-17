# OH_TrafficFilter_IPAddress

```c
typedef struct OH_TrafficFilter_IPAddress {...} OH_TrafficFilter_IPAddress
```

## Overview

IP address in binary form, supports both IPv4 and IPv6

**Since**: 26.0.0

**Related module**: [TrafficFilter](capi-trafficfilter.md)

**Header file**: [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [OH_TrafficFilter_IPFamily](capi-net-trafficfilter-type-h.md#oh_trafficfilter_ipfamily) family | Address family, If not explicitly set, IPv4 is used by default.<br>**Since**: 26.0.0 |
| uint8_t addr[OH_TRAFFICFILTER_IP_ADDRLEN] | IP address bytes.<br> The bytes must be stored in network byte order. For IPv4, {@link addr}[0] to {@link addr}[3] store the IPv4 address,<br>and {@link addr}[4] to {@link addr}[15] must be set to 0.<br>For IPv6, {@link addr}[0] to {@link addr}[15] store the IPv6 address.<br>If the bytes do not match the address layout required by {@link family}, APIs using this structure return [OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode).<br>**Since**: 26.0.0 |


