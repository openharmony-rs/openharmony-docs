# WifiLinkedInfo

WLAN连接信息。

**起始版本：** 23

<!--Device-wifiManager-interface WifiLinkedInfo--><!--Device-wifiManager-interface WifiLinkedInfo-End-->

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

WLAN接入点的频段。

**类型：** int

**起始版本：** 23

<!--Device-WifiLinkedInfo-band: int--><!--Device-WifiLinkedInfo-band: int-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## bssid

```TypeScript
bssid: string
```

WLAN热点的BSSID

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-WifiLinkedInfo-bssid: string--><!--Device-WifiLinkedInfo-bssid: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## channelWidth

```TypeScript
channelWidth: WifiChannelWidth
```

已连接热点的带宽。

**类型：** [WifiChannelWidth](arkts-connectivity-wifimanager-wifichannelwidth-e.md)

**起始版本：** 23

<!--Device-WifiLinkedInfo-channelWidth: WifiChannelWidth--><!--Device-WifiLinkedInfo-channelWidth: WifiChannelWidth-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## connState

```TypeScript
connState: ConnState
```

此WLAN连接的状态。

**类型：** ConnState

**起始版本：** 23

<!--Device-WifiLinkedInfo-connState: ConnState--><!--Device-WifiLinkedInfo-connState: ConnState-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## frequency

```TypeScript
frequency: int
```

WLAN接入点的频率。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-WifiLinkedInfo-frequency: int--><!--Device-WifiLinkedInfo-frequency: int-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## ipAddress

```TypeScript
ipAddress: int
```

此WLAN连接的IP地址。

**类型：** int

**起始版本：** 23

<!--Device-WifiLinkedInfo-ipAddress: int--><!--Device-WifiLinkedInfo-ipAddress: int-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## isHiLinkNetwork

```TypeScript
isHiLinkNetwork: boolean
```

WLAN热点是否是HiLink网络。

**类型：** boolean

**起始版本：** 23

<!--Device-WifiLinkedInfo-isHiLinkNetwork: boolean--><!--Device-WifiLinkedInfo-isHiLinkNetwork: boolean-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## isHidden

```TypeScript
isHidden: boolean
```

此WLAN连接的接入点（AP）的SSID是否隐藏。

**类型：** boolean

**起始版本：** 23

<!--Device-WifiLinkedInfo-isHidden: boolean--><!--Device-WifiLinkedInfo-isHidden: boolean-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## isRestricted

```TypeScript
isRestricted: boolean
```

此WLAN连接是否限制数据量。

**类型：** boolean

**起始版本：** 23

<!--Device-WifiLinkedInfo-isRestricted: boolean--><!--Device-WifiLinkedInfo-isRestricted: boolean-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## linkSpeed

```TypeScript
linkSpeed: int
```

WLAN接入点的速度。

**类型：** int

**起始版本：** 23

<!--Device-WifiLinkedInfo-linkSpeed: int--><!--Device-WifiLinkedInfo-linkSpeed: int-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## macAddress

```TypeScript
macAddress: string
```

设备的WLAN MAC地址。

**类型：** string

**起始版本：** 23

<!--Device-WifiLinkedInfo-macAddress: string--><!--Device-WifiLinkedInfo-macAddress: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## macType

```TypeScript
macType: int
```

macAddress类型：0 - 真实MAC，1 - 随机MAC。

**类型：** int

**起始版本：** 23

<!--Device-WifiLinkedInfo-macType: int--><!--Device-WifiLinkedInfo-macType: int-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## maxSupportedRxLinkSpeed

```TypeScript
maxSupportedRxLinkSpeed: int
```

WLAN接入点的最大下行速度。

**类型：** int

**起始版本：** 23

<!--Device-WifiLinkedInfo-maxSupportedRxLinkSpeed: int--><!--Device-WifiLinkedInfo-maxSupportedRxLinkSpeed: int-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## maxSupportedTxLinkSpeed

```TypeScript
maxSupportedTxLinkSpeed: int
```

WLAN接入点的最大上行速度。

**类型：** int

**起始版本：** 23

<!--Device-WifiLinkedInfo-maxSupportedTxLinkSpeed: int--><!--Device-WifiLinkedInfo-maxSupportedTxLinkSpeed: int-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## rssi

```TypeScript
rssi: int
```

WLAN接入点的RSSI（dBm）。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-WifiLinkedInfo-rssi: int--><!--Device-WifiLinkedInfo-rssi: int-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## rxLinkSpeed

```TypeScript
rxLinkSpeed: int
```

WLAN接入点的下行速度。

**类型：** int

**起始版本：** 23

<!--Device-WifiLinkedInfo-rxLinkSpeed: int--><!--Device-WifiLinkedInfo-rxLinkSpeed: int-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## ssid

```TypeScript
ssid: string
```

WLAN热点的SSID

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-WifiLinkedInfo-ssid: string--><!--Device-WifiLinkedInfo-ssid: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## supportedWifiCategory

```TypeScript
supportedWifiCategory: WifiCategory
```

支持的WLAN类别

**类型：** [WifiCategory](arkts-connectivity-wifimanager-wificategory-e.md)

**起始版本：** 23

<!--Device-WifiLinkedInfo-supportedWifiCategory: WifiCategory--><!--Device-WifiLinkedInfo-supportedWifiCategory: WifiCategory-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## wifiLinkType

```TypeScript
wifiLinkType?: WifiLinkType
```

WLAN连接类型

**类型：** [WifiLinkType](arkts-connectivity-wifimanager-wifilinktype-e.md)

**起始版本：** 23

<!--Device-WifiLinkedInfo-wifiLinkType?: WifiLinkType--><!--Device-WifiLinkedInfo-wifiLinkType?: WifiLinkType-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## wifiStandard

```TypeScript
wifiStandard: WifiStandard
```

当前连接的WLAN标准。

**类型：** [WifiStandard](arkts-connectivity-wifimanager-wifistandard-e.md)

**起始版本：** 23

<!--Device-WifiLinkedInfo-wifiStandard: WifiStandard--><!--Device-WifiLinkedInfo-wifiStandard: WifiStandard-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

