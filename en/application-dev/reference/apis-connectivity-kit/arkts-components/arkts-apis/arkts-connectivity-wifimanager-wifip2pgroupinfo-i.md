# WifiP2pGroupInfo

```TypeScript
interface WifiP2pGroupInfo
```

P2P group information.

@typedef WifiP2pGroupInfo

**Since:** 9

<!--Device-wifiManager-interface WifiP2pGroupInfo--><!--Device-wifiManager-interface WifiP2pGroupInfo-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## clientDevices

```TypeScript
clientDevices: WifiP2pDevice[]
```

Client list

**Type:** [WifiP2pDevice](arkts-connectivity-wifimanager-wifip2pdevice-i.md)[]

**Since:** 9

<!--Device-WifiP2pGroupInfo-clientDevices: WifiP2pDevice[]--><!--Device-WifiP2pGroupInfo-clientDevices: WifiP2pDevice[]-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## frequency

```TypeScript
frequency: number
```

Frequency

**Type:** number

**Since:** 9

<!--Device-WifiP2pGroupInfo-frequency: int--><!--Device-WifiP2pGroupInfo-frequency: int-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## goIpAddress

```TypeScript
goIpAddress: string
```

Group owner IP address

**Type:** string

**Since:** 9

<!--Device-WifiP2pGroupInfo-goIpAddress: string--><!--Device-WifiP2pGroupInfo-goIpAddress: string-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## groupName

```TypeScript
groupName: string
```

Group name

**Type:** string

**Since:** 9

<!--Device-WifiP2pGroupInfo-groupName: string--><!--Device-WifiP2pGroupInfo-groupName: string-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## interface

```TypeScript
interface: string
```

Interface name

**Type:** string

**Since:** 9

<!--Device-WifiP2pGroupInfo-interface: string--><!--Device-WifiP2pGroupInfo-interface: string-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## isP2pGo

```TypeScript
isP2pGo: boolean
```

Indicates whether it is group owner

**Type:** boolean

**Since:** 9

<!--Device-WifiP2pGroupInfo-isP2pGo: boolean--><!--Device-WifiP2pGroupInfo-isP2pGo: boolean-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## networkId

```TypeScript
networkId: number
```

Network ID

**Type:** number

**Since:** 9

<!--Device-WifiP2pGroupInfo-networkId: int--><!--Device-WifiP2pGroupInfo-networkId: int-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## ownerInfo

```TypeScript
ownerInfo: WifiP2pDevice
```

Group owner information

**Type:** [WifiP2pDevice](arkts-connectivity-wifimanager-wifip2pdevice-i.md)

**Since:** 9

<!--Device-WifiP2pGroupInfo-ownerInfo: WifiP2pDevice--><!--Device-WifiP2pGroupInfo-ownerInfo: WifiP2pDevice-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## passphrase

```TypeScript
passphrase: string
```

The group passphrase

**Type:** string

**Since:** 9

<!--Device-WifiP2pGroupInfo-passphrase: string--><!--Device-WifiP2pGroupInfo-passphrase: string-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P
