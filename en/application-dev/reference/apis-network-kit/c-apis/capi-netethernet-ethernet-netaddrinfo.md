# Ethernet_NetAddrInfo

```c
struct Ethernet_NetAddrInfo {...}
```

## Overview

Defines the network address of the Ethernet NIC, including the Ethernet NIC name and the network address information.

**System capability**: SystemCapability.Communication.NetManager.Ethernet

**Since**: 26.0.0

**Related module**: [NetEthernet](capi-others-netethernet.md)

**Header file**: [net_ethernet_type.h](capi-net-ethernet-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char ifaceName[ETHERNET_MAX_STR_LEN] | The ethernet iface name.<br>**Since**: 26.0.0 |
| [Ethernet_NetAddr](capi-netethernet-ethernet-netaddr.md) netAddrInfo[ETHERNET_MAX_NET_SIZE] | The network address.<br>**Since**: 26.0.0 |
| int32_t netAddrInfoSize | Actual size of the **netAddrInfo** array.<br>**Since**: 26.0.0 |


