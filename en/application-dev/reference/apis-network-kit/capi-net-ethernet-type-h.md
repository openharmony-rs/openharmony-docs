# net_ethernet_type.h

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=993bc5d275badf6a555bd5d61b59a1ec117055af translatedAt=2026-09-23T01:12:39.599Z pushedAt=2026-09-24T06:00:14.090Z -->


## Overview

Defines the data structures for the C APIs of the Ethernet NIC module.

**File to include:** <network/netmanager_ext/net_ethernet_type.h>

**Library:** libnet_ethernet.so

**System capability:** SystemCapability.Communication.NetManager.Ethernet

**Since**: 26.0.0

**Related module:** [NetEthernet](capi-netethernet.md)

## Summary

### Structs

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [Ethernet_MacAddressInfo](capi-netethernet-ethernet-macaddressinfo.md) | Ethernet_MacAddressInfo | Defines the MAC address of the Ethernet NIC. |
| [Ethernet_MacAddrInfoList](capi-netethernet-ethernet-macaddrinfolist.md) | Ethernet_MacAddrInfoList | Defines the MAC address list of Ethernet NICs. |
| [Ethernet_NetAddr](capi-netethernet-ethernet-netaddr.md) | Ethernet_NetAddr | Defines a network address. |
| [Ethernet_NetAddrInfo](capi-netethernet-ethernet-netaddrinfo.md) | Ethernet_NetAddrInfo | Defines the network address of the Ethernet NIC, including the Ethernet NIC name and the network address information. |
| [Ethernet_NetAddrList](capi-netethernet-ethernet-netaddrlist.md) | Ethernet_NetAddrList | Defines the network address list of Ethernet NICs. |

### Macros

| Name | Description |
| -- | -- |
| ETHERNET_MAX_NET_SIZE 32 | Maximum number of Ethernet NIC connections.<br>**Since:** 26.0.0 |
| ETHERNET_MAX_STR_LEN 256 | Maximum length of the Ethernet NIC MAC address and IP address.<br>**Since:** 26.0.0 |

