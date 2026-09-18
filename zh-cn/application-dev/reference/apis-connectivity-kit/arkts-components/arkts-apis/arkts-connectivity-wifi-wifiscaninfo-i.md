# WifiScanInfo

Wi-Fi热点信息。

> **说明：** 
> 
> 从API version 6开始支持，从API version 9开始废弃。

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

Wi-Fi接入点的频段。1表示2.4GHz；2表示5GHz。

**类型：** number

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [band](arkts-connectivity-wifimanager-wifiscaninfo-i.md#band)

**系统能力：** SystemCapability.Communication.WiFi.STA

## bssid

```TypeScript
bssid: string
```

热点的BSSID，例如：00:11:22:33:44:55。

**类型：** string

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [bssid](arkts-connectivity-wifimanager-wifiscaninfo-i.md#bssid)

**系统能力：** SystemCapability.Communication.WiFi.STA

## capabilities

```TypeScript
capabilities: string
```

热点能力。

**类型：** string

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [capabilities](arkts-connectivity-wifimanager-wifiscaninfo-i.md#capabilities)

**系统能力：** SystemCapability.Communication.WiFi.STA

## channelWidth

```TypeScript
channelWidth: number
```

Wi-Fi接入点的带宽。

**类型：** number

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [channelWidth](arkts-connectivity-wifimanager-wifiscaninfo-i.md#channelwidth)

**系统能力：** SystemCapability.Communication.WiFi.STA

## frequency

```TypeScript
frequency: number
```

Wi-Fi接入点的频率，单位：MHz。

**类型：** number

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [frequency](arkts-connectivity-wifimanager-wifiscaninfo-i.md#frequency)

**系统能力：** SystemCapability.Communication.WiFi.STA

## rssi

```TypeScript
rssi: number
```

热点的信号强度(dBm)。

**类型：** number

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [rssi](arkts-connectivity-wifimanager-wifiscaninfo-i.md#rssi)

**系统能力：** SystemCapability.Communication.WiFi.STA

## securityType

```TypeScript
securityType: WifiSecurityType
```

Wi-Fi加密类型。

**类型：** [WifiSecurityType](arkts-connectivity-wifi-wifisecuritytype-e.md)

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [securityType](arkts-connectivity-wifimanager-wifiscaninfo-i.md#securitytype)

**系统能力：** SystemCapability.Communication.WiFi.STA

## ssid

```TypeScript
ssid: string
```

热点的SSID，最大长度为32字节，编码格式为UTF-8。

**类型：** string

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [ssid](arkts-connectivity-wifimanager-wifiscaninfo-i.md#ssid)

**系统能力：** SystemCapability.Communication.WiFi.STA

## timestamp

```TypeScript
timestamp: number
```

时间戳。

**类型：** number

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [timestamp](arkts-connectivity-wifimanager-wifiscaninfo-i.md#timestamp)

**系统能力：** SystemCapability.Communication.WiFi.STA
