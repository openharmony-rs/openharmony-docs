# CertReference

```TypeScript
export interface CertReference
```

Represents the reference information of the credential.

**Since:** 22

<!--Device-certificateManagerDialog-export interface CertReference--><!--Device-certificateManagerDialog-export interface CertReference-End-->

**System capability:** SystemCapability.Security.CertificateManagerDialog

## Modules to Import

```TypeScript
import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
```

## certType

```TypeScript
certType: CertificateType
```

Certificate type.

**Type:** [CertificateType](arkts-devicecertificate-certificatemanagerdialog-certificatetype-e.md)

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

<!--Device-CertReference-certType: CertificateType--><!--Device-CertReference-certType: CertificateType-End-->

**System capability:** SystemCapability.Security.CertificateManagerDialog

## keyUri

```TypeScript
keyUri: string
```

Unique identifier of the credential. The value contains up to 256 bytes.

**Type:** string

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

<!--Device-CertReference-keyUri: string--><!--Device-CertReference-keyUri: string-End-->

**System capability:** SystemCapability.Security.CertificateManagerDialog
