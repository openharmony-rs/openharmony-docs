# WifiEapConfig

WLAN EAP配置。

**起始版本：** 23

<!--Device-wifiManager-interface WifiEapConfig--><!--Device-wifiManager-interface WifiEapConfig-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## altSubjectMatch

```TypeScript
altSubjectMatch: string
```

备用主题匹配

**类型：** string

**起始版本：** 23

<!--Device-WifiEapConfig-altSubjectMatch: string--><!--Device-WifiEapConfig-altSubjectMatch: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## anonymousIdentity

```TypeScript
anonymousIdentity: string
```

匿名身份信息

**类型：** string

**起始版本：** 23

<!--Device-WifiEapConfig-anonymousIdentity: string--><!--Device-WifiEapConfig-anonymousIdentity: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## caCertAlias

```TypeScript
caCertAlias: string
```

CA证书别名

**类型：** string

**起始版本：** 23

<!--Device-WifiEapConfig-caCertAlias: string--><!--Device-WifiEapConfig-caCertAlias: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## caPath

```TypeScript
caPath: string
```

CA证书路径

**类型：** string

**起始版本：** 23

<!--Device-WifiEapConfig-caPath: string--><!--Device-WifiEapConfig-caPath: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## certEntry

```TypeScript
certEntry: Uint8Array
```

用户证书内容

**类型：** Uint8Array

**起始版本：** 23

<!--Device-WifiEapConfig-certEntry: Uint8Array--><!--Device-WifiEapConfig-certEntry: Uint8Array-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## certPassword

```TypeScript
certPassword: string
```

用户证书密码

**类型：** string

**起始版本：** 23

<!--Device-WifiEapConfig-certPassword: string--><!--Device-WifiEapConfig-certPassword: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## clientCertAlias

```TypeScript
clientCertAlias: string
```

客户端证书别名

**类型：** string

**起始版本：** 23

<!--Device-WifiEapConfig-clientCertAlias: string--><!--Device-WifiEapConfig-clientCertAlias: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## domainSuffixMatch

```TypeScript
domainSuffixMatch: string
```

域名后缀匹配

**类型：** string

**起始版本：** 23

<!--Device-WifiEapConfig-domainSuffixMatch: string--><!--Device-WifiEapConfig-domainSuffixMatch: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## eapMethod

```TypeScript
eapMethod: EapMethod
```

EAP认证方式

**类型：** EapMethod

**起始版本：** 23

<!--Device-WifiEapConfig-eapMethod: EapMethod--><!--Device-WifiEapConfig-eapMethod: EapMethod-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## eapSubId

```TypeScript
eapSubId: int
```

SIM卡的子ID

**类型：** int

**起始版本：** 23

<!--Device-WifiEapConfig-eapSubId: int--><!--Device-WifiEapConfig-eapSubId: int-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## identity

```TypeScript
identity: string
```

身份信息

**类型：** string

**起始版本：** 23

<!--Device-WifiEapConfig-identity: string--><!--Device-WifiEapConfig-identity: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## password

```TypeScript
password: string
```

密码

**类型：** string

**起始版本：** 23

<!--Device-WifiEapConfig-password: string--><!--Device-WifiEapConfig-password: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## phase2Method

```TypeScript
phase2Method: Phase2Method
```

Phase 2认证方式

**类型：** Phase2Method

**起始版本：** 23

<!--Device-WifiEapConfig-phase2Method: Phase2Method--><!--Device-WifiEapConfig-phase2Method: Phase2Method-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## plmn

```TypeScript
plmn: string
```

Passpoint凭据提供者的公共陆地移动网络（PLMN）

**类型：** string

**起始版本：** 23

<!--Device-WifiEapConfig-plmn: string--><!--Device-WifiEapConfig-plmn: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## realm

```TypeScript
realm: string
```

Passpoint凭据的Realm

**类型：** string

**起始版本：** 23

<!--Device-WifiEapConfig-realm: string--><!--Device-WifiEapConfig-realm: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

