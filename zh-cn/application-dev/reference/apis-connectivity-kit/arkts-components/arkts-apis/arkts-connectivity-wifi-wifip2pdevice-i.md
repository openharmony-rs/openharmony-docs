# WifiP2pDevice

```TypeScript
interface WifiP2pDevice
```

表示P2P设备信息。

> **说明：** 
> 
> 从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [WifiP2pDevice](arkts-connectivity-wifimanager-wifip2pdevice-i.md)

<!--Device-wifi-interface WifiP2pDevice--><!--Device-wifi-interface WifiP2pDevice-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## deviceAddress

```TypeScript
deviceAddress: string
```

设备MAC地址。

**类型：** string

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [deviceAddress](arkts-connectivity-wifimanager-wifip2pdevice-i.md#deviceaddress)

<!--Device-WifiP2pDevice-deviceAddress: string--><!--Device-WifiP2pDevice-deviceAddress: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## deviceName

```TypeScript
deviceName: string
```

设备名称。

**类型：** string

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [deviceName](arkts-connectivity-wifimanager-wifip2pdevice-i.md#devicename)

<!--Device-WifiP2pDevice-deviceName: string--><!--Device-WifiP2pDevice-deviceName: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## deviceStatus

```TypeScript
deviceStatus: P2pDeviceStatus
```

设备状态。

**类型：** [P2pDeviceStatus](arkts-connectivity-wifi-p2pdevicestatus-e.md)

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [deviceStatus](arkts-connectivity-wifimanager-wifip2pdevice-i.md#devicestatus)

<!--Device-WifiP2pDevice-deviceStatus: P2pDeviceStatus--><!--Device-WifiP2pDevice-deviceStatus: P2pDeviceStatus-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## groupCapabilitys

```TypeScript
groupCapabilitys: number
```

群组能力，以位掩码形式表示群组支持的特性。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** groupCapabilitys

<!--Device-WifiP2pDevice-groupCapabilitys: number--><!--Device-WifiP2pDevice-groupCapabilitys: number-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

## primaryDeviceType

```TypeScript
primaryDeviceType: string
```

主设备类型。

**类型：** string

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [primaryDeviceType](arkts-connectivity-wifimanager-wifip2pdevice-i.md#primarydevicetype)

<!--Device-WifiP2pDevice-primaryDeviceType: string--><!--Device-WifiP2pDevice-primaryDeviceType: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P
