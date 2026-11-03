# Ethernet_MacAddressInfo

```c
struct Ethernet_MacAddressInfo {...}
```

## Overview

Defines the MAC address of the Ethernet NIC.

**System capability**: SystemCapability.Communication.NetManager.Ethernet

**Since**: 26.0.0

**Related module**: [NetEthernet](capi-others-netethernet.md)

**Header file**: [net_ethernet_type.h](capi-net-ethernet-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char ifaceName[ETHERNET_MAX_STR_LEN] | The ethernet iface name.<br>**Since**: 26.0.0 |
| char macAddr[ETHERNET_MAX_STR_LEN] | The character array of device Mac address.<br>**Since**: 26.0.0 |


