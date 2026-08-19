# WifiP2PConfig

P2P配置信息。

**起始版本：** 23

<!--Device-wifiManager-interface WifiP2PConfig--><!--Device-wifiManager-interface WifiP2PConfig-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## deviceAddress

```TypeScript
deviceAddress: string
```

设备MAC地址

**类型：** string

**起始版本：** 23

<!--Device-WifiP2PConfig-deviceAddress: string--><!--Device-WifiP2PConfig-deviceAddress: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## deviceAddressType

```TypeScript
deviceAddressType?: DeviceAddressType
```

设备MAC地址类型

**类型：** [DeviceAddressType](arkts-connectivity-wifimanager-deviceaddresstype-e.md)

**起始版本：** 23

<!--Device-WifiP2PConfig-deviceAddressType?: DeviceAddressType--><!--Device-WifiP2PConfig-deviceAddressType?: DeviceAddressType-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## goBand

```TypeScript
goBand: GroupOwnerBand
```

群主带宽

**类型：** GroupOwnerBand

**起始版本：** 23

<!--Device-WifiP2PConfig-goBand: GroupOwnerBand--><!--Device-WifiP2PConfig-goBand: GroupOwnerBand-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## goFreq

```TypeScript
goFreq?: int
```

群主频率

**类型：** int

**起始版本：** 23

<!--Device-WifiP2PConfig-goFreq?: int--><!--Device-WifiP2PConfig-goFreq?: int-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## groupName

```TypeScript
groupName: string
```

群组名称

**类型：** string

**起始版本：** 23

<!--Device-WifiP2PConfig-groupName: string--><!--Device-WifiP2PConfig-groupName: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## netId

```TypeScript
netId: int
```

群组网络ID。创建群组时，-1表示创建临时组， -2表示创建永久组

**类型：** int

**起始版本：** 23

<!--Device-WifiP2PConfig-netId: int--><!--Device-WifiP2PConfig-netId: int-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## passphrase

```TypeScript
passphrase: string
```

此{@code WifiP2pConfig}实例的密钥

**类型：** string

**起始版本：** 23

<!--Device-WifiP2PConfig-passphrase: string--><!--Device-WifiP2PConfig-passphrase: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

