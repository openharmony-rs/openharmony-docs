# WifiLinkedInfo

WLAN连接信息。

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

WLAN接入点的频段。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

## bssid

```TypeScript
bssid: string
```

WLAN热点的BSSID

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.WiFi.STA

## channelWidth

```TypeScript
channelWidth: WifiChannelWidth
```

已连接热点的带宽。

**类型：** [WifiChannelWidth](arkts-connectivity-wifimanager-wifichannelwidth-e.md)

**起始版本：** 10

**系统能力：** SystemCapability.Communication.WiFi.STA

## connState

```TypeScript
connState: ConnState
```

此WLAN连接的状态。

**类型：** ConnState

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

## frequency

```TypeScript
frequency: number
```

WLAN接入点的频率。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.WiFi.STA

## ipAddress

```TypeScript
ipAddress: number
```

此WLAN连接的IP地址。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

## isHidden

```TypeScript
isHidden: boolean
```

此WLAN连接的接入点（AP）的SSID是否隐藏。

**类型：** boolean

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

## isRestricted

```TypeScript
isRestricted: boolean
```

此WLAN连接是否限制数据量。

**类型：** boolean

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

## linkSpeed

```TypeScript
linkSpeed: number
```

WLAN接入点的速度。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

## macAddress

```TypeScript
macAddress: string
```

设备的WLAN MAC地址。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

## macType

```TypeScript
macType: number
```

macAddress类型：0 - 真实MAC，1 - 随机MAC。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

## maxSupportedRxLinkSpeed

```TypeScript
maxSupportedRxLinkSpeed: number
```

WLAN接入点的最大下行速度。

**类型：** number

**起始版本：** 10

**系统能力：** SystemCapability.Communication.WiFi.STA

## maxSupportedTxLinkSpeed

```TypeScript
maxSupportedTxLinkSpeed: number
```

WLAN接入点的最大上行速度。

**类型：** number

**起始版本：** 10

**系统能力：** SystemCapability.Communication.WiFi.STA

## rssi

```TypeScript
rssi: number
```

WLAN接入点的RSSI（dBm）。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.WiFi.STA

## rxLinkSpeed

```TypeScript
rxLinkSpeed: number
```

WLAN接入点的下行速度。

**类型：** number

**起始版本：** 10

**系统能力：** SystemCapability.Communication.WiFi.STA

## ssid

```TypeScript
ssid: string
```

WLAN热点的SSID

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

## wifiLinkType

```TypeScript
wifiLinkType?: WifiLinkType
```

WLAN连接类型

**类型：** [WifiLinkType](arkts-connectivity-wifimanager-wifilinktype-e.md)

**起始版本：** 18

**系统能力：** SystemCapability.Communication.WiFi.STA

## wifiStandard

```TypeScript
wifiStandard: WifiStandard
```

当前连接的WLAN标准。

**类型：** [WifiStandard](arkts-connectivity-wifimanager-wifistandard-e.md)

**起始版本：** 10

**系统能力：** SystemCapability.Communication.WiFi.STA
