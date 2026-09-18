# net_ethernet.h

## Overview

Provides C APIs for the Ethernet NIC module.

**Library**: libnet_ethernet.so

**System capability**: SystemCapability.Communication.NetManager.Ethernet

**Since**: 26.0.0

**Related module**: [netmanager_ext](capi-netmanager-ext.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [int32_t OH_Ethernet_GetMacAddress(Ethernet_MacAddrInfoList *macAddrList)](#oh_ethernet_getmacaddress) | Obtains the MAC address list of Ethernet NICs. |
| [int32_t OH_Ethernet_GetNetAddress(Ethernet_NetAddrList *netAddrList)](#oh_ethernet_getnetaddress) | Obtains the IP address list of Ethernet NICs. |

## Function description

### OH_Ethernet_GetMacAddress()

```c
int32_t OH_Ethernet_GetMacAddress(Ethernet_MacAddrInfoList *macAddrList)
```

**Description**

Obtains the MAC address list of Ethernet NICs.

**System capability**: SystemCapability.Communication.NetManager.Ethernet

**Required permission**: ohos.permission.GET_ETHERNET_LOCAL_MAC

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| Ethernet_MacAddrInfoList *macAddrList | Pointer to the MAC address list of NICs. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0: Success.      <br>201: Missing permissions.      <br>2200001: Parameter error. 2200002: Service connection failure.      <br>2201005: Device information does not exist. |

### OH_Ethernet_GetNetAddress()

```c
int32_t OH_Ethernet_GetNetAddress(Ethernet_NetAddrList *netAddrList)
```

**Description**

Obtains the IP address list of Ethernet NICs.

**System capability**: SystemCapability.Communication.NetManager.Ethernet

**Required permission**: ohos.permission.GET_NETWORK_INFO

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| Ethernet_NetAddrList *netAddrList | Pointer to the IP address list of NICs. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0: Success.      <br>201: Missing permissions.      <br>2200001: Parameter error. 2200002: Service connection failure.      <br>2201005: Device information does not exist. |


