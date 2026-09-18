# Ethernet_NetAddr

```c
typedef struct Ethernet_NetAddr {...} Ethernet_NetAddr
```

## Overview

Defines a network address.

**Since**: 26.0.0

**Related module**: [netmanager_ext](capi-netmanager-ext.md)

**Header file**: [net_ethernet_type.h](capi-net-ethernet-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t family |  |
| uint8_t prefixlen |  |
| uint16_t port |  |
| char address[ETHERNET_MAX_STR_LEN] |  |


