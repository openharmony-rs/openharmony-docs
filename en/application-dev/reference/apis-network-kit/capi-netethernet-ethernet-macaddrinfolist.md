# Ethernet_MacAddrInfoList

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=91d29d346031c525e80e74559440427fdd76d0ca translatedAt=2026-08-12T09:53:24.483Z pushedAt=2026-08-12T10:56:07.268Z -->

```c
typedef struct Ethernet_MacAddrInfoList {...} Ethernet_MacAddrInfoList
```

## Overview

Defines the MAC address list of Ethernet NICs.

**Since**: 26.0.0

**Related module:** [NetEthernet](capi-netethernet.md)

**File to include:** [net_ethernet_type.h](capi-net-ethernet-type-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| [Ethernet_MacAddressInfo](capi-netethernet-ethernet-macaddressinfo.md) macInfoList[ETHERNET_MAX_NET_SIZE] | MAC address list of Ethernet NICs. |
| int32_t macInfoListSize | Actual size of the **macInfoList** array. |