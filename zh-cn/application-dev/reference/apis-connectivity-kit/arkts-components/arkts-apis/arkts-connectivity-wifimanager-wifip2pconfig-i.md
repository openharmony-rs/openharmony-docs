# WifiP2PConfig

```TypeScript
interface WifiP2PConfig
```

表示P2P配置信息。

**起始版本：** 9

<!--Device-wifiManager-interface WifiP2PConfig--><!--Device-wifiManager-interface WifiP2PConfig-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## deviceAddress

```TypeScript
deviceAddress: string
```

设备地址。

**类型：** string

**起始版本：** 9

<!--Device-WifiP2PConfig-deviceAddress: string--><!--Device-WifiP2PConfig-deviceAddress: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## deviceAddressType

```TypeScript
deviceAddressType?: DeviceAddressType
```

设备地址类型。

**类型：** [DeviceAddressType](arkts-connectivity-wifimanager-deviceaddresstype-e.md)

**起始版本：** 10

<!--Device-WifiP2PConfig-deviceAddressType?: DeviceAddressType--><!--Device-WifiP2PConfig-deviceAddressType?: DeviceAddressType-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## goBand

```TypeScript
goBand: GroupOwnerBand
```

群组带宽。

**类型：** [GroupOwnerBand](arkts-connectivity-wifimanager-groupownerband-e.md)

**起始版本：** 9

<!--Device-WifiP2PConfig-goBand: GroupOwnerBand--><!--Device-WifiP2PConfig-goBand: GroupOwnerBand-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## goFreq

```TypeScript
goFreq?: number
```

群组频率，若群组带宽和群组频率同时添加的情况下，当频率合法时（频率在2400MHz-2500MHz或者4900MHz-5900MHz范围内认为合法），以频率为准，否则以带宽为准。

**类型：** number

**起始版本：** 23

<!--Device-WifiP2PConfig-goFreq?: int--><!--Device-WifiP2PConfig-goFreq?: int-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## groupName

```TypeScript
groupName: string
```

群组名称。

**类型：** string

**起始版本：** 9

<!--Device-WifiP2PConfig-groupName: string--><!--Device-WifiP2PConfig-groupName: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## netId

```TypeScript
netId: number
```

网络ID。创建群组时-1表示创建临时组，-2表示创建永久组。

**类型：** number

**起始版本：** 9

<!--Device-WifiP2PConfig-netId: int--><!--Device-WifiP2PConfig-netId: int-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## passphrase

```TypeScript
passphrase: string
```

群组密钥。

**类型：** string

**起始版本：** 9

<!--Device-WifiP2PConfig-passphrase: string--><!--Device-WifiP2PConfig-passphrase: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P
