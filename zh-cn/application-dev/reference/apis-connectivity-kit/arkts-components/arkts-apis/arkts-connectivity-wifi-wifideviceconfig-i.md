# WifiDeviceConfig

Wi-Fi配置信息。

> **说明：** 
> 
> 从API version 6开始支持，从API version 9开始废弃。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [WifiDeviceConfig](arkts-connectivity-wifimanager-wifideviceconfig-i.md)

**系统能力：** SystemCapability.Communication.WiFi.STA

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## bssid

```TypeScript
bssid: string
```

热点的BSSID，例如：00:11:22:33:44:55。

**类型：** string

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [bssid](arkts-connectivity-wifimanager-wifideviceconfig-i.md#bssid)

**系统能力：** SystemCapability.Communication.WiFi.STA

## isHiddenSsid

```TypeScript
isHiddenSsid: boolean
```

是否是隐藏网络。true:是隐藏网络，false:不是隐藏网络。

**类型：** boolean

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [isHiddenSsid](arkts-connectivity-wifimanager-wifideviceconfig-i.md#ishiddenssid)

**系统能力：** SystemCapability.Communication.WiFi.STA

## preSharedKey

```TypeScript
preSharedKey: string
```

热点的密钥，最大长度为64字节。

**类型：** string

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [preSharedKey](arkts-connectivity-wifimanager-wifideviceconfig-i.md#presharedkey)

**系统能力：** SystemCapability.Communication.WiFi.STA

## securityType

```TypeScript
securityType: WifiSecurityType
```

加密类型。

**类型：** [WifiSecurityType](arkts-connectivity-wifi-wifisecuritytype-e.md)

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [securityType](arkts-connectivity-wifimanager-wifideviceconfig-i.md#securitytype)

**系统能力：** SystemCapability.Communication.WiFi.STA

## ssid

```TypeScript
ssid: string
```

热点的SSID，最大长度为32字节，编码格式为UTF-8。

**类型：** string

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [ssid](arkts-connectivity-wifimanager-wifideviceconfig-i.md#ssid)

**系统能力：** SystemCapability.Communication.WiFi.STA
