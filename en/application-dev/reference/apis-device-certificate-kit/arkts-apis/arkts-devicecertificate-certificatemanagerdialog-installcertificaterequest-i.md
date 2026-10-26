# InstallCertificateRequest

```TypeScript
export interface InstallCertificateRequest
```

The request parameter of the install certificate dialog box.

**Since:** 26.1.0

<!--Device-certificateManagerDialog-export interface InstallCertificateRequest--><!--Device-certificateManagerDialog-export interface InstallCertificateRequest-End-->

**System capability:** SystemCapability.Security.CertificateManagerDialog

## Modules to Import

```TypeScript
import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
```

## cert

```TypeScript
cert: Uint8Array
```

Certificate data. The size cannot exceed 8 KB. <br>When certificateType is set to CA_CERT, the certificate data must be in PEM or DER format. <br>When certType is set to CREDENTIAL_USER or CREDENTIAL_SYSTEM, the encoding format must be P12.

**Type:** Uint8Array

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-InstallCertificateRequest-cert: Uint8Array--><!--Device-InstallCertificateRequest-cert: Uint8Array-End-->

**System capability:** SystemCapability.Security.CertificateManagerDialog

## certScope

```TypeScript
certScope: CertificateScope
```

Usage scope of the certificate to install. **CURRENT_USER** and **NOT_SPECIFIED** are currently supported.

**Type:** [CertificateScope](arkts-devicecertificate-certificatemanagerdialog-certificatescope-e.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-InstallCertificateRequest-certScope: CertificateScope--><!--Device-InstallCertificateRequest-certScope: CertificateScope-End-->

**System capability:** SystemCapability.Security.CertificateManagerDialog

## certType

```TypeScript
certType: CertificateType
```

Type of the certificate to install. **CA_CERT**, **CREDENTIAL_USER**, and **CREDENTIAL_SYSTEM** are currently supported.

**Type:** [CertificateType](arkts-devicecertificate-certificatemanagerdialog-certificatetype-e.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-InstallCertificateRequest-certType: CertificateType--><!--Device-InstallCertificateRequest-certType: CertificateType-End-->

**System capability:** SystemCapability.Security.CertificateManagerDialog

## keystorePwd

```TypeScript
keystorePwd?: string
```

Password of the keystore file. This parameter is valid only when certType is set to CREDENTIAL_USER or CREDENTIAL_SYSTEM. If keystorePwd is specified, the user does not need to enter the password in the dialog box. The maximum length is 128.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-InstallCertificateRequest-keystorePwd?: string--><!--Device-InstallCertificateRequest-keystorePwd?: string-End-->

**System capability:** SystemCapability.Security.CertificateManagerDialog
