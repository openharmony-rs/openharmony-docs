# Ethernet_MacAddrInfoList

```c
struct Ethernet_MacAddrInfoList {...}
```

## Overview

Defines the MAC address list of Ethernet NICs.

**System capability**: SystemCapability.Communication.NetManager.Ethernet

**Since**: 26.0.0

**Related module**: [NetEthernet](capi-others-netethernet.md)

**Header file**: [net_ethernet_type.h](capi-net-ethernet-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [Ethernet_MacAddressInfo](capi-netethernet-ethernet-macaddressinfo.md) macInfoList[ETHERNET_MAX_NET_SIZE] | The ethernet mac address list.<br>**Since**: 26.0.0 |
| int32_t macInfoListSize | Actual size of the **macInfoList** array.<br>**Since**: 26.0.0 |


