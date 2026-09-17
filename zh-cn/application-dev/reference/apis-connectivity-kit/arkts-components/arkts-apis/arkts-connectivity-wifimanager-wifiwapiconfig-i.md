# WifiWapiConfig

WAPI(Wireless LAN Authentication and Privacy Infrastructure) 身份验证协议配置。

当用户通过WAPI身份验证协议连接无线网时，可通过以下方式配置参数或者证书进行连接。

- 方式一：通过配置证书进行连接。WifiDeviceConfig中关键字段的配置如下：  
- preSharedKey无需传参；  
- securityType设置为WIFI_SEC_TYPE_WAPI_CERT;  
- 在wapiConfig中：  
- wapiAsCert传递AS证书的文本内容。  
- wapiUserCert传递用户证书的文本内容。  
- 方式二：通过配置preSharedKey进行连接。WifiDeviceConfig中关键字段的配置如下：  
- preSharedKey传参为路由器上设置的密码；  
- securityType设置为WIFI_SEC_TYPE_WAPI_PSK。

**起始版本：** 12

**系统能力：** SystemCapability.Communication.WiFi.STA

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## wapiAsCert

```TypeScript
wapiAsCert: string
```

AS证书(Authentication Server Certificate，认证服务器证书)。

**类型：** string

**起始版本：** 12

**系统能力：** SystemCapability.Communication.WiFi.STA

## wapiPskType

```TypeScript
wapiPskType: WapiPskType
```

加密类型。

**类型：** [WapiPskType](arkts-connectivity-wifimanager-wapipsktype-e.md)

**起始版本：** 12

**系统能力：** SystemCapability.Communication.WiFi.STA

## wapiUserCert

```TypeScript
wapiUserCert: string
```

用户证书。

**类型：** string

**起始版本：** 12

**系统能力：** SystemCapability.Communication.WiFi.STA
