# WifiScanInfo

描述WLAN扫描信息。

**起始版本：** 12

**系统能力：** SystemCapability.Communication.WiFi.STA

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## band

```TypeScript
band: number
```

频段，1：2.4G，2：5G

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

## bssid

```TypeScript
bssid: string
```

WLAN BSSID（MAC）：长度为6

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.WiFi.STA

## bssidType

```TypeScript
bssidType: DeviceAddressType
```

WLAN BSSID类型

**类型：** [DeviceAddressType](arkts-connectivity-wifimanager-deviceaddresstype-e.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.WiFi.STA

## capabilities

```TypeScript
capabilities: string
```

热点能力

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

## centerFrequency0

```TypeScript
centerFrequency0: number
```

中心频率0。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

## centerFrequency1

```TypeScript
centerFrequency1: number
```

中心频率1。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

## channelWidth

```TypeScript
channelWidth: number
```

带宽

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

## frequency

```TypeScript
frequency: number
```

频率

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.WiFi.STA

## infoElems

```TypeScript
infoElems: Array<WifiInfoElem>
```

信息元素。

**类型：** Array&lt;[WifiInfoElem](arkts-connectivity-wifimanager-wifiinfoelem-i.md)&gt;

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

## isHiLinkNetwork

```TypeScript
isHiLinkNetwork: boolean
```

WLAN热点是否是HiLink网络。

**类型：** boolean

**起始版本：** 12

**系统能力：** SystemCapability.Communication.WiFi.STA

## rssi

```TypeScript
rssi: number
```

接收信号强度指示（RSSI）

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.WiFi.STA

## securityType

```TypeScript
securityType: WifiSecurityType
```

加密类型：参考WifiSecurityType的定义

**类型：** WifiSecurityType

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.WiFi.STA

## ssid

```TypeScript
ssid: string
```

WLAN SSID：最大长度为32

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.WiFi.STA

## supportedWifiCategory

```TypeScript
supportedWifiCategory: WifiCategory
```

支持的WLAN类别

**类型：** [WifiCategory](arkts-connectivity-wifimanager-wificategory-e.md)

**起始版本：** 12

**系统能力：** SystemCapability.Communication.WiFi.STA

## timestamp

```TypeScript
timestamp: number
```

时间戳

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA
