# CertBlob (System API)

Represents the certificate information.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [CertBlob](arkts-mdm-securitymanager-certblob-i.md)

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { deviceSettings } from '@kit.MDMKit';
```

## alias

```TypeScript
alias: string
```

Certificate alias. The value length must be less than 40 characters.

**Type:** string

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** alias

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**System API:** This is a system API.

## inData

```TypeScript
inData: Uint8Array
```

Binary content of the certificate.

**Type:** Uint8Array

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** inData

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**System API:** This is a system API.
