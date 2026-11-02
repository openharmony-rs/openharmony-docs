# Ethernet_NetAddrList

```c
struct Ethernet_NetAddrList {...}
```

## Overview

Defines the network address list of Ethernet NICs.

**System capability**: SystemCapability.Communication.NetManager.Ethernet

**Since**: 26.0.0

**Related module**: [NetEthernet](capi-others-netethernet.md)

**Header file**: [net_ethernet_type.h](capi-net-ethernet-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [Ethernet_NetAddrInfo](capi-netethernet-ethernet-netaddrinfo.md) netAddrList[ETHERNET_MAX_NET_SIZE] | The ethernet network address list.<br>**Since**: 26.0.0 |
| int32_t netAddrListSize | Actual size of **netAddrList**.<br>**Since**: 26.0.0 |


