# WifiP2pLinkedInfo

```TypeScript
interface WifiP2pLinkedInfo
```

提供P2P连接的相关信息。

> **说明：** 
> 
> 从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [WifiP2pLinkedInfo](arkts-connectivity-wifimanager-wifip2plinkedinfo-i.md)

<!--Device-wifi-interface WifiP2pLinkedInfo--><!--Device-wifi-interface WifiP2pLinkedInfo-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## connectState

```TypeScript
connectState: P2pConnectState
```

P2P连接状态。

**类型：** [P2pConnectState](arkts-connectivity-wifi-p2pconnectstate-e.md)

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [connectState](arkts-connectivity-wifimanager-wifip2plinkedinfo-i.md#connectstate)

<!--Device-WifiP2pLinkedInfo-connectState: P2pConnectState--><!--Device-WifiP2pLinkedInfo-connectState: P2pConnectState-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## groupOwnerAddr

```TypeScript
groupOwnerAddr: string
```

群组MAC地址。

**类型：** string

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [groupOwnerAddr](arkts-connectivity-wifimanager-wifip2plinkedinfo-i.md#groupowneraddr)

<!--Device-WifiP2pLinkedInfo-groupOwnerAddr: string--><!--Device-WifiP2pLinkedInfo-groupOwnerAddr: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## isGroupOwner

```TypeScript
isGroupOwner: boolean
```

是否是群主。true:是群主，false:不是群主。

**类型：** boolean

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isGroupOwner](arkts-connectivity-wifimanager-wifip2plinkedinfo-i.md#isgroupowner)

<!--Device-WifiP2pLinkedInfo-isGroupOwner: boolean--><!--Device-WifiP2pLinkedInfo-isGroupOwner: boolean-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P
