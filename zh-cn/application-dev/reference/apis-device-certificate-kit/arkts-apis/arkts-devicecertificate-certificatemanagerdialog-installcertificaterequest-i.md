# InstallCertificateRequest

```TypeScript
export interface InstallCertificateRequest
```

安装证书对话框请求参数。

**起始版本：** 26.1.0

<!--Device-certificateManagerDialog-export interface InstallCertificateRequest--><!--Device-certificateManagerDialog-export interface InstallCertificateRequest-End-->

**系统能力：** SystemCapability.Security.CertificateManagerDialog

## 导入模块

```TypeScript
import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
```

## cert

```TypeScript
cert: Uint8Array
```

证书数据。大小不能超过8KB。<br>certType为CA_CERT时，证书数据必须为PEM或DER格式。<br>certType为CREDENTIAL_USER或CREDENTIAL_SYSTEM时，必须为P12编码格式。

**类型：** Uint8Array

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InstallCertificateRequest-cert: Uint8Array--><!--Device-InstallCertificateRequest-cert: Uint8Array-End-->

**系统能力：** SystemCapability.Security.CertificateManagerDialog

## certScope

```TypeScript
certScope: CertificateScope
```

待安装证书的使用范围。**当前用户**和**NOT_Specific**目前支持。

**类型：** [CertificateScope](arkts-devicecertificate-certificatemanagerdialog-certificatescope-e.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InstallCertificateRequest-certScope: CertificateScope--><!--Device-InstallCertificateRequest-certScope: CertificateScope-End-->

**系统能力：** SystemCapability.Security.CertificateManagerDialog

## certType

```TypeScript
certType: CertificateType
```

安装的证书类型。目前支持**CA_CERT**、**CREDENTIAL_USER**和**CREDENTIAL_SYSTEM**。

**类型：** [CertificateType](arkts-devicecertificate-certificatemanagerdialog-certificatetype-e.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InstallCertificateRequest-certType: CertificateType--><!--Device-InstallCertificateRequest-certType: CertificateType-End-->

**系统能力：** SystemCapability.Security.CertificateManagerDialog

## keystorePwd

```TypeScript
keystorePwd?: string
```

密钥库文件的密码。该参数仅当certType取值为CREDENTIAL_USER或CREDENTIAL_SYSTEM时有效，如果指定了keystorePwd参数，则对话框中无需用户输入密码。最大长度为128。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InstallCertificateRequest-keystorePwd?: string--><!--Device-InstallCertificateRequest-keystorePwd?: string-End-->

**系统能力：** SystemCapability.Security.CertificateManagerDialog
