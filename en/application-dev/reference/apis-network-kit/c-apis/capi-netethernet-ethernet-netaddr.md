# Ethernet_NetAddr

```c
struct Ethernet_NetAddr {...}
```

## Overview

Defines a network address.

**System capability**: SystemCapability.Communication.NetManager.Ethernet

**Since**: 26.0.0

**Related module**: [NetEthernet](capi-others-netethernet.md)

**Header file**: [net_ethernet_type.h](capi-net-ethernet-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t family | Network address family. IPv4 = 1, IPv6 = 2.<br>**Since**: 26.0.0 |
| uint8_t prefixlen | Prefix length.<br>**Since**: 26.0.0 |
| uint16_t port | Port number.<br>**Since**: 26.0.0 |
| char address[ETHERNET_MAX_STR_LEN] | IP address.<br>**Since**: 26.0.0 |


