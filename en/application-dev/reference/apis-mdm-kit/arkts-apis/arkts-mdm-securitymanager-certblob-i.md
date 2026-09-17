# CertBlob

Represents the certificate information.

**Since:** 12

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

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## inData

```TypeScript
inData: Uint8Array
```

Binary content of the certificate.

**Type:** Uint8Array

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
