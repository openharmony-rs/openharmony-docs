# WifiP2PConfig

表示P2P配置信息。

> **说明：** 
> 
> 从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [WifiP2PConfig](arkts-connectivity-wifimanager-wifip2pconfig-i.md)

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

**系统能力：** SystemCapability.Communication.WiFi.P2P
