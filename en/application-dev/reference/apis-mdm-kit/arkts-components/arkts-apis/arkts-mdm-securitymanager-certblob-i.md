# CertBlob

```TypeScript
export interface CertBlob
```

Represents the certificate information.

**Since:** 12

<!--Device-securityManager-export interface CertBlob--><!--Device-securityManager-export interface CertBlob-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { securityManager } from '@kit.MDMKit';
```

## alias

```TypeScript
alias: string
```

Certificate alias. The value length must be less than 40 characters.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-CertBlob-alias: string--><!--Device-CertBlob-alias: string-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## inData

```TypeScript
inData: Uint8Array
```

Binary content of the certificate.

**Type:** Uint8Array

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-CertBlob-inData: Uint8Array--><!--Device-CertBlob-inData: Uint8Array-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
