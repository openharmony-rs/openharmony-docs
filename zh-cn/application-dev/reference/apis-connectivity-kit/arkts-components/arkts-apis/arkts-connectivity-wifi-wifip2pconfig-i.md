# WifiP2PConfig

```TypeScript
interface WifiP2PConfig
```

表示P2P配置信息。

> **说明：** 
> 
> 从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [WifiP2PConfig](arkts-connectivity-wifimanager-wifip2pconfig-i.md)

<!--Device-wifi-interface WifiP2PConfig--><!--Device-wifi-interface WifiP2PConfig-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## deviceAddress

```TypeScript
deviceAddress: string
```

设备地址。

**类型：** string

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [deviceAddress](arkts-connectivity-wifimanager-wifip2pconfig-i.md#deviceaddress)

<!--Device-WifiP2PConfig-deviceAddress: string--><!--Device-WifiP2PConfig-deviceAddress: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## goBand

```TypeScript
goBand: GroupOwnerBand
```

群组带宽。

**类型：** [GroupOwnerBand](arkts-connectivity-wifi-groupownerband-e.md)

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [goBand](arkts-connectivity-wifimanager-wifip2pconfig-i.md#goband)

<!--Device-WifiP2PConfig-goBand: GroupOwnerBand--><!--Device-WifiP2PConfig-goBand: GroupOwnerBand-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## groupName

```TypeScript
groupName: string
```

群组名称。

**类型：** string

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [groupName](arkts-connectivity-wifimanager-wifip2pconfig-i.md#groupname)

<!--Device-WifiP2PConfig-groupName: string--><!--Device-WifiP2PConfig-groupName: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## netId

```TypeScript
netId: number
```

网络ID。创建群组时-1表示创建临时组，-2表示创建永久组。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [netId](arkts-connectivity-wifimanager-wifip2pconfig-i.md#netid)

<!--Device-WifiP2PConfig-netId: number--><!--Device-WifiP2PConfig-netId: number-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## passphrase

```TypeScript
passphrase: string
```

群组密钥。

**类型：** string

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [passphrase](arkts-connectivity-wifimanager-wifip2pconfig-i.md#passphrase)

<!--Device-WifiP2PConfig-passphrase: string--><!--Device-WifiP2PConfig-passphrase: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P
