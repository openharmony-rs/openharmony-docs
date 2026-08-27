# WifiScanInfo

描述扫描到的WLAN信息。@interface WifiScanInfo

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [WifiScanInfo](arkts-connectivity-wifimanager-wifiscaninfo-i.md)

**系统能力：** SystemCapability.Communication.WiFi.STA

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## band

```TypeScript
band: number
```

频段，1:2.4G，2:5G

**类型：** number

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [band](arkts-connectivity-wifimanager-wifiscaninfo-i.md#band)

**系统能力：** SystemCapability.Communication.WiFi.STA

## bssid

```TypeScript
bssid: string
```

WLAN BSSID(MAC)：长度为6

**类型：** string

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [bssid](arkts-connectivity-wifimanager-wifiscaninfo-i.md#bssid)

**系统能力：** SystemCapability.Communication.WiFi.STA

## capabilities

```TypeScript
capabilities: string
```

热点能力

**类型：** string

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [capabilities](arkts-connectivity-wifimanager-wifiscaninfo-i.md#capabilities)

**系统能力：** SystemCapability.Communication.WiFi.STA

## channelWidth

```TypeScript
channelWidth: number
```

带宽

**类型：** number

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [channelWidth](arkts-connectivity-wifimanager-wifiscaninfo-i.md#channelwidth)

**系统能力：** SystemCapability.Communication.WiFi.STA

## frequency

```TypeScript
frequency: number
```

频率

**类型：** number

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [frequency](arkts-connectivity-wifimanager-wifiscaninfo-i.md#frequency)

**系统能力：** SystemCapability.Communication.WiFi.STA

## rssi

```TypeScript
rssi: number
```

接收信号强度指示(RSSI)

**类型：** number

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [rssi](arkts-connectivity-wifimanager-wifiscaninfo-i.md#rssi)

**系统能力：** SystemCapability.Communication.WiFi.STA

## securityType

```TypeScript
securityType: WifiSecurityType
```

加密类型：参考WifiSecurityType的定义

**类型：** WifiSecurityType

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [securityType](arkts-connectivity-wifimanager-wifiscaninfo-i.md#securitytype)

**系统能力：** SystemCapability.Communication.WiFi.STA

## ssid

```TypeScript
ssid: string
```

WLAN SSID：最大长度为32

**类型：** string

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [ssid](arkts-connectivity-wifimanager-wifiscaninfo-i.md#ssid)

**系统能力：** SystemCapability.Communication.WiFi.STA

## timestamp

```TypeScript
timestamp: number
```

时间戳

**类型：** number

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [timestamp](arkts-connectivity-wifimanager-wifiscaninfo-i.md#timestamp)

**系统能力：** SystemCapability.Communication.WiFi.STA
