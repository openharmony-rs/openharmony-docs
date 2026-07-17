# CertReference

表示证书凭据的引用信息。

**起始版本：** 22

<!--Device-certificateManagerDialog-export interface CertReference--><!--Device-certificateManagerDialog-export interface CertReference-End-->

**系统能力：** SystemCapability.Security.CertificateManagerDialog

## 导入模块

```TypeScript
import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
```

## certType

```TypeScript
certType: CertificateType
```

表示证书类型。

**类型：** CertificateType

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CertReference-certType: CertificateType--><!--Device-CertReference-certType: CertificateType-End-->

**系统能力：** SystemCapability.Security.CertificateManagerDialog

## keyUri

```TypeScript
keyUri: string
```

表示证书凭据的唯一标识符，长度限制256字节以内。

**类型：** string

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CertReference-keyUri: string--><!--Device-CertReference-keyUri: string-End-->

**系统能力：** SystemCapability.Security.CertificateManagerDialog

