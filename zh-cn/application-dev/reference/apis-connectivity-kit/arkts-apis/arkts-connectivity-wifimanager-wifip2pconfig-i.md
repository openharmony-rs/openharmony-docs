# WifiP2PConfig

P2P配置信息。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.P2P

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## deviceAddress

```TypeScript
deviceAddress: string
```

设备MAC地址

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.P2P

## deviceAddressType

```TypeScript
deviceAddressType?: DeviceAddressType
```

设备MAC地址类型

**类型：** [DeviceAddressType](arkts-connectivity-wifimanager-deviceaddresstype-e.md)

**起始版本：** 10

**系统能力：** SystemCapability.Communication.WiFi.P2P

## goBand

```TypeScript
goBand: GroupOwnerBand
```

群主带宽

**类型：** GroupOwnerBand

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.P2P

## goFreq

```TypeScript
goFreq?: number
```

群主频率

**类型：** number

**起始版本：** 23

**系统能力：** SystemCapability.Communication.WiFi.P2P

## groupName

```TypeScript
groupName: string
```

群组名称

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.P2P

## netId

```TypeScript
netId: number
```

群组网络ID。创建群组时，-1表示创建临时组， -2表示创建永久组

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.P2P

## passphrase

```TypeScript
passphrase: string
```

此{@code WifiP2pConfig}实例的密钥

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.P2P
