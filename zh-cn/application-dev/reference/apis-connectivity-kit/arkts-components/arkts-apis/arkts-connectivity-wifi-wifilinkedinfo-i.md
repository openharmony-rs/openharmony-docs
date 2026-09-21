# WifiLinkedInfo

```TypeScript
interface WifiLinkedInfo
```

提供Wi-Fi连接的相关信息。

> **说明：** 
> 
> 从API version 6开始支持，从API version 9开始废弃。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [WifiLinkedInfo](arkts-connectivity-wifimanager-wifilinkedinfo-i.md)

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

**替代接口：** [band](arkts-connectivity-wifimanager-wifilinkedinfo-i.md#band)

**系统能力：** SystemCapability.Communication.WiFi.STA

## bssid

```TypeScript
bssid: string
```

热点的BSSID，例如：00:11:22:33:44:55。

**类型：** string

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [bssid](arkts-connectivity-wifimanager-wifilinkedinfo-i.md#bssid)

**系统能力：** SystemCapability.Communication.WiFi.STA

## connState

```TypeScript
connState: ConnState
```

Wi-Fi连接状态。

**类型：** [ConnState](arkts-connectivity-wifi-connstate-e.md)

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [connState](arkts-connectivity-wifimanager-wifilinkedinfo-i.md#connstate)

**系统能力：** SystemCapability.Communication.WiFi.STA

## frequency

```TypeScript
frequency: number
```

Wi-Fi接入点的频率，单位：MHz。

**类型：** number

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [frequency](arkts-connectivity-wifimanager-wifilinkedinfo-i.md#frequency)

**系统能力：** SystemCapability.Communication.WiFi.STA

## ipAddress

```TypeScript
ipAddress: number
```

Wi-Fi连接的IP地址。

**类型：** number

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [ipAddress](arkts-connectivity-wifimanager-wifilinkedinfo-i.md#ipaddress)

**系统能力：** SystemCapability.Communication.WiFi.STA

## isHidden

```TypeScript
isHidden: boolean
```

Wi-Fi接入点是否是隐藏网络。true:是隐藏网络，false:不是隐藏网络。

**类型：** boolean

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [isHidden](arkts-connectivity-wifimanager-wifilinkedinfo-i.md#ishidden)

**系统能力：** SystemCapability.Communication.WiFi.STA

## isRestricted

```TypeScript
isRestricted: boolean
```

Wi-Fi接入点是否限制数据量。true: 限制，false:不限制。

**类型：** boolean

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [isRestricted](arkts-connectivity-wifimanager-wifilinkedinfo-i.md#isrestricted)

**系统能力：** SystemCapability.Communication.WiFi.STA

## linkSpeed

```TypeScript
linkSpeed: number
```

Wi-Fi接入点的速度，单位Mbps。

**类型：** number

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [linkSpeed](arkts-connectivity-wifimanager-wifilinkedinfo-i.md#linkspeed)

**系统能力：** SystemCapability.Communication.WiFi.STA

## macAddress

```TypeScript
macAddress: string
```

设备的MAC地址。

**类型：** string

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [macAddress](arkts-connectivity-wifimanager-wifilinkedinfo-i.md#macaddress)

**系统能力：** SystemCapability.Communication.WiFi.STA

## rssi

```TypeScript
rssi: number
```

热点的信号强度(dBm)。

**类型：** number

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [rssi](arkts-connectivity-wifimanager-wifilinkedinfo-i.md#rssi)

**系统能力：** SystemCapability.Communication.WiFi.STA

## ssid

```TypeScript
ssid: string
```

热点的SSID，最大长度为32字节，编码格式为UTF-8。

**类型：** string

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [ssid](arkts-connectivity-wifimanager-wifilinkedinfo-i.md#ssid)

**系统能力：** SystemCapability.Communication.WiFi.STA
