# ValidationContext

```TypeScript
export interface ValidationContext
```

验证远端服务器身份时的证书上下文信息，作为[ValidationCallback](arkts-network-http-validationcallback-t.md)的参数传入。

**起始版本：** 26.0.0

<!--Device-http-export interface ValidationContext--><!--Device-http-export interface ValidationContext-End-->

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { http } from '@kit.NetworkKit';
```

## host

```TypeScript
host: string
```

本次请求的目标主机名。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ValidationContext-host: string--><!--Device-ValidationContext-host: string-End-->

**系统能力：** SystemCapability.Communication.NetStack

## ip

```TypeScript
ip: string
```

本次请求实际连接的IP地址。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ValidationContext-ip: string--><!--Device-ValidationContext-ip: string-End-->

**系统能力：** SystemCapability.Communication.NetStack

## pemCerts

```TypeScript
pemCerts: string[]
```

PEM格式的证书原始数据。

**类型：** string[]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ValidationContext-pemCerts: string[]--><!--Device-ValidationContext-pemCerts: string[]-End-->

**系统能力：** SystemCapability.Communication.NetStack

## x509Certs

```TypeScript
x509Certs: X509Cert[]
```

X509证书链。

**类型：** [X509Cert](arkts-network-http-x509cert-t.md)[]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ValidationContext-x509Certs: X509Cert[]--><!--Device-ValidationContext-x509Certs: X509Cert[]-End-->

**系统能力：** SystemCapability.Communication.NetStack
