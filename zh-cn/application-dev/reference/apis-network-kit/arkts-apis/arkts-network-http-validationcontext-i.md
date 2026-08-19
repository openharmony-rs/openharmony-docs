# ValidationContext

[ValidationCallback](arkts-network-http-validationcallback-t.md)的验证上下文

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

此请求的主机

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ValidationContext-host: string--><!--Device-ValidationContext-host: string-End-->

**系统能力：** SystemCapability.Communication.NetStack

## ip

```TypeScript
ip: string
```

此请求连接到的真实IP

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ValidationContext-ip: string--><!--Device-ValidationContext-ip: string-End-->

**系统能力：** SystemCapability.Communication.NetStack

## pemCerts

```TypeScript
pemCerts: string[]
```

证书的PEM格式的原始数据

**类型：** string[]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ValidationContext-pemCerts: string[]--><!--Device-ValidationContext-pemCerts: string[]-End-->

**系统能力：** SystemCapability.Communication.NetStack

## x509Certs

```TypeScript
x509Certs: X509Cert[]
```

X509证书链

**类型：** X509Cert[]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ValidationContext-x509Certs: X509Cert[]--><!--Device-ValidationContext-x509Certs: X509Cert[]-End-->

**系统能力：** SystemCapability.Communication.NetStack

