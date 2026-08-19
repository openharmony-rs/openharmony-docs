# WifiP2pLinkedInfo

P2P连接信息。

**起始版本：** 23

<!--Device-wifiManager-interface WifiP2pLinkedInfo--><!--Device-wifiManager-interface WifiP2pLinkedInfo-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## connectState

```TypeScript
connectState: P2pConnectState
```

P2P连接状态。

**类型：** P2pConnectState

**起始版本：** 23

<!--Device-WifiP2pLinkedInfo-connectState: P2pConnectState--><!--Device-WifiP2pLinkedInfo-connectState: P2pConnectState-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## groupOwnerAddr

```TypeScript
groupOwnerAddr: string
```

群主地址。

**类型：** string

**起始版本：** 23

<!--Device-WifiP2pLinkedInfo-groupOwnerAddr: string--><!--Device-WifiP2pLinkedInfo-groupOwnerAddr: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## isGroupOwner

```TypeScript
isGroupOwner: boolean
```

{@code true}表示是群主，{@code false}表示不是群主。

**类型：** boolean

**起始版本：** 23

<!--Device-WifiP2pLinkedInfo-isGroupOwner: boolean--><!--Device-WifiP2pLinkedInfo-isGroupOwner: boolean-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

