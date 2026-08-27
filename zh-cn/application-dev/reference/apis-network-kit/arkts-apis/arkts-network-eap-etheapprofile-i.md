# EthEapProfile

可扩展身份验证协议配置信息。

**起始版本：** 20

**系统能力：** SystemCapability.Communication.NetManager.Eap

## 导入模块

```TypeScript
import { eap } from '@kit.NetworkKit';
```

## altSubjectMatch

```TypeScript
altSubjectMatch: string
```

替代主题匹配。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.Communication.NetManager.Eap

## anonymousIdentity

```TypeScript
anonymousIdentity: string
```

匿名身份。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.Communication.NetManager.Eap

## caCertAliases

```TypeScript
caCertAliases: string
```

CA证书别名。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.Communication.NetManager.Eap

## caPath

```TypeScript
caPath: string
```

CA证书路径。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.Communication.NetManager.Eap

## certEntry

```TypeScript
certEntry: Uint8Array
```

CA证书内容。

**类型：** Uint8Array

**起始版本：** 20

**系统能力：** SystemCapability.Communication.NetManager.Eap

## certPassword

```TypeScript
certPassword: string
```

CA证书密码。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.Communication.NetManager.Eap

## clientCertAliases

```TypeScript
clientCertAliases: string
```

客户端证书别名。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.Communication.NetManager.Eap

## domainSuffixMatch

```TypeScript
domainSuffixMatch: string
```

域后缀匹配。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.Communication.NetManager.Eap

## eapMethod

```TypeScript
eapMethod: EapMethod
```

AP认证方式。

**类型：** EapMethod

**起始版本：** 20

**系统能力：** SystemCapability.Communication.NetManager.Eap

## eapSubId

```TypeScript
eapSubId: number
```

SIM卡的子ID。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.Communication.NetManager.Eap

## identity

```TypeScript
identity: string
```

身份信息。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.Communication.NetManager.Eap

## password

```TypeScript
password: string
```

Password

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.Communication.NetManager.Eap

## phase2Method

```TypeScript
phase2Method: Phase2Method
```

第二阶段认证方式。

**类型：** Phase2Method

**起始版本：** 20

**系统能力：** SystemCapability.Communication.NetManager.Eap

## plmn

```TypeScript
plmn: string
```

公共陆地移动网的直通凭证提供商。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.Communication.NetManager.Eap

## realm

```TypeScript
realm: string
```

通行证凭证的领域。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.Communication.NetManager.Eap
