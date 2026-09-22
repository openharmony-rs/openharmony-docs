# Ethernet_MacAddressInfo

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=91d29d346031c525e80e74559440427fdd76d0ca translatedAt=2026-08-12T09:53:18.638Z pushedAt=2026-08-12T10:56:07.261Z -->

```c
typedef struct Ethernet_MacAddressInfo {...} Ethernet_MacAddressInfo
```

## Overview

Defines the MAC address of the Ethernet NIC.

**Since**: 26.0.0

**Related module:** [NetEthernet](capi-netethernet.md)

**File to include:** [net_ethernet_type.h](capi-net-ethernet-type-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| char ifaceName[ETHERNET_MAX_STR_LEN] | Name of the Ethernet NIC. |
| char macAddr[ETHERNET_MAX_STR_LEN] | MAC address of the Ethernet NIC. |