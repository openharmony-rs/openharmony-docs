# WifiP2pGroupInfo

表示P2P群组相关信息。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.P2P

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## clientDevices

```TypeScript
clientDevices: WifiP2pDevice[]
```

接入的设备列表信息。

**类型：** [WifiP2pDevice](arkts-connectivity-wifimanager-wifip2pdevice-i.md)[]

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.P2P

## frequency

```TypeScript
frequency: number
```

群组的频率。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.P2P

## goIpAddress

```TypeScript
goIpAddress: string
```

群组IP地址。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.P2P

## groupName

```TypeScript
groupName: string
```

群组名称。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.P2P

## interface

```TypeScript
interface: string
```

接口名称。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.P2P

## isP2pGo

```TypeScript
isP2pGo: boolean
```

是否是群主。true表示是群主，false表示不是群主。

**类型：** boolean

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.P2P

## networkId

```TypeScript
networkId: number
```

网络ID。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.P2P

## ownerInfo

```TypeScript
ownerInfo: WifiP2pDevice
```

群组的设备信息。

**类型：** [WifiP2pDevice](arkts-connectivity-wifimanager-wifip2pdevice-i.md)

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.P2P

## passphrase

```TypeScript
passphrase: string
```

群组密钥。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.P2P
