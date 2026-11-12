# MacAddressInfo

```TypeScript
export interface MacAddressInfo
```

Defines the name and MAC address of an Ethernet NIC.

**Since:** 14

<!--Device-ethernet-export interface MacAddressInfo--><!--Device-ethernet-export interface MacAddressInfo-End-->

**System capability:** SystemCapability.Communication.NetManager.Ethernet

## Modules to Import

```TypeScript
import { ethernet } from '@kit.NetworkKit';
```

## iface

```TypeScript
iface: string
```

Ethernet NIC name, for example, "eth0". It can be obtained through [getMacAddress](arkts-network-ethernet-getmacaddress-f.md).

**Type:** string

**Since:** 14

<!--Device-MacAddressInfo-iface: string--><!--Device-MacAddressInfo-iface: string-End-->

**System capability:** SystemCapability.Communication.NetManager.Ethernet

## macAddress

```TypeScript
macAddress: string
```

MAC address information of the Ethernet NIC, in the format of "XX:XX:XX:XX:XX:XX".

**Type:** string

**Since:** 14

<!--Device-MacAddressInfo-macAddress: string--><!--Device-MacAddressInfo-macAddress: string-End-->

**System capability:** SystemCapability.Communication.NetManager.Ethernet
