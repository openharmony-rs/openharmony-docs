# NetEthernet

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=2cc0b53d6d9308029bd0b32747c13d3e23336bee translatedAt=2026-08-12T09:53:51.751Z pushedAt=2026-08-12T10:56:07.273Z -->

## Overview

This module is used to obtain the MAC address list and IP address list of all Ethernet NICs on a device. It can be used to obtain the wired network connection information.<br> An Ethernet NIC is a wired network interface on a device. Each Ethernet NIC has a unique MAC address (physical address) and an IP address that can be configured. The MAC address uniquely identifies a network device in the network, and the IP address is used for network communication.<br> How to use: Call **OH_Ethernet_GetMacAddress** to obtain the MAC address list of Ethernet NICs, and call **OH_Ethernet_GetNetAddress** to obtain the IP address list of Ethernet NICs. The returned data structure contains the API name and the corresponding address.<br>

**Since**: 26.0.0

## Files

| Name | Description |
| -- | -- |
| [net_ethernet.h](capi-net-ethernet-h.md) | Provides C APIs for the Ethernet NIC module. |
| [net_ethernet_type.h](capi-net-ethernet-type-h.md) | Defines the data structures for the C APIs of the Ethernet NIC module. |