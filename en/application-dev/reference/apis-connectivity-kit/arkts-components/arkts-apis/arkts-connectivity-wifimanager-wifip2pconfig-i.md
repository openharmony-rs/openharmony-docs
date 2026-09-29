# WifiP2PConfig

```TypeScript
interface WifiP2PConfig
```

P2P config.

@typedef WifiP2PConfig

**Since:** 9

<!--Device-wifiManager-interface WifiP2PConfig--><!--Device-wifiManager-interface WifiP2PConfig-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## deviceAddress

```TypeScript
deviceAddress: string
```

Device mac address

**Type:** string

**Since:** 9

<!--Device-WifiP2PConfig-deviceAddress: string--><!--Device-WifiP2PConfig-deviceAddress: string-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## deviceAddressType

```TypeScript
deviceAddressType?: DeviceAddressType
```

Device mac address type

**Type:** [DeviceAddressType](arkts-connectivity-wifimanager-deviceaddresstype-e.md)

**Since:** 10

<!--Device-WifiP2PConfig-deviceAddressType?: DeviceAddressType--><!--Device-WifiP2PConfig-deviceAddressType?: DeviceAddressType-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## goBand

```TypeScript
goBand: GroupOwnerBand
```

Group owner band

**Type:** [GroupOwnerBand](arkts-connectivity-wifimanager-groupownerband-e.md)

**Since:** 9

<!--Device-WifiP2PConfig-goBand: GroupOwnerBand--><!--Device-WifiP2PConfig-goBand: GroupOwnerBand-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## goFreq

```TypeScript
goFreq?: number
```

Group owner frequency

**Type:** number

**Since:** 23

<!--Device-WifiP2PConfig-goFreq?: int--><!--Device-WifiP2PConfig-goFreq?: int-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## groupName

```TypeScript
groupName: string
```

Group name

**Type:** string

**Since:** 9

<!--Device-WifiP2PConfig-groupName: string--><!--Device-WifiP2PConfig-groupName: string-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## netId

```TypeScript
netId: number
```

Group network ID. When creating a group, -1 indicates creates a temporary group, -2: indicates creates a persistent group

**Type:** number

**Since:** 9

<!--Device-WifiP2PConfig-netId: int--><!--Device-WifiP2PConfig-netId: int-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## passphrase

```TypeScript
passphrase: string
```

The passphrase of this `WifiP2pConfig` instance

**Type:** string

**Since:** 9

<!--Device-WifiP2PConfig-passphrase: string--><!--Device-WifiP2PConfig-passphrase: string-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P
