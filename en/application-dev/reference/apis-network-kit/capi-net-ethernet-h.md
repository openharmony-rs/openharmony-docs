# net_ethernet.h

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=417110679ffbc4e6910173369ae0f364f3a7739a translatedAt=2026-09-28T01:05:24.548Z pushedAt=2026-10-09T01:39:37.105Z -->


## Overview

Provides C APIs for the Ethernet NIC module.

**File to include:** <network/netmanager_ext/net_ethernet.h>

**Library:** libnet_ethernet.so

**System capability:** SystemCapability.Communication.NetManager.Ethernet

**Since:** 26.0.0

**Related module:** [NetEthernet](capi-netethernet.md)

## Summary

### Functions

| Name | Description |
| -- | -- |
| [int32_t OH_Ethernet_GetMacAddress(Ethernet_MacAddrInfoList *macAddrList)](#oh_ethernet_getmacaddress) | Obtains the MAC address list of the Ethernet NIC. |
| [int32_t OH_Ethernet_GetNetAddress(Ethernet_NetAddrList *netAddrList)](#oh_ethernet_getnetaddress) | Obtains the IP address list of the Ethernet NIC. |

## Function Description

### OH_Ethernet_GetMacAddress()

```c
int32_t OH_Ethernet_GetMacAddress(Ethernet_MacAddrInfoList *macAddrList)
```

**Description**

Obtains the MAC address list of the Ethernet NIC.

**System capability:** SystemCapability.Communication.NetManager.Ethernet

**Required permissions:** ohos.permission.GET_ETHERNET_LOCAL_MAC

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [Ethernet_MacAddrInfoList](capi-netethernet-ethernet-macaddrinfolist.md) *macAddrList | Pointer to the MAC address list of the Ethernet NIC. |

**Return**

| Type | Description |
| -- | -- |
| int32_t | Result code.<br> 0 - success. 201 - permission denied.<br>         2200001 - invalid parameter. 2200002 - failed to connect to the service.<br>         2201005 - device information does not exist. |

### OH_Ethernet_GetNetAddress()

```c
int32_t OH_Ethernet_GetNetAddress(Ethernet_NetAddrList *netAddrList)
```

**Description**

Obtains the IP address list of the Ethernet NIC.

**System capability:** SystemCapability.Communication.NetManager.Ethernet

**Required permissions:** ohos.permission.GET_NETWORK_INFO

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [Ethernet_NetAddrList](capi-netethernet-ethernet-netaddrlist.md) *netAddrList | Pointer to the IP address list of the Ethernet NIC. |

**Return**

| Type | Description |
| -- | -- |
| int32_t | Result code.<br> 0 - success. 201 - permission denied.<br>         2200001 - invalid parameter. 2200002 - failed to connect to the service.<br>         2201005 - device information does not exist. |


