# WifiDeviceConfig

WLAN设备配置信息。

**起始版本：** 23

<!--Device-wifiManager-interface WifiDeviceConfig--><!--Device-wifiManager-interface WifiDeviceConfig-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## bssid

```TypeScript
bssid?: string
```

WLAN BSSID（MAC）：长度为6。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-WifiDeviceConfig-bssid?: string--><!--Device-WifiDeviceConfig-bssid?: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## bssidType

```TypeScript
bssidType?: DeviceAddressType
```

WLAN BSSID类型。

**类型：** [DeviceAddressType](arkts-connectivity-wifimanager-deviceaddresstype-e.md)

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-WifiDeviceConfig-bssidType?: DeviceAddressType--><!--Device-WifiDeviceConfig-bssidType?: DeviceAddressType-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## eapConfig

```TypeScript
eapConfig?: WifiEapConfig
```

EAP配置信息。

**类型：** [WifiEapConfig](arkts-connectivity-wifimanager-wifieapconfig-i.md)

**起始版本：** 23

<!--Device-WifiDeviceConfig-eapConfig?: WifiEapConfig--><!--Device-WifiDeviceConfig-eapConfig?: WifiEapConfig-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## isHiddenSsid

```TypeScript
isHiddenSsid?: boolean
```

是否隐藏SSID，false（默认）：不隐藏

**类型：** boolean

**起始版本：** 23

<!--Device-WifiDeviceConfig-isHiddenSsid?: boolean--><!--Device-WifiDeviceConfig-isHiddenSsid?: boolean-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## netId

```TypeScript
netId?: int
```

分配的networkId

**类型：** int

**起始版本：** 23

<!--Device-WifiDeviceConfig-netId?: int--><!--Device-WifiDeviceConfig-netId?: int-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## preSharedKey

```TypeScript
preSharedKey: string
```

WLAN密钥：最大长度为64。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-WifiDeviceConfig-preSharedKey: string--><!--Device-WifiDeviceConfig-preSharedKey: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## securityType

```TypeScript
securityType: WifiSecurityType
```

加密类型：参考WifiSecurityType的定义

**类型：** WifiSecurityType

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-WifiDeviceConfig-securityType: WifiSecurityType--><!--Device-WifiDeviceConfig-securityType: WifiSecurityType-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## showNoInternetDialog

```TypeScript
showNoInternetDialog?: boolean
```

首次网络探测检测到无网络时是否显示对话框。 如果为false，默认网络绑定到蜂窝网络，不显示对话框。 如果为true，将显示无网络对话框，提示用户选择默认网络绑定。 默认值：true。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WifiDeviceConfig-showNoInternetDialog?: boolean--><!--Device-WifiDeviceConfig-showNoInternetDialog?: boolean-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## ssid

```TypeScript
ssid: string
```

WLAN SSID：最大长度为32。

**类型：** string

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-WifiDeviceConfig-ssid: string--><!--Device-WifiDeviceConfig-ssid: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## wapiConfig

```TypeScript
wapiConfig?: WifiWapiConfig
```

WAPI配置信息。

**类型：** [WifiWapiConfig](arkts-connectivity-wifimanager-wifiwapiconfig-i.md)

**起始版本：** 23

<!--Device-WifiDeviceConfig-wapiConfig?: WifiWapiConfig--><!--Device-WifiDeviceConfig-wapiConfig?: WifiWapiConfig-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

