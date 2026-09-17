# WifiEapConfig

可扩展身份验证协议配置信息。

- WifiEapConfig是一个用于配置Wi-Fi网络EAP认证的类型。  
- 包含EAP认证方式、第二阶段认证方式、身份信息、密码、证书等配置项。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.WiFi.STA

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## altSubjectMatch

```TypeScript
altSubjectMatch: string
```

替代主题匹配。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.Communication.WiFi.STA

## anonymousIdentity

```TypeScript
anonymousIdentity: string
```

匿名身份。暂未使用。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.Communication.WiFi.STA

## caCertAlias

```TypeScript
caCertAlias: string
```

CA证书别名。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.Communication.WiFi.STA

## caPath

```TypeScript
caPath: string
```

CA证书路径。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.Communication.WiFi.STA

## certEntry

```TypeScript
certEntry: Uint8Array
```

CA证书内容。当eapMethod为EAP_TLS时，如果该字段为空，则clientCertAlias不能为空。

**类型：** Uint8Array

**起始版本：** 10

**系统能力：** SystemCapability.Communication.WiFi.STA

## certPassword

```TypeScript
certPassword: string
```

CA证书密码，最大长度为128字节。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.Communication.WiFi.STA

## clientCertAlias

```TypeScript
clientCertAlias: string
```

客户端证书别名。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.Communication.WiFi.STA

## domainSuffixMatch

```TypeScript
domainSuffixMatch: string
```

域后缀匹配。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.Communication.WiFi.STA

## eapMethod

```TypeScript
eapMethod: EapMethod
```

EAP认证方式。

**类型：** [EapMethod](arkts-connectivity-wifimanager-eapmethod-e.md)

**起始版本：** 10

**系统能力：** SystemCapability.Communication.WiFi.STA

## eapSubId

```TypeScript
eapSubId: number
```

SIM卡的子ID。

**类型：** number

**起始版本：** 10

**系统能力：** SystemCapability.Communication.WiFi.STA

## identity

```TypeScript
identity: string
```

身份信息。当eapMethod为EAP_PEAP、EAP_TLS或EAP_PWD时，该字段不能为空串。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.Communication.WiFi.STA

## password

```TypeScript
password: string
```

密码。当eapMethod为EAP_PEAP或EAP_PWD时，该字段不能为空串，最大长度为128字节。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.Communication.WiFi.STA

## phase2Method

```TypeScript
phase2Method: Phase2Method
```

第二阶段认证方式。只有eapMethod为EAP_PEAP或EAP_TTLS时需要填写。

**类型：** [Phase2Method](arkts-connectivity-wifimanager-phase2method-e.md)

**起始版本：** 10

**系统能力：** SystemCapability.Communication.WiFi.STA

## plmn

```TypeScript
plmn: string
```

公共陆地移动网的直通凭证提供商。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.Communication.WiFi.STA

## realm

```TypeScript
realm: string
```

通行证凭证的领域。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.Communication.WiFi.STA
