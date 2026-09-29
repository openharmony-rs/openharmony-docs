# NetIpMacInfo

```TypeScript
export interface NetIpMacInfo
```

Defines information about entries in the IP neighbor table.

**Since:** 22

<!--Device-connection-export interface NetIpMacInfo--><!--Device-connection-export interface NetIpMacInfo-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## iface

```TypeScript
iface: string
```

NIC name.

**Type:** string

**Since:** 22

<!--Device-NetIpMacInfo-iface: string--><!--Device-NetIpMacInfo-iface: string-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

## ipAddress

```TypeScript
ipAddress: NetAddress
```

IP address information.

**Type:** [NetAddress](arkts-network-connection-netaddress-i.md)

**Since:** 22

<!--Device-NetIpMacInfo-ipAddress: NetAddress--><!--Device-NetIpMacInfo-ipAddress: NetAddress-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

## macAddress

```TypeScript
macAddress: string
```

MAC address.

**Type:** string

**Since:** 22

<!--Device-NetIpMacInfo-macAddress: string--><!--Device-NetIpMacInfo-macAddress: string-End-->

**System capability:** SystemCapability.Communication.NetManager.Core
