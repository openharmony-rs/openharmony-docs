# WifiScanInfo

Wi-Fi热点信息。

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

热点的BSSID，例如：00:11:22:33:44:55。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.WiFi.STA

## bssidType

```TypeScript
bssidType: DeviceAddressType
```

热点的BSSID类型。

**类型：** [DeviceAddressType](arkts-connectivity-wifimanager-deviceaddresstype-e.md)

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.WiFi.STA

## capabilities

```TypeScript
capabilities: string
```

热点能力。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

## centerFrequency0

```TypeScript
centerFrequency0: number
```

热点的中心频率。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

## centerFrequency1

```TypeScript
centerFrequency1: number
```

热点的中心频率。如果热点使用两个不重叠的Wi-Fi信道，则返回两个中心频率，分别用centerFrequency0和centerFrequency1表示。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

## channelWidth

```TypeScript
channelWidth: number
```

Wi-Fi接入点的带宽，具体定义参见[WifiChannelWidth](arkts-connectivity-wifimanager-wifichannelwidth-e.md)。

**类型：** number

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

热点是否支持hiLink，true表示支持， false表示不支持。

**类型：** boolean

**起始版本：** 12

**系统能力：** SystemCapability.Communication.WiFi.STA

## rssi

```TypeScript
rssi: number
```

热点的信号强度(dBm)。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.WiFi.STA

## securityType

```TypeScript
securityType: WifiSecurityType
```

Wi-Fi加密类型。

**类型：** [WifiSecurityType](arkts-connectivity-wifimanager-wifisecuritytype-e.md)

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.WiFi.STA

## ssid

```TypeScript
ssid: string
```

热点的SSID，最大长度为32字节，编码格式为UTF-8。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.WiFi.STA

## supportedWifiCategory

```TypeScript
supportedWifiCategory: WifiCategory
```

热点支持的最高Wi-Fi级别。

**类型：** [WifiCategory](arkts-connectivity-wifimanager-wificategory-e.md)

**起始版本：** 12

**系统能力：** SystemCapability.Communication.WiFi.STA

## timestamp

```TypeScript
timestamp: number
```

时间戳。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA
