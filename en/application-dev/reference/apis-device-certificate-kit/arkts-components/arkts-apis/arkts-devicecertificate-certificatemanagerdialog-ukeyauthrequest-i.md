# UkeyAuthRequest

```TypeScript
export interface UkeyAuthRequest
```

USB key PIN authentication request.

**Since:** 22

**System capability:** SystemCapability.Security.CertificateManagerDialog

## Modules to Import

```TypeScript
import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
```

## customData

```TypeScript
customData?: Uint8Array
```

The customized data transferred to the Ukey authentication dialog box. Generally, this field is required only when the openAuthDialogForUkeyProvider interface is invoked. The maximum length is 2048 bytes.

**Type:** Uint8Array

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.CertificateManagerDialog

## keyUri

```TypeScript
keyUri: string
```

Unique identifier of the USB Key credential. The value contains up to 256 bytes. The value of this parameter can be obtained from the CertReference returned by invoking the [openAuthorizeDialog](arkts-devicecertificate-certificatemanagerdialog-openauthorizedialog-f.md) interface.

**Type:** string

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.CertificateManagerDialog

## timeoutDuration

```TypeScript
timeoutDuration?: number
```

The timeout duration for operations in the Ukey authentication dialog box. Unit: Seconds. Default value: 300. The value must be an integer within [180,600]. Default value: 300.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.CertificateManagerDialog
