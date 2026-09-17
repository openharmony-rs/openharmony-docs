# WifiDeviceConfig

Wi-Fi配置信息。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## bssid

```TypeScript
bssid?: string
```

热点的BSSID，例如：00:11:22:33:44:55。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.WiFi.STA

## bssidType

```TypeScript
bssidType?: DeviceAddressType
```

热点的BSSID类型。

**类型：** [DeviceAddressType](arkts-connectivity-wifimanager-deviceaddresstype-e.md)

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.WiFi.STA

## eapConfig

```TypeScript
eapConfig?: WifiEapConfig
```

可扩展身份验证协议配置。只有securityType为WIFI_SEC_TYPE_EAP时需要填写。

**类型：** [WifiEapConfig](arkts-connectivity-wifimanager-wifieapconfig-i.md)

**起始版本：** 10

**系统能力：** SystemCapability.Communication.WiFi.STA

## isHiddenSsid

```TypeScript
isHiddenSsid?: boolean
```

是否是隐藏网络。true表示是隐藏网络，false表示不是隐藏网络。

**类型：** boolean

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

## netId

```TypeScript
netId?: number
```

分配的网络ID。

**类型：** number

**起始版本：** 22

**系统能力：** SystemCapability.Communication.WiFi.STA

## preSharedKey

```TypeScript
preSharedKey: string
```

热点的密钥，最大长度为64字节。

当securityType为WIFI_SEC_TYPE_OPEN时该字段需为空串，其他加密类型不能为空串。

当securityType为WIFI_SEC_TYPE_WEP时，该字段长度只允许为5、10、13、26、16和32字节其中之一，并且当字段长度为偶数时，该字段必须为纯十六进制数字构成。

当securityType为WIFI_SEC_TYPE_SAE时，该字段最小长度为1字节。

当securityType为WIFI_SEC_TYPE_PSK时，该字段最小长度为8字节。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.WiFi.STA

## securityType

```TypeScript
securityType: WifiSecurityType
```

加密类型。

**类型：** [WifiSecurityType](arkts-connectivity-wifimanager-wifisecuritytype-e.md)

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.WiFi.STA

## showNoInternetDialog

```TypeScript
showNoInternetDialog?: boolean
```

当首次网络探测检测到无互联网连接时，是否显示提示框。若为false，默认网络绑定到蜂窝网络，不显示提示框；若为true，显示无互联网连接提示框，提示用户选择默认网络绑定。默认值为true。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

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

## wapiConfig

```TypeScript
wapiConfig?: WifiWapiConfig
```

WAPI身份验证协议配置。只有securityType为WIFI_SEC_TYPE_WAPI_CERT或WIFI_SEC_TYPE_WAPI_PSK时需要填写。

**类型：** [WifiWapiConfig](arkts-connectivity-wifimanager-wifiwapiconfig-i.md)

**起始版本：** 12

**系统能力：** SystemCapability.Communication.WiFi.STA
