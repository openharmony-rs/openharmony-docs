# AuthorizeRequest

Represents the authorization request information of the credentials.

**Since:** 22

**System capability:** SystemCapability.Security.CertificateManagerDialog

## Modules to Import

```TypeScript
import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
```

## certPurpose

```TypeScript
certPurpose?: certificateManager.CertificatePurpose
```

Certificate usage. If the **certTypes** parameter contains the **CertificateType.CREDENTIAL_UKEY** type, the **certPurpose** parameter takes effect , indicating that the certificate credentials of the USB key are filtered based on the specified certificate usage.

**Type:** [certificateManager.CertificatePurpose](arkts-devicecertificate-certificatemanager-certificatepurpose-e.md)

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.CertificateManagerDialog

## certTypes

```TypeScript
certTypes: Array<CertificateType>
```

List of certificate types.

**Type:** Array&lt;[CertificateType](arkts-devicecertificate-certificatemanagerdialog-certificatetype-e.md)&gt;

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.CertificateManagerDialog

## issuers

```TypeScript
issuers?: Array<Uint8Array>
```

Indicates the certificate issuer, which is encoded in DER format. This parameter is used to filter the list of certificates that can be selected by users in the Authorization dialog box. Only the certificates that match the certificate issuer are displayed.

**Type:** Array&lt;Uint8Array&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.CertificateManagerDialog

## keyAlgIDs

```TypeScript
keyAlgIDs?: Array<string>
```

Indicates the algorithm type of the public key of the certificate. It is used to filter the list of certificates that can be selected in the authorization dialog box. Only the certificates that match the public key algorithm are displayed. The value can only be RSA, EC, or ECDSA (case sensitive). If this parameter is not specified, certificates are not filtered by algorithm type. If the keyAlgIDs array contains an unsupported algorithm type, the keyAlgIDs filter does not take effect. The maximum length is 20.

**Type:** Array&lt;string&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.CertificateManagerDialog

## uri

```TypeScript
uri?: string
```

This URI is displayed in the authorization dialog box and is used to provide the user with more context about requesting authorization to use certificate credentials.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.CertificateManagerDialog
