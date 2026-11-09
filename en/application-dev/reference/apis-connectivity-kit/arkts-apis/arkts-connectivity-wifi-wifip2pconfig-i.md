# WifiP2PConfig

```TypeScript
interface WifiP2PConfig
```

Represents P2P group configuration.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [WifiP2PConfig](arkts-connectivity-wifimanager-wifip2pconfig-i.md)

<!--Device-wifi-interface WifiP2PConfig--><!--Device-wifi-interface WifiP2PConfig-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## deviceAddress

```TypeScript
deviceAddress: string
```

Device address.

**Type:** string

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [deviceAddress](arkts-connectivity-wifimanager-wifip2pconfig-i.md#deviceaddress)

<!--Device-WifiP2PConfig-deviceAddress: string--><!--Device-WifiP2PConfig-deviceAddress: string-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## goBand

```TypeScript
goBand: GroupOwnerBand
```

Frequency band of the group.

**Type:** [GroupOwnerBand](arkts-connectivity-wifi-groupownerband-e.md)

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [goBand](arkts-connectivity-wifimanager-wifip2pconfig-i.md#goband)

<!--Device-WifiP2PConfig-goBand: GroupOwnerBand--><!--Device-WifiP2PConfig-goBand: GroupOwnerBand-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## groupName

```TypeScript
groupName: string
```

Group name.

**Type:** string

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [groupName](arkts-connectivity-wifimanager-wifip2pconfig-i.md#groupname)

<!--Device-WifiP2PConfig-groupName: string--><!--Device-WifiP2PConfig-groupName: string-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## netId

```TypeScript
netId: number
```

Network ID. The value **-1** indicates a temporary group, and **-2** indicates a persistent group.

**Type:** number

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [netId](arkts-connectivity-wifimanager-wifip2pconfig-i.md#netid)

<!--Device-WifiP2PConfig-netId: number--><!--Device-WifiP2PConfig-netId: number-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## passphrase

```TypeScript
passphrase: string
```

Passphrase of the group.

**Type:** string

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [passphrase](arkts-connectivity-wifimanager-wifip2pconfig-i.md#passphrase)

<!--Device-WifiP2PConfig-passphrase: string--><!--Device-WifiP2PConfig-passphrase: string-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P
