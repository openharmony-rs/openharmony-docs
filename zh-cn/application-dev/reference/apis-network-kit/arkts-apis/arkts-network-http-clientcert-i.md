# ClientCert

客户端证书类型。

**起始版本：** 23

<!--Device-http-export interface ClientCert--><!--Device-http-export interface ClientCert-End-->

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { http } from '@kit.NetworkKit';
```

## certPath

```TypeScript
certPath: string
```

证书路径。

**类型：** string

**起始版本：** 23

<!--Device-ClientCert-certPath: string--><!--Device-ClientCert-certPath: string-End-->

**系统能力：** SystemCapability.Communication.NetStack

## certType

```TypeScript
certType?: CertType
```

证书类型，默认是PEM。

**类型：** CertType

**起始版本：** 23

<!--Device-ClientCert-certType?: CertType--><!--Device-ClientCert-certType?: CertType-End-->

**系统能力：** SystemCapability.Communication.NetStack

## keyPassword

```TypeScript
keyPassword?: string
```

证书密钥的密码。默认值为空字符串。

**类型：** string

**起始版本：** 23

<!--Device-ClientCert-keyPassword?: string--><!--Device-ClientCert-keyPassword?: string-End-->

**系统能力：** SystemCapability.Communication.NetStack

## keyPath

```TypeScript
keyPath: string
```

证书密钥的路径。

**类型：** string

**起始版本：** 23

<!--Device-ClientCert-keyPath: string--><!--Device-ClientCert-keyPath: string-End-->

**系统能力：** SystemCapability.Communication.NetStack

