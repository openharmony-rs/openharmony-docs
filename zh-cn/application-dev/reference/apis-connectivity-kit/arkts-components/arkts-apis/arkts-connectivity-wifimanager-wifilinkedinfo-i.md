# WifiLinkedInfo

Wi-Fi连接信息。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## band

```TypeScript
band: number
```

Wi-Fi接入点的频段，1表示2.4GHz；2表示5GHz。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

## bssid

```TypeScript
bssid: string
```

热点的BSSID（Basic Service Set Identifier，基本服务集标识符）即无线网络的MAC地址。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.WiFi.STA

## channelWidth

```TypeScript
channelWidth: WifiChannelWidth
```

当前连接热点的信道带宽。

**类型：** [WifiChannelWidth](arkts-connectivity-wifimanager-wifichannelwidth-e.md)

**起始版本：** 10

**系统能力：** SystemCapability.Communication.WiFi.STA

## connState

```TypeScript
connState: ConnState
```

Wi-Fi连接状态。

**类型：** [ConnState](arkts-connectivity-wifimanager-connstate-e.md)

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

## frequency

```TypeScript
frequency: number
```

Wi-Fi接入点的频率。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.WiFi.STA

## ipAddress

```TypeScript
ipAddress: number
```

Wi-Fi连接的IP地址。

1. IP地址在WiFi连接信息和"设置 &gt; 关于本机 &gt; 状态信息"中可以查看。
2. ipAddress值为number类型，需要转换为点分十进制格式的IP地址（如192.168.1.1），具体请参考[IP格式转换](https://developer.huawei.com/consumer/cn/doc/harmonyos-faqs/faqs-connectivity-4)。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

## isHidden

```TypeScript
isHidden: boolean
```

Wi-Fi接入点是否是隐藏网络，true表示是隐藏网络，false表示不是隐藏网络。

**类型：** boolean

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

## isHiLinkNetwork

```TypeScript
isHiLinkNetwork: boolean
```

热点是否支持hilink，true表示支持， false表示不支持。

**类型：** boolean

**起始版本：** 12

**系统能力：** SystemCapability.Communication.WiFi.STA

## isRestricted

```TypeScript
isRestricted: boolean
```

Wi-Fi接入点是否限制数据量，true表示限制，false表示不限制。

**类型：** boolean

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

## linkSpeed

```TypeScript
linkSpeed: number
```

Wi-Fi接入点的上行速度，单位Mbps。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

## macAddress

```TypeScript
macAddress: string
```

设备的MAC地址。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

## macType

```TypeScript
macType: number
```

MAC地址类型。0 - 随机MAC地址，1 - 设备MAC地址。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

## maxSupportedRxLinkSpeed

```TypeScript
maxSupportedRxLinkSpeed: number
```

当前支持的最大下行速率，单位Mbps。

**类型：** number

**起始版本：** 10

**系统能力：** SystemCapability.Communication.WiFi.STA

## maxSupportedTxLinkSpeed

```TypeScript
maxSupportedTxLinkSpeed: number
```

当前支持的最大上行速率，单位Mbps。

**类型：** number

**起始版本：** 10

**系统能力：** SystemCapability.Communication.WiFi.STA

## rssi

```TypeScript
rssi: number
```

热点的信号强度(dBm)。

RSSI（Received Signal Strength Indicator，接收信号强度指示），其标准取值范围为-127dBm至0dBm。在正常使用场景下，常见有效范围为-100dBm（弱信号）至-30dBm（强信号），接近0dBm表示信号极强。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.WiFi.STA

## rxLinkSpeed

```TypeScript
rxLinkSpeed: number
```

Wi-Fi接入点的下行速度，单位Mbps。

**类型：** number

**起始版本：** 10

**系统能力：** SystemCapability.Communication.WiFi.STA

## ssid

```TypeScript
ssid: string
```

热点的SSID（Service Set Identifier，服务集标识符），用于获取当前设备已连接的Wi-Fi热点的公开名称（即无线网络的名称），编码格式为UTF-8。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.WiFi.STA

## supportedWifiCategory

```TypeScript
supportedWifiCategory: WifiCategory
```

当前设备连接Wi-Fi后支持的最高协议版本。

**类型：** [WifiCategory](arkts-connectivity-wifimanager-wificategory-e.md)

**起始版本：** 12

**系统能力：** SystemCapability.Communication.WiFi.STA

## wifiLinkType

```TypeScript
wifiLinkType?: WifiLinkType
```

Wi-Fi7连接类型。

**类型：** [WifiLinkType](arkts-connectivity-wifimanager-wifilinktype-e.md)

**起始版本：** 18

**系统能力：** SystemCapability.Communication.WiFi.STA

## wifiStandard

```TypeScript
wifiStandard: WifiStandard
```

当前路由器支持的最高Wi-Fi标准。

**类型：** [WifiStandard](arkts-connectivity-wifimanager-wifistandard-e.md)

**起始版本：** 10

**系统能力：** SystemCapability.Communication.WiFi.STA
