# CertAbstract

表示证书简要信息。

**起始版本：** 11

<!--Device-certificateManager-export interface CertAbstract--><!--Device-certificateManager-export interface CertAbstract-End-->

**系统能力：** SystemCapability.Security.CertificateManager

## 导入模块

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

## certAlias

```TypeScript
certAlias: string
```

表示证书的别名，最大长度为128字节。

**类型：** string

**起始版本：** 11

<!--Device-CertAbstract-certAlias: string--><!--Device-CertAbstract-certAlias: string-End-->

**系统能力：** SystemCapability.Security.CertificateManager

## state

```TypeScript
state: boolean
```

表示证书的状态，true为启用状态、false为禁用状态。

**类型：** boolean

**起始版本：** 11

<!--Device-CertAbstract-state: boolean--><!--Device-CertAbstract-state: boolean-End-->

**系统能力：** SystemCapability.Security.CertificateManager

## subjectName

```TypeScript
subjectName: string
```

表示证书的使用者名称，最大长度为1024字节。

**类型：** string

**起始版本：** 11

<!--Device-CertAbstract-subjectName: string--><!--Device-CertAbstract-subjectName: string-End-->

**系统能力：** SystemCapability.Security.CertificateManager

## uri

```TypeScript
uri: string
```

表示证书的唯一标识符，最大长度为256字节。

**类型：** string

**起始版本：** 11

<!--Device-CertAbstract-uri: string--><!--Device-CertAbstract-uri: string-End-->

**系统能力：** SystemCapability.Security.CertificateManager

