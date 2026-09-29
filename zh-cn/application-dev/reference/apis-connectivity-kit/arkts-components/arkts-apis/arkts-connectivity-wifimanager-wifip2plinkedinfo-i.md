# WifiP2pLinkedInfo

```TypeScript
interface WifiP2pLinkedInfo
```

提供Wi-Fi连接的相关信息。

**起始版本：** 9

<!--Device-wifiManager-interface WifiP2pLinkedInfo--><!--Device-wifiManager-interface WifiP2pLinkedInfo-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## connectState

```TypeScript
connectState: P2pConnectState
```

P2P连接状态。

**类型：** [P2pConnectState](arkts-connectivity-wifimanager-p2pconnectstate-e.md)

**起始版本：** 9

<!--Device-WifiP2pLinkedInfo-connectState: P2pConnectState--><!--Device-WifiP2pLinkedInfo-connectState: P2pConnectState-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## groupOwnerAddr

```TypeScript
groupOwnerAddr: string
```

群组IP地址。

**类型：** string

**起始版本：** 9

<!--Device-WifiP2pLinkedInfo-groupOwnerAddr: string--><!--Device-WifiP2pLinkedInfo-groupOwnerAddr: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## isGroupOwner

```TypeScript
isGroupOwner: boolean
```

true表示是群主，false表示不是群主。

**类型：** boolean

**起始版本：** 9

<!--Device-WifiP2pLinkedInfo-isGroupOwner: boolean--><!--Device-WifiP2pLinkedInfo-isGroupOwner: boolean-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P
