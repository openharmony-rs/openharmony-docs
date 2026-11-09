# WifiP2pGroupInfo

```TypeScript
interface WifiP2pGroupInfo
```

Represents the P2P group information.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [WifiP2pGroupInfo](arkts-connectivity-wifimanager-wifip2pgroupinfo-i.md)

<!--Device-wifi-interface WifiP2pGroupInfo--><!--Device-wifi-interface WifiP2pGroupInfo-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## clientDevices

```TypeScript
clientDevices: WifiP2pDevice[]
```

List of connected devices.

**Type:** [WifiP2pDevice](arkts-connectivity-wifi-wifip2pdevice-i.md)[]

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [clientDevices](arkts-connectivity-wifimanager-wifip2pgroupinfo-i.md#clientdevices)

<!--Device-WifiP2pGroupInfo-clientDevices: WifiP2pDevice[]--><!--Device-WifiP2pGroupInfo-clientDevices: WifiP2pDevice[]-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## frequency

```TypeScript
frequency: number
```

Frequency of the group, in MHz.

**Type:** number

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [frequency](arkts-connectivity-wifimanager-wifip2pgroupinfo-i.md#frequency)

<!--Device-WifiP2pGroupInfo-frequency: number--><!--Device-WifiP2pGroupInfo-frequency: number-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## goIpAddress

```TypeScript
goIpAddress: string
```

IP address of the group.

**Type:** string

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [goIpAddress](arkts-connectivity-wifimanager-wifip2pgroupinfo-i.md#goipaddress)

<!--Device-WifiP2pGroupInfo-goIpAddress: string--><!--Device-WifiP2pGroupInfo-goIpAddress: string-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## groupName

```TypeScript
groupName: string
```

Group name.

**Type:** string

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [groupName](arkts-connectivity-wifimanager-wifip2pgroupinfo-i.md#groupname)

<!--Device-WifiP2pGroupInfo-groupName: string--><!--Device-WifiP2pGroupInfo-groupName: string-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## interface

```TypeScript
interface: string
```

Interface name.

**Type:** string

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [interface](arkts-connectivity-wifimanager-wifip2pgroupinfo-i.md#interface)

<!--Device-WifiP2pGroupInfo-interface: string--><!--Device-WifiP2pGroupInfo-interface: string-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## isP2pGo

```TypeScript
isP2pGo: boolean
```

Whether the device is the group owner. The value **true** indicates that the device is the group owner, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [isP2pGo](arkts-connectivity-wifimanager-wifip2pgroupinfo-i.md#isp2pgo)

<!--Device-WifiP2pGroupInfo-isP2pGo: boolean--><!--Device-WifiP2pGroupInfo-isP2pGo: boolean-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## networkId

```TypeScript
networkId: number
```

Network ID.

**Type:** number

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [networkId](arkts-connectivity-wifimanager-wifip2pgroupinfo-i.md#networkid)

<!--Device-WifiP2pGroupInfo-networkId: number--><!--Device-WifiP2pGroupInfo-networkId: number-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## ownerInfo

```TypeScript
ownerInfo: WifiP2pDevice
```

Device information of the group.

**Type:** [WifiP2pDevice](arkts-connectivity-wifi-wifip2pdevice-i.md)

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [ownerInfo](arkts-connectivity-wifimanager-wifip2pgroupinfo-i.md#ownerinfo)

<!--Device-WifiP2pGroupInfo-ownerInfo: WifiP2pDevice--><!--Device-WifiP2pGroupInfo-ownerInfo: WifiP2pDevice-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## passphrase

```TypeScript
passphrase: string
```

Passphrase of the group.

**Type:** string

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [passphrase](arkts-connectivity-wifimanager-wifip2pgroupinfo-i.md#passphrase)

<!--Device-WifiP2pGroupInfo-passphrase: string--><!--Device-WifiP2pGroupInfo-passphrase: string-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P
