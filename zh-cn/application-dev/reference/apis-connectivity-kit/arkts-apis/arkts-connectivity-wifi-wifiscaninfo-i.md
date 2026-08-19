# WifiScanInfo

描述扫描到的WLAN信息。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [WifiScanInfo](arkts-connectivity-wifimanager-wifiscaninfo-i.md)

<!--Device-wifi-interface WifiScanInfo--><!--Device-wifi-interface WifiScanInfo-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
import { wifiext } from '@kit.ConnectivityKit';
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
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

<!--Device-WifiScanInfo-band: number--><!--Device-WifiScanInfo-band: number-End-->

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

<!--Device-WifiScanInfo-bssid: string--><!--Device-WifiScanInfo-bssid: string-End-->

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

<!--Device-WifiScanInfo-capabilities: string--><!--Device-WifiScanInfo-capabilities: string-End-->

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

<!--Device-WifiScanInfo-channelWidth: number--><!--Device-WifiScanInfo-channelWidth: number-End-->

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

<!--Device-WifiScanInfo-frequency: number--><!--Device-WifiScanInfo-frequency: number-End-->

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

<!--Device-WifiScanInfo-rssi: number--><!--Device-WifiScanInfo-rssi: number-End-->

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

<!--Device-WifiScanInfo-securityType: WifiSecurityType--><!--Device-WifiScanInfo-securityType: WifiSecurityType-End-->

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

<!--Device-WifiScanInfo-ssid: string--><!--Device-WifiScanInfo-ssid: string-End-->

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

<!--Device-WifiScanInfo-timestamp: number--><!--Device-WifiScanInfo-timestamp: number-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

