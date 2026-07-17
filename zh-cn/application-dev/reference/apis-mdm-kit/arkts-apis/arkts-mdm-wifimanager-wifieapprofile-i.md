# WifiEapProfile

可扩展身份验证协议配置信息。

**起始版本：** 12

<!--Device-wifiManager-interface WifiEapProfile--><!--Device-wifiManager-interface WifiEapProfile-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { wifiManager } from '@kit.MDMKit';
```

## altSubjectMatch

```TypeScript
altSubjectMatch: string
```

替代主题匹配。证书验证中，除了检查证书主域名，还检查证书的主题备用名称是否匹配。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WifiEapProfile-altSubjectMatch: string--><!--Device-WifiEapProfile-altSubjectMatch: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## anonymousIdentity

```TypeScript
anonymousIdentity: string
```

匿名身份。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WifiEapProfile-anonymousIdentity: string--><!--Device-WifiEapProfile-anonymousIdentity: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## caCertAliases

```TypeScript
caCertAliases: string
```

CA 证书别名。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WifiEapProfile-caCertAliases: string--><!--Device-WifiEapProfile-caCertAliases: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## caPath

```TypeScript
caPath: string
```

CA 证书路径。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WifiEapProfile-caPath: string--><!--Device-WifiEapProfile-caPath: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## certEntry

```TypeScript
certEntry: Uint8Array
```

客户端证书内容。当eapMethod为EAP_TLS时，如果该字段为空，则客户端证书别名不能为空。

**类型：** Uint8Array

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WifiEapProfile-certEntry: Uint8Array--><!--Device-WifiEapProfile-certEntry: Uint8Array-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## certPassword

```TypeScript
certPassword: string
```

CA证书密码。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WifiEapProfile-certPassword: string--><!--Device-WifiEapProfile-certPassword: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## clientCertAliases

```TypeScript
clientCertAliases: string
```

客户端证书别名。当客户端证书内容为空时，客户端证书需先调用证书管理接口安装后传入别名。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WifiEapProfile-clientCertAliases: string--><!--Device-WifiEapProfile-clientCertAliases: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## domainSuffixMatch

```TypeScript
domainSuffixMatch: string
```

域后缀匹配。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WifiEapProfile-domainSuffixMatch: string--><!--Device-WifiEapProfile-domainSuffixMatch: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## eapMethod

```TypeScript
eapMethod: EapMethod
```

EAP认证方式。

**类型：** EapMethod

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WifiEapProfile-eapMethod: EapMethod--><!--Device-WifiEapProfile-eapMethod: EapMethod-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## eapSubId

```TypeScript
eapSubId: number
```

SIM卡的子ID。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WifiEapProfile-eapSubId: number--><!--Device-WifiEapProfile-eapSubId: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## identity

```TypeScript
identity: string
```

身份信息。当eapMethod为TLS时，该字段不能为空。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WifiEapProfile-identity: string--><!--Device-WifiEapProfile-identity: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## password

```TypeScript
password: string
```

密码。当eapMethod为EAP_PEAP或EAP_PWD时，该字段不能为空串，最大长度为128字节。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WifiEapProfile-password: string--><!--Device-WifiEapProfile-password: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## phase2Method

```TypeScript
phase2Method: Phase2Method
```

第二阶段认证方式。只有eapMethod为EAP_PEAP或EAP_TTLS时需要填写。

**类型：** Phase2Method

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WifiEapProfile-phase2Method: Phase2Method--><!--Device-WifiEapProfile-phase2Method: Phase2Method-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## plmn

```TypeScript
plmn: string
```

凭证提供商。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WifiEapProfile-plmn: string--><!--Device-WifiEapProfile-plmn: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## realm

```TypeScript
realm: string
```

通行证凭证的领域。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WifiEapProfile-realm: string--><!--Device-WifiEapProfile-realm: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

