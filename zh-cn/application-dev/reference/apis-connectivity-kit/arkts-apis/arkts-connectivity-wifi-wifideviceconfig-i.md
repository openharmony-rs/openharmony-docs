# WifiDeviceConfig

WLAN设备配置信息。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [WifiDeviceConfig](arkts-connectivity-wifimanager-wifideviceconfig-i.md)

<!--Device-wifi-interface WifiDeviceConfig--><!--Device-wifi-interface WifiDeviceConfig-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
import { wifiext } from '@kit.ConnectivityKit';
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## bssid

```TypeScript
bssid: string
```

WLAN BSSID(MAC)：长度为6

**类型：** string

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [bssid](arkts-connectivity-wifimanager-wifideviceconfig-i.md#bssid)

<!--Device-WifiDeviceConfig-bssid: string--><!--Device-WifiDeviceConfig-bssid: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## isHiddenSsid

```TypeScript
isHiddenSsid: boolean
```

是否隐藏SSID，false(默认):不隐藏

**类型：** boolean

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [isHiddenSsid](arkts-connectivity-wifimanager-wifideviceconfig-i.md#ishiddenssid)

<!--Device-WifiDeviceConfig-isHiddenSsid: boolean--><!--Device-WifiDeviceConfig-isHiddenSsid: boolean-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## preSharedKey

```TypeScript
preSharedKey: string
```

WLAN密钥：最大长度为64

**类型：** string

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [preSharedKey](arkts-connectivity-wifimanager-wifideviceconfig-i.md#presharedkey)

<!--Device-WifiDeviceConfig-preSharedKey: string--><!--Device-WifiDeviceConfig-preSharedKey: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## securityType

```TypeScript
securityType: WifiSecurityType
```

加密类型：参考WifiSecurityType的定义

**类型：** WifiSecurityType

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [securityType](arkts-connectivity-wifimanager-wifideviceconfig-i.md#securitytype)

<!--Device-WifiDeviceConfig-securityType: WifiSecurityType--><!--Device-WifiDeviceConfig-securityType: WifiSecurityType-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## ssid

```TypeScript
ssid: string
```

WLAN SSID：最大长度为32

**类型：** string

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [ssid](arkts-connectivity-wifimanager-wifideviceconfig-i.md#ssid)

<!--Device-WifiDeviceConfig-ssid: string--><!--Device-WifiDeviceConfig-ssid: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

