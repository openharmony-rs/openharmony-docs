# UkeyAuthDialogInfo

```TypeScript
export interface UkeyAuthDialogInfo
```

Information about the Ukey authentication dialog box to be opened.

**Since:** 26.0.1

<!--Device-certificateManagerDialog-export interface UkeyAuthDialogInfo--><!--Device-certificateManagerDialog-export interface UkeyAuthDialogInfo-End-->

**System capability:** SystemCapability.Security.CertificateManagerDialog

## Modules to Import

```TypeScript
import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
```

## abilityName

```TypeScript
abilityName: string
```

Ability name of the Ukey authentication dialog box. The maximum length is 256 bytes and cannot be empty.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UkeyAuthDialogInfo-abilityName: string--><!--Device-UkeyAuthDialogInfo-abilityName: string-End-->

**System capability:** SystemCapability.Security.CertificateManagerDialog

## abilityType

```TypeScript
abilityType: AbilityType
```

Ability type of the Ukey authentication dialog box.

**Type:** [AbilityType](arkts-devicecertificate-certificatemanagerdialog-abilitytype-e.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UkeyAuthDialogInfo-abilityType: AbilityType--><!--Device-UkeyAuthDialogInfo-abilityType: AbilityType-End-->

**System capability:** SystemCapability.Security.CertificateManagerDialog
