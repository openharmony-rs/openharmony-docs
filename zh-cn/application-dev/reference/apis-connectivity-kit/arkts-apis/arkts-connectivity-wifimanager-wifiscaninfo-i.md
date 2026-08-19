# WifiScanInfo

描述WLAN扫描信息。

**起始版本：** 23

<!--Device-wifiManager-interface WifiScanInfo--><!--Device-wifiManager-interface WifiScanInfo-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## band

```TypeScript
band: int
```

频段，1：2.4G，2：5G

**类型：** int

**起始版本：** 23

<!--Device-WifiScanInfo-band: int--><!--Device-WifiScanInfo-band: int-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## bssid

```TypeScript
bssid: string
```

WLAN BSSID（MAC）：长度为6

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-WifiScanInfo-bssid: string--><!--Device-WifiScanInfo-bssid: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## bssidType

```TypeScript
bssidType: DeviceAddressType
```

WLAN BSSID类型

**类型：** [DeviceAddressType](arkts-connectivity-wifimanager-deviceaddresstype-e.md)

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-WifiScanInfo-bssidType: DeviceAddressType--><!--Device-WifiScanInfo-bssidType: DeviceAddressType-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## capabilities

```TypeScript
capabilities: string
```

热点能力

**类型：** string

**起始版本：** 23

<!--Device-WifiScanInfo-capabilities: string--><!--Device-WifiScanInfo-capabilities: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## centerFrequency0

```TypeScript
centerFrequency0: int
```

中心频率0。

**类型：** int

**起始版本：** 23

<!--Device-WifiScanInfo-centerFrequency0: int--><!--Device-WifiScanInfo-centerFrequency0: int-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## centerFrequency1

```TypeScript
centerFrequency1: int
```

中心频率1。

**类型：** int

**起始版本：** 23

<!--Device-WifiScanInfo-centerFrequency1: int--><!--Device-WifiScanInfo-centerFrequency1: int-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## channelWidth

```TypeScript
channelWidth: int
```

带宽

**类型：** int

**起始版本：** 23

<!--Device-WifiScanInfo-channelWidth: int--><!--Device-WifiScanInfo-channelWidth: int-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## frequency

```TypeScript
frequency: int
```

频率

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-WifiScanInfo-frequency: int--><!--Device-WifiScanInfo-frequency: int-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## infoElems

```TypeScript
infoElems: Array<WifiInfoElem>
```

信息元素。

**类型：** Array&lt;[WifiInfoElem](arkts-connectivity-wifimanager-wifiinfoelem-i.md)&gt;

**起始版本：** 23

<!--Device-WifiScanInfo-infoElems: Array<WifiInfoElem>--><!--Device-WifiScanInfo-infoElems: Array<WifiInfoElem>-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## isHiLinkNetwork

```TypeScript
isHiLinkNetwork: boolean
```

WLAN热点是否是HiLink网络。

**类型：** boolean

**起始版本：** 23

<!--Device-WifiScanInfo-isHiLinkNetwork: boolean--><!--Device-WifiScanInfo-isHiLinkNetwork: boolean-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## rssi

```TypeScript
rssi: int
```

接收信号强度指示（RSSI）

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-WifiScanInfo-rssi: int--><!--Device-WifiScanInfo-rssi: int-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## securityType

```TypeScript
securityType: WifiSecurityType
```

加密类型：参考WifiSecurityType的定义

**类型：** WifiSecurityType

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-WifiScanInfo-securityType: WifiSecurityType--><!--Device-WifiScanInfo-securityType: WifiSecurityType-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## ssid

```TypeScript
ssid: string
```

WLAN SSID：最大长度为32

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-WifiScanInfo-ssid: string--><!--Device-WifiScanInfo-ssid: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## supportedWifiCategory

```TypeScript
supportedWifiCategory: WifiCategory
```

支持的WLAN类别

**类型：** [WifiCategory](arkts-connectivity-wifimanager-wificategory-e.md)

**起始版本：** 23

<!--Device-WifiScanInfo-supportedWifiCategory: WifiCategory--><!--Device-WifiScanInfo-supportedWifiCategory: WifiCategory-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## timestamp

```TypeScript
timestamp: long
```

时间戳

**类型：** long

**起始版本：** 23

<!--Device-WifiScanInfo-timestamp: long--><!--Device-WifiScanInfo-timestamp: long-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

