# CertificateScope

```TypeScript
export enum CertificateScope
```

Defines the usage scope of the certificate to be installed.

**Since:** 14

<!--Device-certificateManagerDialog-export enum CertificateScope--><!--Device-certificateManagerDialog-export enum CertificateScope-End-->

**System capability:** SystemCapability.Security.CertificateManagerDialog

## NOT_SPECIFIED

```TypeScript
NOT_SPECIFIED = 0
```

No user is specified.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

<!--Device-CertificateScope-NOT_SPECIFIED = 0--><!--Device-CertificateScope-NOT_SPECIFIED = 0-End-->

**System capability:** SystemCapability.Security.CertificateManagerDialog

## CURRENT_USER

```TypeScript
CURRENT_USER = 1
```

The installed certificate is accessible only to the current user.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

<!--Device-CertificateScope-CURRENT_USER = 1--><!--Device-CertificateScope-CURRENT_USER = 1-End-->

**System capability:** SystemCapability.Security.CertificateManagerDialog

## GLOBAL_USER

```TypeScript
GLOBAL_USER = 2
```

The installed certificate is accessible to all users of the device.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

<!--Device-CertificateScope-GLOBAL_USER = 2--><!--Device-CertificateScope-GLOBAL_USER = 2-End-->

**System capability:** SystemCapability.Security.CertificateManagerDialog
