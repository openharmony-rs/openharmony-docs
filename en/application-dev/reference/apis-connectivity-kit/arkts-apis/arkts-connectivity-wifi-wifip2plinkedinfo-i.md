# WifiP2pLinkedInfo

```TypeScript
interface WifiP2pLinkedInfo
```

Provides information about the P2P connection.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [WifiP2pLinkedInfo](arkts-connectivity-wifimanager-wifip2plinkedinfo-i.md)

<!--Device-wifi-interface WifiP2pLinkedInfo--><!--Device-wifi-interface WifiP2pLinkedInfo-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## connectState

```TypeScript
connectState: P2pConnectState
```

P2P connection state.

**Type:** [P2pConnectState](arkts-connectivity-wifi-p2pconnectstate-e.md)

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [connectState](arkts-connectivity-wifimanager-wifip2plinkedinfo-i.md#connectstate)

<!--Device-WifiP2pLinkedInfo-connectState: P2pConnectState--><!--Device-WifiP2pLinkedInfo-connectState: P2pConnectState-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## groupOwnerAddr

```TypeScript
groupOwnerAddr: string
```

MAC address of the group.

**Type:** string

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [groupOwnerAddr](arkts-connectivity-wifimanager-wifip2plinkedinfo-i.md#groupowneraddr)

<!--Device-WifiP2pLinkedInfo-groupOwnerAddr: string--><!--Device-WifiP2pLinkedInfo-groupOwnerAddr: string-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

## isGroupOwner

```TypeScript
isGroupOwner: boolean
```

Whether the device is the group owner. The value **true** indicates that the device is the group owner, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [isGroupOwner](arkts-connectivity-wifimanager-wifip2plinkedinfo-i.md#isgroupowner)

<!--Device-WifiP2pLinkedInfo-isGroupOwner: boolean--><!--Device-WifiP2pLinkedInfo-isGroupOwner: boolean-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P
