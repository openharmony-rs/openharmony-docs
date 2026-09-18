# CertBlob

Indicates the certificate file data.

**Since:** 26.0.0

**System capability:** SystemCapability.Security.CertificateManager

## Modules to Import

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

## certData

```TypeScript
certData: Uint8Array
```

Certificate file data. When certFormat is transferred to PEM_DER, the maximum length is 8 KB. When certFormat is set to P7B, the maximum length is 300 KB.

**Type:** Uint8Array

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.CertificateManager

## certFormat

```TypeScript
certFormat? : CertFileFormat
```

Indicates the certificate file format. Default value: PEM_DER.

**Type:** [CertFileFormat](arkts-devicecertificate-certificatemanager-certfileformat-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.CertificateManager

## certScope

```TypeScript
certScope? : CertScope
```

Indicates the storage location of the user CA certificate. Default value: Current_USER.

**Type:** [CertScope](arkts-devicecertificate-certificatemanager-certscope-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.CertificateManager
