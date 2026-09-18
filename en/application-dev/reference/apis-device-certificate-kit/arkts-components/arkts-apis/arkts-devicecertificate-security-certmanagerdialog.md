# @ohos.security.certManagerDialog

The **certificateManagerDialog** module provides APIs for opening the certificate management pages, on which you can view and manage certificates (install, uninstall, and authorize certificates).

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.CertificateManagerDialog

## Modules to Import

```TypeScript
import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [openAuthorizeDialog](arkts-devicecertificate-certificatemanagerdialog-openauthorizedialog-f.md) | Opens the authorization page of the certificate management dialog box to grant a credential to the application. After the API is successfully called, the app can use the URI of the authorization certificate returned by the API to sign, verify the signature, and query details. This API uses a promise to return the result. |
| [openAuthorizeDialog](arkts-devicecertificate-certificatemanagerdialog-openauthorizedialog-f.md) | Opens the Certificate Credential Authorization page of the Certificate Management dialog box. On the page that is displayed, you can authorize the application to use certificate credentials. After the API is called successfully, the app can use the URI of the authorization certificate returned by the API to sign, verify the signature, and query details. The types of certificates that can be authorized include application certificate credentials, user certificate credentials, and USB Key certificate credentials. Using Promise Asynchronous Callbacks. |
| [openCertificateDetailDialog](arkts-devicecertificate-certificatemanagerdialog-opencertificatedetaildialog-f.md) | Opens the Certificate Management dialog box to display the certificate details. After the interface is invoked successfully, detailed information about the certificate, such as the basic information, validity period, issuer, and user, is displayed. Use Promise asynchronous callback. |
| [openCertificateManagerDialog](arkts-devicecertificate-certificatemanagerdialog-opencertificatemanagerdialog-f.md) | Opens the certificate management dialog box and displays the page of the specified type. After the interface is invoked successfully, you can view, install, and uninstall the certificate in the dialog box that is displayed. This API uses a promise to return the result. |
| [openInstallCertificateDialog](arkts-devicecertificate-certificatemanagerdialog-openinstallcertificatedialog-f.md) | Opens the Certificate Management Install Certificate dialog box. After the certificate is successfully installed, the unique identifier of the certificate is returned. Applications can use the identifier to use the certificate. Use Promise asynchronous callback. |
| [openUkeyAuthDialog](arkts-devicecertificate-certificatemanagerdialog-openukeyauthdialog-f.md) | Opens the PIN authentication dialog box of the USB Key credential. On the displayed page, the user can enter the PIN to authorize the USB credential. After the call is successful, the USB key credential will be unlocked. The app can use the credential to perform operations such as signing and encryption. This API uses a promise to return the result. |
| [openUninstallCertificateDialog](arkts-devicecertificate-certificatemanagerdialog-openuninstallcertificatedialog-f.md) | Open the Certificate Management Uninstall Certificate dialog. The corresponding page is displayed. Use Promise asynchronous callbacks. |
| [supportsCACertDialog](arkts-devicecertificate-certificatemanagerdialog-supportscacertdialog-f.md) | Check whether the device supports the [openCertificateDetailDialog](arkts-devicecertificate-certificatemanagerdialog-opencertificatedetaildialog-f.md), [openInstallCertificateDialog](arkts-devicecertificate-certificatemanagerdialog-openinstallcertificatedialog-f.md), and [openUninstallCertificateDialog](arkts-devicecertificate-certificatemanagerdialog-openuninstallcertificatedialog-f.md) interfaces to open the dialog box for managing CA certificates. |

### Interfaces

| Name | Description |
| --- | --- |
| [AuthorizeRequest](arkts-devicecertificate-certificatemanagerdialog-authorizerequest-i.md) | Represents the authorization request information of the credentials. |
| [CertificateDialogProperty](arkts-devicecertificate-certificatemanagerdialog-certificatedialogproperty-i.md) | Defines the property of the certificate management dialog box. |
| [CertReference](arkts-devicecertificate-certificatemanagerdialog-certreference-i.md) | Represents the reference information of the credential. |
| [UkeyAuthRequest](arkts-devicecertificate-certificatemanagerdialog-ukeyauthrequest-i.md) | USB key PIN authentication request. |

### Enums

| Name | Description |
| --- | --- |
| [CertificateDialogErrorCode](arkts-devicecertificate-certificatemanagerdialog-certificatedialogerrorcode-e.md) | Enumerates the error codes reported when the certificate management dialog box APIs are called. |
| [CertificateDialogPageType](arkts-devicecertificate-certificatemanagerdialog-certificatedialogpagetype-e.md) | Enumerates the page types of the certificate management dialog box. |
| [CertificateScope](arkts-devicecertificate-certificatemanagerdialog-certificatescope-e.md) | Defines the usage scope of the certificate to be installed. |
| [CertificateType](arkts-devicecertificate-certificatemanagerdialog-certificatetype-e.md) | Enumerates the types of the certificate to be installed. |
