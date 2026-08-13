# net_ethernet.h

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=434de930b1eb27757cab0c168892c60abe5b3e26 translatedAt=2026-08-11T08:14:36.345Z pushedAt=2026-08-12T11:04:30.952Z -->

## Overview

Provides C APIs for the Ethernet NIC module.

**File to include:** &lt;network/net_ethernet/net_ethernet.h&gt;

**Library:** libnet_ethernet.so

**System capability:** SystemCapability.Communication.NetManager.Ethernet

**Since**: 26.0.0

**Related module:** [NetEthernet](capi-netethernet.md)

## Summary

### Functions

| Name | Description |
| -- | -- |
| [int32_t OH_Ethernet_GetMacAddress(Ethernet_MacAddrInfoList *macAddrList)](#oh_ethernet_getmacaddress) | Obtains the MAC address list of Ethernet NICs. |
| [int32_t OH_Ethernet_GetNetAddress(Ethernet_NetAddrList *netAddrList)](#oh_ethernet_getnetaddress) | Obtains the IP address list of Ethernet NICs. |

## Function Description

### OH_Ethernet_GetMacAddress()

```c
int32_t OH_Ethernet_GetMacAddress(Ethernet_MacAddrInfoList *macAddrList)
```

**Description**

Obtains the MAC address list of Ethernet NICs.

**System capability:** SystemCapability.Communication.NetManager.Ethernet

**Required permissions:** ohos.permission.GET_ETHERNET_LOCAL_MAC

**Since**: 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [Ethernet_MacAddrInfoList](capi-netethernet-ethernet-macaddrinfolist.md) *macAddrList | Pointer to the MAC address list of NICs. |

**Returns**

| Type | Description |
| -- | -- |
| int32_t | **0**: Success.<br>         **201**: Missing permissions.<br>         **2200001**: Parameter error. **2200002**: Service connection failure.<br>         **2201005**: Device information does not exist. |

### OH_Ethernet_GetNetAddress()

```c
int32_t OH_Ethernet_GetNetAddress(Ethernet_NetAddrList *netAddrList)
```

**Description**

Obtains the IP address list of Ethernet NICs.

**System capability:** SystemCapability.Communication.NetManager.Ethernet

**Required permissions:** ohos.permission.GET_NETWORK_INFO

**Since**: 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [Ethernet_NetAddrList](capi-netethernet-ethernet-netaddrlist.md) *netAddrList | Pointer to the IP address list of NICs. |

**Returns**

| Type | Description |
| -- | -- |
| int32_t | **0**: Success.<br>         **201**: Missing permissions.<br>         **2200001**: Parameter error. **2200002**: Service connection failure.<br>         **2201005**: Device information does not exist. |